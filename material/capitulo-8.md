# SLAYERSCRIPT
## Capítulo 8: Bucles en JavaScript

### 1. ¿Qué son los bucles?

Un bucle es una estructura de programación que permite ejecutar un bloque de código repetidamente mientras se cumpla una condición o hasta alcanzar un criterio de finalización.

Se utilizan para realizar tareas repetitivas, como:

- Contar números.
- Ejecutar operaciones matemáticas.
- Recorrer colecciones de datos.
- Buscar elementos dentro de una lista.
- Mantener un menú activo hasta que el usuario elija salir.

Por ejemplo, si queremos mostrar cinco números, podemos escribir cinco instrucciones `console.log()`. Sin embargo, sería mucho más práctico utilizar un bucle para repetir la misma operación.

En este capítulo vamos a trabajar con tres estructuras principales:

- `while`
- `do...while`
- `for`

También aprenderemos a controlar la ejecución mediante `break` y `continue`.

---

### 2. El bucle `while`

El bucle `while` ejecuta un bloque de código mientras su condición sea verdadera.

#### Sintaxis

```javascript
while (condicion) {
    // Código que se repite
}
```

Primero se evalúa la condición. Si es verdadera, se ejecuta el bloque. Después, la condición vuelve a evaluarse.

Si resulta falsa, el bucle termina.

#### Ejemplo: contar del 0 al 4

```javascript
let i = 0;

while (i < 5) {
    console.log(i);
    i++;
}
```

**Resultado:**

```text
0
1
2
3
4
```

¿Qué sucede en este código?

1. Se declara la variable `i` con el valor `0`.
2. Se comprueba si `i < 5`.
3. Si la condición se cumple, se muestra el valor de `i`.
4. `i++` incrementa el contador en uno.
5. El proceso se repite hasta que `i` alcanza el valor `5`.

Cuando `i` vale `5`, la condición `i < 5` es falsa y el bucle finaliza.

**Importante:** el número 5 no aparece porque la condición utiliza `<` en lugar de `<=`.

#### ¿Qué ocurre si no actualizamos el contador?

```javascript
let i = 0;

while (i < 5) {
    console.log(i);
}
```

Este código produce un bucle infinito porque `i` permanece en `0`. La condición siempre es verdadera y nunca existe un avance hacia la finalización.

Para evitarlo, debemos comprobar que las variables que controlan el bucle cambien correctamente.

---

### 3. Los bucles infinitos

Un bucle infinito ocurre cuando una estructura repetitiva nunca alcanza una condición de salida.

Puede suceder por distintos motivos:

- El contador no se incrementa ni se modifica.
- La condición nunca puede volverse falsa.
- El contador cambia en la dirección equivocada.
- Se utiliza `while (true)` sin una salida adecuada.

Por ejemplo:

```javascript
while (true) {
    console.log("Esto se repite indefinidamente");
}
```

La condición `true` siempre es verdadera, por lo que el bucle no termina por sí solo.

Los bucles infinitos no son siempre un error. Pueden utilizarse en sistemas que necesitan permanecer activos, pero deben contar con un mecanismo de salida cuando corresponda.

#### Ejemplo con `break`

```javascript
let contraseña = "";

while (true) {
    contraseña = prompt("Ingresá la contraseña:");

    if (contraseña === "ABC") {
        console.log("Acceso permitido");
        break;
    }
}
```

El bucle solicita una contraseña repetidamente. Cuando el usuario ingresa `"ABC"`, se ejecuta `break` y la ejecución sale del bucle.

En este ejemplo, `break` funciona como una salida explícita.

**Precaución:** un bucle infinito que se ejecuta continuamente en el hilo principal del navegador puede congelar la página. En aplicaciones reales, una solicitud de entrada del usuario o un proceso asíncrono suele ser más apropiado que una repetición intensiva sin pausas.

---

### 4. El bucle `do...while`

El bucle `do...while` es parecido a `while`, pero tiene una diferencia fundamental: **ejecuta el bloque al menos una vez antes de comprobar la condición**.

#### Sintaxis

```javascript
do {
    // Código que se ejecuta
} while (condicion);
```

A diferencia de `while`, la primera ejecución no depende de que la condición sea verdadera.

#### Ejemplo: contar del 0 al 4

```javascript
let i = 0;

do {
    console.log(i);
    i++;
} while (i < 5);
```

**Resultado:**

```text
0
1
2
3
4
```

El procedimiento es el siguiente:

1. Se ejecuta el bloque.
2. Se muestra el contador.
3. Se incrementa `i`.
4. Se comprueba si `i < 5`.
5. Si la condición es verdadera, se repite el proceso.

Cuando `i` llega a `5`, la condición es falsa y el bucle termina.

#### Diferencia entre `while` y `do...while`

```javascript
let numero = 10;

while (numero < 5) {
    console.log("While");
}
```

No se muestra nada porque la condición es falsa desde el principio.

En cambio:

```javascript
let numero = 10;

do {
    console.log("Do while");
} while (numero < 5);
```

Se muestra `"Do while"` una vez, aunque la condición sea falsa.

Esto ocurre porque `do...while` evalúa la condición después de ejecutar el bloque.

#### Ejemplo: repetir un menú

```javascript
let opcion;

do {
    opcion = prompt("Elegí una opción o escribí salir");
} while (opcion !== "salir");
```

El programa solicita una opción y continúa haciéndolo hasta que el usuario escribe `"salir"`.

En esta versión, la comparación distingue mayúsculas y minúsculas. Por eso, `"Salir"` no equivale a `"salir"`.

---

### 5. El bucle `for`

El bucle `for` permite reunir en una sola estructura la inicialización, la condición y la actualización del contador.

Es muy utilizado cuando conocemos el punto de inicio y podemos definir claramente cuándo debe terminar la repetición.

#### Sintaxis

```javascript
for (inicializacion; condicion; actualizacion) {
    // Código que se repite
}
```

Sus tres partes son:

1. **Inicialización:** se ejecuta una vez al comenzar el bucle.
2. **Condición:** se comprueba antes de cada repetición.
3. **Actualización:** se ejecuta después de cada repetición, si el flujo continúa normalmente.

#### Ejemplo: contar del 0 al 4

```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

**Resultado:**

```text
0
1
2
3
4
```

Este código realiza el mismo recorrido que los ejemplos anteriores, pero concentra el control del contador en la cabecera del `for`.

#### ¿Qué pasa si cambiamos la condición?

```javascript
for (let i = 0; i <= 5; i++) {
    console.log(i);
}
```

Ahora se muestra:

```text
0
1
2
3
4
5
```

La diferencia está en `<=`, que incluye el número 5.

#### Las partes del `for` pueden omitirse

JavaScript permite omitir una o más de las tres expresiones, siempre que se mantengan los puntos y coma correspondientes.

Por ejemplo:

```javascript
let i = 0;

for (; i < 5; i++) {
    console.log(i);
}
```

La inicialización se realizó fuera del bucle.

También es posible omitir la actualización de la cabecera y realizarla dentro del bloque. Sin embargo, hay que tener cuidado: si se omite y no se actualiza el contador en otro lugar, el bucle podría no terminar.

Si se omite la condición, se considera verdadera, por lo que el bucle continuará hasta que se produzca una salida, por ejemplo, mediante `break`.

---

### 6. Comparación entre `while`, `do...while` y `for`

| Característica | `while` | `do...while` | `for` |
|---|---|---|---|
| Cuándo comprueba la condición | Antes de ejecutar | Después de ejecutar | Antes de ejecutar |
| Ejecuciones mínimas | 0 | 1 | 0 |
| Inicialización del contador | Generalmente externa | Generalmente externa | Puede ir en la cabecera |
| Actualización del contador | Dentro del bloque, normalmente | Dentro del bloque, normalmente | Puede ir en la cabecera |
| Uso habitual | Repetir mientras se cumpla una condición | Ejecutar al menos una vez y luego repetir | Recorridos con inicio, condición y actualización definidos |

Los tres bucles pueden resolver muchos de los mismos problemas. La diferencia principal está en cómo se organiza el control de la repetición y en si el bloque debe ejecutarse al menos una vez.

---

### 7. La instrucción `break`

La instrucción `break` termina inmediatamente el bucle en el que se encuentra.

No hace falta esperar a que la condición original del bucle se vuelva falsa.

#### Ejemplo

```javascript
for (let i = 0; i <= 5; i++) {
    if (i === 3) {
        console.log("Terminamos");
        break;
    }

    console.log(i);
}
```

**Resultado:**

```text
0
1
2
Terminamos
```

Cuando `i` alcanza el valor `3`, se cumple el `if` y se ejecuta `break`.

El bucle termina sin procesar los valores `4` y `5`.

#### ¿Para qué sirve?

`break` resulta útil cuando encontramos el dato que estábamos buscando o cuando debemos detener un recorrido al alcanzar cierto límite.

Por ejemplo, si recorremos una lista de clientes y encontramos el registro que necesitamos, podemos detener la búsqueda en lugar de continuar revisando elementos innecesarios.

También puede utilizarse en un `switch`, como vimos en el capítulo anterior.

---

### 8. La instrucción `continue`

La instrucción `continue` omite el resto del bloque correspondiente a la repetición actual y pasa a la siguiente iteración.

A diferencia de `break`, **no termina el bucle**.

#### Ejemplo: omitir el número 3

```javascript
for (let i = 0; i <= 5; i++) {
    if (i === 3) {
        continue;
    }

    console.log(i);
}
```

**Resultado:**

```text
0
1
2
4
5
```

Cuando `i` vale `3`, se ejecuta `continue`. Por eso, el `console.log(i)` de esa iteración se omite.

El bucle continúa con los valores restantes.

#### Diferencia entre `break` y `continue`

- `break`: finaliza el bucle por completo.
- `continue`: omite la iteración actual y permite que el bucle continúe.

Podemos recordarlo de esta forma:

- `break` significa salir.
- `continue` significa seguir, pero saltando lo que queda de la vuelta actual.

**Atención con `while`:** si utilizás `continue`, asegurate de que el contador avance antes de volver a evaluar la condición. De lo contrario, podés crear un bucle infinito.

---

### 9. Comprobar si un número es par o impar

En el capítulo de números estudiamos el operador módulo `%`, que devuelve el resto de una división.

Podemos aprovecharlo para identificar números pares e impares.

```javascript
let numero = 8;

if (numero % 2 === 0) {
    console.log("El número es par");
} else {
    console.log("El número es impar");
}
```

Si el resto de dividir el número por 2 es cero, el número es par. Si el resto es uno, en el caso de los enteros positivos, es impar.

#### Aplicación con un bucle

```javascript
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        console.log(i + " es par");
    }
}
```

**Resultado:**

```text
2 es par
4 es par
6 es par
8 es par
10 es par
```

Este ejemplo combina un bucle con un condicional. El bucle recorre los números del 1 al 10 y el `if` determina cuáles deben mostrarse.

#### Aplicación con `continue`

```javascript
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        continue;
    }

    console.log(i);
}
```

Ahora se muestran únicamente los números impares porque se omiten las iteraciones en las que el número es par.

---

### 10. Ejercicios prácticos

#### Ejercicio 1. Resolver el mismo recorrido con tres bucles

Crear un programa que utilice una variable contador para imprimir los números del 0 al 4.

Resolverlo tres veces:

1. Utilizando `while`.
2. Utilizando `do...while`.
3. Utilizando `for`.

Los tres programas deben producir el mismo resultado:

```text
0
1
2
3
4
```

Después, explicar las diferencias entre las tres estructuras y por qué es importante actualizar el contador correctamente.

**Objetivo:** comprender la sintaxis y el funcionamiento de cada bucle, evitando las repeticiones infinitas.

#### Ejercicio 2. Detectar y corregir bucles infinitos

Analizar tres programas que no terminan correctamente.

Para cada uno:

1. Identificar qué provoca que el bucle continúe indefinidamente.
2. Explicar por qué la condición no llega a ser falsa o por qué el control del bucle falla.
3. Modificar el código para que termine correctamente.

**Objetivo:** aprender a reconocer errores frecuentes en las estructuras repetitivas y corregirlos.

La transcripción menciona tres programas con errores, pero no incluye sus fragmentos de código completos. Por lo tanto, los ejercicios específicos deben resolverse a partir de los ejemplos que se proporcionen junto con la tarea.

#### Ejercicio 3. Practicar `break` y `continue`

**Parte A: omitir el número 4**

Recorrer los números del 0 al 9, pero evitar que el número 4 sea procesado. Los demás números deben mostrarse normalmente.

**Objetivo:** utilizar `continue` para omitir una iteración concreta sin detener el bucle.

**Parte B: finalizar en el número 6**

Crear un recorrido que comience en 0 y avance de uno en uno. Cuando llegue al número 6, el bucle debe finalizar, independientemente de que el límite original sea mayor.

**Objetivo:** utilizar `break` para terminar el recorrido antes de alcanzar el límite establecido inicialmente.

---

### 11. Resumen del capítulo

| Elemento | Función |
|---|---|
| `while` | Repite un bloque mientras la condición sea verdadera |
| `do...while` | Ejecuta el bloque al menos una vez y después comprueba la condición |
| `for` | Agrupa inicialización, condición y actualización |
| `break` | Termina inmediatamente el bucle |
| `continue` | Omite la iteración actual y continúa con la siguiente |
| `++` | Incrementa una variable en uno |
| `%` | Devuelve el resto de una división |

La clave de este capítulo es aprender a controlar el inicio, la repetición y la finalización de un bucle. Una condición correcta y una actualización adecuada del contador son esenciales para evitar errores.

### 12. Recursos para estudiar

- MDN: [Bucles e iteración en JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Loops_and_iteration)
- MDN: [Sentencia `while`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/while)
- MDN: [Sentencia `do...while`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/do...while)
- MDN: [Sentencia `for`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/for)
- MDN: [Sentencia `break`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/break)
- MDN: [Sentencia `continue`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/continue)

**Fin del capítulo 8.** Los bucles permiten automatizar tareas repetitivas, pero necesitan una lógica de control clara. El siguiente paso será aprovecharlos para trabajar con estructuras de datos y recorrer colecciones de manera eficiente.
