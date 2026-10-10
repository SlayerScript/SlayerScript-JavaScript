# SLAYERSCRIPT
## Capítulo 5: Numbers en JavaScript

**Material complementario de estudio**

En este capítulo vamos a trabajar con operaciones matemáticas en JavaScript, aprender cómo se evalúan las expresiones y utilizar los métodos del objeto `Math` para redondear números y generar valores aleatorios.

---

## 1. Operaciones matemáticas básicas

JavaScript permite realizar operaciones matemáticas mediante operadores aritméticos.

| Operación | Operador | Ejemplo | Resultado |
|---|---|---|---:|
| Suma | `+` | `5 + 5` | `10` |
| Resta | `-` | `10 - 5` | `5` |
| Multiplicación | `*` | `5 * 5` | `25` |
| División | `/` | `10 / 5` | `2` |
| Potencia | `**` | `5 ** 2` | `25` |
| Resto | `%` | `101 % 5` | `1` |

Podemos imprimir los resultados en la consola utilizando `console.log()`.

```javascript
console.log(5 + 5);
console.log(10 - 5);
console.log(5 * 5);
console.log(10 / 5);
console.log(5 ** 2);
console.log(101 % 5);
```

### ¿Qué significa el operador de resto `%`?

El operador `%` devuelve el resto de una división.

```javascript
console.log(100 % 5); // 0
console.log(101 % 5); // 1
console.log(12 % 2);  // 0
console.log(13 % 2);  // 1
```

Este operador resulta especialmente útil para comprobar si un número es par o impar:

- Si `numero % 2` devuelve `0`, el número es par.
- Si `numero % 2` devuelve `1`, el número es impar cuando se trata de enteros positivos.

Más adelante, este recurso será útil al trabajar con condicionales y filtros.

---

## 2. Divisiones y resultados especiales

No todas las operaciones producen un número convencional.

### División por cero

```javascript
console.log(10 / 0);  // Infinity
console.log(10 / -0); // -Infinity
```

En JavaScript, dividir un número distinto de cero por `0` no genera automáticamente un error: produce `Infinity` o `-Infinity`, según el signo.

En cambio, `0 / 0` produce `NaN`.

### ¿Qué significa `NaN`?

`NaN` significa *Not-a-Number*. Representa un resultado numérico inválido.

```javascript
console.log(10 / "hola"); // NaN
console.log(0 / 0);       // NaN
```

Podemos comprobar si un resultado es `NaN` mediante `Number.isNaN()`:

```javascript
const resultado = 10 / "hola";

console.log(Number.isNaN(resultado)); // true
```

### Cuidado con los strings

JavaScript puede convertir algunos strings a números automáticamente según el operador utilizado.

```javascript
console.log(10 / "10"); // 1
console.log(10 + "10"); // "1010"
```

En el primer caso, la división convierte el string `"10"` en un número. En el segundo, el operador `+` concatena ambos valores como texto.

Para convertir explícitamente un valor a número, podemos usar `Number()`:

```javascript
const precio = "10";
const cantidad = 10;

console.log(Number(precio) + cantidad); // 20
```

**Importante:** no conviene depender de conversiones automáticas cuando queremos realizar cálculos. Es mejor comprobar y convertir los datos de forma explícita.

---

## 3. Precedencia de operadores

La precedencia determina qué operaciones se realizan primero dentro de una expresión.

Por ejemplo:

```javascript
console.log(10 * 10 + 20 + 20); // 140
```

La multiplicación se realiza antes que las sumas.

En cambio, podemos cambiar el orden mediante paréntesis:

```javascript
console.log(10 * (10 + 20) + 20); // 320
```

En este caso, primero se resuelve `10 + 20`, después se multiplica por `10` y finalmente se suma `20`.

### Orden general de prioridad

Para las operaciones vistas en este capítulo, recordá estas reglas:

1. Los paréntesis permiten agrupar operaciones y controlar su orden.
2. Las potencias tienen mayor precedencia que la multiplicación, la división, el resto, la suma y la resta.
3. La multiplicación, la división y el resto tienen mayor precedencia que la suma y la resta.
4. Cuando varios operadores tienen la misma precedencia, se aplica su asociatividad.

No hace falta memorizar todas las reglas de JavaScript de una sola vez. Lo importante es aprender a leer las expresiones y utilizar paréntesis cuando el orden pueda generar dudas.

---

## 4. Asociatividad

La asociatividad determina cómo se agrupan las operaciones cuando hay varios operadores con la misma precedencia.

### Operaciones de izquierda a derecha

La suma y la resta se agrupan normalmente de izquierda a derecha.

```javascript
console.log(20 + 6 + 54); // 80
console.log(20 - 6 - 54); // -40
```

En el segundo ejemplo, el cálculo es `(20 - 6) - 54`, cuyo resultado es `-40`.

### La excepción de las potencias

El operador de potencia `**` se asocia de derecha a izquierda.

```javascript
console.log(2 ** 3 ** 2); // 512
```

Esto equivale a:

```javascript
console.log(2 ** (3 ** 2)); // 512
```

Primero se calcula `3 ** 2`, que da `9`, y luego `2 ** 9`, que da `512`.

No equivale a `(2 ** 3) ** 2`, cuyo resultado sería `64`.

Cuando tengas dudas sobre el orden de una expresión, los paréntesis son tus aliados. La computadora no va a adivinar qué quisiste decir, por mucho entusiasmo que le pongas.

---

## 5. Redondeo con el objeto `Math`

JavaScript incluye el objeto `Math`, que ofrece métodos y propiedades para realizar operaciones matemáticas.

En este capítulo vamos a trabajar con tres métodos: `Math.round()`, `Math.floor()` y `Math.ceil()`.

### `Math.round()`: redondeo al entero más cercano

```javascript
console.log(Math.round(3.5));  // 4
console.log(Math.round(3.49)); // 3
console.log(Math.round(3.9));  // 4
```

`Math.round()` redondea al entero más cercano. En los casos que terminan exactamente en `.5`, el resultado se aproxima hacia el infinito positivo.

Por eso, con números negativos:

```javascript
console.log(Math.round(-3.5)); // -3
console.log(Math.round(-3.51)); // -4
```

### `Math.floor()`: redondeo hacia abajo

```javascript
console.log(Math.floor(3.99));  // 3
console.log(Math.floor(3.01));  // 3
console.log(Math.floor(-3.01)); // -4
```

`Math.floor()` devuelve el mayor entero que sea menor o igual al valor original.

En otras palabras, avanza hacia el infinito negativo. Por eso, `Math.floor(-3.01)` devuelve `-4`, no `-3`.

### `Math.ceil()`: redondeo hacia arriba

```javascript
console.log(Math.ceil(3.01));  // 4
console.log(Math.ceil(3.99));  // 4
console.log(Math.ceil(-3.01)); // -3
```

`Math.ceil()` devuelve el menor entero que sea mayor o igual al valor original. Avanza hacia el infinito positivo.

### Comparación rápida

| Método | Ejemplo | Resultado |
|---|---|---:|
| `Math.round()` | `Math.round(4.76)` | `5` |
| `Math.floor()` | `Math.floor(4.76)` | `4` |
| `Math.ceil()` | `Math.ceil(4.01)` | `5` |

Los tres métodos reciben un valor numérico y devuelven un resultado redondeado según su propia regla.

---

## 6. Números aleatorios con `Math.random()`

`Math.random()` devuelve un número pseudoaleatorio mayor o igual que `0` y menor que `1`.

```javascript
console.log(Math.random());
```

Algunos resultados posibles son `0.55`, `0.04` o `0.86`. Cada llamada puede devolver un valor diferente.

Pero ¿qué pasa si queremos un número entero entre `0` y `9`?

### Generar un entero entre 0 y 9

Podemos combinar `Math.random()` con `Math.floor()`:

```javascript
const numeroAleatorio = Math.floor(Math.random() * 10);

console.log(numeroAleatorio);
```

La fórmula funciona de la siguiente manera:

1. `Math.random()` genera un valor entre `0` inclusive y `1` exclusive.
2. Multiplicarlo por `10` produce un valor entre `0` inclusive y `10` exclusive.
3. `Math.floor()` redondea hacia abajo y devuelve un entero entre `0` y `9`.

### Generar un entero entre 1 y 10

Si queremos incluir el `10` y excluir el `0`, sumamos `1` al resultado:

```javascript
const numeroAleatorio = Math.floor(Math.random() * 10) + 1;

console.log(numeroAleatorio);
```

Ahora el resultado puede ser cualquier entero entre `1` y `10`, ambos incluidos.

### Crear un dado de seis caras

Para simular un dado necesitamos obtener un entero entre `1` y `6`.

```javascript
const dado = Math.floor(Math.random() * 6) + 1;

console.log(dado);
```

La multiplicación por `6` genera un rango que incluye el `0`, pero excluye el `6`. `Math.floor()` transforma ese rango en enteros de `0` a `5`. Finalmente, sumamos `1` para obtener los resultados posibles del dado: `1`, `2`, `3`, `4`, `5` y `6`.

**¿Por qué no usar `Math.ceil()`?**

Porque `Math.ceil(Math.random() * 6)` puede devolver resultados entre `0` y `6`, con una distribución distinta: el `0` puede aparecer cuando `Math.random()` devuelve exactamente `0`, mientras que los demás resultados no tienen la misma probabilidad. Para este caso, `Math.floor()` más `1` es la solución sencilla y adecuada.

---

## 7. Buenas prácticas

- Usá `console.log()` para comprobar los resultados de tus operaciones.
- Utilizá paréntesis para dejar claro el orden de cálculo.
- Recordá que `+` puede sumar números o concatenar strings.
- No confundas `Math.round()`, `Math.floor()` y `Math.ceil()`.
- Para generar un entero aleatorio dentro de un rango, calculá cuidadosamente los límites.
- No supongas que `Math.random()` puede devolver `1`: su resultado siempre es menor que `1`.
- Si trabajás con datos que vienen de formularios o strings, validalos antes de usarlos en operaciones matemáticas.

---

## 8. Actividades prácticas

### Ejercicio 1: operaciones aritméticas

Escribí un programa que muestre por consola una operación de cada tipo:

- Suma.
- Resta.
- Multiplicación.
- División.
- Potencia.
- Resto.

Los resultados deben corresponder a las operaciones realizadas.

### Ejercicio 2: precedencia

Creá una expresión matemática que combine multiplicación y suma.

1. Mostrá el resultado sin paréntesis.
2. Modificá la expresión utilizando paréntesis.
3. Explicá por qué cambió el resultado.

### Ejercicio 3: asociatividad

Escribí expresiones con sumas y restas encadenadas. Mostrá sus resultados y explicá cómo se agrupan las operaciones.

Incluí también un ejemplo con potencias que permita comprobar la asociatividad de derecha a izquierda.

### Ejercicio 4: redondeo

Utilizá los tres métodos vistos en el capítulo: `Math.round()`, `Math.floor()` y `Math.ceil()`.

Probá cada método con estos números:

- `4.76`
- `150`
- `94.49`
- `-13.49`

Imprimí los resultados por consola e identificá qué regla aplica cada método.

### Ejercicio 5: crear un dado

Programá un dado de seis caras que muestre un resultado aleatorio entre `1` y `6` cada vez que se ejecuta.

**Condiciones:**

- El resultado debe ser un número entero.
- El `1` y el `6` deben estar incluidos entre los resultados posibles.
- Utilizá `Math.random()` y un método de redondeo adecuado.
- Explicá por qué elegiste esa fórmula.

---

## 9. Resumen del capítulo

| Concepto | Para qué sirve |
|---|---|
| Operadores aritméticos | Realizar cálculos |
| `%` | Obtener el resto de una división |
| Precedencia | Determinar qué operación se ejecuta primero |
| Asociatividad | Determinar cómo se agrupan operadores de igual precedencia |
| `Math.round()` | Redondear al entero más cercano |
| `Math.floor()` | Redondear hacia el infinito negativo |
| `Math.ceil()` | Redondear hacia el infinito positivo |
| `Math.random()` | Generar un número pseudoaleatorio entre `0` inclusive y `1` exclusive |
| `Number()` | Convertir explícitamente un valor a número |
| `Number.isNaN()` | Comprobar si un valor es `NaN` |

---

## 10. Recursos adicionales

- MDN: [Operadores aritméticos](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Expressions_and_operators#operadores_aritm%C3%A9ticos)
- MDN: [Precedencia de operadores](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Operator_precedence)
- MDN: [`Math.round()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/round)
- MDN: [`Math.floor()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
- MDN: [`Math.ceil()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil)
- MDN: [`Math.random()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Math/random)

**Conclusión:** practicar es fundamental para aprender programación. No alcanza con reconocer los operadores o copiar una fórmula: hay que ejecutarla, observar el resultado y entender por qué funciona.
