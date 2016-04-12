---
published: true
layout: post
date: 
  "Tue Apr 12 2016 14:00:00 GMT+0200 (CEST)": null
author: Start Bootstrap
"header-img": "img/post-bg-05.jpg"
title: "Blogueando como un developer: Jekyll + GitHub + Prose.io"
---


Llevaba un tiempo con ganas de publicar mi blog y subir contenido habitualmente. Para ello me he decantado por las github pages. De esta manera tendre un blog dentro de un repositorio de git sin necesidad de bases de datos.



1. Fork-ear [otro blog](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll).
2. Después de fork-ear, ir a __Settings__ y cambia el nombre del repositorio a __blog__.
3. Preparar el entorno:
	- `sudo apt-get install libruby2.0 ruby2.0-dev`
	- `sudo gem2.0 install jekyll-paginate`
	- `sudo gem2.0 install jekyll-feed`
	- `gem2.0 install jekyll`
4. Clonar el repositorio:
	- `git clone https://github.com/nombredeusuario/blog`
	- `cd blog blog`
	- `jekyll serve`
5. Tendrás en blog funcionando en local en [http://127.0.0.1:4000/startbootstrap-clean-blog-jekyll/](http://127.0.0.1:4000/startbootstrap-clean-blog-jekyll/)
6. Editando el con [Prose.io](http://prose.io):
	- Autorizate en [Prose.io](http://prose.io)
	- Vete al proyecto.
	- Abrir __config.yml__
	- Modificar baseurl a http://nombredeusuario.github.io/blog/. Guardar.
	- El blog estara funcionando en http://nombredeusuario.github.io/blog/
7. Crear / editar contenido:
	- Ir a __posts__.
	- Crear página y añadir el contenido necesario.
	- Clickar en el botón metatags y añadir lo siguiente:
		- `layout: post`
		- `author: nombredeusuario`
		- `"header-img": "img/post-bg-05.jpg"`
	- Guardar
	- El post aparecera automáticamente en el listado del blog. :-)

