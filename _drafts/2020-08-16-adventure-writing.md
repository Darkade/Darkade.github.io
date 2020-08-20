---
layout: post
title: "How I wrote a D&D adventure using Emacs + org-mode"
featuredimage: /assets/2020-08-16/2020-08-16-Arcane-Moon.png
description: I just published a D&D adventure and I wrote it just using Emacs... kind of.
imagewidth: 1920
imageheight: 1280
---

![Arcane Moon is now available!][cover]

Emacs + org-mode is the definitive writing experience, it allowed me to organize my writing process, write, export to PDF, and quickly make revisions. Yes, I am a developer, and yes Emacs is my "IDE" of choice, however, even if you are not, I think there's a lot you can get by using emacs, though it will take a large-ish amount of setup.

<!--more-->

---

![Arcane Moon Adventure][FullAdventure]
_Arcane Moon was made in Emacs_

So After the click-batty title, did I really just used Emacs? The answer is, I could have just used Emacs and org-mode, but I of course used some other tools. And since you are probably here for the tool list, here's what you'll need:

**If you want a barebones adventure output:**
- [Emacs + org-mode][emacs]
- [The DnD 5e LaTeX Template github repo][template]
- [A LaTeX environment][latex]

**If you want to have a cover:**
- [Adobe spark][spark]
- Preview or a similar PDF viewer with minimal editing functionality

**If you want to add maps:**
- [Dungeondraft][dungeondraft]
- [Krita][krita]

**If you want to have spot art:**
- A LaTeX editor

**If you want to collaborate with a proof reader:**
- Google docs

I'm really not here to teach you how to install these tools, there's plenty of [tutorials][orgmode] on that, but I will tell you how I used them.

## Barebones Adventure Output

Really emacs, and more precisely org-mode was the central tool for everything. I used it to:

![Arcane Moon on Emacs][emacsscreenshot]
_Arcane Moon on Emacs_

### Outline my adventure
I began by adding sections I wanted to have, Introduction, the adventure and it's chapters.

### Schedule my tasks
Tracking when you want to get things done, scheduling and being aware of time constraints will help to bring out the creative energy, and emacs is amazing at [scheduling](https://orgmode.org/guide/Dates-and-Times.html).

You can add a deadline by using the command `C-c C-d` or a simple time stamp by using `C-c .`. After you can see your agenda with `C-c a`

### Mark different states of completion

You can always mark things as `DONE` and `TODO`. But can configure any [states of completition](https://orgmode.org/guide/TODO-Basics.html) you want for your workflow.

The basic ones were enough for me. I used them to keep track of the _phase_ the project was in: at the start of drafting every heading was `TODO`, by the end they were `DONE`. At the start of proof reading everything was `TODO` by the end `DONE`

The main reason to use a plain text editor, and in this case Emacs is that you don't have to worry about layout until you **need** to worry about layout, before that I find it to be distracting, which is why even when you could be using Word, Pages, or Google Docs I wouldn't recommend it. But eventually you will want to do layout, and you will want to export to, provably PDF. So how do you export?

### Exporting to PDF

After you install your preferred [latex] distribution you can [export](https://orgmode.org/manual/LaTeX-Export.html) from org to PDF by using `C-c C-e l p`. However you probably will find this export lacking. For one, it looks nothing like a D&D book, and we were talking about working on layout this is the final product. So, install the [DnD 5e LaTeX Template][template]. Then you must configure org to find the theme.

![Exporting Adventure without a theme][FullAdventureNoClass]
_Exporting Adventure without a theme_

Add this to your `.emacs` file:

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

And then add this to the top of your work file on Emacs:

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

Fill it as you see fit and then try exporting again with `C-c C-e l p`. Now it should look like the way we want, like a proper D&D book!

Try and play commenting some of the lines you added to the `.emacs` file. If you remove the `("\\part\{\%s}" . "\\part*\{\%s}")` then the top level of your tree will render as the chapter headings, and so on.

Other things you could do is use the helpers from the DnD 5e LaTeX Template. You can learn more at their documentation, but you can use `DndComment`, `DndReadAloud` and `DndSidebar` very easily by including something like this:

```
#+BEGIN_DndComment
This will show up as a Dungeons & Dragons comment
#+END_DndComment
```

Capitalization is important! If you want to use other helpers you can use `#+BEGIN_DndComment`, `#+BEGIN_ReadAloud` or `#+BEGIN_DndSidebar` as you require.

The template also includes a `DndMonster` helper, which there's not easy "org-way" to use. But org does support embedding LaTeX text directly, so you can still use it here without editing a Tex file.

![Full Adventure with the DnD 5e template][FullAdventureDnD]
_Full Adventure with the DnD 5e template_

These is pretty much the configuration I used and you could leave it there.

## Adding a cover

I made my cover using stock art by [Rian Trost] and Adobe Spark. Spark has templates you can use for print and digital. And it allows you to quickly get to a descent cover. The other advantage is that you can resize to any export size and it will redistribute for you, so I also use it for my social media posts; including this article's cover.

Once you are satisfied with your cover download it as a PNG file. If you are using macOS, open both your cover and your PDF export with preview, make sure you see the sidebar thumbnails and drag the cover thumbnail to your pdf export. Save and you are done!

## Adding maps

I used [Dungeondraft][dungeondraft] to make my maps. And I think they came out pretty cool. Dungeondraft is a whole thing, but my recomendation is get familiar with the "levels" and "layers" and understand those are different things. Also be aware during export you can overlay two levels, but only two. In my case I did the grass and stone walk on one level, and for all subsequent levels I only did the tower floors; then I used the bottom layer and exported the other levels over. It's confusing, really, but if you plan to make a layered dungeon you'll save yourself a ton of work.

After the export I used [Krita][krita] to add some number markers to reference in my text and to resize as thumbnails; make sure to make copies of the original size!

This should suffice to put the images in your org work file, and have them be a part of the PDF export.

```org
#+CAPTION: your caption text
#+NAME: fig:C2E2
[[./maps/thumbs/C2E2_001.jpg]]
```

Notice you'll have to use your own maps path, for me it was `./maps/thumbs` for you will be different.

## Adding spot art

You could also add your maps by editing the `.tex` file you've probably noticed by now. This file is used to generate your PDF and to edit it you'll need a Tex editor, which should be included with your LaTeX distribution; in my case it's TeXShop.

Open your file using TeXShop and find an aproximate place you would like your image to be placed at, then paste this:

```tex
\begin{figure}[h]
\centering
\includegraphics[width=.9\linewidth]{./assets/accents/line1.png}
\end{figure}
```

Again, make sure you have the right path to the image you want to include. In this example it's `./assets/accents` which was my spot art dir. But this could be a map or another image. Also notice I've added a `width=.9` so that it doesn't occupy the same space as the text. Finally notice the `[h]` it stands for _"here"._ So once you export to PDF the image will be paced roughly _"there"._ There are [many options][https://www.overleaf.com/learn/latex/Positioning_of_Figures] and you should try the ones that fit each need.

If you want to use the art to make a page break a simple hack is to tweak the `width=` parameter, a little bit more or less to force the text to break.

There's plenty you can do here, editing the `.tex` file. You could even write your adventure directly here, but I don't recommend doing that, which is why I'm using org.

## Collaborating with a proof reader

This is hacky at best and not practical at worst, so I don't really recommend doing it like this, but it did work for me, so it might work for you. Export your file to ODT from emacs with `C-c C-e o o` this will produce an ODT file you can then upload to Google Drive edit with Docs. Your editor can use comments and the suggestion modes and you would need to keep your org file up to date so that you don't keep re-uploading the file.

As I said it's hacky at best, but it did work for me.

---

¡Gracias por leer este ultra deep dive! Tomó un mes de trabajar de a poco pero seguía encontrando cosas que no sabía si agregar o no. Mi plan original era pasar de esto a la demografía y el producto interno bruto de Waterdeep en el mismo post, pero hubiera sido mucho más largo de lo que ya es. Así que en algún momento espera leer ese otro artículo.

Si te gustó lo que leeiste y quieres más análisis a fondo e innecesarios puedes leer sobre la [Bag of Holding]. Este post es uno de muchos que he estado escribiendo sobre juegos de rol. Si te gusta D&D puedes leer [cómo jugar D&D online] o sobre [Ironsworn], el juego que más he recomendado últimamente.

<!--Images-->
[cover]: {{ page.featuredimage }}
[FullAdventure]: /assets/2020-08-16/FullAdventure.png
[FullAdventureNoClass]: /assets/2020-08-16/FullAdventureNoClass.jpg
[FullAdventureDnD]: /assets/2020-08-16/FullAdventureDnD.png
[emacsscreenshot]: /assets/2020-08-16/emacs.png

<!--Credits-->

[Rian Trost]: https://www.drivethrurpg.com/browse/pub/8587/Rian-Trost-RPG-Stock-Art

<!--Internal-Links-->
[Bag of Holding]: {% post_url 2020-04-25-bag-of-holding %}
[cómo jugar D&D online]: {% post_url 2020-04-05-dnd-online %}
[Ironsworn]: {% post_url 2020-04-01-Ironsworn-pt1 %}


<!--External-Links-->
[emacs]: https://www.gnu.org/software/emacs/
[orgmode]:https://orgmode.org/
[template]: https://github.com/rpgtex/DND-5e-LaTeX-Template
[latex]: https://www.latex-project.org/get/
[spark]: https://spark.adobe.com/
[dungeondraft]: https://dungeondraft.net/
[krita]: https://krita.org/en/
