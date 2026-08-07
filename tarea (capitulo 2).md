# ⚔️ Tarea - Capítulo 2: Variables

### 1. Tipos de datos

**a) String**
Crear una variable de tipo `string` utilizando comillas dobles, comillas simples o backticks.

**b) Number**
Crear una variable de tipo `number`, utilizando un número entero o decimal.

**c) Boolean**
Crear una variable de tipo `boolean` utilizando `true` o `false`.

Mostrar las tres variables por consola, ya sea **juntas o por separado**.

---

### 2. Comparación y errores

**a) Tipos de datos**

Observar las siguientes variables:

```javascript
var edad1 = 10;
var edad2 = "10";
```

Responder:

> ¿Estas dos variables son iguales? ¿Por qué?

---

**b) Diferencia entre mayúsculas y minúsculas**

Analizar el siguiente código:

```javascript
var bruja = "Willow";

console.log(Bruja);
```

Responder:

> ¿Por qué este código produce un error?
> ¿Cómo lo solucionarías?

---

### 3. Convenciones para nombrar variables

**a) Convención `camelCase`**

Según lo visto en clase, ¿cuál de las siguientes opciones sigue la convención que utilizamos habitualmente en JavaScript?

```javascript
var ProtagonistaDeSerie = "Buffy";
var protagonista_de_serie = "Buffy";
var protagonistadeserie = "Buffy";
var protagonistaDeSerie = "Buffy";
```

---

**b) Variables booleanas**

Según las buenas prácticas vistas en clase, ¿cuál de las siguientes opciones representa mejor una variable que almacena un valor booleano?

```javascript
var VIVO = true;
var estavivo = true;
var estaVivo = true;
var verdad = true;
```

---

### 4. Reasignación de variables

**a) Reasignación del mismo tipo**

Analizar el siguiente código:

```javascript
var protagonista = "Sonic";
var protagonista = "Shadow";

console.log(protagonista);
```

Responder:

> ¿Está correctamente reasignado el valor?
> ¿Qué valor se mostrará por consola?

---

**b) Reasignación a otro tipo de dato**

Analizar el siguiente código:

```javascript
var año = 1990;
var año = "1991";

console.log(año);
```

Responder:

> ¿Está correctamente reasignado el valor?
> ¿Qué tipo de dato tiene `año` al final?
