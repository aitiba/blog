---
published: true
layout: post
title: Push notification con ionic I (Limited push)
date: 
  "Tue Apr 25 2016 14:00:00 GMT+0200 (CEST)": null
author: aitiba
"header-img": "img/post-bg-05.jpg"
---
Existen dos modos de notificaciones push con ionic.io:

- **Limited push**: Este modo no pasa por la configuración de los APN, GCM, y perfiles de seguridad. Lo cual reduce en gran medida los pasos necesarios para ver una notificación en su aplicación. Además, tiene el beneficio de trabajar en un navegador o un emulador. Estamos en este modo cuando, *dev_push* esta a *true*.
Se recomienda iniciar con este modo para asegurarse que su aplicación se ha configurado correctamente antes de preocuparse por otras configuraciones.

- **Full push**: Se comunica con APN, GCM y perfiles de seguridad. Modo recomendado cuando se sienta cómoda con las *limited push*. Estamos en este modo cuando, *dev_push* esta a *false*.


> Estamos usando la API beta de push. Hace unas semanas, se cambio de la versión alpha a esta beta. Por lo que, la API push esta teniendo cambios constantes y **no es nada estable**. Estos pasos están probados para las siguientes versiones:
- Cordova CLI: 5.4.1
-  Ionic Version: 1.3.0
- Ionic CLI Version: 1.7.14
- Ionic App Lib Version: 0.7.0
- Node Version: v5.11.0


Proceso a explicar como hacer funcionar las push notification en modo limited push.

Empezamos creando la aplicación Ionic. Para ello, usaremos el starter *tab*:
  - `ionic start myApp tabs`
  - `cd tabs`

Instalamos los componentes necesarios:
  - `ionic add ionic-platform-web-client` (para comunicarnos con ionic.io)
  - `ionic plugin add phonegap-plugin-push -variable SENDER_ID=(sender_id)`
> El dato para (sender_id) se consigue haciendo un nuevo proyecto dentro de [Google Developers Console](https://cloud.google.com/console).

Conectamos la app con ionic.io:
  - `ionic io init`

Ponemos la app en modo development para que sepa que queremos usar *limited push*:
  - `ionic config set dev_push true`

Escribimos el siguiente código dentro de *app.js*:

  ``` javascript
  .run(function($ionicPlatform) {
    $ionicPlatform.ready(function() {
      var push = new Ionic.Push({
        "debug": true
      });

      push.register(function(token) {
        // Log out your device token (Save this!)
        console.log("Got Token:",token.token);
      });
    });
  })
```
Creamos un perfil de seguridad dentro de la opción push de una aplicacion en ionic.io. Clicamos en *Configure profile*. Después en *New Security Profile*. En *Profile name* ponemos *fake_push_profile*. En *type*, seleccionamos *Development*. Clicamos en *Create*.

Creamos un token para la aplicación de ionic.io. Nos logueamos en [apps.ionic.io](http://apps.ionic.io) y vamos a *Settings -> API Keys*. Dentro, vamos a *API Tokens*. Creamos un nuevo token y le damos un nombre. Después, clicamos en *show token* y copiamos el token para ser usado más tarde como API_TOKEN.

Ponemos el servidor ionic en marcha (`ionic serve`). Se abrirá un navegador en http://localhost:8100. Abrimos la consola (F11) y copiamos el device_token para ser usado en el siguiente paso como DEV_DEVICE_TOKEN.

Para finalizar, probamos que se manda la notificación push. Cambiamos API_TOKEN y DEV_DEVICE_TOKEN por los datos correspondientes:

      curl -X POST -H "Authorization: Bearer API_TOKEN" -d '{
          "tokens": ["DEV_DEVICE_TOKEN"],
          "profile": "fake_push_profile",
          "notification": {
              "message": "Hello World!"
          }
      }' "https://api.ionic.io/push/notifications"

En el navegador abierto por *ionic serve*, aparecerá un alert diciendo "Hello World!" :-)

He subido el código del proyecto a [github](https://github.com/aitiba/ionicLimitedPush) por si resulta de ayuda.

Thanks @rudy for help! So appreciate! :-)
