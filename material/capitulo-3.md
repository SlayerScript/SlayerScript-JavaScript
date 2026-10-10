# SLAYERSCRIPT
## Capítulo 3: var, let y const en JavaScript

### 1. Objetivos de aprendizaje

Al finalizar este capítulo, vas a poder:

- Comprender las diferencias entre `var`, `let` y `const`.
- Distinguir entre declarar, redeclarar y reasignar una variable.
- Reconocer los errores que pueden producirse al utilizar cada palabra clave.
- Elegir la declaración adecuada según las necesidades del programa.
- Comprender por qué `let` y `const` son preferibles a `var` en el código moderno.

### 2. ¿Qué significa declarar, redeclarar y reasignar?

Antes de comparar las tres palabras clave, es importante distinguir estos conceptos.

**Declarar:** crear una variable por primera vez.

```javascript
let personaje = "Sonic";
```

**Redeclarar:** volver a declarar una variable con el mismo identificador dentro del mismo ámbito.

```javascript
var personaje = "Sonic";
var personaje = "Shadow";
```

Esto es válido con `var` en el mismo ámbito, pero produce un error con `let` y `const`.

**Reasignar:** cambiar el valor de una variable que ya existe.

```javascript
let personaje = "Sonic";

personaje = "Shadow";
```

La variable sigue llamándose `personaje`, pero ahora almacena `"Shadow"`.

### 3. var: la forma tradicional

`var` es una palabra clave que se utilizaba tradicionalmente para declarar variables en JavaScript.

Una de sus características es que permite redeclarar y reasignar variables dentro del mismo ámbito.

```javascript
var serie = "ER";

var serie = "Dr. House";

serie = "The Good Doctor";

console.log(serie);
```

**Resultado:**

```text
The Good Doctor
```

La última asignación determina el valor que se muestra.

Aunque el código funciona, el uso de `var` puede generar confusiones cuando un programa crece. Entre sus particularidades se encuentra el alcance de función y el hecho de que no respeta el alcance de bloque como lo hacen `let` y `const`.

Por eso, en código nuevo generalmente se prefiere utilizar `let` o `const`.

### 4. let: variables que pueden cambiar

`let` permite declarar una variable cuyo valor puede cambiar durante la ejecución del programa.

```javascript
let erizo = "Sonic";

erizo = "Shadow";

erizo = "Silver";

console.log(erizo);
```

**Resultado:**

```text
Silver
```

La variable se declara una sola vez y después se reasigna cuando es necesario.

#### ¿Qué sucede si intentamos redeclararla?

```javascript
let erizo = "Sonic";

let erizo = "Shadow";
```

JavaScript produce un error de sintaxis porque la variable ya fue declarada en ese mismo ámbito.

La forma correcta de cambiar su valor es:

```javascript
let erizo = "Sonic";

erizo = "Shadow";

console.log(erizo);
```

**Regla principal:** utilizá `let` cuando necesites que el valor de una variable pueda cambiar.

### 5. const: variables que no pueden reasignarse

`const` permite declarar una variable que debe recibir un valor inicial y que no puede reasignarse posteriormente.

```javascript
const libro = "The Shining";

console.log(libro);
```

Esto funciona correctamente.

Sin embargo, si intentamos cambiar su valor:

```javascript
const libro = "The Shining";

libro = "Pet Sematary";
```

JavaScript produce un error porque no se permite reasignar una variable declarada con `const`.

Tampoco podemos redeclararla en el mismo ámbito:

```javascript
const libro = "The Shining";

const libro = "Pet Sematary";
```

Este código también produce un error.

**Regla principal:** utilizá `const` cuando no necesites reasignar la variable.

Una aclaración importante: `const` no significa que absolutamente todo lo almacenado sea inmutable. Si una variable constante contiene un objeto o un array, sus propiedades o elementos pueden modificarse, aunque no se pueda asignar un objeto o array diferente a esa misma variable.

### 6. Comparación entre var, let y const

| Característica | `var` | `let` | `const` |
|---|---|---|---|
| Permite declarar una variable | Sí | Sí | Sí |
| Permite redeclarar en el mismo ámbito | Sí | No | No |
| Permite reasignar el valor | Sí | Sí | No |
| Requiere valor inicial | No | No | Sí |
| Respeta el alcance de bloque | No | Sí | Sí |

El alcance de bloque significa que una variable declarada con `let` o `const` dentro de un bloque, delimitado por llaves `{}`, queda limitada a ese bloque. `var` no sigue esa misma regla.

### 7. ¿Por qué evitar var?

El problema de `var` no es que siempre funcione mal. El problema es que su comportamiento puede resultar inesperado.

Observá este ejemplo:

```javascript
if (true) {
    var mensaje = "Hola";
}

console.log(mensaje);
```

El código muestra:

```text
Hola
```

La variable declarada con `var` puede utilizarse fuera del bloque `if`.

En cambio:

```javascript
if (true) {
    let mensaje = "Hola";
}

console.log(mensaje);
```

En este caso se produce un error porque `mensaje` solo existe dentro del bloque.

Lo mismo sucede con `const`.

Este comportamiento hace que `let` y `const` permitan limitar mejor el alcance de las variables y reduzcan ciertos errores accidentales.

### 8. ¿Cuándo utilizar let y cuándo const?

Una buena regla para comenzar es la siguiente:

- Utilizá `const` por defecto cuando la variable no necesite reasignarse.
- Utilizá `let` cuando necesites cambiar su valor.
- Evitá `var` en código nuevo, salvo que exista una razón concreta para utilizarlo.

Ejemplo con `const`:

```javascript
const nombreUsuario = "Valentín";
const pais = "Argentina";

console.log(nombreUsuario, pais);
```

Ejemplo con `let`:

```javascript
let nivel = 1;

nivel = 2;
nivel = 3;

console.log(nivel);
```

Resultado: `3`.

No hace falta utilizar `let` en todas las variables por costumbre. Elegir `const` cuando corresponde ayuda a dejar claro qué valores no necesitan reasignarse.

### 9. Actividades prácticas

Realizá las siguientes actividades en un archivo llamado `main.js`.

**Actividad 1. Identificar la palabra clave**

Indicá si cada declaración utiliza `var`, `let` o `const` y explicá qué permite hacer.

```javascript
var serie = "ER";
let videojuego = "Sonic";
const libro = "The Shining";
```

**Actividad 2. Detectar errores**

Analizá el código:

```javascript
let personaje = "Sonic";

let personaje = "Shadow";

console.log(personaje);
```

Respondé:

- ¿Qué error se produce?
- ¿Por qué sucede?
- ¿Cómo lo solucionarías sin cambiar el nombre de la variable?

**Actividad 3. Reasignación**

¿Qué resultado produce este programa?

```javascript
let protagonista = "Sonic";

protagonista = "Shadow";

protagonista = "Silver";

console.log(protagonista);
```

Explicá por qué se imprime ese valor.

**Actividad 4. El caso de const**

Encontrá el problema:

```javascript
const consola = "PlayStation 1";

consola = "PlayStation 2";

console.log(consola);
```

¿Por qué no funciona? ¿Qué palabra clave utilizarías si necesitaras cambiar el valor?

**Actividad 5. Alcance de bloque**

Analizá el siguiente ejemplo:

```javascript
if (true) {
    let nombre = "Buffy";
}

console.log(nombre);
```

¿El programa funciona? Justificá tu respuesta.

**Actividad 6. Elegir correctamente**

Creá tres variables para representar:

- El nombre de un videojuego que no necesitás cambiar.
- La cantidad de vidas de un personaje que puede variar.
- El nombre de un libro que no necesitás cambiar.

Elegí entre `let` y `const` para cada una y explicá tu decisión.

### 10. Resumen del capítulo

- `var` es la forma tradicional y permite redeclarar y reasignar dentro del mismo ámbito.
- `let` permite reasignar, pero no redeclarar el mismo identificador en el mismo ámbito.
- `const` requiere una inicialización y no permite reasignar la variable.
- `let` y `const` respetan el alcance de bloque.
- En JavaScript moderno se recomienda utilizar `const` cuando sea posible y `let` cuando sea necesario cambiar el valor.
- Comprender estas diferencias ayuda a escribir código más claro, predecible y fácil de mantener.

### 11. Recursos recomendados

- [MDN: Declaraciones y tipos de variables](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#declarations)
- [MDN: var](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
- [MDN: let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [MDN: const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

**Consejo final:** no memorices solamente qué palabra clave usar. Practicá los tres casos, provocá los errores y observá los mensajes de JavaScript. Entender por qué algo falla es tan importante como saber escribir código que funciona.
