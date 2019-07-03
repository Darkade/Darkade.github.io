---
title: "Modelando las probabilidades en Arkham Horror: The Card Game"
---

[Arkham Horror: The Cardgame](https://www.fantasyflightgames.com/en/products/arkham-horror-the-card-game/) es un juego de cartas por Fantasy Flight Games en el universo de Cthulhu Mythos. En este juego los investigadores intentan detener a cultistas de invocar a sus oscuros amos desde otros planos para destruir la tierra; y siendo un juego de cartas, obviamente se ha convertido en mi nueva obsesión.

<!--more-->

En este juego cada jugador es uno de cinco detectives cada uno con una mazo de cartas diferente. Y cada uno con dos cartas que solo ese investigador puede tener, una es "buena" y la otra es "mala". Al ser únicas generalmente quieres tener esta carta tan rápido como sea posible para poderla jugar. Pero **¿Cual es la probabilidad de que pueda tener esta carta en mi primer turno?** ... Vamos a modelarlas – es el título de este blogpost...

Un mazo de Arkham, en el juego base, esta compuesto de 33 cartas:

- 20 cartas de clase
- 10 cartas genéricas
- 1 carta única de detective
- 1 weakness única
- 1 weakness básico

Al principio del juego se toman 5 cartas y si se toma una weakness se ignora y se toma otra carta. De modo que en ese momento la probabilidad de que saquemos la _carta única_ es de  5/31  y la probabilidad de no sacarla es de  (31-5)/31 = 26/31  Estas probabilidades complementarias son importantes porque en realidad vamos a modelar _la probabilidad de que al final de la primera ronda no tengas la carta core de tu detective._

Si a esta altura no tienes tu carta core, puedes hacer un _[mulligan,](https://en.wikipedia.org/wiki/Mulligan_(games)#Collectible_card_games)_ es decir, apartar tus cinco cartas y tomar otras cinco. Técnicamente lo puedes hacer con cualquier número de cartas en tu mano, pero como queremos tu core, harías mulligan de las cinco. Pero ya no estas tomando de las 31 cartas originales, si no de las 26 que dejaste. Entonces la probabilidad es  5/26  y su complemento  21/26

Una vez más no tienes tu carta core en la mano. Pero ya no puedes hacer mulligan, esta por empezar tu primer turno. Por lo cual todas las cartas que apartaste, las weaknesses y las cinco de tu mulligan anterior se revuelven de vuelta a tu mazo.

Ahora, en tu primer turno tienes tres acciones, las cuales vas a ocupar tomando cada vez una carta de tu mazo de, ahora, veintiocho cartas. La primera vez tienes una probabilidad de 1/28, la segunda 1/27 y la tercera 1/26 y sus respectivos complementos. ¿Por qué modelo cada una de estas cartas aparte? Porque cada una es una acción separada. En las ocasiones anteriores habíamos tomado las cartas en conjunto y no teníamos oportunidad de detenernos en caso de tomar la carta que necesitabamos.

Finalmente en la fase de _upkeep_ vas a tomar una última carta con probabilidad de éxito de 1/25

En total la probabilidad de que **termines la primera ronda sin tu carta core es:**

![Probabilidad de no tener tu core: 58.1%](/assets/2019-04-03/latex_probabilidad.png)

Y la probabilidad máxima de que termines la primera rónda con tu carta core es de 41.9% sin considerar efectos especiales.

Ahora... ¿qué sería la vida y de mi sin un poco de código? Vamos a corroborarlo programáticamente utilizando Python


```python
from random import shuffle

class ArkhamDeck:

    def __init__(self, core=1, player=30, weaknesses=2):
        self._deck = [True]*core + [None]*player + [False]*weaknesses
        self._shuffle()
        self._w = 0

    def draw(self, initial=False):
        drawed = self._deck.pop()
        if drawed == False and initial:
            self._w += 1
            self.draw(True)
        return drawed

    def mulligan(self):
        self._deck = self._deck + [False]*self._w
        self._shuffle()
        self._w = 0

    def _shuffle(self):
        shuffle(self._deck)
```


```python
def GotCore():
    ad = ArkhamDeck()
    for i in range(2):
        j = 0
        while j < 5:
            if ad.draw(True):
                return True
            j+=1
    else:
        ad.mulligan()
        j = 0
        while j < 4:
            if ad.draw():
                return True
            j+=1
    return False
```


```python
success = 0
tries = 1000000
for i in range(tries):
    success += GotCore()

print("Tried", tries)
print("Did not got core:", tries - success, "that is", (tries - success)/tries*100, "%")
print("Did got core:", success, "that is", success/tries*100, "%")
```

    Tried 1000000
    Did not got core: 578392 that is 57.839200000000005 %
    Did got core: 421608 that is 42.160799999999995 %


Que se aproxima bastante a nuestro resultado teórico!

## ¿Qué podemos concluir?

Que si quieres tener lo antes posible tu carta core en _Arkham Horror: The Card Game_ seguramente deberías hacer mulligan de toda tu mano y tomar tres acciones para tomar tres cartas en tu primer turno. Porque no vas a superar el 42% de probabilidad de conseguirla.
