---
title: Custom Elements or How I Learned to Stop Worrying and Love the Web Components
---

![Custom Car][custom]

Un [_web component_](https://developer.mozilla.org/en-US/docs/Web/Web_Components) es una forma de crear tu propio  _HTML Custom Element_ que puede ser utilizado en cualquier sitio web y en la [mayoría de los browsers](https://www.webcomponents.org/). Su funcionalidad esta _encapsulada_ del resto de la página y eso quiere decir que puedes también utilziar los _web components_ de alguien más en tu propio sitio. Hoy vamos a crear un Web Component utilizando Angular Elements.

<!--more-->

Para entender los _web components_ hay que hablar de [Polyfills](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill), el [Shadow DOM](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_shadow_DOM), [HTML5](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/template) y exactamente qué es un [Custom Element](https://developer.mozilla.org/en-US/docs/Web/API/CustomElementRegistry) en términos de Javascript. Afortunadamente para usarlos no necesitas entender mucho de ninguna de esas cosas :laughing:

## Angular Elements

[Angular Elements](https://angular.io/guide/elements) nos permite empaquetar cualquier Angular Component como un _web component._ El resultante lo podemos utilizar en cualquier lugar independientemente del resto de la plataforma de Angular.

La ventaja de crear un web component con Angular es que angular se va a encargar de crear los polyfills que necesitamos, vamos a tener acceso a todas las librerías y podemos utilizar Typescript, lo cual siempre es bueno y bonito.

Vamos a empezar con un proyecto nuevo. Si tienes dudas de cómo empezar un proyecto más "tradicional" puedes ver la [guía anterior]({% post_url 2019-09-27-angular-part-1 %}).

```bash
ng new tesel-ce --style scss
cd tesel-ce
ng add @angular/elements
```

En este caso solo vamos a modificar el componente principal `src/app/app.component.ts`

```typescript
import { Component, ViewEncapsulation } from '@angular/core';

@Component({

  //...

  encapsulation: ViewEncapsulation.ShadowDom
})
export class AppComponent { }
```

La parte importante es el `encapsulation: ViewEncapsulation.ShadowDom` Shadow DOM  significa que nuestro componente va a estar aislado del resto del documento HTML dónde lo vamos a integrar. En el sentido práctico quiere decir que puedes usar cualquier class, id, name, css, etc. sin preocuparte de que interfiera con el resto de la página y viceversa.

En `src/app/app.component.html` voy a colocar uno de los ejemplos de Bootstrap, porque quiero mostrar cómo el Shadow DOM aisla el componente.

```html
<div class="card" style="width: 18rem;">
  <img src="https://picsum.photos/400" class="card-img-top">
  <div class="card-body">
    <h5 class="card-title">Hello World!</h5>
    <p class="card-text">Ejemplo de cómo el Shadow DOM nos permite aislar el component.</p>
  </div>
  <ul class="list-group list-group-flush">
    <li class="list-group-item">Cras justo odio</li>
  </ul>
  <div class="card-body">
    <a href="#" class="card-link">Card link</a>
  </div>
</div>
```

Finalmente hay que modificar `src/app/app.module.ts`. Nuestro componente ya no a ser un componente _bootstrap_ si no que es un _entryComponent_. Esto nos permite registrarlo como un _Custom Element_

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule, Injector } from '@angular/core';
import { createCustomElement } from "@angular/elements";

import { AppComponent } from './app.component';

@NgModule({

  //...

  entryComponents: [AppComponent] //  bootstrap: [AppComponent]
})
export class AppModule {
  constructor(private injector: Injector) {}

  ngDoBootstrap() {
    let custom = createCustomElement(AppComponent, { injector: this.injector });
    customElements.define("custom-example", custom);
  }
}
```

Al agregar `@angular/elements` tenemos acceso al método `createCustomElement` que le permite al DOM reconocer en qué momento se esta mandando a llamar nuestro propio custom element.

Lo único que queda es compilar nuestro componente.

```bash
ng build --prod --output-hashing=none
cat dist/tesel-ce/{runtime,polyfills,main}-es5.js > tesel-ce.js
```

Lo compilamos en modo de producción porque no hay comments y minimiza el resultado entre otras cosas; lo compilamos sin hashes para hacer más fácil poner nuestro `runtime-es5.js`, `polyfills-es5.js` y `main-es5.js` en el mismo archivo más fácilmente.

## La prueba

Voy a crear un `index.html` en cuyo body solo hay estas lineas, y voy a agregar bootstrap para mostrar el efecto del Shadow DOM.

```html
<!doctype html>
<html>
  <head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
  </head>
  <body>
    <custom-example></custom-example>
    <script src="tesel-ce.js"></script>
  </body>
</html>
```

Si abres este index en tu browser vas a notar que se despliega todo lo que creamos antes aunque no hay ningún CSS. Esto se debe al Shadow DOM!

![Angular Element aislado por el Shadow DOM][noformat]

Mientras que si colocas el html del _custom element_ en el `index.html` se va a mostrar así.

![HTML nativo mostrando su CSS][format]

Una vez más, esto te permite utilizar cualquier clase, estilos y nombres que quieras sin preocuparte.

---

Eso es todo en este post, espero que te ayude a empezar a probar los web elements. Si quieres saber más sobre Angular puedes revisar [este post]({% post_url 2019-09-27-angular-part-1 %}). Y si quieres leer algo más entretenido puedes leer mi post acerca de [dados]({% post_url 2019-02-07-dice %}).

[custom]: /assets/2019-10-09/custom.jpg
[noformat]: /assets/2019-10-09/noformat.png
[format]: /assets/2019-10-09/format.png
