---
layout: mathpost
title: "Las Matemáticas de D&D: Economía y Productividad en Waterdeep"
featuredimage: /assets/2020-05-22/candles.jpg
description: Con el Dungeon's Master Guide y el Player's Handbook ¿Podemos hacer un análisis de la economía de Dungeons & Dragons?
imagewidth: 1920
imageheight: 1280
---

![Aprendamos de economía][cover]

Es hora de lo que todos estaban esperando, de descargar los papers de macroeconomía, de buscar números en manuales viejos, de obsesionarse por cosas quizás solo le importan a otras tres personas. ¡Es hora de analizar la economía de Waterdeep!

<!--more-->

He estado leyendo detenidamente el Player's Handbook (PHB) y Dungeon Master's Guide (DMG) de D&D Quinta edición y me llamaron la atención tres cosas que ni siquiera sabía que estaban en los manuales:

1. [El costo de una vela][OtherAdventuringGear]
2. [Puedes practicar una profesión][PracticingaProfession]
3. [El costo de tu estilo de vida][LifestyleExpenses]

¿Qué tienen estas tres cosas de interesante? Que podemos estimar cuanto tiempo le toma a alguien ganar suficiente dinero para pagar por una vela!!!

![Velas][candles]
_By [Zoran Kokanovic]_

_**¡Espera antes de que te vayas!**_ Con estos datos podemos calcular el producto interno bruto de una ciudad dentro del mundo de Dungeons & Dragons. Podemos saber la productividad de la población. Y podemos extrapolar cosas cómo el efecto que tiene la magia en la economía de los Forgotten Realms. Pero para todo eso necesitamos hablar de William Nordhaus, premio Nobel de economía..... _**ahhh ok... de todos modos te fuiste.**_

## William Nordhaus

[William Nordhaus] ganó el premio Nobel de economía en 2018 por su trabajo describiendo la relación entre la economía y el cambio climático. Su trabajo en este campo es muy importante, pero lo que a nosotros nos interesa el día hoy es un paper que escribió en 1996 dónde describe sus conclusiones de pasar meses en su cocina midiendo cuanta [luz por hora da una vela][planetmoney]. _**¿Así es cómo se fueron los demás?**_

![William Nordhaus][nordhouse_pic]
_[William Nordhaus]_

Claro que estoy exagerando. Nordhaus, si pasó meses midiendo la luz de velas, pero su objetivo fue, en términos muy sencillos: _Comparar cuanto tiempo de trabajo le toma a una persona generar la riqueza necesaria para iluminar el equivalente a "una vela"._ Publicó lo que encontró en su paper ["Do real output and real wage measures capture reality?"][chicagopress]

Cuando lo piensas en el pasado, iluminar el equivalente a una vela necesitaba... pues una vela. Y hacer una vela necesitaba criar una vaca, conseguir el alimento para hacer que la vaca creciera, matar a la vaca, juntar la grasa de la vaca, cocinar la grasa, y convertir esa grasa en velas. En algunos sentidos ¡tomaba años hacer una vela!

Según lo que encontró Nordhaus, en la antigua Babilonia el salario de un día entero solo hubiera alcanzado para iluminar una habitación unos diez minutos. Para los 90's, cuando escribió su paper, en algunos lugares, un día de trabajo podría haber iluminado una habitación durante **veintemil horas.**

Estos datos y comparaciones son importantes porque la iluminación es una necesidad universal. Para poder comparar la productividad de D&D con la productividad en el mundo real necesitamos comparar cosas que necesitemos en la misma medida y el esfuerzo que toma en cada universo obtenerlas.

Entonces ¿cuanto necesitas trabajar en Dungeons & Dragons para iluminar con una vela?

## El costo de una vela en Dungeons & Dragons

_A partir de este punto, la información oficial de D&D ha sido tomada de manuales de 3.5e para consistencia._

Una vela, en D&D, cuesta 1 Copper Piece, que básicamente es un un centavo de Gold Piece. En el PHB (3.5e p165) Hay muchas otras formas de iluminación en D&D incluidos _spells,_ pero Excepto por Continual Flame todos duran menos que el "fuego natural", y de cualquier forma hacer una Continual Flame toma 50gp de polvo de ruby; nada barato.

Otros métodos de iluminación y el aceite que algunos usan como combustible, en 3.5e son:

|        Item       | Bright Illumination       | Shadowy Illumination |  Duration  |  Cost  |
|-------------------|--------------------------:|---------------------:|-----------:|-------:|
| Candle            |        `n/a`              |         `5ft`        |   `1hr`    |  `1cp` |
| Lamp, common      |       `15ft (4.6m)`       |        `30ft`        | `6hr/pint` |  `1sp` |
| Lantern, bullseye |       `60ft (18.3m)` cone |       `120ft` cone   | `6hr/pint` | `12gp` |
| Lantern, hooded   |       `30ft (9.1m)`       |        `60ft`        | `6hr/pint` |  `7gp` |
| Torch             |       `20ft (6.1m)`       |        `40ft`        |   `1hr`    |  `1cp` |
| Oil               |         –                 |            –         |     –      |  `1sp` |

_**Esta es una tabla generada a partir de tablas en las páginas la 128 y 165 del PHB 3.5e**_

Vamos a comparar las lámparas y las velas entre la vida real y el universo de D&D. Una vela puede iluminar "pobremente" un radio de ~`1.5m`, lo cual suena a esas veces que mi abuela prendía la vela en la sala. Y una lámpara ilumina un radio de `4.6m` nunca he usado una lámpara de aceite pero si espero que pudiera iluminar un cuarto.

Necesitamos tres definiciones formales para seguir hablando de luz:
- Flux: El volúmen de luz emitido desde una fuente de iluminación. Su unidad es el `lumen`
- Lux: Es la luminicencia (Flux) en un área. Su unidad es el `Lux` que es `1 lux = 1 lumen / m^2`
- La eficiencia de un dispositivo de iluminación se puede medir en `lumens / hora`

Y del paper de Nordhaus sabemos que:
- Una vela emite al rededor de `13 lumens`
  * Un cuarto iluminado por dos velas tiene ~`5 lux`
- Una lámpara de aceite `~97.5 lumens`
- Un foco de `100w` emite ~`1200 lumens`
- Un foco flourecente de `18w` emite `1290 lumens`
- La luz de día da `10,000 lux`
- El nivel de luminicencia en una casa normal es ~`100 lux`
_Tomado de "Do real output and real wage measures capture reality?"_

## Puedes practicar una profesión

En el PHB (3.5e p80) se especifica que para practicar una profesión tienes que hacer un _check_ de tu _Profession Skill,_ que siempre esta asociado con Wisdom. En la misma regla vemos que un personaje ganaría la mitad del resultado del check en oro para esa semana.

> You can practice your trade and make a decent living, earning about half your Profession check result in gold pieces per week of dedicated work.

Supongamos un personaje `LVL 1` con `Wisdom 12~13`, los valores promedio para cualquier estadística, esto nos da un `stat modifier +1`. En 3.5e empezamos también agregando _ranks_ a los skills; así que asumiremos que se agregan `4 ranks` a `Wis (Profession)`, porque el rank máximo que puedes tener es `LVL + 3`. Siendo así, ese personaje `LVL 1` ganaría $$ 7gp $$ por semana. Y en el mejor de los casos, un personaje `LVL 1` ganaría $$ 9gp $$ por semana, con `Wisdom 18`.

$$
 \lfloor E([1d20 + 1 + 4] \div 2) \rfloor =7gp
$$

$$
 \lfloor E([1d20 + 4 + 4] \div 2) \rfloor =9gp
$$

_En D&D las divisiones ~~casi~~ siempre se redondean hacia abajo. PHB (3.5e p304)_

Entonces, en iluminación ¿Cuanta podemos comprar? Ganando 7gp a la semana un adventurer podría comprar `1,300 lumen/hora` si comprara velas, o `5,850 lumen/hora` en aceite para lámparas.

Esto es porque 7gp semanales son 100cp diarios; con ese dinero comprarías 100 velas al día y cada vela ilumina `13 Lumen / hora`. Con el mismo dinero comparías 10 pintas de aicete al día, cada una de las cuales alcanza para iluminar 6 lámparas durante una hora; un total de 60 lámparas cada una de las cuales ilumina `97.5 velas/hora`.

| GP / semana | Velas / día | Lumen / hora (Vela) | Pintas aceite / día | Lumen / Hora (Lámpara) |
|-----------|--------------|-----------------------|-----------------|---------------------|
| 7         | 100.0        | 1,300.0               | 10.0            | 5,850.0             |
| 8         | 114.3        | 1,485.7               | 11.4            | 6,685.7             |
| 9         | 128.6        | 1,671.4               | 12.9            | 7,521.4             |

La siguiente tabla tiene el tiempo de trabajo que le tomaría a una persona adquirir `1,000 lumen/hora` en los 1800s. Vemos que si fuéramos a obtener `1,000 lumen/hora`, con velas, tomaría `6 hrs ~ 10.6 hrs` de trabajo. Y para una lámpara de aceite tomaría `4.9 hrs ~ 5.9 hrs` de trabajo.

| Device          | Stage of Technology | Approximate Date   | Labor Price (hours of work per 1,000 lumen-hours) |
|-----------------|---------------------|--------------------|---------------------------------------------------|
| Candle          | Tallow              | 1800               | 5.370000                                          |
|                 | Tallow              | 1830               | 3.000000                                          |
| Lamp            | Whale oil           | 1815-1845          | 4.900000                                          |
|                 | Other oils          | 1855               | 5.940000                                          |

_**Nordhaus. Table 1.6 Labor Price of Light**_

Para nuestro personaje, ganando 7gp a la semana, comprar `1,000 lumen/hora` de iluminación:
- En velas:   tomaría `7.7 hrs` de trabajo
- En aceite: tomaría `1.7 hrs` de trabajo

El trabajo necesario para adquirir velas es bastante parecido al mundo real, de ahí podemos inferir que la tecnología de velas, en Forgotten Realms, es bastante parecida a la nuestra. Mientras que la tecnología de aceite es debería ser bastante más avanzada, al menos comparada con los 1800s, para que tome ese tiempo. Esto puede ser porque el método de extracción es mejor, o porque el aceite de mucha mejor calidad que los que nosotros tuviéramos disponibles en la época.

Sin embargo el costo de las lámparas en sí es lo que hace prohibitivo iluminar con esta tecnología

Para obtener `1,000 lumen/hora` necesitas `11 lámparas` prendidas al mismo tiempo. A un costo de 7gp cada una, adquirirlas te tomaría `11 semanas` de trabajo. 77 días en los que todas tus ganancias se destinarían a comprar lámparas. Y recordemos que esas **11 lámparas, no producen ni siquiera la misma iluminación que un solo foco de 100 incandescente de 100 watts.**

$$
{1000 {lumen \over hora} \over 97.5 {lampara\ lumen \over hora}} = 10.25641026\ lampara
$$

Por esta razón podemos justificar la existencia de velas como método de iluminación dentro del universo de D&D. Aunque el aceite es bastante más eficiente que las velas, la "plataforma" para utilizarlo es extremadamente cara.


## El costo de tu estilo de vida en Dungeons & Dragons

El DMG (3.5e p130) enlista el costo que le toma a un adventurer mantener su estilo de vida bajo la regla _Upkeep._ Creo que es razonable decir que algunos de estos estilos de vida incluyen, al menos, una hora de iluminación al día.

> The upkeep can be assumed to take into consideration every expense except the cost of specific adventuring equipment—even taxes. Ultimately, each player should choose the level of upkeep she’s willing to pay.

_Dungeon Master's Guide 3.5e p130_

| Lifestyle 3.5e | Cost 3.5e   |
|----------------|-------------|
| Meager         |     `16 cp` |
| Poor           |      `4 sp` |
| Common         |     `15 sp` |
| Good           |     `33 sp` |
| Extravagant    |     `66 sp` |

En el DMG los costos se presentan mensualmente. Los convertí en costos diarios para hacerlo más manejable. Para los siguientes cálculos voy a tomar el costo del estilo "Common", precisamente porque es el común.




| Lifestyle 5e | Cost 5e | Lifestyle 3.5e | Cost 3.5e |
|--------------|---------|----------------|-----------|
| Squalid      |   10 cp | Meager         |     16 cp |
| Poor 	       |    2 sp | Poor           |      4 sp |
| Modest       |   10 sp | Common         |     15 sp |
| Comfortable  |   20 sp | Good           |     33 sp |
| Wealthy 	   |   40 sp | Extravagant    |     66 sp |


Me puse a seguir revisando de la economía en 3.5e y el costo de vida es pinches enormeeeee

En 5e el manual dice que si practicas una profesión te alcanza para mantener un estilo de vida normal.

Me di cuenta de que no había leido eso explicitamente en 3.5e y me puse a buscarlo.


- “common” lifestyle: 10.5 gp / week.  You live in inns and eat tavern meals every day, a practice that quickly grows to be moderately expen- sive. This level of upkeep assumes the occasional night drinking in the tavern or a nice glass of wine with dinner.


El costo de mantener un estilo de vida “common” es 10.5 gp / week

No te alcanza para eso.

Un estilo de vida “Poor” cuesta 2.8 gp / week


Y el manual explicitamente dice que un trabajador promedio gana 3gp / week. O sea solo podrías vivir, no podrías comprarte nada excepto sobrevivir.

———

Incluso si tuvieras 18 de ability score y 4 ranks a tu profesión. Eso solo te daría, en promedio 9gp / week. De todos modos no te alcanza!

El oro de una profesión te deja vivir un estilo de vida entre poor y common.

———

Y así, finalmente, esta explicado por qué chingados la gente sale a la aventura, por qué la gente arriesga su vida, es porque no les queda de otra. No es solo porque hay cosas allá afuera que no hay en las poblaciones. Es porque es la única forma de avanzar tu estilo de vida

> The upkeep can be assumed to take into consideration every expense except the cost of specific adventuring equipment—even taxes. Ultimately, each player should choose the level of upkeep she’s willing to pay.

even taxes y mi alma descansó un chingo
---

¡Gracias por leer este deep dive! Si no leiste la primera parte de mi análisis de la Bag of Holding puedes hacerlo [aquí]({% post_url 2020-04-25-bag-of-holding %}).

Este post es uno de muchos que he estado escribiendo sobre juegos de rol. Si te gusta D&D puedes leer [cómo jugar D&D online]({% post_url 2020-04-05-dnd-online %}) o sobre [Ironsworn]({% post_url 2020-04-01-Ironsworn-pt1 %}), el juego que más he recomendado últimamente.

_Some photos by [Zoran Kokanovic] on Unsplash_

---

## Fuentes

- [Dungeon Master's Guide (3.5e Core Rulebook)][dmg]
- [Player's Handbook (3.5e Core Rulebook)][phb]
- [A Grand History of the Realms (3.5e Campaign Accesory)][history]
- [City of Splendors: Waterdeep (3.5e Campaign Supplement)][waterdeep]
- [Nordhaus, William D. 1997. "Do Real Output and Real Wage Measures Capture Reality? The History of Light Suggests Not." The Economics of New Goods. Edited by Robert J. Gordon and Timothy F. Bresnahan. University of Chicago Press for the National Bureau of Economic Research. 27-70.][chicagopress]

<!--Images-->
[cover]: {{ page.featuredimage }}
[nordhouse_pic]: /assets/2020-05-22/nordhaus.jpg


<!--Credits-->

[Zoran Kokanovic]: https://www.flickriver.com/photos/noonchaka/popular-interesting/?utm_medium=referral&utm_source=unsplash

<!--Links-->

[LifestyleExpenses]: https://www.dndbeyond.com/sources/basic-rules/equipment#LifestyleExpenses
[OtherAdventuringGear]: https://www.dndbeyond.com/sources/basic-rules/equipment#OtherAdventuringGear
[PracticingaProfession]: https://www.dndbeyond.com/sources/basic-rules/adventuring#PracticingaProfession

[William Nordhaus]: https://en.wikipedia.org/wiki/William_Nordhaus
[planetmoney]: https://www.npr.org/sections/money/2018/10/08/655597272/episode-534-the-history-of-light-nobel-edition
[chicagopress]: https://press.uchicago.edu/ucp/books/book/chicago/E/bo3637763.html

[dmg]: https://www.dmsguild.com/product/149132/Dungeon-Masters-Guide-35
[phb]: https://www.dmsguild.com/product/148008/Players-Handbook-35
[history]: https://www.dmsguild.com/product/51644/Grand-History-of-the-Realms-35
[waterdeep]: https://www.dmsguild.com/product/25995/City-of-Splendors-Waterdeep-35
