---
layout: mathpost
permalink: /:year/:month/:day/:title:output_ext
title: "Las Matemáticas de D&D: Bag of Holding Parte 2"
image:
  path: /assets/2020-05-05/math.jpg
  width: 800
  height: 534
description: Después de averiguar cómo se ve por dentro una Bag of Holding ¿Cuánto puedes en verdad cargar?
---

![Esta es una Bag of Holding][bagofholding]

_En capitulos anteriores_ pasé más tiempo del que debía pensando en cómo se ve realmente una  [Bag of Holding]({% post_url ES/2020-04-25-bag-of-holding %}). Hoy vamos a ver que puedes meter en ella, por volumen, peso y forma.

<!--more-->

En las reglas básicas y el Players Handbook solo se menciona el volumen de los contenedores: barriles, mochilas, cofres, la Bag of Holding, etc. Mientras que para las cosas que guardas, como monedas, items, pociones generalmente se menciona solo el peso. Pero por eso yo estoy aquí: para considerar todas esas cosas y decirte qué puedes y qué no puedes meter en una Bag of Holding.

Todo esto empezó porque [@Khyo](https://twitter.com/khyo) me habló de lo prácticas que son las Bag of Holding al momento de _lootear_ así que vamos a analizar cosas que podrías encontrar en un dungeon. Específicamente vamos a ver el loot en _Wave Echo Cave_ parte de la aventura _[Lost Mine of Phandelver.](https://dnd.wizards.com/products/tabletop-games/rpg-products/rpg_starterset)_


![Lost Mine of Phandelver][phandelver]
_**Minor spoilers for the treasure in Lost Mine of Phandelver**_

## Monedas

Vamos a comenzar por las monedas porque tienen el peso y volumen más fácil de calcular.

Según las [reglas básicas](https://www.dndbeyond.com/sources/basic-rules/equipment#Coinage) _"one standard coin"_ pesa $$ 1/3 oz $$ y entonces $$ 50 $$ monedas estandar pesan $$ 1lb $$. Haciendo algunas conversiones sencillas vemos que coincide con los pesos y valores de la [Trade Goods Table](https://www.dndbeyond.com/sources/basic-rules/equipment#TradeGoodsTable) para Gold, Silver, Copper y Platinum Pieces. Por ejemplo:

- para el Platinum $$ 500 gp = 1lb \text{ Platinum} $$
- pero también $$ 500 gp = 50 pp $$
- y por transitividad $$ 50 pp = 1lb \text{ Platinum} $$

La tabla no menciona el valor de una libra de Electrum, pero vamos a suponer que también aplica.


### Gold Pieces



Entonces ¿Cuantas Gold Pieces podemos meter en nuestra Bag of Holding? Partimos de que:

- La densidad del oro puro es de $$ 19.32 g/cm^3 $$
- $$ 50 gp $$ pesan $$ 1 lb $$
- $$ 1 lb $$ en medidas de verdad es $$ 453.592 g $$

Para saber cuanto volumen ocuparía esto en oro puro solo hay que saber la fórmula de la densidad.

{% raw %}
$$ {{453.592 g} \over {V}} = 19.32 g/cm^3 $$

$$ V = 23.47784 cm^3 $$
{% endraw %}

$$ 1 lb $$ de oro tiene un volumen de ~$$ 23.5 cm^3 $$

Suponiendo que las Gold Pieces tienen forma de monedas de $$ 2cm $$ de diámetro. ¿Cuánto espacio ocuparían cincuenta monedas acomodadas una sobre la otra, como un cilindro? Elegí $$ 2cm $$ porque es la medida aproximada de un [Aureus](https://www.coins-auctioned.com/learn/coin-articles/collecting-ancient-roman-coins-part-iv-identify).

{% raw %}
$$ \pi {(1 cm)}^2 h = 23.47784 cm^3 $$

$$ h = 7.47323 cm $$
{% endraw %}
Es un cilindro de $$ 2cm $$ de diámetro y ~$$ 7.5cm $$ de altura para las cincuenta monedas. Cada una de las cuales tiene $$ 0.149465 cm $$ de alto, suponiendo que las monedas son perfectamente planas y de oro puro.

![Un aureus de la época de Octavio][aureus]
_Un aureus de la época de Octavio_

Por otro lado, sabemos que una Bag of Holding solo puede tener hasta $$ 500 lb $$ de peso, lo cual serían $$500 lb * 50 {gp \over lb} = 25,0000 gp $$ ¡Puedes meter hasta 25,000 Gold Pieces en una Bag of Holding!

Pero lo más sorprendente es que eso solo ocupan ~$$ 0.4 \text{ft}^3 $$ y una Bag of Holding tiene capacidad para ¡$$ 64\text{ft}^3 $$! En otras palabras: El oro es tan denso que puedes cargar con muchas GP, de mucho valor, y de todos modos tu Bag of Holding estaría practicamente vacía.

{% raw %}

$$ V = {{ 226,796 g} \over {19.32 g/cm^3}}  $$

$$ V \approx 11738.92 cm^3$$

$$ V \approx 0.41455604747 ft^3$$

{% endraw %}

![25,000 Gold Pieces][goldpieces]
_Solo eso ocupan 25,000 gp_

Para ponerlo en perspectiva: 25,000 gp te compran un [War Ship](https://www.dndbeyond.com/sources/basic-rules/equipment#WaterborneVehicles): un barco de treinta metros de largo con capacidad para cien personas. La Bag of Holding no puede cargar un gramo más, pero sigue casi vacía. El oro es muy denso.

Tenía mis dudas sobre si era posible hacer las monedas de oro puro, pero aparentemente los Aureus suelen ser de 24 kilates lo cual es de $$ 99.95\% $$ a  $$ 100\% $$ de pureza y tenían un peso estandarizado de ~$$ 8g $$. Así que 50 Aureus pesarían $$ 400g $$. Las Gold Pieces y los Aureus estan razonablemente cercanos.

![Cómo se hacían monedas en roma][romanmint]
*[Cómo se hacían monedas en roma](https://www.youtube.com/watch?v=b6T_ZutXzNQ)*

### Platinum, Silver, Electrum y Copper Pieces

Entonces, $$ 1gp $$ es una moneda de radio $$ r_{gp}= 1cm $$ y altura $$ h \approx 0.14 cm $$, sabemos que su peso es $$ w = 1/3 oz \approx 9.44g $$. Vamos a usar estas medidas para calcular el tamaño de las monedas de los demás metales, para hacerlo necesitamos su densidad.

|   Metal  | Densidad $$ (d_M) $$ | Densidad respecto a Gold $$ \left(d_M \over d_g \right) $$ |
|----------|----------------------|------------------------------------------------------------|
| Platinum |     21.45 g/cm^3     | 1.11                                                       |
| Gold     |     19.32 g/cm^3     | 1.00                                                       |
| Electrum |     13.00 g/cm^3     | 0.67                                                       |
| Silver   |     10.49 g/cm^3     | 0.54                                                       |
| Copper   |      8.96 g/cm^3     | 0.46                                                       |

_El [electrum](https://www.chemistrylearner.com/electrum.html) es una aleación natural de oro y plata, y su densidad varía entre $$ 12.5 g/cm^3 $$ y $$ 15 g/cm^3 $$ así que tomé un punto medio._

La columna `Densidad respecto a Gold` es simplemente $$ \text{Densidad Metal} \over \text{Densidad gold} $$. Para el Copper:

{% raw %}
$$ {{8.96 g/cm^3} \over {19.32 g/cm^3}} = 0.46376811594 $$
{% endraw %}

Sabemos que nuestras monedas van a tener un peso constante $$ w $$ y vamos a decir que todas nuestras monedas van a tener la misma altura $$ h $$, pero radios variantes. Esta variación va a estar en función de las desidades. Para las Copper Pieces:

{% raw %}
$$ d_g = {{w} \over {\pi r^2_{gp} h}} ; d_c = {{w} \over {\pi r^2_{cp} h}} $$

$$ \text{ entonces } \left( d_c \over d_g \right) d_g = d_c $$

$$ \left( d_c \over d_g \right){{w} \over {\pi r^2_{gp} h}} = {{w} \over {\pi r^2_{cp} h}} $$

$$ { d_c \over d_g } = {{1} \over { r^2_{cp}}} $$

$$ r_{cp} = \sqrt{ d_g \over d_c } = \sqrt{ 1 \over 0.46 } $$

$$ r_{cp} = 1.47441956155 $$
{% endraw %}

De modo que una moneda de Copper tiene un diámetro de ~$$  2.94cm $$.

Luego. Para todas las monedas de altura $$ h \approx 0.14 cm $$:

|   Metal  |   $$ d_M $$  | $$ d_M \over d_g $$ | Radio   | diámetro |
|----------|--------------|---------------------|---------|----------|
| Platinum | 21.45 g/cm^3 | 1.11                | 0.95 cm | 1.90 cm  |
| Gold     | 19.32 g/cm^3 | 1.00                | 1.00 cm | 2.00 cm  |
| Electrum | 13.00 g/cm^3 | 0.67                | 1.22 cm | 2.44 cm  |
| Silver   | 10.49 g/cm^3 | 0.54                | 1.36 cm | 2.71 cm  |
| Copper   | 8.96  g/cm^3 | 0.46                | 1.47 cm | 2.94 cm  |

![Monedas mexicanas y sus escalas][monedas]
_Monedas mexicanas y sus escalas_

Honestamente me sorprende que una moneda de $10 MXN mida casi 3cm y que una Gold Piece sea más pequeña. Si me detengo a pensarlo tiene mucho sentido pero me sorprendió.

En total en la mina de _Mine of Phandelver_ encontramos:

|  Metal   | Unidades |   Peso   | Volumen     |
|----------|----------|----------|-------------|
| Platinum |	   15   |	 0.30 lb | 0.0002 ft^3 |
| Gold     |	  190   |	 3.80 lb | 0.0032 ft^3 |
| Electrum |	  153   |	 3.06 lb | 0.0038 ft^3 |
| Silver   |	  340   |	 6.80 lb | 0.0104 ft^3 |
| Copper   |	1,905   |	38.10 lb | 0.0681 ft^3 |
|----------|----------|----------|-------------|
| Total    |          | 52.06 lb | 0.0860 ft^3 |

O en medidas de verdad ~$$ 23.6 kg $$ con un volumen de ~$$ 2.4 $$ Litros. Si la forma no fuera importante puedes meter todas estas monedas en menos de tres cartones de leche.

![Todas las monedas dentro de la mina][lootcoins]
_Todas las monedas dentro de la mina en Mine of Phandelver_

## El resto del loot

Otras cosas a encontrar en la mina son:

- Boots of Striding
- Wand of Magic Missiles
- Potion of vitality
- Tres Diamantes
- Una pipa de madera con un adorno de platino
- Lightbringer: un mazo
- Dragonguard: una coraza
- Guantlets of Ogre Power
- Potion of Healing
- Spider Staff
- Nueve piedras preciosas
- Un tarro de electrum

Voy a decir en este momento que seguramente todo cabe. Difícilmente todas estas cosas pesan más de las 448 libras que nos quedan de capacidad, y la mayoría son pequeñas, así que por volúmen tampoco me preocupo. Lo más grande es sería Lightbringer, Dragonguard y el Spider Staff, que si vamos a revisar.

### Lightbringer

No hay enlistado ni peso ni medidas para Lightbringer. Así que revisé varios sitios de subastas de armas medievales ~~[because](https://www.liveauctioneers.com/en-gb/item/84709975_a-german-gothic-mace-circa-1500) this [is](https://www.liveauctioneers.com/en-gb/item/84709988_a-heavy-polish-or-hungarian-mace-circa-1600) serious [stuff](https://www.liveauctioneers.com/en-gb/item/84709973_a-light-german-gothic-mace-circa-1500).~~ Y vamos a utilizar como medida $$ 60 cm $$ de largo.

El peso de un mazo normal, [según el manual](https://www.dndbeyond.com/equipment/mace), es $$ 4 lb $$ lo cual esta bastante cercano al peso enlistado en algunos sitios de [replicas de armas.](https://www.gdfb.co.uk/medieval-flanged-battle-mace-steellength-approx-62cm-width-approx-16cm-weight-14kg-approx-30535-p.asp) ~~porque en los sitios de subastas no había pesos~~

Seguramente, Lightbringer pesaría un poco más, ya que la cabeza esta hecha de latón, que es más denso que el hierro.

Definitivamente no es la precisión que esperaba, pero una vez que te das cuenta que un mazo solo mide $$ 60cm $$, definitivamente cabe en la Bag of Holding.

### Dragonguard

El Dragonguard es un breastplate, o sea una coraza como la de Vegeta. Según el manual tiene un peso de 20 lb ¿Pero que hay sobre sus medidas?

![Vegeta][vegeta]
_El principe de los Saiyajin_

En general, la parte de mayor circunferencia de una coraza sería el pecho. Así que hay que averiguar cual es la circunferencia promedio del pecho de nuestros adventurers.

Gracias a uno de mis [podcasts favoritos,](https://99percentinvisible.org/episode/on-average/) di con _['The "Average Man"?'](https://apps.dtic.mil/dtic/tr/fulltext/u2/010203.pdf)_ La fuerza aérea de los estados unidos comisionó este documento en 1977 para determinar las medidas promedio de sus pilotos. Para estas personas su circunferencia promedio va de $$ 96.95 cm $$ a $$ 100.95 cm $$. De ahí podemos inferir que el diámetro del pecho de alguien, sería ~ $$ 30.86 cm $$.

$$ 2 \pi r = 96.95 cm $$

$$ 2r = 30.8601 $$

Este es un buen número, aunque la gente es ovalada en el pecho y no circular. Para el caso ovalado, incluso si una persona fuera casi "plana" y de todos modos tuviera $$ 96.95cm $$ de circunferencia el diámetro no sería mayor que $$ 48.475 cm $$. Seguiría entrando en la Bag of Holding ya que su diámetro en la boca es de $$ 60.96 cm$$.

### Spider Staff

De acuerdo al manual pesa $$ 6 lbs $$, no es un impedimento. Pero cuando piensas en el báculo de un mago definitivamente **es** al menos tan alto como el mago.

El sitio de [Weta Workshop](https://www.wetanz.com/shop/prop-replicas/pipe-staff-of-gandalf-the-grey) lista el báculo de Gandalf el Gris midiendo $$ 178cm $$ de altura. Y dice que es una replica exácta del báculo que utilizaron en la película. Por otro lado la [altura de Ian McKellen](https://www.celebheights.com/s/Ian-McKellen-260.html) es $$ 178.4cm $$. Entonces si: el báculo de un mago es al menos tan alto como el mago.

Y si fueramos a meter el báculo en vertical al Bag of Holding definitivamente no entraría, solo tiene ~ $$ 1.2m $$ de altura. Pero en el fondo mide más de $$ 2m $$. Entonces ¿Qué tan largo puede ser algo que estamos tratando de meter a la bolsa?

Comencemos por determinar la longitud del lado de la bolsa. Recordemos que la Bag of Holding tiene estas medidas:

![Medidas de la Bag of Holding][boh_medidas]
_Bag of Holding y las medidas que determinamos la vez anterior_

Entonces tenémos un tríangulo y estamos buscando su hipotenusa

{% raw %}
$$ c^2 = \left( {{2.018 - 0.6096} \over {2}} \right)^2 + 1.2192^ 2 $$

$$ c = \sqrt { 0.7042^2 + 1.2192^ 2 } $$

$$ c= 1.4079581954 m $$

{% endraw %}

El lado de la bolsa mide $$ 1.4 m $$ de largo. Esto sería una limitante si la bolsa no fuera de tela, y pudieramos estirar la boca. Sabemos que diámetro de la boca es de $$ 0.6096 m $$. Entonces lo que voy a hacer es obtener el perimetro de la boca y dividirlo por dos: la boca completamente estirada.

$$ p = \pi 0.6096 $$

$$ p = 1.91511488163m $$

$$ { p \over 2 } = 0.95755744081m $$

![La Bag of Holding con la boca estirada][boh_estirada]
_De lo cual obtenemos este diagrama_

Y podemos deducir que lo más largo que puede entrar en la bolsa mide ~$$ 2.04m$$ a penas un poco más que el fondo. Estaría estirando la bolsa y estaría inclinado, además de que tendría un radio cero. Pero eso es lo más largo que podríamos meter

$$ c = \sqrt {1.646^2 + 1.2192^2} $$

$$ c = 2.04835657052 $$

De modo que mientras seas un mago de menos de ~$$ 2.04m $$ de altura definitivamente puedes meter tu báculo en la Bag of Holding.

## ¿Qué podemos meter en la bolsa?

La tabla de los pesos quedaría de esta forma, algunos son pesos que yo aproxime con un _educated guess._ Pero aunque pesaran más seguiríamos dentro de nuestra capacidad.

| Item looteado           | Peso     |
|-------------------------|----------|
| Boots of Striding       | ~ 2 lb   |
| Wand of Magic Missiles  | 1 lb     |
| Potion of vitality      | 1/2 lb   |
| Tres Diamantes          | ~ 1 oz   |
| Una pipa de madera      | ~ 1/2 lb |
| Lightbringer            | 4 lb     |
| Dragonguard             | 20 lb    |
| Guantlets of Ogre Power | ~ 1 lb   |
| Potion of Healing       | 1/2 lb   |
| Spider Staff            | 6 lb     |
| Nueve piedras preciosas | 1/2 lb   |
| Un tarro de electrum    | ~4lb     |
| TOTAL                   | 40.063lb |

_El tarro de electrum es sorprendentemente pesado, si solo tomamos su valor en electrum. El valor enlistado es de 100gp, que son 200ep, que son 4lb de electrum pieces._

**Al final todo el loot de la mina pesa $$ 40.063 lb + 52.06 lb = 92.123 lb $$ o en medidas de verdad $$ 41.786 kg $$. Y como vimos todo cabe en la bolsa por su volumen.**

---

Después de dedicarle mucho tiempo a este item tengo que decir que: Si. la Bag of Holding es un item muy útil, pero desde mi perspectiva bastante _overkill._

Solo es necesario si siempre quieres cargar con todo el equipo y loot que has obtenido a lo largo de tu aventura y, para mi, parte de la diversión esta en elegir que llevas contigo. Después de todo solo puedes llevar seis Pokémon.

¡Gracias por leer este deep dive! Si no leiste la primera parte de mi análisis de la Bag of Holding puedes hacerlo [aquí]({% post_url ES/2020-04-25-bag-of-holding %}).

Este post es uno de muchos que he estado escribiendo sobre juegos de rol. Si te gusta D&D puedes leer [cómo jugar D&D online]({% post_url ES/2020-04-05-dnd-online %}) o sobre [Ironsworn]({% post_url ES/2020-04-01-Ironsworn-pt1 %}), el juego que más he recomendado últimamente.

[bagofholding]: {{ page.image.path }}
[romanmint]: https://img.youtube.com/vi/b6T_ZutXzNQ/0.jpg
[goldpieces]: /assets/2020-05-05/goldpieces.png
[lootcoins]: /assets/2020-05-05/lootcoins.png
[monedas]: /assets/2020-05-05/monedas.jpg
[aureus]: https://upload.wikimedia.org/wikipedia/commons/8/8b/Octavian_aureus_circa_30_BCE.jpg
[boh_medidas]: /assets/2020-05-05/medidas.png
[vegeta]: https://vignette.wikia.nocookie.net/dragonball/images/3/30/Vegeta_DBS_Broly_dise%C3%B1o.png/revision/latest?&path-prefix=es
[phandelver]: /assets/2020-05-05/phandelver.jpg
[boh_estirada]: /assets/2020-05-05/boh_estirada.png
