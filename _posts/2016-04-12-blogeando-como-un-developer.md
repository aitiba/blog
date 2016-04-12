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



- Fork-ear [otro blog](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll).
- Después de fork-ear, ir a Settings y cambia el nombre del repositorio a blog.
- Preparar el entorno:
	- `sudo apt-get install libruby2.0 ruby2.0-dev`
	- `sudo gem2.0 install jekyll-paginate`
	- `sudo gem2.0 install jekyll-feed`
	- `gem2.0 install jekyll`
- Clonar el repositorio:
	- `git clone https://github.com/nombredeusuario/blog`
	- `cd blog blog`
	- `jekyll serve`
- Tendras en blog funcionando en local en [http://127.0.0.1:4000/startbootstrap-clean-blog-jekyll/](http://127.0.0.1:4000/startbootstrap-clean-blog-jekyll/)

