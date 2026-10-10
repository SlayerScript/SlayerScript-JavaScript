# SLAYERSCRIPT
## Capítulo 2: Variables y tipos de datos en JavaScript

### 1. Objetivos de aprendizaje

Al finalizar este capítulo, vas a poder:

- Comprender qué es una variable y para qué sirve.
- Declarar variables utilizando `let`, `const` y conocer `var`.
- Identificar los tipos de datos básicos de JavaScript.
- Reasignar valores y comprender cómo cambian las variables.
- Aplicar buenas prácticas al nombrar variables.
- Reconocer errores comunes relacionados con los tipos de datos y las mayúsculas.

### 2. ¿Qué es una variable?

Una variable es un nombre que utilizamos para acceder a un valor almacenado durante la ejecución de un programa.

Por ejemplo:

```javascript
let nombre = "Lucía";

console.log(nombre);
```

**Resultado:**

```text
Lucía
```

En este ejemplo:

- `let` declara la variable.
- `nombre` es el identificador de la variable.
- `=` es el operador de asignación.
- `"Lucía"` es el valor almacenado.
- `console.log()` muestra el valor en la consola.

La ventaja de utilizar variables es que podemos reutilizar un dato sin tener que escribirlo repetidamente.

### 3. Tipos de datos básicos

JavaScript permite almacenar diferentes tipos de valores. En este capítulo vamos a trabajar con los siguientes.

#### 3.1. String: cadenas de texto

Un `string` representa texto, como nombres, palabras o frases.

Podemos escribir cadenas de texto utilizando comillas simples, comillas dobles o *backticks*.

```javascript
let nombre = "Lucía";
let apellido = 'Gómez';
let saludo = `Hola, mundo`;

console.log(nombre, apellido, saludo);
```

Los tres ejemplos son cadenas de texto válidas.

Los *backticks* también permiten insertar variables dentro de un texto mediante las expresiones `${...}`:

```javascript
let nombre = "Lucía";

console.log(`Hola, ${nombre}`);
```

**Resultado:**

```text
Hola, Lucía
```

Esta característica se conoce como *interpolación de cadenas* y resulta especialmente útil cuando trabajamos con mensajes dinámicos.

#### 3.2. Number: números

En JavaScript, el tipo `number` representa tanto números enteros como números decimales.

```javascript
let edad = 25;
let precio = 1999.99;
let temperatura = -5;

console.log(edad, precio, temperatura);
```

No necesitamos declarar por separado un tipo entero y otro decimal. JavaScript utiliza `number` para ambos.

**Importante:** en el código se utiliza el punto para representar decimales, no la coma.

#### 3.3. Boolean: valores lógicos

Un `boolean` solo puede tener dos valores:

- `true`: verdadero.
- `false`: falso.

```javascript
let estaActivo = true;
let tienePermiso = false;

console.log(estaActivo, tienePermiso);
```

Estos valores se utilizan habitualmente en condiciones, validaciones y decisiones dentro de un programa.

No es lo mismo escribir `true` que `"true"`:

```javascript
let activo = true;
let texto = "true";

console.log(typeof activo); // "boolean"
console.log(typeof texto); // "string"
```

Las comillas convierten el contenido en texto.

#### 3.4. Undefined: valor no definido

Una variable declarada sin asignarle un valor comienza con el valor `undefined` si se declara con `let` o `var`.

```javascript
let nombre;

console.log(nombre);
```

**Resultado:**

```text
undefined
```

Esto significa que la variable existe, pero todavía no tiene un valor asignado.

#### 3.5. Null: ausencia intencional de valor

`null` representa la ausencia intencional de un valor.

```javascript
let usuarioSeleccionado = null;

console.log(usuarioSeleccionado);
```

**Resultado:**

```text
null
```

Aunque `undefined` y `null` suelen relacionarse con la ausencia de un valor, no significan exactamente lo mismo.

Una particularidad histórica de JavaScript es que:

```javascript
console.log(typeof null);
```

Devuelve `"object"`. Es un comportamiento heredado del lenguaje que se conserva por compatibilidad. No significa que `null` sea realmente un objeto.

### 4. Declaración de variables: var, let y const

En JavaScript existen tres palabras clave tradicionales para declarar variables.

**`var`**

Es una forma antigua de declarar variables. Tiene reglas de alcance y redeclaración que pueden provocar confusiones, por lo que no suele recomendarse para código nuevo.

**`let`**

Permite declarar una variable cuyo valor puede cambiar.

```javascript
let edad = 20;

edad = 21;

console.log(edad);
```

Resultado: `21`.

**`const`**

Permite declarar una variable que no puede recibir una nueva asignación después de su inicialización.

```javascript
const pais = "Argentina";

console.log(pais);
```

No podemos hacer posteriormente `pais = "Chile"`.

Como regla inicial, utilizá `const` cuando no necesites reasignar el valor y `let` cuando sí necesites cambiarlo. Reservá `var` para comprender código existente o estudiar sus particularidades.

### 5. Reasignación de variables

La reasignación consiste en darle un nuevo valor a una variable que ya fue declarada.

```javascript
let protagonista = "Buffy";

console.log(protagonista);

protagonista = "Faith";

console.log(protagonista);
```

**Resultado:**

```text
Buffy
Faith
```

La variable mantiene su nombre, pero su valor cambia.

También podemos reasignar números y valores booleanos:

```javascript
let edad = 10;
edad = 15;

let estaVivo = true;
estaVivo = false;

console.log(edad);
console.log(estaVivo);
```

Resultado:

```text
15
false
```

Si imprimimos la variable después de reasignarla, obtenemos su valor actual. Si la imprimimos antes y después, vemos ambos valores en el orden en que se ejecutó el programa.

**Una buena práctica:** procurá que cada variable tenga un propósito claro y un tipo de dato coherente. JavaScript permite cambiar el tipo de valor de una variable declarada con `let`, pero mezclar tipos sin una razón clara puede volver el código más difícil de comprender.

### 6. Buenas prácticas al nombrar variables

#### 6.1. Utilizar nombres descriptivos

Un nombre debe explicar qué representa el dato.

Menos claro:

```javascript
let x = "Lucía";
```

Más claro:

```javascript
let nombreUsuario = "Lucía";
```

En un ejemplo matemático, utilizar `x` o `y` puede tener sentido. En una aplicación real, los nombres descriptivos ayudan a comprender el código.

#### 6.2. Utilizar camelCase

En JavaScript es habitual utilizar *camelCase* para los nombres de variables.

La primera palabra comienza en minúscula y las siguientes comienzan con mayúscula.

```javascript
let nombreUsuario = "Lucía";
let precioFinal = 1500;
let cantidadProductos = 3;
```

Estas formas no son equivalentes:

```javascript
let nombreUsuario = "Lucía";
let nombreusuario = "María";
let NombreUsuario = "Pedro";
```

JavaScript distingue entre mayúsculas y minúsculas, por lo que son tres identificadores diferentes.

#### 6.3. Evitar declarar dos veces la misma variable innecesariamente

Con `let` no podemos declarar dos veces el mismo identificador en el mismo ámbito.

```javascript
let nombre = "Buffy";
let nombre = "Faith"; // Error
```

La forma correcta de cambiar el valor es reasignarlo:

```javascript
let nombre = "Buffy";
nombre = "Faith";

console.log(nombre);
```

Resultado: `Faith`.

#### 6.4. Respetar el tipo de dato esperado

Observá estos dos ejemplos:

```javascript
let suma = 10 + 10;
console.log(suma);
```

Resultado: `20`.

En cambio:

```javascript
let texto = "10" + "10";
console.log(texto);
```

Resultado: `"1010"`.

En el segundo caso, ambos operandos son cadenas de texto y el operador `+` concatena los valores.

Por eso es importante prestar atención a las comillas y al tipo de dato que queremos utilizar.

### 7. Errores comunes

**Error 1: olvidar las comillas en una cadena de texto.**

```javascript
let nombre = Lucía;
```

JavaScript interpretará `Lucía` como un identificador, no como texto, y producirá un error si ese identificador no está definido.

Corrección:

```javascript
let nombre = "Lucía";
```

**Error 2: escribir un booleano como texto.**

```javascript
let activo = "false";
```

Esto es un `string`, no un `boolean`.

Corrección:

```javascript
let activo = false;
```

**Error 3: utilizar un nombre con mayúsculas diferentes.**

```javascript
let precioFinal = 100;

console.log(preciofinal);
```

La segunda línea provoca un error porque `preciofinal` no es el mismo identificador que `precioFinal`.

**Error 4: volver a declarar una variable con `let`.**

```javascript
let edad = 20;
let edad = 21;
```

Corrección:

```javascript
let edad = 20;
edad = 21;
```

**Error 5: creer que `null` y `undefined` son idénticos.**

Ambos se relacionan con la ausencia de valor, pero se utilizan en situaciones diferentes. `undefined` suele indicar que un valor no fue asignado, mientras que `null` puede utilizarse para representar una ausencia explícita.

### 8. Actividades prácticas

Realizá las siguientes actividades en un archivo llamado `main.js`.

**Actividad 1. Declaración de variables**

Creá tres variables:

- Una cadena de texto que almacene tu nombre.
- Un número que represente tu edad.
- Un booleano que indique si estás estudiando programación.

Mostrá los tres valores en la consola. Podés imprimirlos en una misma llamada a `console.log()` o en llamadas separadas.

**Actividad 2. Comparación de valores**

Analizá el siguiente código:

```javascript
let nombre = "Willow";
let Nombre = "Willow";
```

Respondé: ¿las dos variables son iguales? Justificá tu respuesta considerando cómo JavaScript interpreta los identificadores.

**Actividad 3. Corrección de errores**

Encontrá y corregí el problema:

```javascript
let bruja = "Willow";

console.log(Bruja);
```

Explicá por qué se produce el error.

**Actividad 4. Convenciones de nombres**

¿Cuál de estas opciones sigue la convención camelCase?

```javascript
let protagonista_de_serie = "Buffy";
let ProtagonitaDeSerie = "Buffy";
let protagonistaDeSerie = "Buffy";
let PROTAGONISTADESERIE = "Buffy";
```

Elegí la opción correcta y justificá tu elección.

**Actividad 5. Tipos de datos**

Indicá qué tipo de dato representa cada variable:

```javascript
let nombre = "Sonic";
let edad = 16;
let esHeroe = true;
let enemigoDerrotado = null;
let personajeSecundario;
```

Podés comprobarlo utilizando `typeof`, recordando que `typeof null` devuelve `"object"` por una particularidad histórica de JavaScript.

**Actividad 6. Reasignación**

Analizá el siguiente código:

```javascript
let protagonista = "Sonic";

protagonista = "Shadow";

console.log(protagonista);
```

Indicá qué valor se imprime y explicá por qué.

Luego repetí el ejercicio con una variable numérica:

```javascript
let año = 1990;

año = 1991;

console.log(anio);
```

### 9. Resumen del capítulo

| Concepto | Descripción |
|---|---|
| `let` | Declara una variable que puede reasignarse. |
| `const` | Declara una variable que no puede reasignarse. |
| `var` | Forma tradicional de declarar variables, con reglas particulares. |
| `string` | Representa texto. |
| `number` | Representa números enteros y decimales. |
| `boolean` | Representa `true` o `false`. |
| `undefined` | Indica que un valor no está definido. |
| `null` | Representa una ausencia explícita de valor. |
| Reasignación | Cambia el valor de una variable existente. |
| `camelCase` | Convención habitual para nombrar variables en JavaScript. |
| `case-sensitive` | Distingue entre mayúsculas y minúsculas. |

### 10. Recursos recomendados

- [MDN: Variables](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Variables)
- [MDN: Tipos de datos y estructuras](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Data_structures)
- [MDN: let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [MDN: const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

**Recordá:** aprender programación no consiste solamente en mirar cómo otra persona escribe código. Escribirlo, equivocarse, leer los errores y corregirlos forma parte del aprendizaje.

Practicá los ejercicios antes de consultar las soluciones. El objetivo es que puedas explicar por qué funciona tu código, no solamente conseguir que funcione.
