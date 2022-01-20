# Creando tu primera aplicación para Delta Chat

Vamos a crear una simple aplicación de ejemplo, paso a paso.

## Paso #1

Lo primero que vamos a hacer es crear una carpeta para nuestro proyecto, por ejemplo crea una carpeta `HolaMundo` y dentro vamos a crear un fichero `index.html` con el siguiente contenido:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"/>

        <!-- Esta línea es la que permite la interacción con Delta Chat: -->
        <script src="webxdc.js"></script>
    </head>
    <body>
        <h1>Hola Mundo!</h1>
        <button onclick="cambiarFondo('red');">Rojo</button>
        <button onclick="cambiarFondo('green');">Verde</button>
        <button onclick="cambiarFondo('blue');">Azul</button>
        <button onclick="cambiarFondo('yellow');">Amarillo</button>

        <!-- Este fichero lo vamos a crear en el paso siguiente: -->
        <script src="index.js"></script>
    </body>
</html>
```

## Paso #2

En el paso anterior creamos un fichero `index.html` y al final del mismo incluimos un fichero `index.js` este fichero es el que vamos a crear ahora con la lógica de nuestra aplicación. Crea un fichero llamado `index.js` y escribe en su interior:

```js
var colores = {red: 'Rojo', green: 'Verde', blue: 'Azul', yellow: 'Amarillo'}

// Esta función es llamada cuando el usuario hace click en un botón:
function cambiarFondo(color) {
    // window.webxdc.selfName() permite obtener el nombre del usuario donde está corriendo tu app en este momento, adicionalmente puedes usar window.webxdc.selfAddr() para obtener su dirección de correo para usarla como identificador/ID del usuario
    var info = window.webxdc.selfName() + ' cambió el color de fondo a: ' + colores[color];
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
    var color = update.payload;
    var body = document.getElementsByTagName("body")[0];
    body["style"] = "background-color:" + color;
}

// con window.webxdc.setUpdateListener() registramos una función o callback que será la que processará los estados que recibimos mientras la app está abierta.
window.webxdc.setUpdateListener(receiveUpdate);

// con window.webxdc.getAllUpdates() obtenemos todos los estados que hemos recibido en el pasado, esto nos sirve para restaurar el estado de nuestra aplicación cuando el usuario la abre.
var updates = window.webxdc.getAllUpdates();
// si hay estados antiguos, restablecer el estado de la app con el último estado recibido:
if (updates.length > 0) {
    receiveUpdate(updates[updates.length - 1]);
}
```

## Paso #3 (opcional)

Ya nuestra app está casi lista, ahora vamos a añadir algo que es opcional pero mejora la apariencia de nuestra aplicación al ser compartida en Delta Chat, crea un fichero llamado `manifest.toml` y en su interior escribe:

```toml
name = "Hola Mundo"
```

este fichero permite establecer el nombre de tu aplicación que será mostrado en Delta Chat, cambia "Hola Mundo" por el nombre que quieras ponerle a la app. Además de este fichero `manifest.toml` puedes añadir una foto llamada `icon.png` o `icon.jpg` que servirá de ícono de tu aplicación y será mostrado al compartir tu app.

## Paso #4

Bueno ya nuestra aplicación está lista, es una simple app que muestra el texto "Hola Mundo!" y unos botones para cambiar el color de fondo de la aplicación y, al presionarlos, el color cambia no solo para ti sino para todos los usuarios del chat donde hayas enviado la aplicación!

Ahora solo nos queda empaquetar la aplicación en un fichero `.xdc` para que pueda ser ejecutada dentro de Delta Chat, para ello debes crear un fichero `.zip` que dentro contega el fichero `index.html`, `index.js` y `manifest.toml` que acabamos de crear, luego renombra el fichero `.zip`, cambiando `.zip` por `.xdc` y ya está! ya puedes compartir y usar tu aplicación con tus amigos.

## Notas finales

Importante! el fichero `.zip` debe contener los ficheros `index.html`, `manifest.toml`, etc. directamente en la raíz del zip, NO en una carpeta dentro del zip.

En este ejemplo para separar mejor las cosas a la hora de explicar, creé el fichero `index.js` separado para el JavaScript, pero bien puedes incluir tu lógica dentro del propio fichero `index.html` directamente dentro de unos tags `<script></script>`
