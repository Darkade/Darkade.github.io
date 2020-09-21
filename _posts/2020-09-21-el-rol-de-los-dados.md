---
layout: post
title: "El rol de los dados en los juegos de rol"
featuredimage: /assets/2020-09-20/ian-gonzalez-oVXMtsMejqo-unsplash.jpg
description: "Los dados están presentes en la mayoría de los juegos de rol y estos afectan la percepción del juego y lo que los jugadores esperan del mismo. ¿Qué hacen los dados en tu juego favorito?"
imagewidth: 1920
imageheight: 1283
---

![Un juego de dados poliedricos estandar][postcover]

¿Cuál es el tono con el que se diseño el juego que estas jugando? Todos los juegos tienen influencias, y cada juego es mejor emulando temas específicos, sentimientos y modos de juego al compararlo con otros. Algunos son buenos con el drama, otros con la acción. Algunos le dan soporte al roleo en sus mecánicas y otros son más bien tácticos. Pero la mayoría usa dados.

¿Cómo influyen los dados en la experiencia de juego? Hoy comparo los dos RPGs en los que tengo más experiencia The Veil y D&D in el proceso hago **muchas declaraciones polémicas** de cómo llevar una sesión de D&D.

<!--more-->

_Portada por [Ian Gonzalez]_

---

## ¿Por qué tiramos dados?

Yo veo dos razones principales:
- Porque queremos introducir incertidumbre al juego.
- Porque queremos introducir nuevos elementos al juego.

Creo que la postura común es que tiramos dados para resolver situaciones inciertas. Pero yo creo que lo hacemos por las razones opuestas, no para resolver si no para agregar incertidumbre.

En D&D, cuando un personaje da una estocada con su espada no hay incertidumbre de si lo logrará o no: el personaje es competente, su enemigo esta en rango, deberían lograrlo... y sin embargo pueden no hacerlo.

**Tiramos porque el resultado obvio es eso: obvio. Quizás hasta aburrido**

En The Veil, y otros juegos PbtA, tiramos dados como resultado de _moves,_ que pueden ser exclusivos de ese personaje. Un Move ~~usualmente~~ requiere de tirar los dados y se activa siempre que el personaje toma ciertas acciones particulares.

Investigar puede ser un move específico para mi, pero no para ti. Cuando tiro los dados y fallo obtengo experiencia y algo más ocurre: un _hard move_ de parte del MC. Tomar un riesgo empuja la historia hacia adelante por diseño.

**Tiramos dados porque tengamos éxito o no van a aparecer nuevos elementos en el juego**

## ¿Cómo funcionan los dados?

Hay dos conceptos matemáticos de los que tenemos que hablar:

- independencia
- distribución

**Independencia** significa que cada una de las tiradas de tus dados no se ve afectada por tiradas anteriores o futuras. No, [no estas quemando tus 20s][dados] y tus dados estan tirando ~~en promedio~~ igual de bien que siempre.

**Distribución** es la forma en que la probabilidad de ciertos números se ve afectada por qué y cómo tiramos. Cuando tiramos un solo dado cada número tiene la misma probabilidad de aparecer: `5%` para un `d20`, `16.66%` para un `d6`.

![Una gráfica que muestra tiradas de 1d20 y sus probabilidades][d20chart]
_Tiradas de 1d20 y sus probabilidades_

Un `1` es igual de probable que un `20`, ambos son igual de probables que un `11`. No salen ni más ni menos a menudo que ningún otro número, aunque nuestra mente diga lo contrario. Les asignamos relevancia porque eso es lo que hace el libro, entonces los `1s` parecen más comunes de lo que son y los `20s` menos de lo que son en realidad.

Si tiramos multiples dados empezamos a _tirar en una curva._ Las sumas de algunos números se vuelven más comunes porque hay más combinaciones que los generen. En `2d6` un total de `2` solo tiene probabilidad de `2.7%` mientras que un `7` tiene probabilidad de `16.6%`.

![Una gráfica mostrando las sumas de 2d6 y sus probabilidades][d6chart]
_Tiradas de 2d6 y sus probabilidades_

![Una gráfica mostrando sumas de 2d6 y las combinaciones que los generan][d6rolls]
_Tiradas de 2d6 y las combinaciones que las generan_

Entonces, es mucho más probable obtener un `7` que un `2`. Pero también es el doble de probable obtener un `3` que un `2`. Esto es "la curva".

---

El tirar un solo `d20` en D&D hace que todo sea más dependiente de las estadísticas del personaje. Si tienes un `+0` contra un DC 15 solo tienes `30%` de probabilidades de éxito. Los bonuses a checks, saves y ataques son necesarios para seguir siendo efectivo conforme la campaña progresa y se incrementan el AC y DC.

![Una gráfica mostrando las probabilidades de Hit y Miss con y sin bonus][d20bonus]
_Probabilidades de hit y miss en un d20_

En The Veil y otros PbtAs la balanza de los dados está inclinada hacia el éxito. La mayoría de los moves tiene tres posibles outcomes: miss, weak hit y strong hit.

Un weak hit es éxito con un costo, mientras que un miss es una "oportunidad dorada" en la que el MC hará un hard move, introduciendo una situación desafortunada para los personajes.


![Una gráfica mostrando éxitos y fallos, así como weak, strong y miss en The Veil][pbta]
_Probabilidades en The Veil_

![Una tabla con las combinaciones de tiradas de 2d6 representando strong hits, weak hits y misses en The Veil][hits]
_Tiradas en The Veil y sus combinaciones_

Sin tomar en cuenta las estadísticas del personaje, las probabilidades de un weak hit o strong hit son `58.33%`, esto significa que los personajes probablemente tengan éxito, pero probablemente paguen el precio de haberlo tenido.

**Los dados nos son [#random](https://twitter.com/hashtag/random). Los dados son [Aleatorios](https://mathworld.wolfram.com/Stochastic.html) en el sentido estádistico.**

## ¿Cuando tiramos?

En el caso de D&D tiramos cuando hay consecuencias de fallar y en el caso de The Veil cuando un move se activa.

Con más detalle: la resposabilidad de cuando tirar recae en el [Dungeon Master en D&D](https://www.dndbeyond.com/sources/basic-rules/using-ability-scores#AbilityChecks). Es el DM quien pide las tiradas cuando consideran que hay consecuencias por fallar. Es por esto que muchas veces ves consejos del tipo: "no tienes que pedir taradas para todo"

> Solo pide una tirada cuando hay una consecuencia significativa por fallar.

_^DMG. Ch8 Using Ability Scores_

Esto es porque, en parte, es difícil inventar consecuencias para todo. Entonces si el DM pide una tirada, y los personajes fallan y además no hay consecuencias, el juego rápidamente se convierte en el tipo de juego en que `Los PCs tiran -> fallan -> nada pasa`. El DM esperaba que los personajes tuvieran éxito para continuar con la historia, y los PCs se frustran por no progresar.

Mientras tanto en los PbtAs la responsabilidad de cuando tirar recae en las mecánicas mismas. Las reglas dicen **"para hacerlo tienes que hacerlo"** lo cual significa que si un move se activaría entonces se activa y ~~seguramente~~ se hace una tirada. No es opcional.

Los moves están escritos de modo que refuerzen el concepto de cada personaje, lo cual los hace relevantes a sus acciones. Por ejemplo:

> **La mujer del vestido rojo.** Cuando cambias tu apariencia dentro las restricciones de un constructo digital `roll + Cyberbrain`
> - En un `10+` — es perfecto
> - En un `7-9` — se manifiesta alguna parte de tu subconsciente.

_Esta declarado globalmente que un miss activa un hard move de parte del MC_

No parece ser una gran diferencia. Pero aquí las mecánicas hacen más facil determinar consecuencias. Ya que estas probablmente estan directamente ligadas con las acciones de un personaje específico, no con el grupo ni con el mundo completo. Entonces las consecuencias son personales y dolorosas.

## ¿Como afecta esto el tono del juego?

Esta es la parte de _los consejos._ Hay dos formas en las que creo que todo esto afecta a cualquier RPG:

- Lo que los jugadores esperan al tirar dados
- La forma en que los dados son significativos

En D&D. Los jugadores no deberían sentir el peso del éxito o fracaso cuando tiran, porque no están teniendo éxito o fracasando; estan agregando nuevas cosas a la aventura. No fallaron en abrir una puerta, activaron un "tic" en el cuarto. No fallaron al apuntar su flecha al enemigo, destruyeron una lámpara y el fuego se esparcirá rápidamente en el barco. En juegos que dirijo ni el sonido ni la lámpara estaban ahí antes, pero ahora lo están, como resultado de los dados.

En The Veil y en muchos otros sistemas hablamos de _grados de éxito._ **Intenta agregar éxito con un costo a tus checks. Sobre todo si esperas que los personajes tuvieran éxito.** De esta forma los jugadores están esperando la forma en que el mundo se ve afectado por sus acciones, no esperando un número.

~~En una nota relacionada, esto es por lo mismo que en D&D yo pido los attack y damage rolls al mismo tiempo. Podrían destruir algo en caso de un miss.~~

Y aun más, busca que los números no sean significativos. Como mencioné en la sección anterior, D&D depende mucho en las estadísticas por la forma en que funcionan los dados. Por lo mismo hay muchos consejos de cómo manejar _éxitos automáticos._

Si un jugador se frustra por tirar `1s` quizás es porque esta fue su única tirada importante de la sesión. **Contrario a muchos consejos, intenta tirar más a menudo.** Si tiras dos veces en una sesión la probabilidad de tirar `1` ambas veces es solo `0.25%`. Los `1s` se diluyen  rápidamente en el resto de las tiradas.

| Tiradas en una sesión | Prabilidad de tirar solo `1s` |
|:---------------------:|------------------------------:|
| Una                   | `5.00%`                       |
| Dos                   | `0.25%`                       |
| Tres                  | `0.01%`                       |
| Cuatro                | `0.000625%`                   |

Estas son las mecánicas detrás de las recomendaciones de _failing forward;_ dejar que los jugadores tiren de nuevo los va a sacar de aprietos, pero no es solo una herramienta narrativa, esta respaldada por las matemáticas. Sin embargo, todas las veces se debería agregar algo nuevo al mundo, si no ¿para qué tirar? solo deberían tener éxito.

**Es por esto que creo que D&D se beneficia de un tono Gonzo.** Un tono loco y extraño donde los jugadores tiran frecuentemente, y sus fracasos son igual de exagerados que heroicos son sus éxitos. Aunque para mi esto viene desde el ADN [pulp](https://en.wikipedia.org/wiki/Pulp_magazine) del juego, también es hacia donde empujan las mecánicas del juego.

Si quieres una campaña de fantasia épica se puede hacer, pero vas a tener que domar constantemente el juego, como muchas personas han visto antes. Si quieres una campaña realista e intensa, también se puede hacer, pero los fracasos van a doler mucho, y no solo _dentro_ de la ficción del juego.

Entonces. Trata de tirar más frecuentemente, mientras integras éxitos con un costo. Quizás encuentres que los jugadores toman más riesgos y están más dispuestos a tirar ¿Y no es eso genial?

---

Gracias por leer este post! He estado pensando en esto desde que alguien que sigo habló de frustración con sus dados. Si te gustaría probar The Veil puedes encontrarlo [aquí][The Veil].

Hace unas semanas publiqué mi primera aventura para D&D [Arcane Moon]! Puedes leer del [proceso de crearla aquí][arcanemoonpost]. También puedes leer mi análisis geométrico de una [Bag of Holding]. O como hacemos para jugar [D&D online] Y mis primeras impresiones de [The Veil][veilpost].


<!--Images-->
[postcover]: {{ page.featuredimage }}
[d6chart]: /assets/2020-09-20/d6chart.png
[d6rolls]: /assets/2020-09-20/d6rolls.png
[d20chart]: /assets/2020-09-20/d20chart.png
[d20bonus]: /assets/2020-09-20/d20bonus.png
[hits]: /assets/2020-09-20/hits.png
[pbta]: /assets/2020-09-20/pbta.png

<!--Credits-->

[Ian Gonzalez]: https://unsplash.com/@ian_gonz

<!--Internal-Links-->
[Bag of Holding]: {% post_url 2020-04-25-bag-of-holding %}
[D&D online]: {% post_url 2020-04-05-dnd-online %}
[Ironsworn]: {% post_url 2020-04-01-Ironsworn-pt1 %}
[veilpost]: {% post_url 2020-04-14-the-veil %}
[arcanemoonpost]: {% post_url 2020-09-05-adventure-writing %}
[dados]: {% post_url 2019-02-07-dice %}

<!--External-Links-->
[Arcane Moon]: https://bit.ly/ArcaneMoon
[The Veil]: http://bit.ly/TheVeilRPG
[emacs]: https://www.gnu.org/software/emacs/
