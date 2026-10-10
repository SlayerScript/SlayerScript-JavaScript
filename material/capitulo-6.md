# SLAYERSCRIPT
## Capítulo 6: Operadores en JavaScript (Parte 1)

**Material complementario de estudio**

En este capítulo vamos a estudiar cuatro grupos de operadores: asignación, incremento y decremento, comparación y operadores lógicos.

Estos conceptos son fundamentales para trabajar con variables, construir expresiones y preparar nuestros primeros condicionales.

---

## 1. Repaso: operadores aritméticos

Los operadores aritméticos permiten realizar cálculos matemáticos.

| Operación | Operador | Ejemplo |
|---|---|---|
| Suma | `+` | `5 + 5` |
| Resta | `-` | `10 - 5` |
| Multiplicación | `*` | `5 * 5` |
| División | `/` | `10 / 5` |
| Potencia | `**` | `5 ** 2` |
| Resto | `%` | `101 % 5` |

Ejemplo:

```javascript
console.log(5 + 5);   // 10
console.log(10 - 5);  // 5
console.log(5 * 5);   // 25
console.log(10 / 5);  // 2
console.log(5 ** 2);  // 25
console.log(101 % 5); // 1
```

En este capítulo vamos a reutilizar estos operadores para modificar el valor de una variable.

---

## 2. Operadores de asignación

El operador de asignación `=` permite guardar un valor en una variable.

```javascript
let numero = 10;

console.log(numero); // 10
```

Si necesitamos modificar ese valor, podemos reasignarlo:

```javascript
numero = 20;

console.log(numero); // 20
```

También podemos combinar una operación aritmética con la asignación para actualizar el valor almacenado.

### Operadores de asignación compuesta

| Operador | Equivale a | Ejemplo con `numero = 10` |
|---|---|---|
| `+=` | `numero = numero + valor` | `numero += 5` |
| `-=` | `numero = numero - valor` | `numero -= 5` |
| `*=` | `numero = numero * valor` | `numero *= 2` |
| `/=` | `numero = numero / valor` | `numero /= 2` |
| `**=` | `numero = numero ** valor` | `numero **= 2` |
| `%=` | `numero = numero % valor` | `numero %= 3` |

Ejemplo:

```javascript
let numero = 10;

numero += 10;
console.log(numero); // 20

numero -= 5;
console.log(numero); // 15

numero *= 2;
console.log(numero); // 30

numero /= 3;
console.log(numero); // 10
```

Cada operación modifica el valor de la variable. Por eso, el resultado de una instrucción influye en las siguientes.

**Importante:** `=` asigna un valor. No significa que dos valores sean iguales. Para compararlos vamos a utilizar otros operadores.

---

## 3. Incremento y decremento

Los operadores de incremento y decremento permiten aumentar o disminuir una variable numérica en una unidad.

- `++` incrementa el valor en `1`.
- `--` decrementa el valor en `1`.

Ejemplo:

```javascript
let vidas = 3;

vidas++;
console.log(vidas); // 4

vidas--;
console.log(vidas); // 3
```

Si necesitamos aumentar o disminuir el valor en una cantidad diferente de uno, podemos utilizar la asignación compuesta:

```javascript
let vidas = 3;

vidas += 2;
console.log(vidas); // 5

vidas -= 2;
console.log(vidas); // 3
```

### Prefijo y postfijo

Los operadores `++` y `--` pueden escribirse antes o después de la variable. La diferencia importa cuando utilizamos la operación dentro de una expresión.

**Prefijo:** el operador aparece antes de la variable. Primero modifica el valor y después devuelve el nuevo valor.

```javascript
let vidas = 3;

console.log(++vidas); // 4
console.log(vidas);   // 4
```

**Postfijo:** el operador aparece después de la variable. Primero devuelve el valor anterior y después modifica la variable.

```javascript
let vidas = 3;

console.log(vidas++); // 3
console.log(vidas);   // 4
```

Lo mismo ocurre con el decremento:

```javascript
let contador = 3;

console.log(--contador); // 2
console.log(contador--); // 2
console.log(contador);   // 1
```

En la primera instrucción se decrementa antes de devolver el resultado. En la segunda se devuelve el valor anterior y luego se decrementa.

**Regla práctica:** si solamente escribís `vidas++` como una instrucción independiente, la variable aumenta en uno. La diferencia entre prefijo y postfijo se vuelve importante cuando usás el resultado de esa expresión.

Estos operadores serán especialmente útiles cuando estudiemos bucles y contadores.

---

## 4. Operadores de comparación

Los operadores de comparación permiten comparar dos valores. El resultado siempre es un booleano: `true` o `false`.

| Operador | Significado | Ejemplo |
|---|---|---|
| `==` | Igualdad no estricta | `5 == "5"` |
| `===` | Igualdad estricta | `5 === 5` |
| `!=` | Desigualdad no estricta | `5 != "6"` |
| `!==` | Desigualdad estricta | `5 !== "5"` |
| `>` | Mayor que | `10 > 5` |
| `<` | Menor que | `5 < 10` |
| `>=` | Mayor o igual que | `5 >= 5` |
| `<=` | Menor o igual que | `5 <= 5` |

### Igualdad estricta y no estricta

La igualdad no estricta `==` puede convertir automáticamente los valores antes de compararlos.

```javascript
console.log(5 == "5"); // true
```

Aunque `5` es un número y `"5"` es un string, la comparación no estricta los considera iguales después de la conversión.

En cambio, la igualdad estricta `===` compara el valor sin realizar esa conversión automática entre tipos.

```javascript
console.log(5 === 5);   // true
console.log(5 === "5"); // false
```

Por eso, en la mayoría de los casos es recomendable utilizar `===` cuando queremos comprobar igualdad.

### Desigualdad estricta y no estricta

```javascript
console.log(5 != "5");  // false
console.log(5 !== "5"); // true
```

`!=` comprueba si los valores son diferentes después de las posibles conversiones. `!==` también considera si los tipos son distintos.

### Comparaciones numéricas

```javascript
console.log(5 > 3);   // true
console.log(5 > 6);   // false
console.log(5 >= 5);  // true
console.log(10 < 20); // true
console.log(10 <= 10); // true
```

Recordá la diferencia:

- `>` significa estrictamente mayor.
- `>=` significa mayor o igual, por lo que incluye el mismo valor.
- `<` significa estrictamente menor.
- `<=` significa menor o igual, por lo que también incluye el mismo valor.

---

## 5. Operadores lógicos

Los operadores lógicos permiten combinar o negar condiciones. Son fundamentales para evaluar más de una condición en un programa.

En JavaScript, los tres operadores lógicos principales son `&&`, `||` y `!`.

### AND: `&&`

El operador AND devuelve `true` cuando **ambas condiciones son verdaderas**.

```javascript
const edad = 20;
const tieneEntrada = true;

console.log(edad >= 18 && tieneEntrada === true); // true
```

En este ejemplo, las dos condiciones se cumplen: la persona tiene al menos 18 años y tiene entrada.

Si una de las condiciones es falsa, el resultado de la expresión será falso.

### Tabla de verdad de AND

| A | B | `A && B` |
|---|---|---|
| `true` | `true` | `true` |
| `true` | `false` | `false` |
| `false` | `true` | `false` |
| `false` | `false` | `false` |

### OR: `||`

El operador OR devuelve `true` cuando **al menos una de las condiciones es verdadera**. Solo devuelve `false` cuando ambas son falsas.

```javascript
const tieneTarjeta = false;
const tieneEfectivo = true;

console.log(tieneTarjeta || tieneEfectivo); // true
```

La condición se cumple porque la persona tiene efectivo, aunque no tenga tarjeta.

### Tabla de verdad de OR

| A | B | `A || B` |
|---|---|---|
| `true` | `true` | `true` |
| `true` | `false` | `true` |
| `false` | `true` | `true` |
| `false` | `false` | `false` |

### NOT: `!`

El operador NOT niega un valor booleano. Si recibe `true`, devuelve `false`; si recibe `false`, devuelve `true`.

```javascript
const estaJugando = false;

console.log(!estaJugando); // true
```

También podemos negar una comparación:

```javascript
const edad = 16;

console.log(!(edad >= 18)); // true
```

Como la comparación `edad >= 18` es falsa, al negarla obtenemos `true`.

### Resumen de operadores lógicos

| Operador | Nombre | Regla principal |
|---|---|---|
| `&&` | AND | Todas las condiciones deben cumplirse |
| `||` | OR | Al menos una condición debe cumplirse |
| `!` | NOT | Invierte el valor booleano |

**Nota:** los operadores lógicos de JavaScript pueden devolver valores distintos de `true` y `false` cuando se utilizan directamente con otros tipos de datos. En los ejemplos de este capítulo trabajamos con condiciones booleanas para comprender su funcionamiento básico.

---

## 6. ¿Por qué necesitamos estos operadores?

Los operadores permiten que un programa tome decisiones a partir de los datos.

Por ejemplo, podemos comprobar si una persona cumple una edad mínima y si tiene una entrada:

```javascript
const edad = 20;
const tieneEntrada = true;

const puedeIngresar = edad >= 18 && tieneEntrada;

console.log(puedeIngresar); // true
```

O comprobar si un contador llegó a un límite:

```javascript
let contador = 0;

contador++;
contador++;
contador++;

console.log(contador >= 3); // true
```

En los próximos capítulos, estos conceptos servirán para trabajar con estructuras condicionales y bucles.

---

## 7. Actividades prácticas

### Ejercicio 1: operadores de asignación

Creá una variable numérica y realizá un ejemplo práctico de cada uno de estos operadores:

- `+=`
- `-=`
- `*=`
- `/=`
- `**=`
- `%=`

Mostrá los resultados por consola y explicá cómo cambia el valor almacenado.

### Ejercicio 2: incremento y decremento

Analizá los siguientes ejemplos y explicá el resultado de cada instrucción.

```javascript
let contador = 100;

console.log(contador++);
console.log(contador);
```

```javascript
let contador = 100;

console.log(++contador);
console.log(contador);
```

Indicá qué diferencia hay entre el prefijo y el postfijo.

### Ejercicio 3: operadores de comparación

Explicá el resultado de cada expresión. Justificá tus respuestas.

```javascript
console.log(85 === 85);
console.log(85 === "85");
console.log(85 == "85");
console.log(85 !== "85");
console.log(10 >= 10);
console.log(10 < 5);
```

### Ejercicio 4: operadores lógicos

Creá dos variables booleanas y escribí ejemplos con `&&` y `||` que representen las cuatro combinaciones posibles:

1. Verdadero y verdadero.
2. Verdadero y falso.
3. Falso y verdadero.
4. Falso y falso.

Después, escribí dos ejemplos utilizando `!` y explicá cómo cambia el resultado.

---

## 8. Resumen del capítulo

| Concepto | Función |
|---|---|
| `=` | Asigna un valor a una variable |
| `+=`, `-=`, `*=`, `/=`, `**=`, `%=` | Realizan una operación y reasignan el resultado |
| `++` | Incrementa en uno |
| `--` | Decrementa en uno |
| Prefijo | Modifica la variable antes de devolver el valor de la expresión |
| Postfijo | Devuelve el valor anterior y después modifica la variable |
| `===` y `!==` | Comparan sin convertir automáticamente entre tipos |
| `>`, `<`, `>=`, `<=` | Comparan valores |
| `&&` | Exige que ambas condiciones sean verdaderas |
| `||` | Exige que al menos una condición sea verdadera |
| `!` | Niega un valor booleano |

---

## 9. Recursos adicionales

- MDN: [Expresiones y operadores](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Expressions_and_operators)
- MDN: [Asignación](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Assignment)
- MDN: [Incremento (`++`)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Increment)
- MDN: [Igualdad estricta (`===`)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Strict_equality)
- MDN: [Operador AND lógico (`&&`)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Logical_AND)
- MDN: [Operador OR lógico (`||`)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Logical_OR)
- MDN: [Operador NOT lógico (`!`)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Logical_NOT)

**Conclusión:** los operadores permiten modificar variables, comparar valores y combinar condiciones. Comprenderlos bien es el paso previo para empezar a controlar el comportamiento de un programa.
