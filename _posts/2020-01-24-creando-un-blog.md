---
layout: post
current: post
cover:  assets/images/writting-blog.png
navigation: True
title: Creando tu primer blog con Github Pages y Jekyll
date: 2020-01-24 10:00:00
tags: [Blog]
class: post-template
subclass: 'post tag-getting-started'
---


Hace unos días comencé a pensar en la idea de tener un blog en donde poder ir documentando los problemas, desafíos y aprendizajes de mi día a día. 

Para evaluar las posibles herramientas o plataformas a utilizar arme una lista de lo que esperaba para mi blog:

* Performance: el blog tiene que ser increíblemente super archi rápido. Punto. :D 
* Themes: Contar con un buen catalogo de themes. No tengo el tiempo de sentarme a programas CSS.
* Extensible: Tener la posibilidad de fácilmente extender la funcionalidad del blog (Google Analytics, comentarios, listas de distribución, etc). A travez de plugins o algún otro mecanismo. 
* Markdown: El contenido del blog tiene que estar escrito en su **totalidad** en markdown. Esto debido principalmente a que quiero tener la flexibilidad de moverme a otra plataforma si me encuentro con alguna dificultad en la que seleccione. 
* Divertido: Sabiendo que seguramente pasare algunas horas por semana intentando escribir, la herramienta o plataforma que elija tiene que ser fácil, rápida pero sobre todo muy divertida de usar! 
Hosting: No tener que ademas de elegir una herramienta, usar 
Free: En lo posible que sea gratis o al menos muy económico. El blog es un experimento, quiero ver qué tan fácil es mantenerlo, probar algunas herramientas, etc. Con lo cual, cuanto menos gasto tenga mejor. 

Ahora que sé que quiero, veamos que puedo usar para llevar adelante esta idea!

#### Elixir/Serum

[Elixir](https://elixir-lang.org/) es un lenguaje por el que me he fascinado en estos últimos meses. Así que la primer opción fue buscar si ya había alguna solución que cumpliera con mis condiciones/necesidades.
[Encontré algunas por aquí](https://elixirforum.com/t/elixir-blogging-software/8918) y algunas mas [aquí](https://github.com/h4cc/awesome-elixir#static-page-generation), pero lamentablemente muchas de ellas, hace ya mucho tiempo que se encuentran sin actividad. [Serum](https://github.com/Dalgona/Serum) es la única que se mantiene en pie, con lo que me decidí a probarla y en un par de minutos ya lo tenia corriendo. 

De entraba sabia que usar algo como [Serum](https://github.com/Dalgona/Serum), me iba a obligar también a pensar en donde iba a hospedar el blog, y esa era una de las cosas que no tenia intensiones de hacer, pero mi amor por Elixir me llevo a probarlo igual. 

En cuanto a características, mal que mal reúne todo lo que buscaba, performance, markdown, extensibilidad, cierta madurez, pero el catálogo de themes es muy reducido, al igual que el de plugins. Y el punto de tener que buscar también un hosting que me permitiera publicarla hizo que rechazara esta opción.  Al menos por ahora :)

#### Golang/HUGO

La otra herramienta que evalúe, fue [Hugo](https://gohugo.io/), honestamente reúne todo lo que buscaba, excepto la parte divertida. Sí, lo sé, con este comentario, estoy cavando mi propia tumba. Hoy en día, [Go](https://golang.org/) es **EL** lenguaje, de moda, todos (o la gran mayoría) quiere usarlo y hablan maravillas de él (y no lo dudo). A mí, personalmente, hay un tema de “piel" que hace que no me decida por usarlo (ya escribiré mas acerca de Go porque en algún otro post). Así que HUGO descartado. 

#### Github pages/Jekyll

Hace tiempo que venia con ganas de poder usar [GitHub pages](https://pages.github.com/) para algo. Uso Github en mi dia a dia, en el trabajo y proyectos personales, pero por una cosa o la otra no había podido usar nunca Github Pages. 

Luego de leer la [documentación](https://help.github.com/en/github/working-with-github-pages), investigar un poco, ver como funcionaba, lo fácil que esta conectado con los repositorios, el hecho de que no tenga que manejar deploys, sea gratis (solo para repositorios públicos), estable, extensible gracias a [Jekyll](https://jekyllrb.com/), un catalogo de themes enorme, plugins a mas no poder, y sobre todo divertido! Todo esto hizo de esta opción la mejor de todas. Así que aquí estamos, con mi primer post en el blog corriendo sobre Github Pages.

Ahora a pensar en el siguiente post :) 

Cya!
