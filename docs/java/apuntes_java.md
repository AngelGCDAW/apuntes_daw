# APUNTES DE JAVA

## ÍNDICE

## TEMA 09 - SWING GUI FORMS

### Qué es Swing

La API Swing es un conjunto de componentes para la creación de entornos gráficos de usuarios.

### Cómo funciona

Todos los componentes heredan de javax.swing.JComponent.

* JFrame será la base para la aplicación principal.
* JDialog construirá los diálogos (ventanas). El resto de las clases, serán componentes simples.

#### Jerarquía de Java Swing:

![Jerarquía de Java Swing.](/docs/java/img/jerarquia_swing.png)

### Cuadros de diálogo

Clases JDialog y JOptionPane: cuadros de diálogo que muestran información o del tipo de pedir
confirmación.

* JDialog es modal (no se puede interactuar con el resto de ventanas)
* JOptionPanel no es modal. Al cerrar la ventana principal, se cierra también este cuadro de diálogo.

Existen Diálogos preestablecidos, los cuales pueden tener distinta finalidad:
* Informativos
* Elección
* Mensajes de Error
* Mensajes de Advertencia
* Entrada de datos
* Etc. 

A partir de aquí tenemos una serie de controles que podemos utilizar, a continuación exponemos los más comunes:

### JOptionPane

Para crear diálogos preestablecidos esta la clase JOptionPane. Esta clase implementa métodos (static) de la forma showXXDialog, donde XX va a variar de acuerdo según el tipo de dialogo que se necesite.

* Todos los diálogos son modales.
* Se puede configurar mediante parámetros: titulo, icono, mensajes, etc.

#### JOptionPane.showMessageDialog

Este método permite mostrar ventanas de diálogo que muestran un mensaje y contienen un botón de
aceptación.

##### showMessageDialog(ventana, "Mensaje", “Titulo de ventana”, icono);

Ejemplos:

🗨 Un cuadro de diálogo de contexto general.

```
// Mensaje plano
JOptionPane.showMessageDialog(null, "Mensaje plano", "Mensaje", JOptionPane.PLAIN_MESSAGE);
```

❌ Un cuadro de diálogo de error.

```
// Mensaje de error
JOptionPane.showMessageDialog(null, "Mensaje de error", "Error", JOptionPane.EROR_MESSAGE);
```

💬 Un cuadro de texto informativo.

```
// Mensaje informativo
JOptionPane.showMessageDialog(null, "Mensaje informativo", "Información", JOptionPane.INFORMATION_MESSAGE);
```

❗ Un cuadro de texto de aviso.

```
// Mensaje de aviso
JOptionPane.showMessageDialog(null, "Mensaje de aviso", "Aviso", JOptionPane.WARNING_MESSAGE);
```

❔ Un cuadro de texto de pregunta.

```
// Mensaje de pregunta
JOptionPane.showMessageDialog(null, "Mensaje de pregunta", "Pregunta", JOptionPane.QUESTION_MESSAGE);
```

#### JOptionPane.showConfirmDialog

Este método permite mostrar diálogos donde se puede elegir entre varias opciones (aceptar, cancelar, si o no).

##### showConfirmDialog(ventana, “Mensaje”, “Titulo de ventana”, tipo de opción, icono);

Ejemplos:

✔ Cuadro de confirmación por defecto.

```
// Mensaje de confirmación por defecto
JOptionPane.showMessageDialog(null, "Aquí va el mensaje", "Ventana por defecto", JOptionPane.DEFAULT_OPTION, JOptionPane.INFORMATION_MESSAGE);
```

❔ Cuadro de confirmación Si/No.

```
// Mensaje confirmación si-no
int respuesta = JOptionPane.showConfirmDialog(null, "Aqui va el mensaje", "Ventana SI-NO", JOptionPane.YES_NO_OPTION, JOptionPane.QUESTION_MESSAGE);
String mensaje = "";

if(respuesta == 0) {
    mensaje = "Ha contestado si.";
} else {
    mensaje = "Ha respondido no.";
}

JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.PLAIN_MESSAGE);
```

❓ Cuadro confirmación Si/No/Cancelar.

```
// Mensaje de confirmacion si-no-cancelar
int respuesta = JOptionPane.showConfirmDialog(null, "Aqui va el mensaje", "Ventana SI-NO-Cancelar", JOptionPane.YES_NO_CANCEL_OPTION, JOptionPane.QUESTION_MESSAGE);
String mensaje = "";

switch (respuesta) {
    case 0 -> { mensaje = "Ha contestado si"; }
    case 1 -> { mensaje = "Ha respondido no"; }
    default -> { mensaje = "Ha cancelado"; }
}

JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.PLAIN_MESSAGE);
```

🆗 Cuadro de confirmación Aceptar/Cancelar.

```
// Mensaje de aceptar-cancelar
int respuesta = JOptionPane.showConfirmDialog(null, "Aqui va el mensaje", "Ventana Aceptar-Cancelar", JOptionPane.OK_CANCEL_OPTION, JOptionPane.QUESTION_MESSAGE);
String mensaje = "";

if (respuesta == 0) {
    mensaje = "Ha contestado aceptar";
} else {
    mensaje = "Ha respondido cancelar";
}

JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.PLAIN_MESSAGE);
```

#### JOptionPane.showOptinDialog

Este método permite mostrar diálogos con los botones, iconos, texto, mensajes, titulo, etc. que se desee. Se puede cambiar el texto de los botones. Retorna un int.

##### showOptionDialog(ventana, “Mensaje”, “Titulo de ventana”, tipo de opción, icono, icono especial, “titulo de botones”, boton inicial);

Ejemplo:

💬 Cuadro de pregunta de 3 botones.

```
// Para escoger entre botones
Object[] options = {"Si, fundamental", "No, para nada", "Cancelar"};
int respuesta = JOptionPane.showOptionDialog(null, "¿Es importante unir
programacion y creatividad?", "Pregunta",
                JOptionPane.YES_NO_CANCEL_OPTION,
                JOptionPane.QUESTION_MESSAGE,null, options, options[0]);

// Para mostrar información
String mensaje = switch(respuesta) {
    case 0 -> { "Tu si que sabes."; }
    case 1 -> { "Apaga y vamonos..."; }
    default -> { "No sabe, no contesta."; }
}

JOptionPane.showMessageDialog(null, mensaje, "Respuesta", JOptionPane.WARNING_MESSAGE);
```

#### JOptionPane.InputDialog

Este método permite mostrar diálogos donde se puede ingresar datos o seleccionar opciones de un combo. Retorna un String, un objeto.

##### showInputDialog(ventana, “Mensaje”,”titulo de ventana”, icono, icono especial, “valores”, valor inicial);

Ejemplos:

✍ Cuadro de introducción de String.

```
// Para introducir un String
String contesta = JOptionPane.showInputDialog("Dime tu nombre: ");
JOptionPane.showMessageDialog(null, "Hola " + contesta);
```

📲 Cuadro de desplegable de opciones.

```
// Para elegir entre diferentes opciones
Object color = JOptionPane.showInputDialog(null, "Seleccione Un Color",
    "COLORES", JOptionPane.QUESTION_MESSAGE, null,
    new Object[]{"Seleccione", "Amarillo", "Azul", "Rojo"}, "Seleccione");
JOptionPane.showMessageDialog(null, color.toString());
```

