# SLAYERSCRIPT
## Capítulo 7: Condicionales en JavaScript

### 1. ¿Qué son los condicionales?

Los condicionales permiten ejecutar diferentes bloques de código dependiendo de si una condición se cumple o no.

En programación, una condición se evalúa como verdadera (`true`) o falsa (`false`). Según el resultado, el programa decide qué instrucciones ejecutar.

Por ejemplo:

```javascript
if (2 >= 2) {
    console.log("Dos es mayor o igual a dos");
}
```

Como la condición es verdadera, se ejecuta el `console.log()`.

En cambio:

```javascript
if (2 > 2) {
    console.log("Dos es mayor que dos");
}
```

No se muestra ningún mensaje porque la condición es falsa. El número 2 es igual a 2, pero no es mayor que sí mismo. Las matemáticas siguen teniendo sus límites.

---

### 2. La estructura `if`, `else if` y `else`

Estas tres estructuras permiten controlar distintas posibilidades.

#### 2.1. `if`

Ejecuta un bloque de código únicamente cuando su condición es verdadera.

```javascript
let edad = 20;

if (edad >= 18) {
    console.log("Sos mayor de edad");
}
```

Si `edad` es mayor o igual a 18, se ejecuta el mensaje.

#### 2.2. `else`

Permite ejecutar un bloque alternativo cuando la condición del `if` es falsa.

```javascript
let edad = 16;

if (edad >= 18) {
    console.log("Sos mayor de edad");
} else {
    console.log("Sos menor de edad");
}
```

En este caso, se muestra el segundo mensaje.

#### 2.3. `else if`

Permite comprobar una condición adicional cuando las anteriores no se cumplen.

```javascript
let nota = 7;

if (nota >= 9) {
    console.log("Excelente");
} else if (nota >= 6) {
    console.log("Aprobado");
} else {
    console.log("Desaprobado");
}
```

El programa evalúa las condiciones en orden. Cuando encuentra una verdadera, ejecuta su bloque y omite los siguientes.

**Importante:** el `else` no lleva una condición propia. Representa el caso restante, cuando ninguna condición anterior se cumplió.

---

### 3. Sintaxis de los condicionales

En JavaScript, la condición del `if` debe estar entre paréntesis y el bloque de instrucciones se delimita con llaves.

```javascript
if (condicion) {
    // Código si la condición es verdadera
} else {
    // Código si la condición es falsa
}
```

Las llaves permiten agrupar las instrucciones que pertenecen a cada bloque.

También se pueden combinar condiciones mediante operadores lógicos:

```javascript
let edad = 25;
let tieneEntrada = true;

if (edad >= 18 && tieneEntrada) {
    console.log("Podés ingresar");
} else {
    console.log("No podés ingresar");
}
```

En este ejemplo, ambas condiciones deben cumplirse para permitir el ingreso.

#### JavaScript y Python

Aunque ambos lenguajes permiten trabajar con condicionales, su sintaxis es diferente.

JavaScript:

```javascript
if (edad >= 18) {
    console.log("Mayor de edad");
}
```

Python:

```python
if edad >= 18:
    print("Mayor de edad")
```

En Python se utilizan dos puntos y la indentación para delimitar los bloques. En JavaScript se utilizan llaves y paréntesis alrededor de la condición.

No conviene mezclar las sintaxis: el intérprete no va a adivinar qué lenguaje tenías en mente.

---

### 4. Condicionales con variables booleanas

Una variable booleana puede almacenar `true` o `false`.

```javascript
let estaViva = true;

if (estaViva) {
    console.log("El personaje está vivo");
} else {
    console.log("El personaje está muerto");
}
```

Cuando una variable ya contiene un booleano, se puede utilizar directamente como condición.

Estas expresiones son equivalentes para una variable booleana:

```javascript
if (estaViva) {
    console.log("Está viva");
}
```

```javascript
if (estaViva === true) {
    console.log("Está viva");
}
```

La primera forma suele ser más simple y legible.

Para comprobar que una variable es falsa, se puede utilizar el operador de negación `!`:

```javascript
if (!estaViva) {
    console.log("El personaje está muerto");
}
```

El operador `!` invierte el valor lógico: `true` pasa a `false` y `false` pasa a `true`.

#### Ejemplo con varias condiciones

```javascript
let personaje = "Buffy";
let estaViva = false;
let esVampiro = true;

if (personaje === "Buffy" && estaViva) {
    console.log("Buffy está viva");
} else if (personaje === "Buffy" && esVampiro) {
    console.log("Buffy es un vampiro");
} else {
    console.log("No se cumple ninguna de las condiciones");
}
```

El programa evalúa las condiciones de arriba hacia abajo. Como Buffy no está viva, el primer bloque no se ejecuta. La segunda condición sí se cumple.

Los ejemplos con personajes sirven para practicar, aunque su estado puede depender de la temporada de la serie. La lógica del código, por suerte, no tiene ese problema.

---

### 5. Operadores lógicos en los condicionales

Los operadores lógicos permiten combinar condiciones o invertir su resultado.

| Operador | Nombre | Resultado |
|---|---|---|
| `&&` | AND (Y) | Verdadero si ambas condiciones son verdaderas |
| `||` | OR (O) | Verdadero si al menos una condición es verdadera |
| `!` | NOT (NO) | Invierte el valor lógico |

#### Operador AND (`&&`)

```javascript
let tieneUsuario = true;
let tieneClave = true;

if (tieneUsuario && tieneClave) {
    console.log("Acceso permitido");
}
```

Las dos condiciones deben ser verdaderas.

| Primera condición | Segunda condición | Resultado |
|---|---|---|
| `true` | `true` | `true` |
| `true` | `false` | `false` |
| `false` | `true` | `false` |
| `false` | `false` | `false` |

#### Operador OR (`||`)

```javascript
let tieneEntrada = false;
let estaEnLista = true;

if (tieneEntrada || estaEnLista) {
    console.log("Puede ingresar");
}
```

Basta con que una de las condiciones sea verdadera.

| Primera condición | Segunda condición | Resultado |
|---|---|---|
| `true` | `true` | `true` |
| `true` | `false` | `true` |
| `false` | `true` | `true` |
| `false` | `false` | `false` |

#### Operador NOT (`!`)

```javascript
let bloqueado = false;

if (!bloqueado) {
    console.log("El usuario puede continuar");
}
```

Como `bloqueado` es `false`, la expresión `!bloqueado` resulta verdadera.

---

### 6. La estructura `switch`

La estructura `switch` permite seleccionar entre diferentes alternativas según el valor de una expresión. Resulta especialmente útil para menús, opciones numéricas y categorías con valores concretos.

```javascript
let opcion = 4;

switch (opcion) {
    case 1:
        console.log("Seleccionaste la opción 1");
        break;

    case 2:
        console.log("Seleccionaste la opción 2");
        break;

    case 4:
        console.log("Seleccionaste la opción 4");
        break;

    default:
        console.log("Opción no reconocida");
        break;
}
```

#### Elementos principales

- `switch (opcion)`: indica qué valor se va a evaluar.
- `case`: establece uno de los valores posibles.
- `break`: finaliza la ejecución del `switch`.
- `default`: establece qué hacer cuando ningún `case` coincide.

El bloque `default` cumple una función parecida a la del `else`: ofrece una alternativa cuando no coincide ninguna de las opciones anteriores.

#### ¿Por qué se utiliza `break`?

Si se omite `break`, la ejecución puede continuar por los siguientes casos, incluso cuando ya encontró una coincidencia. Este comportamiento se conoce como *fall-through*.

```javascript
let opcion = 2;

switch (opcion) {
    case 1:
        console.log("Uno");
        break;

    case 2:
        console.log("Dos");
        break;

    case 3:
        console.log("Tres");
        break;

    default:
        console.log("Opción desconocida");
}
```

La salida es:

```text
Dos
```

Si se eliminara el `break` del `case 2`, también se ejecutaría el código posterior hasta encontrar otro `break` o terminar el `switch`.

#### Agrupar varios casos

Varios valores pueden compartir una misma acción:

```javascript
let hora = 13;

switch (hora) {
    case 12:
    case 13:
    case 14:
        console.log("Almuerzo");
        break;

    case 18:
        console.log("Merienda");
        break;

    default:
        console.log("No hay una actividad programada");
}
```

Si `hora` vale 12, 13 o 14, se muestra el mensaje de almuerzo.

Esta técnica evita repetir el mismo código para cada alternativa.

#### ¿Cuándo conviene utilizar `switch`?

Es útil cuando se comparan muchos valores concretos de una misma expresión. Para dos alternativas simples, `if` y `else` suelen ser suficientes.

---

### 7. Operador ternario

El operador ternario permite expresar una condición sencilla en una sola expresión. Puede utilizarse como alternativa compacta a un `if...else`.

Su sintaxis es:

```javascript
condicion ? valorSiVerdadero : valorSiFalso;
```

- `?` separa la condición del resultado que corresponde si es verdadera.
- `:` separa las dos alternativas.

#### Ejemplo

```javascript
let personaje = "Sarah Connor";

let mensaje = personaje === "Sarah Connor"
    ? "Te encontré, Sarah"
    : "Ups, lo siento";

console.log(mensaje);
```

Como la condición es verdadera, `mensaje` contiene `"Te encontré, Sarah"`.

El mismo comportamiento se puede escribir con un condicional tradicional:

```javascript
let personaje = "Sarah Connor";

if (personaje === "Sarah Connor") {
    console.log("Te encontré, Sarah");
} else {
    console.log("Ups, lo siento");
}
```

Ambas versiones evalúan la misma condición.

#### ¿Cuándo utilizarlo?

El ternario es apropiado para decisiones cortas con dos resultados claros. Si la lógica se vuelve extensa o necesita varios pasos, un `if...else` suele ser más fácil de leer y mantener.

No hace falta convertir todo en una sola línea para demostrar que se sabe programar. La legibilidad también cuenta.

---

### 8. Resumen del capítulo

| Estructura | Función |
|---|---|
| `if` | Ejecuta un bloque si una condición es verdadera |
| `else if` | Comprueba otra condición si las anteriores fallan |
| `else` | Ejecuta una alternativa si ninguna condición anterior se cumple |
| `&&` | Exige que ambas condiciones sean verdaderas |
| `||` | Requiere que al menos una condición sea verdadera |
| `!` | Invierte el valor lógico |
| `switch` | Selecciona una alternativa según un valor |
| `case` | Define un caso dentro de `switch` |
| `break` | Evita continuar accidentalmente por los casos siguientes |
| `default` | Define qué hacer si ningún caso coincide |
| `? :` | Permite expresar una condición sencilla con el operador ternario |

**Idea central:** los condicionales permiten que un programa tome decisiones. La elección entre `if`, `switch` y el operador ternario depende de la cantidad de alternativas y de la claridad del código.

---

### 9. Tarea práctica

#### Ejercicio 1. Condicionales y operadores lógicos

1. Crear tres variables utilizando diferentes tipos de datos: `string`, `number` y `boolean`.
2. Crear una estructura condicional en la que el `if` utilice operadores lógicos.
3. Incorporar un `else if` con una única condición.
4. Utilizar `else` para ejecutar un bloque cuando ninguna condición anterior se cumpla.
5. Mostrar un mensaje diferente mediante `console.log()` en cada bloque.

**Objetivo:** practicar las condiciones, los operadores lógicos y la evaluación de varias alternativas.

#### Ejercicio 2. Un reloj con `switch`

Crear un programa que represente un horario con actividades programadas cada cuatro horas.

Por ejemplo:

- 04:00: levantarse.
- 08:00: estudiar.
- 12:00: almorzar.
- 16:00: entrenar.
- 20:00: jugar.

Los horarios y las actividades pueden modificarse libremente.

**Requisitos:**

1. Utilizar `switch`.
2. Incorporar varios `case`.
3. Añadir `break` donde corresponda.
4. Utilizar `default` para informar que no hay una actividad programada.
5. Como desafío adicional, permitir que dos horarios diferentes compartan una misma actividad.

**Objetivo:** practicar la selección de alternativas mediante `switch`, `case` y `default`.

#### Ejercicio 3. Convertir un `if...else` en un ternario

Partir de un condicional que compruebe si una banda es Judas Priest:

```javascript
let banda = "Judas Priest";

if (banda === "Judas Priest") {
    console.log("Judas Priest");
} else {
    console.log("Painkiller");
}
```

Convertirlo en una expresión ternaria que produzca el mismo resultado.

**Objetivo:** aprender a representar una condición sencilla de forma compacta.

---

### 10. Recursos para seguir estudiando

- MDN: [Tomar decisiones en el código: condicionales](https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/Conditionals)
- MDN: [Sentencia `if...else`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/if...else)
- MDN: [Sentencia `switch`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/switch)
- MDN: [Operador condicional (ternario)](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Conditional_operator)
- MDN: [Operadores lógicos](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/Logical_operators)

**Fin del capítulo 7.** El siguiente tema anunciado en la tutoría son los bucles, que permiten repetir instrucciones sin tener que escribir la misma línea veinte veces como si estuviéramos cobrando por tecla.
