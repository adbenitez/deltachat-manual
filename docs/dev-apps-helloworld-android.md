# Creando aplicación para Delta Chat desde Android

En este tutorial veremos como crear y probar **desde Android** una simple aplicación de ejemplo para Delta Chat, paso a paso.

## Paso #1

Lo primero que vamos a hacer es descargar las herramientas que usaremos para programar en Android:

* Editor de código: Necesitamos un editor de código (o IDE) para escribir nuestros programas que soporte lenguajes como HTML, CSS y JavaScript, especialmente para crear apps para Delta Chat necesitamos un editor que nos permita visualizar en un navegador nuestro programa, por eso usaremos la app [Acode](https://f-droid.org/packages/com.foxdebug.acode/) la cual pesa solo 8.9MB y puedes descargarla de F-Droid.
* Administrador de archivos: Necesitamos un administrador de archivos que permita comprimir archivos creando un fichero `.zip` para empaquetar los ficeros de nuestra aplicación, por lo general el administrador de archivos que viene con tu teléfono debe permitirte esto, pero si no es así puedes instalarte la app [Simple File Manager Pro](https://f-droid.org/en/packages/com.simplemobiletools.filemanager.pro/) la cual pesa solo 6.7MB y puedes descargarla de F-Droid.
* Simulador: Para probar nuestra app de forma rápida y poder simular el uso de varios dispositivos/usuarios con Delta Chat a la vez, lo mejor será usar un pequeño simulador, proveído por los creadores de Delta Chat, el cual es un simple fichero llamado `webxdc.js` que debes colocar en la misma carpeta donde está tu `index.html`, puedes bajarte el simulador de aquí: https://raw.githubusercontent.com/deltachat/webxdc-dev/master/webxdc.js

NOTA: si no tienes Internet te puedes bajar todas estas herramientas desde el propio Delta Chat con el bot **File Downloader**, revisa el [listado de bots públicos](https://github.com/adbenitez/deltachat-manual/blob/main/docs/bots.md#bots-p%C3%BAblicos) para más información.

## Paso #2

Ya con todas las herramientas descargadas, podemos comenzar a crear nuestra aplicación.

1. Primeramente vamos a abrir la app Acode, en el menú seleccionamos la opción "Files" ahí se nos muestra un explorador de archivos,
2. vayamos a la carpeta donde guardaremos nuestros proyectos, por ejemplo en la carpeta "Documents"
3. seleccionamos el botón que es un símbolo de adición "+", el cual nos dará varias opciones, selecciona la opción "New project" para crear un nuevo proyecto,
4. entre las varias opciones de nuevo proyecto selecciona la opción "HTML" y como nombre del proyecto escribe: `hola`
5. esto te creará una carpeta "hola" dentro de la cual hay un fichero `index.html` y dos carpetas una para nuestro código JavaScript y otra para los estilos CSS.

# Paso #3

Abre en Acode el fichero `index.html` creado en el paso anterior y modifica su contenido para que quede de la forma siguiente:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="css/index.css">

  <script src="webxdc.js"></script>  <!-- Esta línea es la que permite la interacción con Delta Chat -->
  <script src="js/index.js"></script>
</head>
<body>
    <h1>Hola Mundo!</h1>
    <button onclick="cambiarFondo('red');">Rojo</button>
    <button onclick="cambiarFondo('green');">Verde</button>
    <button onclick="cambiarFondo('blue');">Azul</button>
</body>
</html>
```

## Paso #4

Ahora vamos a editar el fichero `index.js` que se encuentra dentro de la carpeta `js`, abre el fichero con Acode y escribe en su interior:

```js
var colores = {red: 'Rojo', green: 'Verde', blue: 'Azul'}

// Esta función es llamada cuando el usuario hace click en un botón:
function cambiarFondo(color) {
    // window.webxdc.selfName permite obtener el nombre del usuario donde está corriendo tu app en este momento, adicionalmente puedes usar window.webxdc.selfAddr para obtener su dirección de correo para usarla como identificador/ID del usuario
    var info = window.webxdc.selfName + ' cambió el color de fondo a: ' + colores[color];
    var resumen = "Fondo: " + colores[color];
    window.webxdc.sendUpdate({summary: resumen, info: info, payload: color}, info);
    // window.webxdc.sendUpdate() es lo que usas para que tu aplicación se comunique entre varios dispositivos, el primer argumento es un diccionario con los siguientes atributos:
    //     "summary" (es opcional), puedes usarlo si quieres que se muestre un sumario en el mensaje donde se envió tu aplicación por ejemplo para mostrar un resumen del estado de la aplicación.
    //     "info" (es opcional), puedes usarlo si quieres que se muestre un mensaje en el chat avisando que algo cambió dentro de tu app, por ejemplo cuando alguien obtiene una nueva puntuación alta en un juego.
    //     "payload" es el que contiene cualquier información que quieras compartir con los otros dispositivos donde corre tu app, logrando así una interacción en red, en este atributo puedes colocar cualquier objeto de JavaScript, como una lista, diccionarios, etc.
    // el segundo parámetro que pasamos a window.webxdc.sendUpdate() es un texto con una descripción que se mostrará en el correo normal si alguien usa un cliente de correo normal para abrir el mensaje.
}

// esta función es la que usaremos para procesar los estados que recibamos de nuestra aplicación, los cuales fueron enviados con window.webxdc.sendUpdate(), tanto en el dispositivo actual como de otros dispositivos en la red:
function receiveUpdate(update) {
    // el parámetro "update" es el mismo diccionario pasado por nuestra aplicación con window.webxdc.sendUpdate(), por tanto contiene el color que enviamos en el atributo "payload"
    if (update.serial == update.max_serial) {  // con esto se comprueba que estamos procesando el último estado recibido, en este ejemplo ignoraremos los estados anteriores
        var color = update.payload;
        var body = document.getElementsByTagName("body")[0];
        body["style"] = "background-color:" + color;
    }
}

window.addEventListener("load", () => {
    // con window.webxdc.setUpdateListener() registramos una función o callback que será la que processará los estados que recibimos tanto de otros usuarios como los propios. El segundo parámetro es el ID/serial del último estado recibido, si pasas cero, el callback recibirá todos los estados recibidos desde el comienzo, idealmente nuestra app guardaría en localStorage el último serial que hemos procesado y lo pasaría aquí a window.webxdc.setUpdateListener() para no tener que procesar todo de cero cada vez, pero para mantener el ejemplo simple:
    window.webxdc.setUpdateListener(receiveUpdate, 0);
});
```

## Paso #5

Ahora vamos a editar el fichero `index.css` que se encuentra dentro de la carpeta `css`, en este fichero modificarás el estilo de tu aplicación, para nuestra app de ejemplo no lo necesitamos así que simplemente cambiaremos el estilo de los botones, abre el fichero con Acode y escribe en su interior:

```css
button {
    border:none;
    display:inline-block;
    padding:8px 16px;
    vertical-align:middle;
    overflow:hidden;
    text-decoration:none;
    cursor:pointer;
    color:inherit;
    background-color:#ccc;
    text-align:center;
}
```

## Paso #6 (opcional)

Ya nuestra app está casi lista, ahora vamos a añadir algo que es opcional pero mejora la apariencia de nuestra aplicación al ser compartida en Delta Chat, crea un fichero llamado `manifest.toml` y en su interior escribe:

```toml
name = "Hola Mundo"
```

este fichero permite establecer el nombre de tu aplicación que será mostrado en Delta Chat, cambia "Hola Mundo" por el nombre que quieras ponerle a la app. Además de este fichero `manifest.toml` puedes añadir una foto llamada `icon.png` o `icon.jpg` que servirá de ícono de tu aplicación y será mostrado al compartir tu app.

## Paso #7

Llegó la hora de probar nuestra app en el simulador que descargamos en el **Paso #1**. Si aún no lo has hecho coloca el archivo `webxdc.js` del simulador en la misma carpeta donde está nuestro fichero `index.html`, luego abre el fichero `index.html` en Acode y da en el botón que es un símbolo de "play"/reproducir (el triángulo en la barra superior), te saldrán dos opciones, selecciona "BROWSER", para abrir tu app en el navegador del teléfono.

Si seguiste este tutorial al pie de la letra te va a salir la aplicación y podrás añadir nuevos dispositivos ("Add peer") con un menú flotante que aparece al final de pantalla, añade un dispositivo adicional y prueba dar en un botón y ver que el color cambia para todos los dispositivos. Adicionalmente verás un botón flotante que muestra una consola, ese botón es añadido por Acode para que puedas ver la consola donde se registran los errores o texto que tu programa escriba en la consola para "debuguear", el simulador que añadimos imprimirá en la consola los eventos de Delta Chat enviados y recibidos, así podrás analizar si tu programa está funcionando como esperas y en esta consola también puedes probar usar la API de `windows.webxdc` de forma interactiva.

## Paso #8

Bueno ya nuestra aplicación está lista, es una simple app que muestra el texto "Hola Mundo!" y unos botones para cambiar el color de fondo de la aplicación y, al presionarlos, el color cambia no solo para ti sino para todos los usuarios del chat donde hayas enviado la aplicación!

Ahora solo nos queda empaquetar la aplicación en un fichero `.xdc` para que pueda ser ejecutada dentro de Delta Chat, para ello usaremos la app de gestor de archivo que bajamos en el **Paso #1**, abre en el gestor de archivos y ve a la carpeta "hola" donde está nuestro proyecto, selecciona las carpetas `js` y `css` y además selecciona los ficheros `index.html` y `manifest.toml`, da en el menú y selecciona "Comprimir", nombra el fichero `hola`, luego renombra el fichero, cambiando la extensión `.zip` por `.xdc` y ya está! ya puedes compartir y usar tu aplicación con tus amigos en Delta Chat.
