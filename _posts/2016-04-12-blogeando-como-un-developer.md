---
published: true
layout: post
date: 
  "Tue Apr 18 2016 14:00:00 GMT+0200 (CEST)": null
author: Aitor Ibañez
"header-img": "img/post-bg-05.jpg"
title: "Blogueando como un developer: Jekyll + GitHub + Prose.io"
---
Llevaba un tiempo con ganas de publicar mi blog y subir contenido habitualmente. Para ello me he decantado por las github pages. De esta manera, tendré un blog dentro de un repositorio de git sin necesidad de bases de datos.

A continuación, procedo a explicar el proceso para poner el entorno en marcha.

Primero empezamos fork-eando un tema que este hecho en jekyll. Yo he usado [Clean Blog theme by Start Bootstrap](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll) pero existen muchos más: [Notepad](https://github.com/hmfaysal/Notepad) o [más temas](http://jekyllthemes.org/)

Una vez fork-eado el repositorio, vamos a _Settings_ y cambiamos el nombre del repositorio a _blog_.

Preparamos el entorno instalando los siguientes paquetes:

- `sudo apt-get install libruby2.0 ruby2.0-dev`
- `sudo gem2.0 install jekyll-paginate`
- `sudo gem2.0 install jekyll-feed`
- `gem2.0 install jekyll`

Clonamos el repositorio para que podamos usarlo desde nuestro local en [http://127.0.0.1:4000/startbootstrap-clean-blog-jekyll/](http://127.0.0.1:4000/startbootstrap-clean-blog-jekyll/):

- `git clone https://github.com/usuario/blog`
- `cd blog blog`
- `jekyll serve`
        
Para tener un editor donde poder escribir y subir nuevo contenido recomiendo [Prose.io](http://prose.io).

Estos son los pasos que necesitamos para poder usar nuestro blog jekyll recien creado con Prose.io:

- Autorizarse en [Prose.io](http://prose.io)
- Ir al proyecto.
- Abrir __config.yml_
- Modificar baseurl a http://usuario.github.io/blog/ y guardar.
- El blog estara funcionando en http://usuario.github.io/blog/
    
Por último, veremos como crear contenido a traves de prose.io:

- Ir a **posts**.
- Crear una página y añadir el contenido necesario.
- Clickar en el botón _metatags_ (en la derecha de la pantalla)  y añadir lo siguiente:
   - `layout: post`
   - `author: nombredeusuario`
   - `"header-img": "img/post-bg-05.jpg"`
- Guardar.
- El post aparecera automáticamente en la página principal del blog. :-)
