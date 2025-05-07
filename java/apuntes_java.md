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

![Jerarquía de Java Swing.](/java/img/jerarquia_swing.png)

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

