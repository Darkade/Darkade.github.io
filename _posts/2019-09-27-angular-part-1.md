---
layout: post
title: Angular + Firebase. Parte 1
image: /assets/2019-09-27/angular_firebase_1.jpg
description: Utilizamos Angular y Firebase y creamos una tasklist [Parte 1]
---
![Cocinando con Angular + Firebase Parte 1][angular_firebase_1]

Has utilizado Javascript, igual y hasta eres fan de JQuery. Pero quieres usar un framework más moderno y poderoso ¿Por qué no Angular? Hoy vamos a hacer un app para hacer un task list que va a utilzar una base de datos en [Firebase](https://firebase.google.com/) y vamos a aprender un poco sobre [Web Components](https://developer.mozilla.org/en-US/docs/Web/Web_Components). ~~Tengo Hambre ¿Alguien más tiene hambre?~~

<!--more-->

![Aquí hay uno que preparé anteriormente][tasklist]

## Ingredientes

Estas son las librerías y herramientas que vamos a utilizar. La mayoría de estas cosas se van a instalar automáticamente, pero siempre es bueno saber con que estamos por lidiar.

- [Node.js](https://nodejs.org) + [npm](https://docs.npmjs.com/cli/npm) `^5.0.0`
- [Angular cli](https://cli.angular.io/) `^8.0.0`
- [Angular](https://angular.io/) `^8.0.0`
- [Typescript](https://www.typescriptlang.org/) `^2.7`

## Preparación

### (1) Instalando lo necesario

Primero necesitamos tener node, npm y angular-cli. Ya que vamos a utilizar npm para manejar nuestras dependencias. Esta es la única parte específica de tu sistema, nosotros vamos a utilizar homebrew para instalar en macOS.

```shell
$ brew install nvm
$ nvm install v11
$ nvm use v11
$ npm install --global npm@latest
```

Si usas Linux o Mac: [**nvm** (Node Version Manager),](https://github.com/creationix/nvm) te permite instalar y usar versiones diferentes de node.js, es una herrmienta muy útil. También hay `nvm` en Windows, pero no es desarrollado por el mismo equipo.

```shell
$ npm install --global @angular/cli
```

Ya puedes instalar el Angular-cli que nos permitirá generar y administrar nuestro proyecto de angular

> _Instala y reserva para más tarde._

### (2) Levantando el proyecto

Primero crea un app vacía utilizando Angular-cli con el comando `ng`.

```shell
$ ng new tesel-example --routing --style sass
$ cd tesel-example
$ ng serve --open
```

![Tu browser se va a abrir y deberías estar viendo una pantalla parecida][1]

A continuación instalamos `angularfire2` para conectarnos con Firebase

```shell
$ npm install --save @angular/fire
```

> _Mezcla todos los ingredientes secos y cuando esten homogeneos agrega leche y vierte en un molde de hornear_

### (3) Revisa la estructura del proyecto

Hay tres directorios y algunos archivos. Lo más importante es:

- [`angular.json`](https://angular.io/guide/workspace-config) tiene las configuraciones principales de tu workspace. Personalmente solo lo he modificado manualmente en la sección assets.
- [`karma.conf.js`](https://karma-runner.github.io/) es la configuración de tu herramienta de pruebas
- [`tsconfig.json`](https://typescriptlang.org) es la configuración de typescript
- `src/app/app.module.ts` declara la mayoría de las librerías que va a utilizar tu proyecto
- `src/app/app.component.ts` es el componente principal de tu app


> _Precalienta el horno a 180ºC por al menos 20 minutos_

### (4) Creando un componente

Los componentes son las estructuras básicas de angular. Vamos a crear un componente llamado `tasklist` con este comando:

```
ng generate component tasklist
```

Vamos a crear una tasklist en el componente que acabamos de generar `src/app/tasklist`.

En nuestro componente `src/app/tasklist/tasklist.component.ts` vamos a crear una  `interface` y algunos valores de prueba.

```typescript
import { Component, OnInit } from '@angular/core';
import { NgForm } from '@angular/forms';

interface Task {
  done: boolean;
  task: string;
}

@Component({
  selector: 'app-tasklist',
  templateUrl: './tasklist.component.html',
  styleUrls: ['./tasklist.component.sass']
})
export class TasklistComponent implements OnInit {

  tasks: Task[] = [
    {done: false, task:'Iron boots'},
    {done: false, task:'Aprender serenade of water'},
    {done: false, task:'Conseguir hookshot'},
    {done: false, task:'Túnica zora'},
  ];

  newtask: Task = {done: false, task:''};

  constructor() { }

  ngOnInit() {
  }

  submit() {
    this.tasks.push({...this.newtask});
    this.newtask = {done: false, task:''};
  }
}
```

Primero nota `interface Task` estas lineas definen una interfáz, es decir la forma en la que se va a ver un objeto. No es exactamente un tipo pero es [suficientemente cercano a uno.](https://www.typescriptlang.org/docs/handbook/interfaces.html)

Luego `tasks: Task[]` define la variable `tasks` como una lista de objetos tipo `Task` y lo estamos inicializando inmediatamente. `newtask` es parecido pero es un solo objeto que vamos a utilizar para guardar los datos de las tasks que vayamos agregando.

Finalmente la función `submit()` agrega los valores de `newtask` a nuestro arreglo `tasks` y lo vuelve a inicializar.

Toma nota de la linea `selector: 'app-tasklist',` ya que vamos a ocupar este valor más adelante. Este es html tag que vamos a emplear para llamar este objeto.

-------------

En cuanto a nuestro `template` en `src/app/tasklist/tasklist.component.html`.
```html
<ul>
  <li *ngFor="let task of tasks">
    <input type="checkbox" [(ngModel)]="task.done">
    <input [(ngModel)]="task.task">
  </li>
  <li>
    <input type="checkbox" disabled>
    <input (keyup.enter)="submit()" [(ngModel)]="newtask.task" placeholder="Nuevo task">
  </li>
</ul>
```

`*ngFor` repite un html tag y su contenido tantas veces como el _for_ requiera, en este caso va a crear un tag `<li>` tantas veces como tasks hay.

`[(ngModel)]` "amarra" el valor de un objeto a una variable en nuestro componente. En el caso de nuestros primeros dos inputs, su booleano y texto se amarran a respectivo done y descripción de cada task.

Para el cuarto input también estamos utilizando `[(ngModel)]` para guardar la descripción de cada nuevo task. Luego utilizamos `(keyup.enter)="submit()"` para detectar cuando el usuario presiona ENTER y ejecutar la función `submit()` que explicamos antes.

------------

Lo último que tienes que hacer para que esto funcione es agregar un par de lineas a `src/app/app.module.ts`

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { TasklistComponent } from './tasklist/tasklist.component';

@NgModule({
  declarations: [
    AppComponent,
    TasklistComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Lo que estamos haciendo es colocar `FormsModule` en nuestros imports, esto nos permite utilizar `[(ngModule)]` en nuestros templates.

> _Una vez que las orillas se desprendan de tu molde sáca el app del horno, deja enfriar y reserva._

--------

¡Con solo esto ya tienes una lista de tasks! Desde luego no hemos terminado la receta; falta algo de funcionalidad, como borrar tasks, y conectarlo a una base de datos en linea. Lo cual haremos en la [siguiente parte]({% post_url 2019-09-27-angular-part-2 %}).

[tasklist]: /assets/2019-09-27/tasklist.png
[angular_firebase_1]: {{ page.image }}
