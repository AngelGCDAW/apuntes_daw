# APUNTES DE JAVA

## ÍNDICE

9. [SWING GUI FORMS](#tema-09---swing-gui-forms)
   1.  [Qué es Swing.](#qué-es-swing)
   2.  [Cómo funciona.](#cómo-funciona)
       * [Jerarquía de Java Swing.](#jerarquía-de-java-swing)
   3.  [Cuadros de diálogo.](#cuadros-de-diálogo)
   4.  [Componentes, Eventos y Controladores de Eventos.](#componentes-eventos-y-controladores-de-eventos)
   5.  [Métodos comunes de estilo.](#métodos-comunes-de-estilo)

## TEMA 09 - SWING GUI FORMS

### Qué es Swing

La API Swing es un conjunto de componentes para la creación de __entornos gráficos de usuarios__.

### Cómo funciona

Todos los componentes heredan de _javax.swing.JComponent_.

* __JFrame__ será la base para la aplicación principal.
* __JDialog__ construirá los diálogos (ventanas). El resto de las clases, serán componentes simples.

#### Jerarquía de Java Swing:

![Imágen de la Jerarquía de Java Swing.](/docs/java/img/jerarquia_swing.png)

### Cuadros de diálogo

Clases __JDialog__ y __JOptionPane__ son cuadros de diálogo que muestran información o del tipo de pedir confirmación.

* __JDialog__ es modal (no se puede interactuar con el resto de ventanas)
* __JOptionPanel__ no es modal. Al cerrar la ventana principal, se cierra también este cuadro de diálogo.

Existen __diálogos__ preestablecidos, los cuales pueden tener distinta finalidad:

* Informativos
* Elección
* Mensajes de Error
* Mensajes de Advertencia
* Entrada de datos
* Etc. 

A partir de aquí tenemos una serie de controles que podemos utilizar, a continuación se mostrarán los más comunes:

#### JOptionPane

Para crear diálogos preestablecidos esta la clase __JOptionPane__. Esta clase implementa métodos (static) de la forma _showXXDialog_, donde XX va a variar de acuerdo según el tipo de dialogo que se necesite.

* Todos los diálogos son modales.
* Se puede configurar mediante parámetros: titulo, icono, mensajes, etc.

#### JOptionPane.showMessageDialog

Este método permite mostrar ventanas de diálogo que muestran un mensaje y contienen un __botón de aceptación__.

##### showMessageDialog(ventana, "Mensaje", “Titulo de ventana”, icono);

>---
> Ejemplos:
>
> 🗨 Un cuadro de diálogo de contexto general.
>
> ```
> // Mensaje plano
> JOptionPane.showMessageDialog(null, "Mensaje plano", 
> "Mensaje", JOptionPane.PLAIN_MESSAGE);
> ```
>
> ❌ Un cuadro de diálogo de error.
>
> ```
> // Mensaje de error
> JOptionPane.showMessageDialog(null, "Mensaje de error", "Error", JOptionPane.EROR_MESSAGE);
> ```
>
> 💬 Un cuadro de texto informativo.
>
> ```
> // Mensaje informativo
> JOptionPane.showMessageDialog(null, "Mensaje informativo", "Información", JOptionPane.INFORMATION_MESSAGE);
> ```
>
> ❗ Un cuadro de texto de aviso.
>
> ```
> // Mensaje de aviso
> JOptionPane.showMessageDialog(null, "Mensaje de aviso", "Aviso", JOptionPane.WARNING_MESSAGE);
> ```
>
> ❔ Un cuadro de texto de pregunta.
>
> ```
> // Mensaje de pregunta
> JOptionPane.showMessageDialog(null, "Mensaje de pregunta", "Pregunta", JOptionPane.QUESTION_MESSAGE);
> ```
> ---

#### JOptionPane.showConfirmDialog

Este método permite mostrar diálogos donde se puede __elegir entre varias opciones__ (aceptar, cancelar, si o no).

##### showConfirmDialog(ventana, “Mensaje”, “Titulo de ventana”, tipo de opción, icono);

>---
> Ejemplos:
>
> ✔ Cuadro de confirmación por defecto.
>
> ```
> // Mensaje de confirmación por defecto
> JOptionPane.showMessageDialog(null, "Aquí va el mensaje", "Ventana por defecto", JOptionPane.DEFAULT_OPTION, JOptionPane.INFORMATION_MESSAGE);
> ``` 
> 
> ❔ Cuadro de confirmación Si/No.
>
> ```
> // Mensaje confirmación si-no
> int respuesta = JOptionPane.showConfirmDialog(null, "Aqui va el mensaje", "Ventana SI-NO", JOptionPane.YES_NO_OPTION, JOptionPane.QUESTION_MESSAGE);
> String mensaje = "";
>
> if(respuesta == 0) {
>     mensaje = "Ha contestado si.";
> } else {
>     mensaje = "Ha respondido no.";
> }
>
> JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.PLAIN_MESSAGE);
> ```
>
>❓ Cuadro confirmación Si/No/Cancelar.
> 
> ```
> // Mensaje de confirmacion si-no-cancelar
> int respuesta = JOptionPane.showConfirmDialog(null, "Aqui va > el mensaje", "Ventana SI-NO-Cancelar", JOptionPane.YES_NO_CANCEL_OPTION, JOptionPane.QUESTION_MESSAGE);
> String mensaje = "";
>
> switch (respuesta) {
>     case 0 -> { mensaje = "Ha contestado si"; }
>     case 1 -> { mensaje = "Ha respondido no"; }
>     default -> { mensaje = "Ha cancelado"; }
> }
>
> JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.PLAIN_MESSAGE);
> ```
>
> 🆗 Cuadro de confirmación Aceptar/Cancelar.
>
> ```
> // Mensaje de aceptar-cancelar
> int respuesta = JOptionPane.showConfirmDialog(null, "Aqui va > el mensaje", "Ventana Aceptar-Cancelar", JOptionPane.OK_CANCEL_OPTION, JOptionPane.QUESTION_MESSAGE);
> String mensaje = "";
>
> if (respuesta == 0) {
>     mensaje = "Ha contestado aceptar";
> } else {
>     mensaje = "Ha respondido cancelar";
> }
> 
> JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.PLAIN_MESSAGE);
> ```
>---

#### JOptionPane.showOptinDialog

Este método permite mostrar diálogos con los __botones, iconos, texto, mensajes, titulo, etc__. que se desee. Se puede cambiar el __texto de los botones__. _Retorna un int_.

##### showOptionDialog(ventana, “Mensaje”, “Titulo de ventana”, tipo de opción, icono, icono especial, “titulo de botones”, boton inicial);

>---
> Ejemplo:
>
> 💬 Cuadro de pregunta de 3 botones.
>
> ```
> // Para escoger entre botones
> Object[] options = {"Si, fundamental", "No, para nada", "Cancelar"};
> int respuesta = JOptionPane.showOptionDialog(null, "¿Es importante unir programacion y creatividad?",
> "Pregunta", JOptionPane.YES_NO_CANCEL_OPTION, JOptionPane.QUESTION_MESSAGE,null, options, options[0]);
>
> // Para mostrar información
> String mensaje = switch(respuesta) {
>     case 0 -> { "Tu si que sabes."; }
>     case 1 -> { "Apaga y vamonos..."; }
>     default -> { "No sabe, no contesta."; }
> }
> 
> JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.WARNING_MESSAGE);
> ```
>---

#### JOptionPane.InputDialog

Este método permite mostrar diálogos donde se puede __ingresar datos o seleccionar opciones de un combo__. _Retorna un String, un objeto_.

##### showInputDialog(ventana, “Mensaje”,”titulo de ventana”, icono, icono especial, “valores”, valor inicial);

>---
> Ejemplos:
> 
> ✍ Cuadro de introducción de String.
> 
> ```
> // Para introducir un String
> String contesta = JOptionPane.showInputDialog("Dime tu nombre: ");
> JOptionPane.showMessageDialog(null, "Hola " + contesta);
> ```
> 
> 📲 Cuadro de desplegable de opciones.
> 
> ```
> // Para elegir entre diferentes opciones
> Object color = JOptionPane.showInputDialog(null, "Seleccione Un Color", "COLORES", JOptionPane.QUESTION_MESSAGE, null,
>    new Object[]{"Seleccione", "Amarillo", "Azul", "Rojo"}, "Seleccione");
> JOptionPane.showMessageDialog(null, color.toString());
>```
>---

### Componentes, Eventos y controladores de eventos

Un __componente__ es como un control que se puede representar visualmente y suele ser independiente. Tiene una funcionalidad específica y se representa como una clase individual en Swing API. Por ejemplo, la clase __JButton__ en Swing API es un componente de botón y proporciona la funcionalidad de un botón.

Los __eventos__ son la base de la interacción del usuario con la interfaz gráfica. Un evento se desencadena cuando el usuario interactúa con un componente, por ejemplo, al hacer clic en un botón o al escribir en un campo de texto.

Para definir un evento en Swing de Java, debes seguir los siguientes pasos:

1.  Crear una __clase oyente__ que implemente una __interfaz de oyente de eventos__.
2.  Registrar la __instancia del oyente__ con un componente mediante el método _addXXXListene()_. Los listener están asociados a un componente para que se ejecute una respuesta, según un evento que ha ocurrido.
3.  Implementar los __métodos de devolución de llamada__ en la clase oyente. 

![Imágen de diagrama que muestra cómo se comportan el evento y el listener.](/docs/java/img/componente_evento_control_swing.png)

Sobre un __Jframe__ añadimos un __JButton__ , al añadir este componente al menos debemos asignarle y un _nombre_ al control en la pestaña de Code de la ventana de propiedades y una _etiqueta_ al bótón en la pestaña de Properties de la ventana de propiedades. En la pestaña propiedades del __JButton__ se pueden asignar muchas más propiedades como tamaños, si lleva imagen, colores, etc. Añadir la funcionalidad al botón, es decir, la acción que queremos que se desencadene cuando se pulse el botón se elige en la pestaña Events de la ventana de propiedades del componente. Luego en el oyente se ve el cóigo del evento.

### Métodos comunes de estilo

Para pintar lo que está __dentro del componente__:

 * _void setForeground(Color c)._

Para pintar el __fondo del componente__:

* _void setBackground(Color c)._

Para cambiar la __fuente del componente__:

* _void setFont(Font f)._

Para cambiar el __posicionamiento y el tamaño__:

* Tamaño: _void setSize(int width, int height)._
* Ubicar el componente en un punto del contenedor: _void setLocation(int x, int y)._
* Establecer las coordenadas del componente: _void setBounds(int x, int y, int width, int height )._

Para su __habilitación__:

* Habilitar/Deshabilitar un componente: _void setEnabled(boolean b)._
*  Hacer visible/oculto el componente _void setVisible(boolean b)._

Para su __texto__:

* Texto presente en el componente: _void setText(String texto)._
* Texto alternativo (cursor sobre componente): _void setToolTipText (String texto)._

Otros métodos:

* Cambia __estilo de borde__ del componente: _void setBorder(Border borde)._
* __Icono__ asociado al componente (gif, jpg,png): _void setIcon(Icon icono)._

#### Clase javax.swingJLabel

__Área__ de texto editable (una línea):
* Constructores:
    * JTextField().
    * JTextField(String label, int c) [c = numero col].
    * JTextField(String label).
* Métodos:
  * String getText().
  * String getSelectedText().
  * void setText(String s).

#### Clase javax.swing.JTextField

Botón con __estado__ (seleccionado/no seleccionado):

* Constructores:
  * JToggleButton(Icon icono).
  * JToggleButton(String texto).
  * JToggleButton(Icon icono, boolean selec).
* Métodos:
  * void setSelected(boolean selec).

#### Clase javax.swing.JPasswordField

Área de texto para __contraseña__ (una línea):

* Constructores:
  * JPasswordField()
  * JPasswordField(String label, int c) [c = numero col].
  * JPasswordField(String label).
  * JPasswordField(int c).
* Métodos:
  * void setEchoChar(char c) [c = carácter que cambia].

#### Clase javax.swing.JTextArea

Área de texto __editable__ (varias líneas):

* Constructores
  * JTextArea()
  * JTextArea(String label, int c, int f) [c = número col, f = número filas].
  * JTextArea(String label).
* Métodos:
  * void insert (String, int) [Inserta texto en posición determinada].

#### Clase javax.swing.JComboBox

Combinación de __entrada de Texto__ con __Lista de selección desplegable__. Posee _barra de desplazamiento automática_. El primer elemento aparece como seleccionado.

* Constructores:
  * JComboBox().
  * JComboBox(String items[]) [array].
* Propiedades y métodos:
  * void addItem(String txt).
  * String getItemAt(int pos).
  * int getSelectedItem().
  * void remove(int pos).
  * void remove(String item).
  * void removeAll().
  * void setEditable(boolean b).

---
