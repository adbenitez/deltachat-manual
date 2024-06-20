# Publicando en tu blog de WriteFreely desde Delta Chat

Writefreely es una red de blogs descentralizada (utiliza ActivityPub, el mismo protocolo que utiliza Mastodon) hay varias "instancias" o páginas donde puedes
crearte una cuenta y  tener tus propios blogs disponibles en internet completamente gratis!

## Parte 1: Crear la cuenta y enlazarla con Delta Chat

El bot del Fediverso (simplebot@testrun.org) permite escribir en tu blog de writefreely desde Delta Chat!

Puedes ver la lista de instancias de WriteFreely en https://writefreely.org/instances, una vez  creada la cuenta en la página que hayas escogido, por ejemplo
https://paper.wf, usas el comando:

```
/login https://paper.wf fulano contraseña
```

Sustituye "https://paper.wf" por la instancia donde hayas creado la cuenta, "fulano" por tu usuario y "contraseña" por tu contraseña del blog, luego te aparecerán
en delta chat unos chats especiales con el nombre de los blogs que hayas creado (por defecto se crea un blog con tu nombre de usuario) cualquier cosa que publiques
en esos chats se va a publicar en el blog asociando a ese chat.

## Parte 2: ¿Cómo publicar con estilo?

### Estructura de un artículo

El título de tus artículos será la primera línea del mismo, la cual debe comenzar con **#** seguido de un espacio, por ejemplo:

```
# Título de mi artículo

Hola, en este artículo me gustaría comentarte sobre lo bueno que es tener tu blog personal...
```

Cuando el artículo es muy largo, para mostrar solo un párrafo pequeño en la lista de artículos del blog y que aparezca un botón **"Leer más..."** debes añadir este
texto especial: `<!--more-->` por ejemplo:

```
# Tutorial sobre Delta Chat

Hola, en este turorial te enseñaré a instalar y configurar Delta Chat.
<!--more-->

Primero vamos a la página oficial para ver de donde podemos descargarlo.... 
etc,  etc, etc. este texto es muy largo y ocuparía toda la página inicial del blog si no usas "<!--more-->"
para marcar donde debes ser cortado el artículo y mostrar un enlace "Leer más.."
```

Para resaltar texto en **negritas** utiliza `**texto**` y para _itálicas_ utiliza `_texto_`

Para crear listas como esta:

Ingredientes:

* 1 cabeza de ajo
* 2 cebollas
* 1/2 libra de queso 

Pasos:

1. Pelar el ajo y cortar en trozos pequeños
2. Pelar la cebolla y picarla en dados
3. Rallar el queso

Se crearían así(el espacio entre el encabezado y los elementos de la lista es obligatorio):

```
Ingredientes:

* 1 cabeza de ajo
* 2 cebollas
* 1/2 libra de queso 

Pasos:

1. Pelar el ajo y cortar en trozos pequeños
2. Pelar la cebolla y picarla en dados
3. Rallar el queso
```

Puedes crear etiquetas de esta forma: `#etiqueta`, las etiquetas son útiles pues permiten que tus lectores filtren el blog por etiquetas/categorías y puedan
encontrar todos los artículos que contengan una etiqueta determinada, por ejemplo si tienes un canal y tienes varias categorías o secciones dentro del canal,
puedes usar las etiquetas para que tus seguidores puedan leer todas las publicaciones de determinada sección por separado.

Para añadir un enlace y que en lugar del enlace se muestre un texto como "has click: aquí" que al darle click en "aquí" te lleve al enlace, utilizas este formato:

```
has click: [aquí](http://delta.chat)
```

### Editores de texto

Existen apps de blog de notas que te ayudan escribir en este formato utilizado para escribir en los blogs, ese formato se llama **Markdown** y las aplicaciones
que recomiendo utilizar son estas:

* [Notes](https://f-droid.org/packages/org.billthefarmer.notes) es un blog de notas super simple, pesa solo 183KB y puedes descargarla directamente de la página 
  de [F-Droid](https://f-droid.org/packages/org.billthefarmer.notes), esta aplicación te permite escribir texto en este formato que he explicado hoy aquí y
  pre-visualizar como se va a ver en forma de página web(lo convierte a html) antes de que lo publiques.
* [Markor](https://f-droid.org/packages/net.gsantner.markor) es otra app de notas y editor de texto en general, así como creador de listas de cosas por hacer,
  es mucho más avanzado que la app anterior, pesa 7MB y también está disponible en F-Droid, es mucho más avanzada para la creación de artículos en Markdown, 
  con botones para crear listas, poner texto en negritas, etc, al estilo programas más avanzados de ofimática (LibreOffice etc), también permite ver mejor en
  tiempo real, cuando pones texto en negritas etc. sin tener que estar cambiando constantemente al modo "vista previa" para ver si lo que pusiste está bien.

**NOTA:** Todo esto es para los que quieran hacer blogs más complejos/avanzados, si no entendiste nada de lo que dije aquí o no te interesa estar marcando texto
en **negritas** etc. y simplemente quieres un rinconcito en la Internet donde echar tus versos del alma, publicar tus cuentos o novelas, o simplemente un espacio
donde expresar lo que piensas, no te sientas intimidado por todo esto del Markdown, puedes publicar tus artículos en texto sin preocuparte por usar negritas etc.
