# 💡TIP — ¿Cómo usar Mastodon desde Delta Chat?

Es posible convertir Delta Chat en un cliente de Mastodon, publicar en tu cuenta de Mastodon, recibir las publicaciones de las personas que sigues, responder,
retootear, dar "me gusta", chatear en privado con usuarios de Mastodon, etc.

Si no sabes qué es la red social Mastodon, te recomiendo leer [este artículo](https://writefreely.public.cat/adbenitez/mastodon-alternativa-libre-a-twitter) y la
[página de Mastodon en Wikipedia](https://es.wikipedia.org/wiki/Mastodon_(red_social))

## PARTE 1: (Requiere Internet)
Lo primero que necesitas es, obviamente, tener una cuenta en Mastodon, si ya tienes una cuenta en Mastodon, pasa a la segunda parte de este tutorial, si no, para
crearte una cuenta necesitas ir a Internet y:

* Abrir la página de algún servidor (a partir de ahora le diré “instancia“) de Mastodon. Algunas páginas de ayuda para seleccionar la instancia que más vaya con
  tus gustos:
  - https://joinmastodon.org/communities
  - https://instances.social
* Registrarte dando un nombre de usuario, correo electrónico y una contraseña.
* Esperar que te llegue un correo electrónico, para confirmar que la dirección de correo que pusiste te pertenece. (**IMPORTANTE:** ese correo no sale en Delta
  Chat si no tienes la interacción con el correo electrónico en "Todos". En dependencia del servidor que escojas, el mensaje puede tardar unos minutos en llegar)
* Abrir el enlace de verificación que viene dentro de dicho mensaje.
* Una vez tengas una cuenta en Mastodon, digamos que te creaste la cuenta “fulano” en la instancia https://mastodon.online y la creaste usando tu correo nauta:
  “pepito@nauta.cu” y tu contraseña de Mastodon digamos que es “Contraseña123“, teniendo eso en cuenta, remplaza por los valores reales que usaste para crear tu
  cuenta y sigue los pasos que vienen a continuación.

## PARTE 2: (Con acceso al correo es suficiente)

* Abre tu Delta Chat.
* Da en la bolita con el + para agregar un contacto.
* En la barra de arriba pega este correo: **simplebot@testrun.org** y comienza un chat con el bot.
* En el chat con el bot envía un mensaje con este comando (recuerda remplazar cada parámetro por tu instancia, correo y contraseña):
  ```
  /m_login https://mastodon.online pepito@nauta.cu Contraseña123
  ```
* Si pusiste todo bien, estarás logeado en Mastodon!!! y se te crearán dos chats nuevos con el ícono de Mastodon:
  - **Home:** Aquí recibirás todo lo que publican las personas que sigues y además lo que envíes en este chat será mostrado públicamente en tu perfil (cada
    mensaje será un toot en Mastodon), y podrá ser visto por todos los usuarios de Mastodon y saldrá en el “home” de tus seguidores. Además de texto también
    puedes enviar imágenes, gif, mensajes de voz y videos.
  - **Notifications:** En este chat recibirás notificaciones cuando tengas un nuevo seguidor y cuando alguien le de "me gusta" o re-comparta tus publicaciones,
    además, aquí recibirás los toots en que seas mencionado por alguien, públicamente, o cuando fuiste mencionado en privado pero hay varias personas involucradas
    en la conversación.
* Ahora puedes escribir tu primera publicación, para avisarme públicamente que te uniste a Mastodon, has lo siguiente: ve al chat “Home” y envía el mensaje:
  ```
  @adbenitez@mastodon.xyz #Hola, soy nuevo aquí #Cuba
  ```
* Cuando alguien te escriba en privado (1×1) te aparecerá en tu Delta Chat, incluso con su foto de avatar.
* Supongamos que quieres escribirle en privado al usuario “ejemplo@quey.org“, ve al Chat “Notifications” y envía el comando:
`/m_dm ejemplo@quey.org`
* Supongamos que quieres seguir al usuario “ejemplo@mastodon.social“, envía este comando en tu chat “Notifications“:
`/m_follow ejemplo@mastodon.social`
* Para ver los toots públicos más recientes que se han publicado en tu instancia:
`/m_local`
* Para ver los toots públicos más recientes que se han publicado en todo el fediverso conocido:
`/m_public`
* Para ver los toot más recientes que contengan un hashtag dado, por ejemplo `#Cuba`:
`/m_tag Cuba`
* Tambien se pueden hacer búsquedas, etc. para una lista completa de todos los comandos soportados envíale `/help` al bot.
