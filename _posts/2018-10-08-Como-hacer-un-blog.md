---
layout: post
title: Cómo hacer un blog usando Github
image:
  path: /assets/2018-10-08/blag.png
description: Hoy vamos a hacer un blog utilizando Github y Markdown y va a quedar bien bonito y rápido.
---

![Blag]({{ page.image.path }})

Hoy vamos a hacer un blog utilizando Github y Markdown y va a quedar bien bonito y rápido.

Primero vamos a hablar un poco sobre las herramientas que vamos a utilizar: Jekyll, Markdown, Github.

<!--more-->

### Jekyll

[Jekyll](https://jekyllrb.com/) es un motor de páginas web y blogs utilizando solo archivos estáticos. Eso quiere decir que Jekyll no necesita configuraciones complicadas ni cosas como bases de datos y se puede levantar en algo como Github (o incluso Dropbox, pero no vamos a hablar de eso hoy)

### Markdown

Markdown es un lenguaje de _markup._ Entonces utilizando **texto plano** puedes indicar formato. Por ejemplo:

```markdown
Markdown es un lenguaje de _markup._ Entonces utilizando **texto plano** puedes indicar formato.
```

El cuadro anterior es el texto que representa las _italicas_ o las **negritas.** Es muy fácil de aprender a utilizarlo y no necesitas herramientas complicadas como para otros blogs. Todos los archivos de markdown tienen la extensión `.md`

En nuestro caso vamos a utilizar la variedad de [Markdown de Github](https://guides.github.com/features/mastering-markdown/), porque vamos a utilizar Github.

### Github

[Github](https://github.com/) es un sitio dónde puedes compartir fácilmente tu código con otros desarrolladores. Es muy poderoso, pero vamos a utilizar lo mínimo necesario (además de que vamos a tener pronto una guía de Git + GitHub)

## ¿Cómo comenzar?

### Creando un repositorio en Github

Para comenzar necesitas una cuenta de Github, pero como todos estamos grandes voy a asumir que sabes cómo hacer una. Una vez que tengas tu cuenta puedes crear un nuevo repositorio.

![Crear repo](/assets/2018-10-08/new_repo.png)

Nombra tu repositorio con `tu-propio-nombre de-usuario.github.io` así lo podrás visitar en esa dirección. Ten cuidado con las mayúsculas y minúsculas. Por ejemplo, mi blog personal esta en [https://Darkade.github.io](Darkade.github.io)

![Nombre del repo](/assets/2018-10-08/repo_name.png)

Agrega la descripción que tu quieras y asegurate de marcar el repositorio como público. Las demás opciones no importan mucho ahora, así que deja los defaults.

### Eligiendo un tema inicial

Ahora que tu repositorio esta creado deberás tener una pestaña de `settings` y baja hasta encontrar la sección de **GitHub Pages** y elige un tema.

![Choose Theme](/assets/2018-10-08/choose_theme.png)

Github tiene algunos temas iniciales, yo voy a elegir _Cayman_ pero el proceso es muy parecido para cualquiera de los demás temas. Solo presiona el botón `Select theme` cuando hayas decido que tema usar.

![Cayman Theme](/assets/2018-10-08/cayman.png)

Ahora deberías de estar en una pantalla creando un archivo llamado `index.md` por el momento no vamos a cambiar nada en este archivo. Servirá como la página principal de nuestro blog. Una vez que termines de editarlo presiona el botón de **Commit Changes** al final de la página.

![Commit Changes](/assets/2018-10-08/commit.png)

Ahora deberías de poder visitar tu sitio en `https://tu-propio-nombre de-usuario.github.io` si tienes dudas puedes ir otra vez a la sección de Github Pages en los settings del repositorio y verás la dirección dónde esta el blog.

![Blag settings](/assets/2018-10-08/blag_settings.png)

![Blag screenshot](/assets/2018-10-08/blag_screenshot.png)

### Modificando el tema para convertirlo en un blog

Como podrás ver no hay posts en este momento, los temás default de Github no soportan blogging, pero con algunas modificaciones sencillas lo podemos hacer.

Las modificaciones van a consistir en crear dos archivos de formato: un `post.html` y un `home.html` y algunos posts de prueba.

#### post.html

Presiona el botón de **Create new file** y nombralo `_layouts/post.html` el nombre es importante, ya que los posts que creemos estarán buscando este archivo.

![New file](/assets/2018-10-08/new_file.png)

![File Name](/assets/2018-10-08/file_name.gif)

El único contenido que vamos a poner en este archivo son las siguientes cuatro lineas:

```markdown
---
layout: default
---
{{ content }}
```

Los tres guiones arriba y abajo son importantes así que asegurate de colocarlos.

Una vez que termines presiona el botón **Commit Changes**

---

Vamos a hacer algo muy parecido para crear un archivo `_posts/2018-10-08-prueba-uno.md` es importante que coloques la fecha ya que Jekyll la utiliza para crear las URLs de los posts. También nota que este es un archivo `.md` porque será un archivo de Markdown

```markdown
---
layout: post
title: Cómo hacer un blog usando Github
---

Hoy vamos a hacer un blog utilizando Github y Markdown y va a quedar bien bonito y rápido.
```

Nota que en vez de utilizar el `layout: default` utilizamos `layout: post` que es el layout que acabamos de crear. En `title:` puedes poner el titulo que tu queiras, para el post. Y todo lo que esta debajo de los tres guiones va a ser el contenido.

![Contenido del post](/assets/2018-10-08/post_content.gif)


Si todo salió bien deberías poder ver el post en `https://tu-propio-nombre de-usuario.github.io/2018/10/08/prueba-uno`

Cómo puedes ver la fecha que pusiste al inicio del nombre del archivo es muy importante en el link. Y el resto del nombre del archivo lo completa (y no tiene el `.md`).

![Post Publicado](/assets/2018-10-08/post.png)

Ya casi lo logramos!! Ahora solo necesitamos un lugar en dónde ver la lista de todos nuestros posts.

#### home.html

Lo primero que tenemos que hacer es habilitar un plugin para nuestro blog. Para hacerlo, modificaremos el archivo `_config.yml` y agregaremos `jekyll-paginate`

```markdown
theme: jekyll-theme-cayman
paginate: 5
plugins:
  - jekyll-paginate
```


Y ahora, finalmente vamos a modificar el `index.md`. Lo primero que vamos a hacer es renombrarlo a `index.html` y vamos cambiar todo el contenido por:

```html
---
layout: default
---

<!-- This loops through the paginated posts -->
{% for post in paginator.posts %}
  <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
  <p class="author">
    <span class="date">{{ post.date }}</span>
  </p>
  <div class="content">
    {{ post.content }}
  </div>
{% endfor %}

<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}" class="previous">
      Previous
    </a>
  {% else %}
    <span class="previous">Previous</span>
  {% endif %}
  <span class="page_number ">
    Page: {{ paginator.page }} of {{ paginator.total_pages }}
  </span>
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}" class="next">Next</a>
  {% else %}
    <span class="next ">Next</span>
  {% endif %}
</div>
```

Cuando tengas el contenido solo has **Commit** de los cambios. Ahora si visitas `tu-propio-nombre de-usuario.github.io` en la parte de abajo deberías de poder ver el paginador de todos tus posts.

![Paginator](/assets/2018-10-08/paginator.png)

La explicación de este código, en mi mejor imitación de libro de texto, se deja como ejercicio.

## ¿Y luego?

Listo, ahora tienes un blog funcional. Todos los posts que quieras hacer solo necesitas colocarlos dentro de `_posts/` y utilizar la misma estructura de nombre de archivos `2018-01-01-tu-post.md`

Lo siguiente que podrías hacer es utilizar un tema diferente. Solo elige otro desde la sección en los `settings` del repositorio.

También puedes aprender más sobre Jekyll y Markdown para aprender a insertar imágenes en Markdown o seguir modificando los temas; para git pronto vamos a tener una guía básica.

Hay mucho por hacer con este proyecto pero puedes visitar un repositorio de ejemplo [aquí](https://github.com/Darkade/blag-example) y copiar lo que necesites. También puedes verlo funcionando en: https://darkade.github.io/blag-example/

Y en serio te puede tomar solo cinco minutos!

<a href="http://www.youtube.com/watch?feature=player_embedded&v=OXLeYPLefoA
" target="_blank"><img src="http://img.youtube.com/vi/OXLeYPLefoA/0.jpg"
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>
