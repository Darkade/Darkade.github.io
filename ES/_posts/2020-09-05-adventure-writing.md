---
layout: post
title: "Cómo escribí una aventura de D&D usando Emacs"
image:
  path: /assets/2020-08-16/2020-08-16-Arcane-Moon.png
  width: 1920
  height: 1280
description: Acabo de publicar una aventura de D&D y la escribí usando solo Emacs... más o menos.
---

![Arcane Moon ya esta disponible!][cover]

Emacs & org-mode juntos son definitivamente la mejor experiencia para escribir, me permitió organizar mi proceso, escribir, exportar a PDF y hacer revisiones rápidamente. Yes, soy developer, y si, Emacs es mi **IDE** preferido, sin embargo, incluso si  tu uso es diferente al mio, creo que hay mucho que puedes sacar de usar emacs, aunque tome algo de tiempo en configurar.

<!--more-->

---

[![Arcane Moon la aventura][FullAdventure]][Arcane Moon]
_Arcane Moon fue escrita en Emacs_

Entonces. Después del titulo click-bait ¿En verdad solo usé Emacs para escribir [Arcane Moon]? más o menos. Pude solo haber utilizado Emacs y org-mode, pero emplee otras herramientas para complementar el proceso; y como probablemente estas aquí buscando esa lista de herramientas, esto es lo que necesitas para hacer lo mismo:

**Si quieres terminar con una aventura sencilla, necesitas:**
- [Emacs + org-mode][emacs]
- [El repositorio de DnD 5e LaTeX Template en github][template]
- [Un entorno de LaTeX][latex]

**Si quieres tener una portada:**
- [Adobe spark][spark]
- Preview o una herramienta similar para ver PDFs con capacidad de edición mínima

**Si quieres agregar mapas:**
- [Dungeondraft][dungeondraft]
- [Krita][krita]

**Si quieres tener _spot art:_**
- Un editor de LaTeX
- Assets para tu spot art

**Si quieres colaborar con un editor o proof reader:**
- Google docs

No estoy aquí para enseñarte cómo instlar todas estas herramientas, hay muchos [tutoriales][orgmode] que hacen eso, pero te voy a decir cómo las usé yo.

## Aventura sencilla

![Arcane Moon en Emacs][emacsscreenshot]
_Arcane Moon en Emacs_

Emacs, y más precisamente org-mode fue la herramienta central para todo. La utilicé para:

### Esbozar mi aventura
Empecé agregando las secciones que quería tener. Arcane Moon esta dividida en los créditos, la introducción, la aventura e infomración adicional.

### Agendar mis tareas
Dar seguimiento de cuando quería hacer las cosas, agendar y estar conciente de mis restricciones de tiempo me ayuda a sacar la engergía creativa. Org-mode es excelente para [agendar](https://orgmode.org/guide/Dates-and-Times.html) cuando sabes cómo usar1 `agenda-mode`.

Puedes agregar una fecha límite utilizando el comando `C-c C-d` o una fecha sencilla con `C-c .`. Después puedes ver tu agenda con `C-c a`

### Marcar diferentes estados de progreso

Puedes marcar cualquier título como `DONE` y `TODO`. Pero también puedes configurar cualquier otro[estado de progreso](https://orgmode.org/guide/TODO-Basics.html) con bastante facilidad.

Los dos estádos básicos fueron suficientes para mi. Los utilicé para dar seguimiento de en qué _fase_ del proyecto me encontraba: al principio de la fase de borrador todos los encabezados eran `TODO` y cuando había terminado eran `DONE`. Al principio de la fase de proof reading todo era `TODO` y al final eran `DONE`

La razón principal por la que usé un editor de _plain text_ es para no preocuparme por el formato si no hasta que **necesitara** preocuparme por el formato. Creo que pensar en cosas como tipografía es una enorme distracción, y por lo mismo no recomendaría usar Word, Pages or Google Docs.

Pero eventualmente si tuve que preocuparme por formato y tuve que que exportar a PDF. Para esto utilicé LaTeX.

### Exportando a PDF

Después de instalar mi distribución [latex] preferida [exportar](https://orgmode.org/manual/LaTeX-Export.html) de org a PDF utilizando `C-c C-e l p` fue bastante directo. Pero la configuración default es pobre, por decir lo menos.

![Exportando la aventura sin un tema seleccionado][FullAdventureNoClass]
_Exportando la aventura sin un tema seleccionado_

Para empezar, no se ve para nada como un libro de D&D. Así que emplee el [DnD 5e LaTeX Template][template] de Brian Criswell. Para configurar `org-mode` solo es necesario agregar esto a tu archivo `.emacs`:

```lisp
;; Latex D&D https://github.com/rpgtex/DND-5e-LaTeX-Template
(with-eval-after-load 'ox-latex
   (add-to-list 'org-latex-classes
                '("dndbook"
                  "\\documentclass{dndbook}"
                  ("\\part\{\%s}" . "\\part*\{\%s}")
            		  ("\\chapter\{\%s}" . "\\chapter*\{\%s}")
                  ("\\section\{\%s}" . "\\section*\{\%s}")
                  ("\\subsection\{\%s}" . "\\subsection*\{\%s}")
                  ("\\subsubsection\{\%s}" . "\\subsubsection*\{\%s}"))))
```

Y luego hasta arriba de tu archivo de trabajo en Emacs:

```org
#+latex_class: dndbook
#+latex_class_options: [10pt,letterpaper,twocolumn,twoside,openany,nodeprecatedcode]
#+latex_header: \usepackage[english]{babel} \usepackage{titlesec}
#+latex_header_extra: \hypersetup{colorlinks=true, urlcolor=blue, linkcolor=blue, citecolor=red, PDFborder={0 0 0}}
#+latex_compi`ler: PDFlatex

#+OPTIONS: todo:nil
#+OPTIONS: toc:nil
#+OPTIONS: title:nil

#+title:
#+author:
#+email:
#+language: en
#+description:
#+keywords:
#+subtitle:
#+date: \today
```

Llénalo como creas conveniente y vuelve a intentar exportar con `C-c C-e l p`. Ahora debería de verse como queremos que se vea, como un libro de D&D!

Intenta mover y comentar algunas de las lineas que agregas al archivo `.emacs`. Si quitas `("\\part\{\%s}" . "\\part*\{\%s}")` entonces el nivel principal del arbol se va a mostrar como el encabezado de un cápitulo y así sucesivamente.

Otras cosas que podrías hacer es emplear los helpers del DnD 5e LaTeX Template, como `DndComment`, `DndReadAloud` y `DndSidebar` que agregan secciones y cajas fácilmente, que todos sabemos cuan útiles pueden ser.

Puedes aprender más de estos en la documentación, pero ese es su uso en LaTeX directamente. Para usarlos en Emacs puedes intentar esto:

```
#+BEGIN_DndComment
Esto se va a mostrar como un comentario de D&D
#+END_DndComment
```

¡Las mayúsculas y minúsculas son importantes! Si quieres usar los otros helpers puedes escribir `#+BEGIN_DndComment`, `#+BEGIN_ReadAloud` o `#+BEGIN_DndSidebar` conforme lo necesites.

El template también incluye un helper de `DndMonster`. No tengo un modo "org" de usarlos. Pero puedes escribir directamente el LaTeX en el documento y debería funcionar sin más complicaciones.

![La aventura completa con el template de DnD 5e][FullAdventureDnD]
_La aventura completa con el template de DnD 5e_

Eso es escencialmente toda la configuración que utilicé y lo podrías dejar hasta ahí si quisieras. Pero si quieres tener un libro con arte y formato más o menos pulido sigue leyendo.

## Agregando una portada

[![Portada de Arcane Moon][adventurecover]][Arcane Moon]

Hice esta portada con Stock Art de [Rian Trost] y Adobe Spark. Spark tiene plantillas y tamaños pre-configurados que puedes usar para imprimir y para digital y es un modo sencillo de llegar a una portada decente. La otra ventaja es que puedes cambiar el tamaño y Spark va a redistribuir automáticamente el contenido para ti; de modo que lo usé para mis posts de social media y parala portada de este articulo.

Una vez que me sentí bien con mi portada la descargue como un archivo PNG. Y utilizando preview, en macOS, abrí tanto la portada como el PDF previamente exportado y simplemente arrastré la portada, guardé y listo!

## Agregando mapas

Usé [Dungeondraft][dungeondraft] para hacer mis mapas. And I think they came out pretty cool. Dungeondraft is a whole thing, but my recommendation is to get familiar with the "levels" and "layers" and understanding those are different things.

Ten cuidado, al exportar puedes encimar dos niveles, pero solo dos. In my caso hice el pasto y el camino de pierda en un solo nivel, y para todos los niveles superiores solo hice los pisos de la torre; entonces usé la capa de hasta abajo y exporté los otros niveles por encima. Es confuso, pero si planeas hacer un calabozo con varios niveles esto te va a ahorrar mucho trabajo.

![Exportando con Dungeondraft][dungeondraftscreenshot]
_Exportando con Dungeondraft_

Después de exportar usé [Krita][krita] para agregar algunos marcadores, como números de referencia y para cambiar los tamaños de mis miniaturas ¡asegurate de hacer copias del original!

Esto debería ser suficiente para poner las imagenes en tu archivo org y hacerles parte del documento PDF. Utilicé este snippet para agregar los mapas a la aventura, pero podría hacerlo hecho directamente en el export de LaTeX si necesitara más opciones.

```org
#+CAPTION: your caption text
#+NAME: fig:C2E2
[[./maps/thumbs/C2E2_001.jpg]]
```

Debido a que vas a usar tus propios mapas toma nota de las rutas que necesitas, para mi es `./maps/thumbs` pero para ti será diferente.

Finalmente, si te interesa Dungeondraft y la cartografía en general te recomiendo seguir a [@TheAbeilQueen](https://twitter.com/TheAbeilQueen) en twitter.

## Agregando Spot Art

Otra opción para agregar el arte es editando directamente el archivo `.tex` que se esta generando durante el export. Este archivo es usado como un paso intermedio para llegar al PDF final y para editarlo necesitas un editor de Tex, que debería estar incluido con tu distribución de LaTeX; en mi caso es TeXShop.

En TeXShop busco el lugar en el que quiero colocar el arte e inserto un snippet similar a este:

```tex
\begin{figure}[h]
\centering
\includegraphics[width=.9\linewidth]{./assets/accents/line1.png}
\end{figure}
```

La razón por la que hice esto en el archivo `.tex` en vez de en el org es porque quería más control sobre el lugar específico en la distribución.

Otra vez, asegurate de que la ruta a tu imagen es correcta. En este ejemplo es `./assets/accents` que es dónde tengo mi spot art. También nota que he agregado la opción `width=.9` para que ocupe ligeramente menos espacio que el texto.

Finalmente la opción `[h]` significa _"here"._ De modo que al exportar a PDF la imagen va a estar más ao menos_"ahí"._ Hay muchas [otras opciones](https://www.overleaf.com/learn/latex/Positioning_of_Figures), considera probar varias para encontrar la que se ajuste mejor a tu necesidad.

![El spot art en una de las esquinas][spotart]
_El spot art en una de las esquinas_

Si quieres usar el arte para hacer un salto de página un hack sencillo es modificar el parametro de `width=`. Con solo un poco más o menosel texto será forzado a saltar.

Hay muchisimas cosas que puedes hacer editando el archivo `.tex`. Podrías incluso escribir directamente la aventura aquí, pero no recomiendo hacerlo; rápidamente se vuelve dificil de manejar y de leer.

## Colaborando con un proof reader

En el mejor de los casos este es un hack sucio y el peor es un modo impráctico de colaborar. Realmente no recomiendo hacerlo pero a mi si me funcionó así que podría funciar para ti.

Exporté mi trabajo a formato ODT desde emacs con el comando `C-c C-e o o`. Esto me da un archivo ODT que subí a Google Drive para editar con Google Docs. Mi editora utilizó los comentarios y el modo de sugerencias, mientras yo de mi lado mantuve el archivo org actualizado manualmente para no tener que volverlo a subir..

Como dije, en el mejor de los casos es un hack sucio, pero a mi me funcionó.

---

¡Gracias por leer este post! Creo que puede haber alguien allá afuera a quien le ayude saber sobre las herramientas que usé para escribir [Arcane Moon].

Ya que estas aquí leyendo sobre D&D, quizas quieras revisar mi análisis de la [Bag of Holding]. O cómo jugamos [D&D online] o sobre mi primera sesión de [Ironsworn].

<!--Images-->
[cover]: {{ page.image.path }}
[FullAdventure]: /assets/2020-08-16/FullAdventure.png
[FullAdventureNoClass]: /assets/2020-08-16/FullAdventureNoClass.jpg
[FullAdventureDnD]: /assets/2020-08-16/FullAdventureDnD.png
[emacsscreenshot]: /assets/2020-08-16/emacs.png
[adventurecover]: /assets/2020-08-16/ArcaneMoonCover.png
[dungeondraftscreenshot]: /assets/2020-08-16/Dungeondraft.png
[spotart]: /assets/2020-08-16/spotart.png

<!--Credits-->

[Rian Trost]: https://www.drivethrurpg.com/browse/pub/8587/Rian-Trost-RPG-Stock-Art

<!--Internal-Links-->
[Bag of Holding]: {% post_url ES/2020-04-25-bag-of-holding %}
[D&D online]: {% post_url ES/2020-04-05-dnd-online %}
[Ironsworn]: {% post_url ES/2020-04-01-Ironsworn-pt1 %}


<!--External-Links-->
[emacs]: https://www.gnu.org/software/emacs/
[orgmode]:https://orgmode.org/
[template]: https://github.com/rpgtex/DND-5e-LaTeX-Template
[latex]: https://www.latex-project.org/get/
[spark]: https://spark.adobe.com/
[dungeondraft]: https://dungeondraft.net/
[krita]: https://krita.org/en/
[Arcane Moon]: https://bit.ly/ArcaneMoon
