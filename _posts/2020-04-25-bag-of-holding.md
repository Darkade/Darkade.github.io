---
layout: mathpost
title: "Las Matemáticas de D&D: Bag of Holding"
image: /assets/2020-04-25/bagofholding.jpeg
description: Estoy teniendo "issues" con las Bag of Holding. Así decidí decifrár ¿Cómo se vería una por dentro?
---

![Esta es una bag of holding][bagofholding]

Una [Bag of Holding](https://www.dndbeyond.com/magic-items/bag-of-holding) es una bolsa en la cual puedes guardar muchas más cosas de las que pareciera, similar a la bolsa de Mary Poppins ~~o la de Hermione si quieres que los fans de D&D te vean feo~~. Según las reglas básicas:

<!--more-->

> This bag has an interior space considerably larger than its outside dimensions, roughly 2 feet in diameter at the mouth and 4 feet deep. The bag can hold up to 500 pounds, not exceeding a volume of 64 cubic feet. The bag weighs 15 pounds, regardless of its contents.

Haciendo cuentas rápidas, si una bag of holding fuera un cilindro $ (V=πr^2 h) $ su volumén sería $ 12.57 $ pies cubicos, que es considerablemente menos que los $ 64 $ pies cúbicos que dice tener. De modo que no se trata de un cilindro y pareciera más bien que se trata de un [_cono truncado,_](https://mathworld.wolfram.com/ConicalFrustum.html) es decir un cono al que "le quitamos una parte" de arriba.

![Un cono truncado][frustum]
_Un cono truncado_

Pero entonces ¿cómo se ve nuestra bag of holding por dentro? Si tiene 2 pies de diámetro en la boca ¿cual es el diámetro en el fondo?

Hay varios modos fáciles de obtener el diámetro del fondo, pero el más divertido es hacer una integral. Podemos imaginar sumar el volumen de varias "rebanadas" de un cono, cada una de radio menor que la anterior. Si hacemos estas rebanadas tan delgadas que su altura tienda a cero, es decir: $ h \rightarrow 0 $ tendremos el volumen del cono.

!["Rebanadas" de cilindro][slices]
_Así podemos aproximar el volumen de un cono_

La integral entonces queda definida así:

$$ 64 = \int_{0}^{4} {πR(h)^2}dh $$

Dónde $ R(h) $ expresa el radio de cada rebanada en función de a qué altura esta en el cono. Es una función sencilla, y explico de dónde viene en un momento.

- Sabemos que nuestra bolsa tiene 64 pies cúbicos de volumen, de ahí el $ 64 $
- Sabemos que tiene 4 pies de altura por eso integramos en ese rango $ \int_0^4 $
- Y sabemos que el área de cada rebanada es $ πr^2 $ entonces tenemos $ πR(h)^2 $

## La función R(h)

Sabemos al menos uno de los dos radios, el de la boca. Cuando la altura de la bolsa es 4 el radio es 1. Y no sabemos el radio del fondo, cuando la altura de la bolsa es cero; a este radio le llamaremos $ r_1 $

| $ h $ | $ R(h) $ |
|-------|----------|
| $ 4 $ |   $ 1  $ |
| $ 0 $ |   $ r_1 $ |


También sabemos que el radio varía _linealmente,_ porque el cono es un cono. Es recto en sus lados no curvo ni de ninguna otra forma rara. De modo que $ R(h) $ es una función lineal. Solo tenemos que calcular su pendiente $ (1 - r_1) / (4 - 0 ) $ y su punto de intersección con el eje de las _abscisas,_ que es  $R(0) = r_1$. De modo que la ecuación es:

{% raw %}
$$ R(h) = {{1 - r_1}\over{4}}h + r_1 $$
{% endraw %}

## Resolviendo para $r_1$

Al final lo que queremos saber es cual es el diámetro del fondo de la bolsa, entonces tenemos que sustituir, integrar y despejar:

{% raw %}
\$
64 = \int_{0}^{4} {π\left[ {{1 - r_1}\over{4}}h + r_1 \right]^2}dh
\$

\$
64 =π\int_{0}^{4} { \left( {{1 - r_1}\over{4}}  \right)  ^2 h^2  + 2h{{1 - r_1}\over{4}}r_1   + r_1^2 }dh
\$

\$
64 =π  \left[ \left( {{1 - r_1}\over{4}} \right) ^2 {{h^3} \over {3}}  + {{1 - r_1}\over{4}}r_1h^2   + r_1^2h  \right]_{0}^{4}
\$

\$
64 =π  \left[ {{4} \over {3}} \left( {1 - r_1} \right) ^2   + 4 \left( {1 - r_1} \right)r_1   + 4r_1^2  \right]
\$

\$
48 =π  \left[ {\left( {1 - r_1} \right) ^2   +  3\left( {1 - r_1} \right)r_1   + 3r_1^2 }  \right]
\$

\$
48 =π  \left[ { 1 -2r_1+ r_1^2  +  3r_1 - 3r_1^2   + 3r_1^2 }  \right]
\$

\$
48 =π  \left[ { r_1^2 + r_1 +1 }  \right]
\$
{% endraw %}

Que es una ecuación cuadrática y nos da que $ r \approx 3.3117 $

De modo que el fondo de la bolsa, tiene un diámetro de $ 6.6234 $ pies.

## Y en medidas de verdad

El cono tiene una altura de $ 1.2192 $ metros. Un diámetro superior de $ 0.6096 $ metros y un diámetro de fondo de $ 2.018 $ metros. Además de un volumen de $ 1,812.28 $ Litros. Qué es un [rotoplas](https://rotoplas.com.mx) para unas 7 personas, creo\[?\] xD

![Tinacos Rotoplas][rotoplas]
_El catálogo de rotoplas en 2020_

Finalmente, así es como se vería una bag of holding de estas medidas. Si. Si cabes dentro de una Bag of Holding, fácilmente cabes.

![Y así se ve][sketchup]
_Y así se ve_

---

¡Gracias por leer! Este post es uno de muchos que he estado escribiendo sobre juegos de rol. Si te gusta Dungeons puedes leer [cómo jugar D&D online]({% post_url 2020-04-05-dnd-online %}) o sobre la campaña que tengo de [The Veil]({% post_url 2020-04-14-the-veil %})

[bagofholding]: {{ page.image }}
[slices]: /assets/2020-04-25/slices.png
[sketchup]: /assets/2020-04-25/sketchup.png
[rotoplas]: /assets/2020-04-25/rotoplas.png
[frustum]: /assets/2020-04-25/frustum.gif
