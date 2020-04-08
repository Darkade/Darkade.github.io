---
layout: post
title: Angular + Firebase. Parte 2
featuredimage: /assets/2019-09-27/angular_firebase_2.jpg
description: Utilizamos Angular y Firebase y creamos una tasklist [Parte 2]
---
![Cocinando con Angular + Firebase Parte 2][angular_firebase_2]

_Esta es la segunda parte de nuestra guía de Angular. Puedes leer la primera parte [aquí]({% post_url 2019-09-27-angular-part-1 %})._

La ocasión anterior vimos algunas cosas básicas de angular. Hoy para el platillo principal vamos a conectar nuestra task list a Firebase. Esto nos va a servir para hacer persistentes nuestras notas y aprender a utilizar una de las librearías más útiles de angular, `angularfire2`. Aprender a utilizar firebase también tiene la ventaja de que colocar tu app en Firebase va a ser gratuito a menos que tengas mucho tráfico.

<!--more-->

![Así queda en firestore][firestore]

## Ingredientes

Solo vamos a agregar dos ingredientes a nuestra preparación anterior:

- [Firebase](https://firebase.google.com/)
- [Angularfire](https://github.com/angular/angularfire2) `^7.0.0`

Un topping excelente.

## Preparación

### (0) Crea un nuevo proyecto y base de datos en Firebase

Si ya tienes una cuenta en firebase y sabes como crear un proyecto y una base de datos de `firestore` puedes continuar al siguiente paso, si no sigue leyendo.

![El sitio de Firebase circa 2019][get_started]

Vamos a comenzar por crear una [nueva cuenta de firebase,](https://firebase.google.com) para lo cual necesitas una cuenta de google. Una vez en la consola:

1. Da click a _add project_.
2. Nombra tu proyecto. Yo solo voy a utilziar `Task List`.
3. Puedes o no activar analytics. Son muy útiles, pero no vamos a hablar de esa parte en este artículo.

Tu consola se debe ve así una vez creado tu proyecto.
![Consola de firebase para un proyecto recién creado][firebase_console]

4. En la parte de Database crea una base de datos de `Cloud Firestore` y selecciona `test mode` esto *va a hacer tu base de datos insegura,* pero solo vamos a probar. Para la región voy a escoger `nam5`, toma en cuenta que no podrás cambiar esta región una vez que confirmes.

> Antes de lanzar un proyecto a tus usuarios revisa con mucho detenimiento las [_security rules_](https://firebase.google.com/docs/firestore/security/get-started)

5. En project overview, da click al tercer botón `</>` para agregar firebase a un proyecto web. Después de nombrar tu proyecto firebase te va a dar algo de código de javascript y un objeto que se ve así:

```javascript
var firebaseConfig = {
  apiKey: "sGa7pO5vYZAaIE3kr3Do",
  authDomain: "test-project-a0613.firebaseapp.com",
  databaseURL: "https://test-project-a0613.firebaseio.com",
  projectId: "test-project-a0613",
  storageBucket: "test-project-a0613.appspot.com",
  messagingSenderId: "237742080605",
  appId: "1:237742080605:web:B4A4CpnDletYOJqnndcl"
}
```

> Este objeto esta diseñado para ser público, normalmente lo colocarías dentro del `<body>` de tu webapp, de modo que tus usuarios podrán verlo, copiarlo y usarlo en sus propias webapps **siempre.** Por eso es importante que cuando lanzes un proyecto a producción te asegures de que las reglas de tu base de datos son seguras.

Este es lo único que nos importa por el momento, porque es lo único que necesitamos para configurar `angularfire`.

> _Refrigera todos los ingredientes para que adquieran la consistencia adecuada al momento de cocinar._

### (1) Creando datos de prueba

De vuelta en Firestore vamos a crear una _collection_ para tener datos hacia los cuales conectarnos.

![tasks collection][collection]

> _Con un procesador de alimentos integra todos los ingredientes hasta tener una pasta de consistencia cremosa._

### (2) Instalando y configurando angularfire2

Puedes instalar `angularfire` con este comando

`npm install firebase @angular/fire --save`

Una vez instalado necesitarás colocarlo en tu `src/app/app.module.ts`

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { AngularFireModule } from '@angular/fire';
import { environment } from '../environments/environment';

@NgModule({
  imports: [
    BrowserModule,
    AngularFireModule.initializeApp(environment.firebase)
  ],
  declarations: [ AppComponent ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```

Y el objeto que guardamos antes en `/src/environments/environment.ts`

```typescript
export const environment = {
  production: false,
  firebase: {
    apiKey: "sGa7pO5vYZAaIE3kr3Do",
    authDomain: "test-project-a0613.firebaseapp.com",
    databaseURL: "https://test-project-a0613.firebaseio.com",
    projectId: "test-project-a0613",
    storageBucket: "test-project-a0613.appspot.com",
    messagingSenderId: "237742080605",
    appId: "1:237742080605:web:B4A4CpnDletYOJqnndcl"
  }
};
```

Con eso esta lista la configuración de firebase y podemos empezar a conectar nuestro código con la base de datos.

> _Hornea la pasta durante 20 minutos hasta que se redusca_

### (3) Conectando nuestro componente la base de datos

Como notarás los cambios que vamos a hacer a nuestro componente son muy pequeños. En el template solo vamos a agregar algo de funcionalidad y un solo cambio para hacer que funcione. Y en el componente vamos a cambiar los tipos de algunas variables.

`src/app/tasklist/tasklist.component.ts`

```typescript
import { Component, OnInit } from '@angular/core';
import { NgForm } from '@angular/forms';

import { AngularFirestore, AngularFirestoreCollection } from '@angular/fire/firestore';
import { Observable } from 'rxjs';

interface Task {
  done: boolean;
  task: string;
};

interface TaskId extends Task { id: string; };

@Component({
  selector: 'app-tasklist',
  templateUrl: './tasklist.component.html',
  styleUrls: ['./tasklist.component.sass']
})
export class TasklistComponent implements OnInit {

  tasksCollection: AngularFirestoreCollection<Task>;
  tasks: Observable<TaskId[]>;

  newtask: Task = {done: false, task:''};

  constructor(private afs: AngularFirestore) { }

  ngOnInit() {
    this.tasksCollection = this.afs.collection<Task>('tasks');
    this.tasks = this.tasksCollection.valueChanges({idField: 'id'});
  }

  update(task: TaskId) {
    let doc = this.afs.doc<Task>('tasks/' + task.id);
    doc.update({ done: task.done, task: task.task });
  }

  submit() {
    this.tasksCollection.add(this.newtask);
    this.newtask = {done: false, task:''};
  }
}
```

- Primero importamos `AngularFirestore`, `AngularFirestoreCollection` y `Observable` que vamos a ver con detenimiento acontinuación.
- `tasksCollection: AngularFirestoreCollection<Task>;` es una [_collection_](https://github.com/angular/angularfire2/blob/master/docs/firestore/collections.md) y es el objeto que vamos a utilizar para conectarnos con Firestore.  
- `tasks: Observable<TaskId[]>;` Con esta linea creamos un Observable de tipo `TaskId[]`, que es un array dónde todos los elementos son de tipo `TaskId`

> Esta última sintaxis parece compleja pero en el uso es muy cotidiano, si quieres saber más lee sobre [Generic Types](https://www.typescriptlang.org/docs/handbook/generics.html). En la práctica lo que estamos haciendo es _suscribirnos_ a un evento que va a pasar: "En algún momento tasks va a tener un array de TaskId"

- `constructor(private afs: AngularFirestore) { }` agrega como [_service_](https://angular.io/guide/architecture-services) un objeto local llamado `afs` que va ser nuestra interfáz con Firestore. No es necesario configurarlo más ya que toda su configuración esta en `app.module.ts`
- `this.tasksCollection = this.afs.collection<Task>('tasks');` le pide a firestore una referencia hacia toda la _collection_ que esta bajo 'tasks' en nuestra base de datos
- `this.tasks = this.tasksCollection.valueChanges({idField: 'id'});` adquiere todos los valores que estan guardados en nuestra _collection_ junto con sus respectivos id's
- `update(task: TaskId)` las lineas que estan en esta función le piden a Firestore una referencia al documento individual, al task que estamos modificando. Y entonces actualiza el documento. Lo hacemos de esta forma `{ done: task.done, task: task.task }` porque de otra manera estaríamos agregando el campo `id` a nuestro documento y no es necesario. ~Creo que esto se puede hacer de una mejor manera. Si se te ocurre alguna forma por favor deja un comentario.~
- `this.tasksCollection.add(this.newtask);` agrega nuestro nuevo task a la _collection_


Las modificaciones a `src/app/tasklist/tasklist.component.html` son bastante simples.

```html
<ul>
  <li *ngFor="let task of tasks | async">
    <input type="checkbox" (change)="update(task)" [(ngModel)]="task.done">
    <input (change)="update(task)" [(ngModel)]="task.task">
  </li>
  <li>
    <input type="checkbox" disabled>
    <input (keyup.enter)="submit()" [(ngModel)]="newtask.task" placeholder="Nuevo task">
  </li>
</ul>
```
- `let task of tasks | async` agregamos `async`. Esto nos permite _esperar_ a que se _resuelva_ un observable. En otras palabras `tasks` va a conectarse al servidor de firebase y esto puede tomar tiempo; si no agregamos `async` el template devolvería un error en la consola.
- `(change)=update(task)` mandamos a llamar la función `update()` cuando el checkbox o la caja de texto de cada task tiene algun cambio. Es importante que sea en el método `(change)` porque este se ejecuta cuando terminan los cambios son "un hecho", a diferencia de `(click)` o `(keyup)`.

> _Coloca directamente sobre el pay que horneamos anteriormente._

---

Y en realidad eso es todo. Como puedes ver los tasks que crees y modifiques se quedan guardados en tu base de datos y se reflejan instantaneamente en tu base de datos de firestore. Incluso si cambias un valor en la base de datos se va a reflejar de inemediato en tu app, _tal es la mágia de los observables._

En la siguiente parte vamos a convertir esta Task List en un [_Custom Element_](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements) lo cual llega al borde de la brujería sin ser brujería en mi opinión.

[firestore]: /assets/2019-09-27/firestore.png
[angular_firebase_2]: {{ page.featuredimage }}
[get_started]: /assets/2019-09-27/firebase_getstarted.png
[firebase_console]: /assets/2019-09-27/firebase_console.png
[collection]: /assets/2019-09-27/firebase_newcollection.png
