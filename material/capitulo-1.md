# SLAYERSCRIPT
## Capítulo 1: Preparación del entorno y primera ejecución de JavaScript

**Material complementario · Fundamentos de JavaScript**

---

## 1. Objetivos del capítulo

Al finalizar esta unidad, deberías ser capaz de:

- Instalar y utilizar Visual Studio Code.
- Crear archivos HTML y JavaScript.
- Comprender la función de `console.log()`.
- Vincular un archivo JavaScript externo con un documento HTML.
- Ejecutar código con un navegador y con Node.js.
- Reconocer las funciones de Live Server y Code Runner.

## 2. Herramientas de desarrollo

### Visual Studio Code

Visual Studio Code (VS Code) es un editor de código fuente que permite escribir, organizar y modificar programas en diferentes lenguajes.

Entre sus características se encuentran el resaltado de sintaxis, el autocompletado, la terminal integrada y la posibilidad de instalar extensiones.

**Conceptos importantes:**

- **Editor:** programa en el que escribimos y modificamos código.
- **Extensión:** complemento que agrega funcionalidades al editor.
- **Terminal:** interfaz desde la que podemos ejecutar comandos.
- **Proyecto:** conjunto organizado de archivos relacionados con un desarrollo.

Durante este capítulo utilizaremos Visual Studio Code como nuestro entorno de trabajo.

### Node.js

Node.js es un entorno de ejecución que permite ejecutar JavaScript fuera del navegador. Es especialmente útil para desarrollar herramientas, aplicaciones de backend y otros programas.

Para comprobar si está instalado, abrí una terminal y ejecutá:

```bash
node -v
```

Si la instalación está correctamente configurada, el comando mostrará el número de versión.

Si el sistema no reconoce el comando, verificá la instalación y la configuración de la variable `PATH`. Después de instalar Node.js, puede ser necesario reiniciar la terminal o Visual Studio Code para que reconozca los cambios.

## 3. Organización de los archivos

Para trabajar de manera ordenada, crearemos una carpeta para el proyecto y utilizaremos dos archivos principales:

```text
capitulo-1/
├── index.html
└── main.js
```

- `index.html`: contiene la estructura de la página web.
- `main.js`: contiene nuestro código JavaScript.

Los nombres son convenciones habituales, no requisitos obligatorios. Podríamos utilizar otros nombres, siempre que las rutas y referencias coincidan.

## 4. Nuestro primer mensaje con JavaScript

Una de las instrucciones más sencillas para comenzar es `console.log()`.

Su función es mostrar un valor en la consola, una herramienta útil para observar resultados y depurar programas.

Ejemplo:

```javascript
console.log("Slayer");
```

Resultado:

```text
Slayer
```

### ¿Cómo funciona?

- `console` es un objeto que proporciona acceso a la consola.
- `log` es un método que permite registrar información.
- Los paréntesis contienen el valor que queremos mostrar.
- Las comillas indican que `Slayer` es una cadena de texto.
- El punto y coma marca el final de la instrucción en este ejemplo.

También podemos mostrar números:

```javascript
console.log(25);
```

O varios mensajes:

```javascript
console.log("Bienvenidos a SlayerScript");
console.log("Estamos aprendiendo JavaScript");
console.log(100);
```

Cada llamada a `console.log()` registra un mensaje independiente.

**Importante:** el punto y coma es una buena convención para mantener un estilo consistente. JavaScript también dispone de inserción automática de punto y coma (ASI), por lo que no es obligatorio en todos los casos.

## 5. Ejecutar JavaScript desde HTML

Una forma de ejecutar JavaScript en una página web es incorporarlo a un documento HTML.

HTML proporciona la estructura de la página, mientras que JavaScript permite ejecutar instrucciones e incorporar comportamiento.

Podemos escribir el código directamente dentro de una etiqueta `script`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Mi primera página</title>
</head>
<body>
    <script>
        console.log("Slayer");
    </script>
</body>
</html>
```

Cuando abrimos la página en un navegador, el código JavaScript se ejecuta y podemos consultar el resultado en la consola del navegador.

### ¿Qué es la etiqueta `script`?

La etiqueta `script` permite incorporar o cargar código JavaScript en un documento HTML.

En el ejemplo anterior, el código está escrito directamente entre las etiquetas de apertura y cierre:

```html
<script>
    console.log("Slayer");
</script>
```

Esta técnica funciona, pero para proyectos más grandes suele ser preferible separar el código JavaScript del HTML.

## 6. Vincular un archivo JavaScript externo

Para separar responsabilidades, podemos escribir el código en un archivo independiente.

Primero, creamos `main.js`:

```javascript
console.log("Slayer");
```

Después, vinculamos ese archivo desde `index.html`:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>SlayerScript</title>
</head>
<body>
    <script src="./main.js"></script>
</body>
</html>
```

### El atributo `src`

El atributo `src` indica la ubicación del archivo JavaScript que queremos cargar.

En este caso:

```html
<script src="./main.js"></script>
```

La ruta `./main.js` indica que el archivo se encuentra en el mismo directorio que el documento HTML.

Si el archivo estuviera dentro de una carpeta llamada `js`, la referencia sería:

```html
<script src="./js/main.js"></script>
```

La ubicación real de los archivos y la ruta especificada deben coincidir. Una referencia incorrecta puede impedir que el navegador cargue el código.

**Buena práctica:** mantener el código JavaScript en archivos separados facilita la lectura, el mantenimiento y la organización del proyecto.

## 7. Live Server

Live Server es una extensión de Visual Studio Code que permite iniciar un servidor local para visualizar páginas web durante el desarrollo.

En lugar de abrir el archivo HTML manualmente cada vez que realizamos un cambio, podemos utilizar Live Server para trabajar con una dirección local en el navegador.

### Procedimiento básico

1. Abrí la sección de extensiones de Visual Studio Code.
2. Buscá `Live Server`.
3. Instalá la extensión correspondiente.
4. Abrí el proyecto y el archivo `index.html`.
5. Utilizá la opción para abrirlo con Live Server.
6. Modificá el código, guardá los cambios y observá el resultado en el navegador.

Live Server facilita la actualización de la página al guardar los archivos, aunque no reemplaza la necesidad de comprender cómo funciona HTML y JavaScript.

### Consultar la consola del navegador

Para observar los mensajes de `console.log()`:

1. Abrí la página en el navegador.
2. Abrí las herramientas de desarrollo.
3. Seleccioná la pestaña **Console**.
4. Buscá el mensaje generado por el programa.

También podés utilizar la pestaña **Network** para investigar si un archivo JavaScript está fallando al cargarse.

## 8. Ejecutar JavaScript con Node.js

No siempre necesitamos un documento HTML para ejecutar JavaScript.

Con Node.js podemos ejecutar directamente un archivo `.js` desde una terminal.

Si nuestro archivo se llama `main.js`, ejecutamos:

```bash
node main.js
```

Si contiene:

```javascript
console.log("Slayer");
```

La terminal mostrará:

```text
Slayer
```

Para que funcione, debemos tener Node.js instalado y ejecutar el comando desde el directorio correcto, o proporcionar la ruta correspondiente al archivo.

### ¿Cuál es la diferencia entre el navegador y Node.js?

El navegador permite ejecutar JavaScript en el contexto de una página web y proporciona herramientas para interactuar con el documento, como el DOM.

Node.js permite ejecutar JavaScript fuera del navegador y proporciona funcionalidades orientadas al entorno del sistema, como el acceso a archivos mediante sus módulos.

No son exactamente lo mismo: cada entorno ofrece capacidades diferentes.

## 9. Code Runner

Code Runner es una extensión que permite ejecutar código desde Visual Studio Code mediante una opción de ejecución rápida.

Puede resultar práctica para probar ejemplos pequeños, como los que utilizamos en este capítulo.

Sin embargo, es importante comprender que Code Runner no reemplaza a Node.js ni a las herramientas del navegador. La forma en que ejecuta un archivo depende del lenguaje y de su configuración.

Para aprender los fundamentos, conviene saber ejecutar el código directamente con:

```bash
node main.js
```

De esa manera, entendemos qué estamos ejecutando y qué herramienta interviene en el proceso.

## 10. Errores frecuentes

### El comando `node -v` no funciona

Comprobá que Node.js esté instalado correctamente. Si acabás de instalarlo, reiniciá la terminal y volvé a intentarlo.

### El navegador no muestra el resultado esperado

Recordá que `console.log()` escribe en la consola, no directamente en el contenido visible de la página.

### El archivo JavaScript no se ejecuta

Verificá que la etiqueta `script` tenga el atributo `src` correcto y que el archivo exista en la ubicación indicada.

### La terminal indica que no encuentra `main.js`

Comprobá el directorio actual de la terminal y el nombre exacto del archivo. Las rutas deben coincidir con la estructura real del proyecto.

### No aparecen los cambios después de modificar el código

Guardá el archivo y verificá que estés visualizando el proyecto correcto. Si el problema continúa, revisá la consola del navegador y los errores de carga.

### Un detalle sobre los atajos de teclado

En Visual Studio Code, el atajo habitual para abrir la terminal integrada es **Ctrl + `** en Windows, donde la tecla ` suele estar cerca de Esc o a la izquierda del número 1, según el teclado.

`Ctrl + Shift + N` abre una ventana nueva de Visual Studio Code, no la terminal integrada.

## 11. Actividad práctica

Ahora vas a repetir el procedimiento sin seguir el video paso a paso.

**Parte A. Preparación**

1. Creá una carpeta llamada `practica-capitulo-1`.
2. Abrí esa carpeta en Visual Studio Code.
3. Creá los archivos `index.html` y `main.js`.

**Parte B. Código**

En `index.html`, creá una estructura HTML básica y vinculá `main.js` mediante `src`.

En `main.js`, escribí tres llamadas a `console.log()` que muestren:

1. Tu nombre.
2. El nombre de SlayerScript.
3. Una frase que describa qué esperás aprender con JavaScript.

**Parte C. Ejecución**

1. Abrí `index.html` con Live Server.
2. Consultá la consola del navegador.
3. Modificá uno de los mensajes y guardá el archivo.
4. Ejecutá también `main.js` con Node.js.
5. Comprobá que los mensajes aparezcan en la terminal.

**Parte D. Comprobación**

Respondé las siguientes preguntas con tus propias palabras:

- ¿Qué diferencia existe entre HTML y JavaScript?
- ¿Para qué sirve `console.log()`?
- ¿Qué función cumple el atributo `src`?
- ¿Qué diferencia existe entre ejecutar JavaScript en un navegador y hacerlo con Node.js?
- ¿Por qué resulta conveniente separar el código JavaScript en un archivo externo?

## 12. Resumen del capítulo

| Herramienta o concepto | Función principal |
|---|---|
| Visual Studio Code | Escribir y organizar código. |
| HTML | Definir la estructura de una página. |
| `console.log()` | Mostrar información en la consola. |
| `script` | Incorporar o cargar JavaScript desde HTML. |
| `src` | Especificar la ruta de un archivo externo. |
| Live Server | Servir páginas localmente durante el desarrollo. |
| Node.js | Ejecutar JavaScript fuera del navegador. |
| Code Runner | Ejecutar código mediante una extensión del editor. |

## 13. Recursos oficiales

- Visual Studio Code: https://code.visualstudio.com/
- Node.js: https://nodejs.org/
- Documentación de `console.log()`: https://developer.mozilla.org/en-US/docs/Web/API/console/log_static
- Elemento `script` de HTML: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script

---

**Tarea del capítulo:** recreá el proyecto desde cero, ejecutá tu propio código y resolvé el cuestionario de SlayerScript.

**Recordá:** el objetivo no es memorizar cada paso del video, sino comprender qué hace cada herramienta y poder repetir el procedimiento sin depender de él.

*SlayerScript · Aprender, practicar y no abandonar.*
