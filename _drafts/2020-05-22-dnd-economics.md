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
2. [El costo de tu estilo de vida][LifestyleExpenses]
3. [Puedes practicar una profesión][PracticingaProfession]

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

Según lo que encontró Nordhaus, en la antigua Babilonia el salario de un día entero solo hubiera alcanzado para iluminar una habitación unos diez minutos. Para los 90's, cuando escribió su paper, en algunos lugares, un día de trabajo podría haber iluminado una habitación durante **veintemil horas.** Entonces ¿cuanto necesitas trabajar en Dungeons & Dragons para iluminar con una vela?

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
- Un foco de `100w` emite ~`1200 lumens`
- Un foco flourecente de `18w` emite `1290 lumens`
- La luz de día da `10,000 lux`
- El nivel de luminicencia en una casa normal es ~`100 lux`
_Tomado de "Do real output and real wage measures capture reality?"_

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

Considerando que ganas `15sp` diarios podrías comprar 150 velas cada día si dedicaras todo tu salario a hacerlo. 150 velas, cada una emitiendo 13 lúmenes y durando una hora nos da un total de `1950 lumen/hora`. También podrías comprar 15 pintas de aceite, que le darían 6 horas de luz cada una. O podrías repartirlas en noventa diferentes lámparas, para iluminar exactamente una hora y obtener `8775 lumen/hora` de iluminación.

Entonces, Un día de trabajo que mantiene un estilo de vida "Commonn" te da un total de:
- `8775 lumen/hora` si iluminaras con lámparas
- `1950 lumen/hora` si iluminas con con velas.

Pero comprar noventa Hooded Lamps, a 7gp cada una, te tomaría $$ (90 * 70 sp) \div 15 sp/dia = 420 dias $$ de trabajo sin hacer otra cosa que comprar lámparas, no lo más práctico. Quiero poner en perspectiva que 90 lámparas iluminan lo mismo que 7.3 focos incandescentes de 100w.


{% raw %}
$$ 150 * 13 = 1950 {{lumen}\over{hora}} $$
{% endraw %}

De la tabla "Labor Price of Light", de Nordhaus, vemos que si fuéramos a obtener `1,000 lumen/hora` utilizando velas en los 1800~1830 tomaría `6 hrs ~ 10.6 hrs` de trabajo.


## Puedes practicar una profesión

En el PHB (3.5e p80)

Mitad de tu profession check de gp por semana

Check = 1d20 + Wis modifier + skill rank
      = 1d20 + 1 + 4
      = [15,16]

gp per week = [7,8]

12 and 13


Ivan Reyes, [26 May 2020 23:54:30]:
Las lámparas en D&D son como pendejamente eficientes

1,000 lumen/hora de una velas en D&D te toma 3~5.2 horas de trabajo.

Con un día de ejercer tu profesión puedes comprar hasta 1950 lumen/hora.

En la realidad comprar 1,950 lumen/hora de velas en 1830 te hubiera tomado de 6~10.6 hrs de trabajo
Los números coinciden con la realidad más o menos

De una lámpara puedes comprar 8,775 lumen hora con u ndía de trabajo en D&D

Para comprar eso en la vida real te hubiera tomado 26.1 horas de trabajo

Pero ahí es dónde entra la mágia, chuchu

Si es tan pendejamente eficiente tiene que ser porque hay un modo técnológico más avanzado de extracció nde aceites dentro de D&D

o un aceite que sea particularmente luminoso al momento de quemarse




| Device          | Stage of Technology               | Approximate Date   | Labor Price (hours of work per 1,000 lumen-hours) |
|-----------------|-----------------------------------|--------------------|---------------------------------------------------|
| Open Fire       | Wood                              | From earliest time | 58.000000                                         |
| Neolithic lamp  | Animal or vegetable fat           | 38,000-9,000 BC    | 50.000000                                         |
| Babylonian lamp | Sesame oil                        | 1750 BC            | 41.500000                                         |
| Candle          | Tallow                            | 1800               | 5.370000                                          |
|                 | Sperm                             | 1800               | 12.210000                                         |
|                 | Tallow                            | 1830               | 3.000000                                          |
|                 | Sperm                             | 1830               | 6.910000                                          |
| Lamp            | Whale oil                         | 1815-1845          | 4.900000                                          |
|                 | Silliman's experiment: Sperm oil  | 1855               | 16.030000                                         |
|                 | Silliman's experiment: Other oils | 1855               | 5.940000                                          |
| Town gas        | Early lamp                        | 1827               | 7.398000                                          |
|                 | Silliman's experiment             | 1855               | 2.978000                                          |
|                 | Early lamp                        | 1875-1885          | 0.326000                                          |
|                 | Welsbach mantle                   | 1885-1895          | 0.083000                                          |
|                 | Welsbach mantle                   | 1916               | 0.012000                                          |
| Kerosene lamp   | Silliman's experiment             | 1855               | 0.230600                                          |
|                 | 19th centy                        | 1875-1885          | 0.225300                                          |
|                 | Coleman lantern                   | 1993               | 0.009800                                          |
| Electric lamp   | Edison carbon lamp                | 1883               | 0.750239                                          |
|                 | Carbon filament                   | 1900               | 0.220431                                          |
|                 | Carbon filament                   | 1910               | 0.092096                                          |
|                 | Filament lamp                     | 1920               | 0.013538                                          |
|                 | Filament lamp                     | 1930               | 0.010396                                          |
|                 | Filament lamp                     | 1940               | 0.005490                                          |
|                 | Filament lamp                     | 1950               | 0.001883                                          |
|                 | Filament lamp                     | 1960               | 0.001016                                          |
|                 | Filament lamp                     | 1970               | 0.000551                                          |
|                 | Filament lamp                     | 1980               | 0.000678                                          |
|                 | Filament lamp                     | 1990               | 0.000605                                          |
|                 | Compact fluorescent               | 1992               | 0.000119                                          |


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

———

En 3.5 hay un skill que se llama profession. Haces un skill check y ganas la mitad de lo que hayas sacado para esa semana.

Entonces, tenemos estos supuestos.

- gp/week = (1d20 + ability modifier + ranks)/2

- avarage ability modifier = 1

- ranks to profession = 4 (porque vamos a asumir que quieres ser bueno en tu profesión y 4 es el máximo)

- “common” lifestyle: 10.5 gp / week.  You live in inns and eat tavern meals every day, a practice that quickly grows to be moderately expen- sive. This level of upkeep assumes the occasional night drinking in the tavern or a nice glass of wine with dinner.


——

Luego

gp/week = (1d20 + 1 + 4)/2

gp / week = [7,8]


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
