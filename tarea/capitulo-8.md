# Tarea: Bucles en JavaScript
# LOS PROGRAMADORES SE HACEN PROGRAMANDO

## 1. While, Do...While y For

Crear un programa que utilice una variable contador para imprimir los números del `0` al `4`.

Primero, resolvé el ejercicio utilizando un while.

Después, realizá el mismo ejercicio utilizando un do...while.

Finalmente, resolvelo utilizando un for.

Importante: en los tres casos, el resultado debe ser el mismo.

Al terminar, explicá brevemente:

¿Cuándo se evalúa la condición en while?
¿Cuándo se evalúa la condición en do...while?
¿Qué diferencia tiene for respecto de los otros dos?

*¡CUIDADO CON EL BUCLE INFINITO!* Asegurate de que la variable que controla el bucle avance correctamente.

Objetivo: practicar las tres estructuras de repetición, comprender cómo evalúan sus condiciones y reconocer cuándo conviene utilizar cada una.

## 2. Bucle infinito

Mariela tiene tres programas que no paran de ejecutarse sin parar desde hace 2 horas, somos el servicio tecnico de la oficina y tenemos que hallar la solución a esos bucles.

```javascript
let i = 0
while (true) {
    console.log(i);
    i++;
}

let j = 0;
while (j < 5) {
    console.log(j);
    j--;
}

let k = 0;
while (k < 10) {
    console.log(k);
    k++;
    k = 0;
}
```
Objetivo: evaluar y ver como prevenir errores en la programación de bucles

## 3. Break y Continue

Nuestro jefe nos pide ayuda con dos recorridos de números.

## Parte A

Tenemos que recorrer los números del 0 al 9, pero hay un pequeño inconveniente:

*El número `4` no debe ser procesado.*

El resto de los números debe continuar normalmente.

¿Cómo harías para que el bucle ignore únicamente el `4` y continúe con los demás números?

## Parte B

Ahora tenemos otro recorrido.

El programa debe comenzar desde `0` y avanzar de uno en uno, pero cuando llegue al número `6`, el recorrido debe finalizar inmediatamente.

*El `6` debe ser procesado antes de finalizar.*

¿Cómo harías para detener el bucle en ese momento?

Objetivo: resolver situaciones en las que necesitamos modificar el comportamiento normal de un bucle, identificando cuándo debemos saltear una iteración y cuándo debemos finalizar completamente el recorrido.



