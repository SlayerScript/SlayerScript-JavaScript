# SlayerScript | Capítulo 9: Funciones en JavaScript

## 1. ¿Qué son las funciones?

Una función es un bloque de código reutilizable que permite agrupar instrucciones para ejecutar una tarea específica. En lugar de escribir las mismas instrucciones varias veces, podemos declararlas una vez y ejecutarlas cada vez que necesitemos.

Las funciones ayudan a organizar el código, evitar repeticiones y separar las tareas en partes más pequeñas.

### 1.1. Declaración de una función

Para declarar una función tradicional, utilizamos la palabra clave `function`, seguida de un nombre, paréntesis y un bloque de código entre llaves.

```javascript
function space() {
    console.log("----------------");
}

space();
```

**¿Cómo funciona?**

- `function`: declara la función.
- `space`: es el nombre de la función.
- `()`: contiene los parámetros, si los hay.
- `{}`: delimita el bloque de código que se ejecutará.
- `space()`: llama a la función para ejecutar su contenido.

La declaración de una función no significa que su contenido se ejecute inmediatamente. Para ejecutar la tarea, debemos llamarla.

Una vez declarada, podemos invocarla varias veces:

```javascript
space();
space();
space();
```

Cada llamada ejecuta el mismo bloque de código sin necesidad de volver a escribir las instrucciones.

## 2. Funciones con parámetros

Los parámetros permiten que una función reciba información y trabaje con diferentes valores.

Un parámetro funciona como una variable local de la función. Su valor se establece cuando llamamos a la función y le proporcionamos los argumentos correspondientes.

```javascript
function slayer(nombre, rol) {
    console.log(`Hola, ${nombre}. Tu rol hoy es ${rol}.`);
}

slayer("Buffy", "cazar vampiros");
```

**Resultado:**

```text
Hola, Buffy. Tu rol hoy es cazar vampiros.
```

En este ejemplo:

- `nombre` y `rol` son los parámetros.
- `"Buffy"` y `"cazar vampiros"` son los argumentos que pasamos al llamar a la función.
- El primer argumento se asigna a `nombre`.
- El segundo argumento se asigna a `rol`.

Podemos reutilizar la misma función con información diferente:

```javascript
slayer("Faith", "cazar vampiros");
slayer("Giles", "investigar");
```

La estructura de la función permanece igual, pero los datos cambian.

### 2.1. ¿Qué sucede si no proporcionamos los argumentos?

Si llamamos a una función sin proporcionar los argumentos correspondientes, los parámetros que no tengan valores predeterminados recibirán `undefined`.

```javascript
function slayer(nombre, rol) {
    console.log(`Hola, ${nombre}. Tu rol hoy es ${rol}.`);
}

slayer();
```

El mensaje se mostrará, pero los valores de `nombre` y `rol` serán `undefined`.

Esto puede generar resultados no deseados cuando una función necesita información para realizar su tarea.

### 2.2. Parámetros con valores predeterminados

Podemos establecer valores predeterminados para los parámetros. De esta manera, la función tendrá datos que utilizar cuando no se proporcionen argumentos.

```javascript
function slayer(nombre = "Slayer genérica", rol = "cazar vampiros") {
    console.log(`Hola, ${nombre}. Tu rol hoy es ${rol}.`);
}

slayer();
```

**Resultado:**

```text
Hola, Slayer genérica. Tu rol hoy es cazar vampiros.
```

Si proporcionamos argumentos, estos reemplazan los valores predeterminados:

```javascript
slayer("Faith", "cazar duendes");
```

Los valores predeterminados permiten que una función pueda utilizarse sin argumentos o con información personalizada.

## 3. `return` frente a `console.log()`

Una de las diferencias más importantes al trabajar con funciones es distinguir entre mostrar un resultado y devolver un valor.

### 3.1. ¿Qué hace `console.log()`?

`console.log()` muestra información en la consola. Sirve para visualizar mensajes, valores y resultados durante la ejecución del programa.

```javascript
function suma(a, b) {
    console.log(a + b);
}

suma(10, 10);
```

**Resultado:**

```text
20
```

La función muestra el resultado, pero no devuelve ese número como valor de retorno.

### 3.2. ¿Qué hace `return`?

La instrucción `return` devuelve un valor desde una función al lugar donde fue llamada. Ese valor puede almacenarse en una variable, utilizarse en otra operación o pasarse a otra función.

```javascript
function suma(a, b) {
    return a + b;
}

const resultado = suma(10, 10);

console.log(resultado);
```

**Resultado:**

```text
20
```

En este caso, `return` devuelve el resultado de la suma y la variable `resultado` almacena ese valor.

También podemos pasar directamente la llamada a `console.log()`:

```javascript
console.log(suma(10, 10));
```

Esto muestra el valor devuelto por la función.

### 3.3. ¿Qué ocurre si usamos `console.log()` en lugar de `return`?

Consideremos el siguiente ejemplo:

```javascript
function suma(a, b) {
    console.log(a + b);
}

const resultado = suma(10, 10);

console.log(resultado);
```

**Resultado:**

```text
20
undefined
```

¿Por qué aparecen dos resultados diferentes?

1. El primer `console.log()` muestra `20` desde el interior de la función.
2. La función no devuelve explícitamente ningún valor, por lo que devuelve `undefined`.
3. La variable `resultado` recibe ese valor de retorno.
4. El segundo `console.log()` muestra `undefined`.

Por lo tanto, `console.log()` y `return` cumplen funciones distintas.

| `console.log()` | `return` |
|---|---|
| Muestra información en la consola. | Devuelve un valor desde la función. |
| No convierte automáticamente ese resultado en el valor de retorno. | Permite almacenar y reutilizar el resultado. |
| Es útil para visualizar información y depurar. | Es fundamental para construir operaciones reutilizables. |

**Regla práctica:** utilizá `console.log()` cuando quieras mostrar información y `return` cuando necesites obtener un valor para continuar trabajando con él.

Además, cuando se ejecuta un `return`, la función termina en ese punto. Las instrucciones que estén después no se ejecutarán en esa llamada.

## 4. Funciones de expresión (*Function Expressions*)

Una función de expresión consiste en asignar una función a una variable.

En lugar de declarar una función tradicional de forma independiente, podemos guardar la función en una variable y utilizar esa variable para llamarla.

```javascript
const bucle = function() {
    for (let i = 0; i < 5; i++) {
        console.log("Buenos Aires");
    }
};

bucle();
```

**Resultado:** el mensaje `Buenos Aires` se muestra cinco veces.

En este ejemplo:

- `const bucle` declara la variable que almacenará la función.
- `function()` define una función sin nombre.
- El bloque contiene un bucle `for` que se ejecuta cinco veces.
- `bucle()` llama a la función almacenada en la variable.

### 4.1. Diferencia entre `bucle` y `bucle()`

Esta distinción es fundamental:

```javascript
console.log(bucle);
```

Muestra una representación de la función, porque estamos haciendo referencia a ella sin ejecutarla.

En cambio:

```javascript
bucle();
```

Ejecuta la función y realiza las instrucciones de su bloque.

En resumen:

- `bucle`: referencia a la función.
- `bucle()`: llamada que ejecuta la función.

Esta diferencia también será importante cuando trabajemos con funciones como argumentos, eventos y otros mecanismos de JavaScript.

### 4.2. Cuidado con los bucles infinitos

Al combinar funciones con bucles, debemos asegurarnos de que las condiciones puedan dejar de cumplirse.

Por ejemplo, el siguiente código contiene un error:

```javascript
let i = 0;

while (i < 5) {
    console.log("Buenos Aires");
}
```

Como `i` nunca cambia, la condición `i < 5` continúa siendo verdadera y el bucle no termina.

La versión corregida sería:

```javascript
let i = 0;

while (i < 5) {
    console.log("Buenos Aires");
    i++;
}
```

También podemos utilizar un bucle `for`, que reúne la inicialización, la condición y la actualización en una misma estructura.

## 5. Funciones flecha (*Arrow Functions*)

Las funciones flecha son otra forma de definir funciones en JavaScript. Se caracterizan por utilizar el operador `=>` y suelen permitir una sintaxis más breve.

Se pueden guardar en variables, igual que las funciones de expresión.

### 5.1. Sintaxis básica

Podemos escribir una función de suma de la siguiente manera:

```javascript
const suma = (a, b) => {
    return a + b;
};

const resultado = suma(5, 5);

console.log(resultado);
```

**Resultado:**

```text
10
```

La estructura tiene los siguientes elementos:

- `const suma`: declara la variable que almacenará la función.
- `(a, b)`: define los parámetros.
- `=>`: introduce el cuerpo de la función flecha.
- `{}`: contiene las instrucciones.
- `return a + b`: devuelve el resultado de la operación.

La función flecha permite escribir la misma operación que una función tradicional, pero con una sintaxis diferente.

### 5.2. Simplificación de las funciones flecha

Cuando el cuerpo de una función flecha contiene una única expresión, podemos eliminar las llaves y el `return` explícito. JavaScript devuelve automáticamente el resultado de esa expresión.

Por ejemplo:

```javascript
const suma = (a, b) => a + b;

console.log(suma(5, 5));
```

Esta versión produce el mismo resultado que la anterior.

La diferencia es que ahora la función se escribe en una sola línea.

**Importante:** el retorno implícito funciona cuando no utilizamos un bloque de instrucciones entre llaves. Si agregamos llaves, necesitamos escribir `return` cuando queramos devolver un valor.

```javascript
const suma = (a, b) => {
    return a + b;
};
```

Sin `return`, el bloque no devuelve automáticamente el resultado de la expresión.

### 5.3. Funciones flecha con un solo parámetro

Si una función flecha tiene un único parámetro, los paréntesis son opcionales.

```javascript
const potencia = a => a ** 2;

console.log(potencia(2));
```

**Resultado:**

```text
4
```

En este ejemplo, el operador `**` calcula una potencia. La expresión `a ** 2` eleva el valor de `a` al cuadrado.

También podríamos escribirla con paréntesis:

```javascript
const potencia = (a) => a ** 2;
```

Ambas formas son válidas.

### 5.4. Ejemplos de funciones flecha

**Suma:**

```javascript
const suma = (a, b) => a + b;
```

**Resta:**

```javascript
const resta = (a, b) => a - b;
```

**Multiplicación:**

```javascript
const multiplicacion = (a, b) => a * b;
```

**División:**

```javascript
const division = (a, b) => a / b;
```

**Potencia:**

```javascript
const potencia = a => a ** 2;
```

Estas funciones devuelven los resultados de sus operaciones. Para visualizar los valores, podemos llamarlas dentro de `console.log()` o guardar sus resultados en variables.

### 5.5. ¿Cuándo conviene utilizar funciones flecha?

Las funciones flecha resultan especialmente prácticas cuando necesitamos definir operaciones breves, como cálculos matemáticos o transformaciones de valores.

Por ejemplo:

```javascript
const perimetroRectangulo = (base, altura) => 2 * (base + altura);

console.log(perimetroRectangulo(5, 3));
```

**Resultado:**

```text
16
```

La elección entre una función tradicional y una función flecha depende del contexto. Ambas son herramientas válidas, pero no son idénticas en todos sus comportamientos. Más adelante, al trabajar con objetos y otros conceptos de JavaScript, será importante conocer esas diferencias.

## 6. Repaso general

| Concepto | Función |
|---|---|
| `function` | Declara una función tradicional. |
| Parámetros | Permiten recibir información dentro de una función. |
| Argumentos | Son los valores que pasamos al llamar a una función. |
| Valores predeterminados | Proporcionan valores cuando no se envían argumentos. |
| `console.log()` | Muestra información en la consola. |
| `return` | Devuelve un valor desde la función y termina su ejecución. |
| Function Expression | Asigna una función a una variable. |
| Función flecha | Define una función utilizando `=>`. |
| `bucle` | Hace referencia a la función almacenada. |
| `bucle()` | Ejecuta la función. |

## 7. Tarea práctica

### Ejercicio 1. Declaración de funciones

Tenemos la siguiente función:

```javascript
function bienvenida() {
    console.log("Bienvenidos a SlayerScript");
}
```

Convertí esta función en:

1. Una función de expresión.
2. Una función flecha.

**Objetivo:** practicar distintas sintaxis para definir funciones sin cambiar el comportamiento del programa.

### Ejercicio 2. `return` frente a `console.log()`

Valentín está creando una calculadora en JavaScript. Comienza con una función que suma dos valores, pero no entiende por qué no obtiene el resultado esperado en la terminal.

```javascript
function suma(a, b) {
    return a + b;
}

suma(10, 10);
```

Resolvé el ejercicio:

1. Explicá por qué la llamada no muestra automáticamente el resultado en la consola.
2. Modificá el código para mostrar el resultado con `console.log()`.
3. Guardá el resultado en una variable y mostralo.
4. Cambiá `return` por `console.log()` dentro de la función y observá qué ocurre con el valor almacenado en la variable.

**Objetivo:** comprender la diferencia entre devolver un valor y mostrarlo.

### Ejercicio 3. Funciones de expresión

Roberto tiene la siguiente función de expresión:

```javascript
const bucle = function() {
    console.log("Probando función");
};
```

Cuando escribe `console.log(bucle)`, aparece información sobre la función, pero no el mensaje `Probando función`.

Resolvé el ejercicio:

1. Modificá el código para que se ejecute la función.
2. Explicá la diferencia entre `bucle` y `bucle()`.
3. Comprobá qué sucede cuando llamás a la función varias veces.

**Objetivo:** diferenciar la referencia a una función de su ejecución.

### Ejercicio 4. Funciones flecha

Simplificá las siguientes funciones utilizando la sintaxis de función flecha.

**A. Alarma**

La función debe recibir un nombre y devolver un mensaje para que esa persona se despierte.

```javascript
function alarma(nombre) {
    return `Despertate, ${nombre}`;
}
```

**B. División**

La función debe recibir dos números y devolver el resultado de dividir el primero por el segundo.

```javascript
function division(a, b) {
    return a / b;
}
```

**Objetivo:** practicar la sintaxis de las funciones flecha y el retorno implícito cuando corresponda.

---

## Conclusión

Las funciones son una herramienta esencial para escribir código organizado, reutilizable y fácil de mantener. En este capítulo aprendimos a declararlas, pasarles parámetros, establecer valores predeterminados, devolver resultados y utilizar distintas sintaxis para definirlas.

La idea central es que una función no solo sirve para ejecutar instrucciones: también puede recibir información y devolver valores que utilizaremos en otras partes del programa. Dominar esa diferencia nos prepara para trabajar con operaciones más complejas y construir aplicaciones con una estructura más clara.
