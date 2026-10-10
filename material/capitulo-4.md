# SLAYERSCRIPT
## Capítulo 4: Strings en JavaScript (Nivel 1)

### 1. Objetivos de aprendizaje

Al finalizar este capítulo, vas a poder:

- Declarar cadenas de texto utilizando comillas simples, dobles y *backticks*.
- Acceder a caracteres individuales mediante índices.
- Utilizar secuencias de escape para dar formato al texto.
- Concatenar cadenas y utilizar *template literals*.
- Buscar palabras y caracteres dentro de una cadena.
- Obtener la longitud de un texto y extraer fragmentos.
- Eliminar espacios innecesarios con métodos de JavaScript.

### 2. ¿Qué es un string?

Un `string` es un tipo de dato que representa una cadena de texto. Puede contener letras, números, espacios, símbolos y otros caracteres.

Por ejemplo:

```javascript
let personaje = "Buffy";
let videojuego = "Sonic";
let mensaje = "Bienvenidos a SlayerScript";

console.log(personaje);
console.log(videojuego);
console.log(mensaje);
```

Los números también pueden formar parte de un string si están escritos como texto:

```javascript
let numeroComoTexto = "123";
let numeroReal = 123;
```

Aunque ambos contienen los caracteres `123`, representan tipos de datos diferentes. El primero es un `string` y el segundo es un `number`.

### 3. Formas de declarar strings

JavaScript permite declarar cadenas de texto de tres formas principales.

#### 3.1. Comillas dobles

```javascript
let serie = "Buffy the Vampire Slayer";
```

#### 3.2. Comillas simples

```javascript
let serie = 'Stranger Things';
```

#### 3.3. Backticks o comillas invertidas

```javascript
let serie = `Law & Order`;
```

Las tres formas son válidas. Sin embargo, los *backticks* ofrecen características adicionales, como permitir textos multilínea e insertar expresiones dentro de una cadena.

Esta última característica se conoce como *interpolación* y se explica más adelante.

### 4. Índices: acceder a caracteres

Los strings permiten acceder a sus caracteres mediante índices. En JavaScript, **los índices comienzan en cero**, no en uno.

Tomemos como ejemplo la palabra `Kitana`:

| Carácter | K | i | t | a | n | a |
|---|---:|---:|---:|---:|---:|---:|
| Índice | 0 | 1 | 2 | 3 | 4 | 5 |

Podemos acceder a un carácter utilizando corchetes:

```javascript
let personaje = "Kitana";

console.log(personaje[0]);
console.log(personaje[3]);
console.log(personaje[5]);
```

Resultado:

```text
K
a
a
```

Si intentamos acceder a una posición que no existe, obtenemos `undefined`:

```javascript
let personaje = "Kitana";

console.log(personaje[6]);
```

Resultado:

```text
undefined
```

El string tiene seis caracteres y sus índices válidos van del `0` al `5`.

**Importante:** los índices no son infinitos dentro de una cadena. Solo existen posiciones válidas para los caracteres que contiene. Acceder fuera de ese rango no genera automáticamente una nueva posición.

### 5. Secuencias de escape

Las secuencias de escape permiten representar caracteres especiales dentro de un string. Se escriben utilizando una barra invertida, llamada *backslash* (`\`), seguida de otro carácter.

Las más importantes de este capítulo son:

| Secuencia | Función |
|---|---|
| `\n` | Salto de línea |
| `\t` | Tabulación |
| `\'` | Comilla simple |
| `\"` | Comilla doble |
| `\\` | Barra invertida literal |

#### 5.1. Salto de línea

```javascript
let mensaje = "Buffy\nThe Vampire Slayer";

console.log(mensaje);
```

Resultado:

```text
Buffy
The Vampire Slayer
```

La secuencia `\n` indica que el texto debe continuar en una nueva línea.

#### 5.2. Tabulación

```javascript
let serie = "Stranger\tThings";

console.log(serie);
```

La secuencia `\t` inserta una tabulación entre ambas palabras.

#### 5.3. Escapar comillas

Si queremos incluir comillas del mismo tipo que delimitan el string, debemos escaparlas o utilizar otro tipo de comillas para delimitarlo.

Por ejemplo:

```javascript
let frase = 'Ramsés dijo: "Devuelvan la tablilla"';

console.log(frase);
```

También podemos utilizar comillas dobles y escapar las comillas interiores:

```javascript
let frase = "Ramsés dijo: \"Devuelvan la tablilla\"";

console.log(frase);
```

Ambos ejemplos son válidos.

### 6. Strings multilínea con backticks

Una de las ventajas de los *backticks* es que permiten escribir cadenas que ocupan varias líneas sin tener que insertar manualmente `\n`.

```javascript
let serie = `Buffy the Vampire Slayer
Stranger Things
Law & Order`;

console.log(serie);
```

El resultado conserva los saltos de línea escritos en el código.

Esto resulta práctico cuando necesitamos crear mensajes largos, textos descriptivos o contenido con varias líneas.

Los *backticks* también permiten insertar variables dentro del texto, algo que veremos en la siguiente sección.

### 7. Concatenación y template literals

La concatenación consiste en unir dos o más cadenas de texto para formar una nueva.

#### 7.1. Concatenación con el operador +

```javascript
let nombre = "Valentín";
let apellido = "Leorest";

let nombreCompleto = nombre + " " + apellido;

console.log(nombreCompleto);
```

Resultado:

```text
Valentín Leorest
```

El operador `+` une las cadenas. En este ejemplo agregamos `" "` para separar el nombre del apellido.

También podemos construir mensajes completos:

```javascript
let nombre = "Valentín";
let edad = 26;
let bandaFavorita = "Judas Priest";

let mensaje = "Me llamo " + nombre +
    ", tengo " + edad +
    " años y mi banda favorita es " + bandaFavorita + ".";

console.log(mensaje);
```

Este método funciona, pero cuando hay muchas variables puede resultar difícil de leer y mantener los espacios correctamente.

#### 7.2. Template literals

Los *template literals* utilizan backticks y permiten insertar variables o expresiones con la sintaxis `${...}`.

```javascript
let nombre = "Valentín";
let edad = 26;
let bandaFavorita = "Judas Priest";
let videojuegoFavorito = "God of War II";

let mensaje = `Me llamo ${nombre}, tengo ${edad} años.
Mi banda favorita es ${bandaFavorita}.
Mi videojuego favorito es ${videojuegoFavorito}.`;

console.log(mensaje);
```

Este enfoque facilita la lectura del código y permite insertar variables sin concatenar cada fragmento manualmente.

**Recordá:** para interpolar una variable, necesitás utilizar backticks y la sintaxis `${variable}`. Escribir `"Hola ${nombre}"` entre comillas comunes no realiza la interpolación.

### 8. Métodos para trabajar con strings

Los strings cuentan con métodos que permiten buscar contenido, extraer fragmentos y limpiar espacios.

Los métodos no modifican directamente la cadena original: devuelven un resultado que podemos mostrar o almacenar en otra variable.

#### 8.1. indexOf()

El método `indexOf()` busca la primera aparición de un texto dentro de una cadena y devuelve su índice.

```javascript
let juego = "Devil May Cry";

console.log(juego.indexOf("D"));
console.log(juego.indexOf("May"));
console.log(juego.indexOf("Cry"));
```

Resultado:

```text
0
7
10
```

Si el texto buscado no aparece, devuelve `-1`:

```javascript
let juego = "Devil May Cry";

console.log(juego.indexOf("Resident Evil"));
```

Resultado:

```text
-1
```

También podemos indicar desde qué índice comenzar la búsqueda:

```javascript
let texto = "JavaScript es genial. JavaScript es útil.";

console.log(texto.indexOf("JavaScript", 1));
```

El método buscará a partir del índice `1`, por lo que encontrará la siguiente aparición de `JavaScript`.

**Importante:** `indexOf()` distingue entre mayúsculas y minúsculas. Buscar `"may"` no es lo mismo que buscar `"May"`.

#### 8.2. includes()

El método `includes()` permite comprobar si una cadena contiene determinado texto. Devuelve un booleano: `true` o `false`.

```javascript
let juego = "Devil May Cry";

console.log(juego.includes("May"));
console.log(juego.includes("Resident Evil"));
```

Resultado:

```text
true
false
```

También distingue entre mayúsculas y minúsculas:

```javascript
let juego = "Devil May Cry";

console.log(juego.includes("may"));
```

Resultado: `false`.

**Diferencia principal:**

- `indexOf()` devuelve la posición donde encuentra el texto o `-1` si no lo encuentra.
- `includes()` devuelve `true` si lo encuentra y `false` si no.

#### 8.3. length

La propiedad `length` devuelve la longitud de un string.

```javascript
let palabra = "SlayerScript";

console.log(palabra.length);
```

Resultado:

```text
12
```

A diferencia de los métodos anteriores, `length` es una propiedad, por lo que no lleva paréntesis.

Los espacios también cuentan:

```javascript
let frase = "Hola mundo";

console.log(frase.length);
```

Resultado: `10`.

En este caso se cuentan los nueve caracteres de las palabras y el espacio que las separa.

#### 8.4. slice()

El método `slice()` permite extraer una parte de una cadena.

Recibe dos argumentos:

- El índice inicial.
- El índice final, que **no está incluido** en el resultado.

```javascript
let palabra = "SlayerScript";

console.log(palabra.slice(0, 5));
console.log(palabra.slice(5, 12));
```

Resultado:

```text
Slaye
rScript
```

Si omitimos el índice final, se extrae el resto de la cadena desde el índice inicial:

```javascript
let palabra = "SlayerScript";

console.log(palabra.slice(6));
```

Resultado:

```text
Script
```

También podemos utilizar índices negativos para contar desde el final:

```javascript
let palabra = "SlayerScript";

console.log(palabra.slice(-6));
```

Resultado:

```text
Script
```

El método `slice()` no elimina caracteres de la variable original. Devuelve una nueva cadena con el fragmento solicitado.

#### 8.5. trim()

Cuando recibimos texto de un formulario o de otra fuente, puede contener espacios innecesarios al principio o al final.

El método `trim()` elimina esos espacios de ambos extremos.

```javascript
let usuario = "   Valentín   ";

console.log(usuario.trim());
```

Resultado:

```text
Valentín
```

También existen dos métodos para limpiar solamente un extremo:

```javascript
let texto = "   SlayerScript   ";

console.log(texto.trimStart());
console.log(texto.trimEnd());
```

- `trimStart()` elimina los espacios iniciales.
- `trimEnd()` elimina los espacios finales.

Ninguno elimina los espacios que aparecen entre palabras.

### 9. Buenas prácticas

Al trabajar con strings, conviene recordar lo siguiente:

1. Elegí nombres descriptivos para las variables.
2. Utilizá backticks cuando necesites interpolación o textos multilínea.
3. Prestá atención a los espacios al concatenar cadenas.
4. Recordá que los índices comienzan en cero.
5. Tené en cuenta que `indexOf()` devuelve `-1` cuando no encuentra el texto.
6. Usá `includes()` cuando solo necesites comprobar si algo existe.
7. Utilizá `trim()` para limpiar espacios innecesarios en los extremos de una cadena.
8. Guardá el resultado de un método si necesitás reutilizarlo.

Ejemplo:

```javascript
let entrada = "   Buffy   ";
let nombreLimpio = entrada.trim();

console.log(nombreLimpio);
console.log(nombreLimpio.length);
```

### 10. Actividades prácticas

Realizá las siguientes actividades en un archivo llamado `main.js`.

**Actividad 1. Declaración**

Creá tres variables con el nombre de una serie, utilizando respectivamente:

- Comillas dobles.
- Comillas simples.
- Backticks.

Mostrá sus valores en la consola.

**Actividad 2. Acceder a índices**

Creá una variable que almacene la palabra `"Kitana"`.

- Mostrá el primer carácter.
- Mostrá el cuarto carácter.
- Mostrá el último carácter.
- Intentá acceder al índice `6` y explicá qué sucede.

**Actividad 3. Secuencias de escape**

Creá un mensaje que contenga:

- Un salto de línea.
- Una tabulación.
- Una frase entre comillas.

Mostrá el resultado en la consola.

**Actividad 4. Concatenación**

Creá las variables `nombre`, `apellido` y `edad`.

Primero, construí un mensaje utilizando el operador `+`. Después, escribí el mismo mensaje con un template literal.

**Actividad 5. Búsqueda**

Utilizá esta cadena:

```javascript
let juego = "Devil May Cry";
```

Respondé mediante código:

- ¿En qué índice comienza `"May"`?
- ¿Existe la palabra `"Cry"`?
- ¿Qué devuelve `indexOf("Resident Evil")`?
- ¿Qué devuelve `includes("may")` y por qué?

**Actividad 6. Longitud y extracción**

Creá una variable con el texto `"SlayerScript"`.

- Mostrá su longitud.
- Extraé los primeros cinco caracteres.
- Extraé los caracteres desde el índice `6` hasta el final.
- Explicá por qué el índice final de `slice()` no se incluye.

**Actividad 7. Limpieza de texto**

Utilizá la siguiente variable:

```javascript
let texto = "   Aprendiendo JavaScript   ";
```

Mostrá:

- El texto original.
- El texto limpio con `trim()`.
- El texto con los espacios iniciales eliminados.
- El texto con los espacios finales eliminados.

**Actividad 8. Ficha personal**

Creá variables para almacenar tu nombre, edad, videojuego favorito y serie favorita.

Utilizá un template literal para construir una ficha que muestre todos esos datos en varias líneas.

### 11. Resumen del capítulo

| Concepto | Función |
|---|---|
| `string` | Representa una cadena de texto. |
| Comillas simples y dobles | Permiten declarar cadenas de texto. |
| Backticks | Permiten interpolación y textos multilínea. |
| Índices | Permiten acceder a caracteres; comienzan en cero. |
| `\n` | Inserta un salto de línea. |
| `\t` | Inserta una tabulación. |
| `+` | Permite concatenar cadenas. |
| `${...}` | Inserta valores o expresiones en un template literal. |
| `indexOf()` | Busca un texto y devuelve su índice o `-1`. |
| `includes()` | Comprueba si una cadena contiene un texto. |
| `length` | Devuelve la longitud de una cadena. |
| `slice()` | Extrae una parte de una cadena. |
| `trim()` | Elimina espacios en ambos extremos. |
| `trimStart()` | Elimina espacios iniciales. |
| `trimEnd()` | Elimina espacios finales. |

### 12. Recursos recomendados

- [MDN: Strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)
- [MDN: Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
- [MDN: indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)
- [MDN: includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
- [MDN: slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
- [MDN: trim()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim)

**Recordá:** mirar ejemplos ayuda, pero escribirlos por tu cuenta es lo que permite aprender. Probá modificar los valores, buscá palabras que no existan y observá qué devuelve cada método. Entender esos resultados es el primer paso para manipular datos de manera eficaz.
