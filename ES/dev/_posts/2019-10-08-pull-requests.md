---
layout: post
permalink: /:year/:month/:day/:title:output_ext
title: Cómo hacer un pull request integrable en Github
image:
  path: /assets/2019-10-08/paper_stack.jpg
description: Hoy hacemos un pull request de Github y contribuimos a un proyecto Open Source
---

![Paper stacks][papers]

Recientemente he estado probando Twit, una librería de node, ha resultado efectiva, pero para utilizarla en Typescript necesito instalar sus typings, y esos typings estan incompletos. Entonces hoy voy a hacer un pull request a DefinitelyTyped y espero que sea integrable a su proyecto.

<!--more-->

## ¿Qué es DefinitelyTyped?

Es una colección de [_declaration files._](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html) Muchas librerías de node.js no soportan activamente Typescript, en general son compatibles de cualquier forma, pero para utilizarlas necesitamos los _typings_ las funciones, variables, argumentos, etc. que forman parte de la librería.

Usualmente cuando instalamos un _typing_ basta instalar el mismo nombre de la librería precedido con `@types/` por ejemplo:

```bash
npm install --save twit
npm install --save-dev @types/twit
```

## Forking & Cloning

Primero vamos a hacer un _fork_ del [repositorio](https://github.com/DefinitelyTyped/DefinitelyTyped) que queremos modificar. Realmente solo es presionar un botón, pero el efecto es que en tu cuenta de Github vas a tener una copia exacta del repositorio en su estado actual. El resto de las modificaciones las vamos a realizar sobre nuestro fork.

![Forkeando un repositorio][fork]

Clonamos el repositorio, en mi caso `Darkade/DefinitelyTyped`, y buscamos el archivo que queremos modificar. Para estos typings generalmente vamos a modificar `index.d.ts`

```bash
git clone https://github.com/Darkade/DefinitelyTyped.git
cd DefinitelyTyped/types/twit
emacs index.d.ts # emacs o el editor que quieras
```

## Contribution guidelines

Muchos proyectos tienen _contribution guidelines_ básicamente son las prácticas que mejoran las posibilidades de que tu contribución se integre al repositorio principal. Para DefinitelyTyped puedes verlas directamente en su [README.](https://github.com/DefinitelyTyped/DefinitelyTyped#how-can-i-contribute)

Generalmente es hacer modificaciones, correr y escribir pruebas, y hacer un commit message claro. Una vez que esta todo listo

```bash
git commit -a -m "Updated types for @types/twit"
git push origin
```

## Pull request

Una vez que _pusheamos_ de vuelta a [nuestro repositorio](https://github.com/Darkade/DefinitelyTyped) si vamos entonces al [repositorio original](https://github.com/DefinitelyTyped/DefinitelyTyped) vamos a ver un botón de _Compare & pull request._

![Pull request button][request]

Muchos proyectos grandes te van a mostrar una plantilla de cosas que debes incluir en tu pull request. Es importante que la leas por completo y que la llenes lo mejor posible, ya uqe haces más fácil el trabajo de las personas que le dan mantenimiento al proyecto.

![Template para pull requests][template]

[Este es el pull request que yo hice](https://github.com/DefinitelyTyped/DefinitelyTyped/pull/38985) para DefinitelyTyped. Ya esta integrado y puedes ver todo el proceso. ~~En este momento todavía no esta aprobado pero espero que en los siguientes días se integre.~~

Una última cosa que notar es que muchos proyectos han empezado a integrar bots en su proceso de aprobación.

![Bot de pull requests][bot]

De igual manera lee por completo los comentarios que el bot haga, ya que este ahí para hacer más fácil el trabajo de los integradores.

## Tips

- Has cambios "atómicos" que sean pequeños y/o concisos. Si haces muchos cambios a la vez es más dificil para los integradores revisar tus que es lo que hiciste entonces es más dificil que sea integrado
- Has commits claros y pocos. Si haces muchos commits trata de limpiarlos antes de tu pull request utilizando `git rebase -i`
- Mantén un perfil relativamente activo en Github. Sobre todo si haces cambios grandes tener un perfil activo en varios proyectos hace que tus cambios sean más confiables
- En el espíritu del Free Software: si haces un cambio local a un proyecto es posible que valga la pena hacer un pull request. Tener mejor software para todos empieza con buenos pull requests

---

Muchas gracias por leer este artículo, ya que estas aquí quizas te interese aprender más sobre [Angular]({% post_url ES/dev/2019-09-27-angular-part-1 %}) o [Jupyter (python)]({% post_url ES/dev/2019-05-03-jupyter %})

[papers]: {{ page.image.path }}
[fork]: /assets/2019-10-08/fork.png
[request]: /assets/2019-10-08/request.png
[template]: /assets/2019-10-08/template.png
[bot]: /assets/2019-10-08/bot.png
