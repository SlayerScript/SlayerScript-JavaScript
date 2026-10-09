# Tarea: Funciones en JavaScript

## 1. Declaración de funciones

Tenemos la siguiente función:

```javascript
function mensaje() {
    console.log("Bienvenido a SlayerScript");
}
```

Convertí esta función primero en una **función de expresión** y después en una **función flecha**.

**Objetivo:** practicar las distintas sintaxis para crear funciones en JavaScript y reconocer sus diferencias básicas.

---

## 2. Return vs console.log

Vanesa está haciendo una calculadora con JavaScript. Empezó haciendo una función de suma de dos valores, pero no entiende por qué no aparece ningún resultado en su terminal.

```javascript
function suma(a, b) {
    return a + b;
}

suma(90, 44);
```

**¿Cómo la ayudarías?**

1. Modificá el código para poder ver el resultado en la terminal.
2. Explicá qué está haciendo `return`.
3. ¿Qué diferencia hay entre utilizar `return` y utilizar `console.log()` dentro de la función?

**Objetivo:** comprender la diferencia entre devolver un valor con `return` y mostrar un valor con `console.log()`.

---

## 3. Función de expresión

Roberto tiene esta función de expresión:

```javascript
const bucle = function() {
    for (let i = 0; i < 5; i++) {
        console.log("Probando función...");
    }
}

console.log(bucle);
```

Cuando ejecuta el código, en la terminal aparece información sobre la función, pero no se muestran los mensajes del bucle.

**¿Cómo lo ayudarías?**

1. Modificá el código para ejecutar el bucle.
2. Explicá qué diferencia hay entre:

```javascript
bucle
```

y

```javascript
bucle()
```

**Objetivo:** entender la diferencia entre hacer referencia a una función y ejecutar una función de expresión.

---

## 4. Función flecha

Simplificá estas dos funciones flecha:

```javascript
const alarma = (nombre) => {
    return `Despertate ${nombre}!`;
}

const division = (x, y) => {
    return x / y;
}
```

**Objetivo:** practicar la sintaxis abreviada de las funciones flecha y comprender el uso del `return` implícito.
