1 - Instalamos ruby y jekyll
No voy a entrar en el detalle de como instalar ruby, yo lo tengo instalado usando rbenv, Ruby: https://github.com/rbenv/rbenv#installation


Instalamos Jekyll: `gem install jekyll`


2 - Creamos un repositorio en github
3 - Clonamos el repo
4 - Luego vamos a instalar jekyll en el repo
    `jekyll new .`

5 - Corremos el blog `bundle exec jekyll serve` y podremos accederlo a travez de http://localhost:4000

6 - Habilitamos gitlab pages, para ello editamos `Gemfile` y comentamos la linea `# gem "jekyll", "~> 4.0.0"` y luego descomentamos `gem "github-pages", group: :jekyll_plugins`

    Finalmente corremos `bundle update`

7 - Por default github pages usa `/blog` como en la url, asi tenemos que cambiar nuestro `_config.yml` para soportar eso, sino tendremos problemas con los estilos. Basta con cambiar el `baseurl`

  `baseurl: "/blog"`