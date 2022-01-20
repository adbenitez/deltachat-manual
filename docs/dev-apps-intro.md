# ¿Qué son las aplicaciones para Delta Chat?

Delta Chat tiene soporte para una especie de "aplicaciones web" llamadas "webxdc" que no son más que unos ficheros con extensión `.xdc` los cuales se muestran como aplicaciones en Delta Chat y las cuales los usuarios pueden abrir para jugar o obtener alguna utilidad.

Estas aplicaciones tienen la capacidad de interactuar con Delta Chat y poder enviar ciertos mensajes especiales que hacen posible la interacción en red entre varios usuarios dentro de la app en cuestión.

Cada vez que un usuario envía tu aplicación, esto es una instancia distinta de tu aplicación o sea se puede enviar la misma aplicación varias veces y por ejemplo si es un juego, tener partidas distintas por cada instancia enviada.

Las aplicaciones están contenidas dentro de un visor HTML o navegador web especial donde están restringidas y aisladas, no tienen acceso a internet, esto es una ventaja para los usuarios ya que es mejor para su seguridad, la aplicación no puede enviar tu información privada a algún servidor en Internet, todo queda entre el usuario y sus amigos, la única forma de comunicación que tiene la app es en el chat donde esta es enviada.

Como creador, para ti esto significa que tu aplicación debe contener todos los recursos que necesita, imágenes, CSS, JavaScript, bibliotecas como jQuery, React, Bootstrap, etc. todas deben estar incluidas dentro de tu paquete `.xdc`, no puedes cargarlas de la red y que tu aplicación no puede mandar correos a cualquier dirección en particular que tú desees, sino solo en el chat donde el usuario decida usar tu app.

Otro aspecto a tener en cuenta es que estas aplicaciones solo trabajan mientras el usuario las tiene abiertas, o sea no pueden estar funcionando en segundo plano.

## Estructura de una aplicación

Los ficheros `.xdc` no son más que un fichero `.zip` pero renombrados con la extensión cambiada a `.xdc`
* En su interior tienen que contener un fichero `index.html` que es el punto de entrada o página principal de tu aplicación.
* Opcionalmente, pueden contener un fichero `icon.png` o `icon.jpg` que será mostrado como icono de la aplicación en Delta Chat.
* Adicionalmente, puedes incluir un fichero llamado `manifest.toml` que contega algo como `name = "Mi Primera App"` esto se usará como nombre de la aplicación y será mostrado en Delta Chat.
* Y, por supuesto, puedes incluir cualquier cantidad de carpetas con recursos como imágenes, audio, CSS, JavaScript, etc. que necesite tu aplicación.

## ¿Qué tipo de aplicaciones puedo crear para Delta Chat?

Como las aplicaciones solo pueden comunicarse en red a través de mensajes enviados por el propio Delta Chat (correo electrónico) y no es posible utilizar Internet directamente, esto significa que el tipo de aplicaciones que mejor funcionarán son, por ejemplo, los juegos por turnos, o juegos donde solo se utilize la "red" para enviar tus nuevas puntuaciones en algún juego Arcade, etc. o sea no será posible crear juegos que necesiten interacción en red de varios usuarios en tiempo real como juegos de carreras de autos o juegos de tiros/shooters.

## ¿Qué límite de tamaño tienen las applicaciones Webxdc?

De momento (19 de enero del 2022) el tamaño máximo de un fichero `.xdc` permitido por Delta Chat es de 100KB, si tu programa excede ese tamaño, debes optimizar tus imágenes e ícono de la aplicación con herramientas como GIMP, y usar programas que te permitan "minimificar" tu código HTML, CSS y JavaScript, eliminando espacios en blanco y otros caracteres innecesarios.

## Recursos para crear aplicaciones para Delta Chat

Estos son algunos recursos que pueden ser de ayuda a desarrolladores que
quieran comenzar a crear aplicaciones para Delta Chat:

* [Webxdc Development Tool](https://github.com/deltachat/webxdc-dev): Esta es una pequeña herramienta que sirve a modo de simulador para probar tus aplicaciones desde el navegador, en tu computadora por ejemplo, y poder simular el uso de la aplicación desde varios dispositivos y ver como la app interactua entre varios usuarios de Delta Chat. El simulador también viene con un fichero `index.html` que sirve de ejemplo, es una pequeña aplicación de chat (un chat dentro de Delta Chat jeje) que muestra como interactuar con Delta Chat desde JavaScript. Este proyecto sirve de plantilla para crear tus aplicaciones, y viene con un pequeño script en `bash` que te ayuda a empaquetar tu aplicación en un fichero `.xdc`
* [webxdc-python](https://github.com/adbenitez/webxdc-python): Este proyecto sirve de plantilla y ejemplo de como crear aplicaciones para Delta Chat utilizando Python como tu lenguaje de programación!
* Como fuente de inspiración y ejemplos, puedes encontrar aplicaciones creadas por otros en GitHub: https://github.com/topics/webxdc
