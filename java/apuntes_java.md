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

![Jerarquía de Java Swing.](/java/jerarquia_swing.png)

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

#### JOptionPane

Para crear diálogos preestablecidos esta la clase JOptionPane. Esta clase implementa métodos (static) de la forma showXXDialog, donde XX va a variar de acuerdo según el tipo de dialogo que se necesite.

* Todos los diálogos son modales.
* Se puede configurar mediante parámetros: titulo, icono, mensajes, etc.

__JOptionPane.showMessageDialog__

Este método permite mostrar ventanas de diálogo que muestran un mensaje y contienen un botón de
aceptación.

__showMessageDialog(ventana, "Mensaje", “Titulo de ventana”, icono){};__

Ejemplos:

```
//Mensaje plano
JOptionPane.showMessageDialog(null, "Mensaje plano", "Mensaje", JOptionPane.PLAIN_MESSAGE);
```

![Ejemplo Mensaje plano.](/java/ejemplo_jpane_1.png)
