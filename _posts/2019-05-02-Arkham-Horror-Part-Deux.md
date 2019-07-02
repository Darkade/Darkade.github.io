---
title: "Modelando las probabilidades en Arkham Horror: The Card Game"
layout: mathpost
---

![Part1](/assets/2019-05-02/part1.png)

> Esta es una contunación (y mejora) de mi post original de Arkham Horror

[Arkhan Horror: The Cardgame](https://www.fantasyflightgames.com/en/products/arkham-horror-the-card-game/) es un juego de cartas por Fantasy Flight Games en el universo de Cthulhu Mythos. En este juego los investigadores intentan detener a cultistas de invocar a sus oscuros amos desde otros planos para destruir la tierra; y siendo un juego de cartas, obviamente se ha convertido en mi nueva obsesión.

<!--more-->

En este juego cada jugador es uno de cinco detectives cada uno con una mazo de cartas diferente. Y cada uno con dos cartas que solo ese investigador puede tener, una es "buena" y la otra es "mala". Al ser únicas generalmente quieres tener esta carta tan rápido como sea posible para poderla jugar. Pero **¿Cual es la probabilidad de que pueda tener esta carta en mi primer turno?** ... Vamos a modelarlas – es el título de este blogpost...

## ¿Cual es la probabilidad de que tenga mi carta core al final de la primera ronda?

Un mazo de Arkham, en el juego base, esta compuesto de 33 cartas:

- 20 cartas de clase
- 10 cartas genéricas
- 1 carta única de detective
- 1 weakness única
- 1 weakness básico

Al principio del juego se toman 5 cartas y si se toma una weakness se ignora y se toma otra carta. De modo que en ese momento la probabilidad de que saquemos la _carta única_ es de $ 5/31 $ y la probabilidad de no sacarla es de $ (31-5)/31 = 26/31 $ Estas probabilidades complementarias son importantes porque en realidad vamos a modelar _la probabilidad de que al final de la primera ronda no tengas la carta core de tu detective._

Si a esta altura no tienes tu carta core, puedes hacer un [mulligan,](https://en.wikipedia.org/wiki/Mulligan_(games)#Collectible_card_games) es decir, apartar tus cinco cartas y tomar otras cinco. Técnicamente lo puedes hacer con cualquier número de cartas en tu mano, pero como queremos tu core, harías mulligan de las cinco. Pero ya no estas tomando de las 31 cartas originales, si no de las 26 que dejaste. Entonces la probabilidad es $ 5/26 $ y su complemento $ 21/26 $

Una vez más no tienes tu carta core en la mano. Pero ya no puedes hacer mulligan, esta por empezar tu primer turno. Por lo cual todas las cartas que apartaste, las weaknesses y las cinco de tu mulligan anterior se revuelven de vuelta a tu mazo.

Ahora, en tu primer turno tienes tres acciones, las cuales vas a ocupar tomando cada vez una carta de tu mazo de, ahora, veintiocho cartas. La primera vez tienes una probabilidad de $1/28$, la segunda $1/27$ y la tercera $1/26$ y sus respectivos complementos. ¿Por qué modelo cada una de estas cartas aparte? Porque cada una es una acción separada. En las ocasiones anteriores habíamos tomado las cartas en conjunto y no teníamos oportunidad de detenernos en caso de tomar la carta que necesitabamos.

Finalmente en la fase de _upkeep_ vas a tomar una última carta con probabilidad de éxito de $1/25$

En total la probabilidad de que **termines la primera ronda sin tu carta core es:**

{% raw %}
$$ {{26}\over{31}}\cdot{{21}\over{26}}\cdot{{27}\over{28}}\cdot{{26}\over{27}}\cdot{{25}\over{26}}\cdot{{24}\over{25}}\approx {0.58}
$$
{% endraw %}

Y la probabilidad máxima de que termines la primera rónda con tu carta core es de $41.9\%$ sin considerar efectos especiales.

Ahora... ¿qué sería la vida y de mi sin un poco de código? Vamos a corroborarlo programáticamente utilizando Python


```python
from random import shuffle

class Card:

    def __init__(self, name='', kind="event", core=False, desc=''):
        self.name = name
        self.kind = kind
        self.core = core
        self.desc = desc

    @property
    def kind(self):
        return self._kind

    @kind.setter
    def kind(self, kind):
        if not kind in ["event", "asset", "weakness", "skill"]:
            raise TypeError('Not an event, assset, weakness or skill')
        else:
           self._kind = kind

    @property
    def redraw_setup(self):
        return True if self.kind == "weakness" else False

    def __str__(self):
        return '{} ({})'.format(self.name, self.kind)

    def __repr__(self):
        return '"{}"'.format(self.name)
```


```python
class PlayerDeck:

    def __init__(self, deck=None):
        self.deck = deck
        self._shuffle()
        self._w = 0

    @property
    def deck(self):
        return self._deck

    @deck.setter
    def deck(self, deck):
        if deck == None:
            self._deck = [Card(core=True)]*1 + [Card()]*30 + [Card(kind="weakness")]*2
        else:
            self._deck = deck

    def draw(self, initial=False):
        drawed = self._deck.pop()
        if drawed.redraw_setup and initial:
            self._w += 1
            return self.draw(True)
        return drawed

    def mulligan(self, r=0):
        self._deck = self._deck + [Card(kind="weakness")]*self._w + [Card()]*r
        self._shuffle()
        self._w = 0

    def _shuffle(self):
        shuffle(self._deck)

```


```python
def GotCore():
    ad = PlayerDeck([
            Card(name='Forbidden Knowledge', kind='asset'),
            Card(name='Holy Rosary', kind='asset'),
            Card(name='Shrivelling', kind='asset', core=True),
            Card(name='Scrying', kind='asset'),
            Card(name='Arcane Studies', kind='asset'),
            Card(name='Arcane Initiate', kind='asset'),
            Card(name='Drawn to the Flame', kind='event'),
            Card(name='Ward of Protection', kind='event'),
            Card(name='Blinding Light', kind='event'),
            Card(name='Fearless', kind='skill'),
            Card(name='Leather Coat', kind='asset'),
            Card(name='Scavenging', kind='asset'),
            Card(name='Baseball Bat', kind='asset'),
            Card(name='Rabbit\'s Foot', kind='asset'),
            Card(name='Stray Cat', kind='asset'),
            Card(name='Dig Deep', kind='asset'),
            Card(name='Cunning Distraction', kind='event'),
            Card(name='Look what I found!', kind='event'),
            Card(name='Lucky!', kind='event'),
            Card(name='Survival Instinct', kind='skill'),
            Card(name='Heirloom of Hyperborea: Artifact from Another Life', kind='asset'),
            Card(name='Dark Memory', kind='weakness'),
            Card(name='Haunted', kind='weakness'),
            Card(), Card(), Card(), Card(), Card(), Card(), Card(), Card(), Card(), Card(),
        ])
    for i in range(2):
        j = 0
        while j < 5:
            c = ad.draw(True)
            if c.core:
                return True
            j+=1
    else:
        ad.mulligan(r=5)
        j = 0
        while j < 4:
            if ad.draw().core:
                return True
            j+=1
    return False

```


```python
success = 0
tries = 100000
for i in range(tries):
    success += GotCore()

print("Tried", tries)
print("Did not got core:", tries - success, "that is", (tries - success)/tries*100, "%")
print("Did got core:", success, "that is", success/tries*100, "%")

```

    Tried 100000
    Did not got core: 57899 that is 57.899 %
    Did got core: 42101 that is 42.101 %


Que es bastante cercano al resultado que obtuvimos con el modelo probabilistico

## En promedio ¿en qué ronda voy a obtener mi carta core?

![Part2](/assets/2019-05-02/part2.png)

Ahora estamos hablando de [valor esperado](http://mathworld.wolfram.com/ExpectationValue.html). Para una variable aleatoria discreta, este se define como:

$$
E(X)= \sum_{r}{x_r p^\ast_r}
$$

Aquí he escrito como $p^\ast_i$ algo que normalmente se denota sin la estrella. Para distinguirla de otra variable que vamos a usar después.

Esto es: la sumatoría de la probabilidad de cada evento multiplicada por el evento en si. Para un dado de seis caras (d6) sería

{% raw %}
$$
E(X) = 1{{1}\over{6}} + 2 {{1}\over{6}} + 3 {{1}\over{6}} + 4 {{1}\over{6}} + 5 {{1}\over{6}} + 6 {{1}\over{6}} = 3.5
$$
{% endraw %}

Esto quiere decir que, en promedio, nuestras tiradas de un d6 van a resultar en un $3.5$ El valor esperado de muchas variables aletorias es el la media (promedio) debido, en parte, a la [ley fuerte de los grandes números,](http://mathworld.wolfram.com/StrongLawofLargeNumbers.html) de la cual ya hemos hablado antes.

Para nuestro deck de arkham este valor esperado se calcularía de la siguiente manera. Primero vamos a suponer que seguimos la estrategía anterior, es decir, hicimos nuestro mulligan de 5 cartas, usamos nuestras primeras tres acciones para tomar tres cartas y tomamos nuestra carta de upkeep. También vamos a suponer que en todas las rondas subsecuentes solo tomamos nuestra carta de upkeep. Entonces:

Para cualquier ronda $r; r \ge 2$ tenemos que calcular dos probabilidades (1) la probabilidad de que saquemos la carta que queremos. A esta probabilidad le vamos a llamar $p_r$ (2) La probabilidad de que no hayamos sacado esa carta en las rondas anteriores (siendo un poco liberales con la notación) $\hat q_r$

La probabilidad **(1)** es muy fácil. Si $n_r$ es el número de cartas que quedan al principio de la ronda. la probabilidad de que saquemos nuestra carta core es

{% raw %}
$$
{{1}\over{n_r}}
$$
{% endraw %}

La forma de calcular **(2)** es un poco más elaborada.

$$
\hat q_r = \prod_{i=1}^{r-1} (1-p_i)_i
$$

Esa pi mayúscula significa producto, y toda la expresión quiere decir que vamos a multiplicar todas las probabilidades de que no hayamos sacado la carta core en cada ronda anterior. Por ejemplo, para $r=4$

{% raw %}
$$
\hat q_4 = \prod_{i=1}^{3} (1-p_i)_i= \left( 1-0.419 \right) \left( 1-{{1}\over{24}} \right) \left( 1-{{1}\over{23}} \right)
$$
{% endraw %}

Recordemos que $0.58$ es la probabilidad de que no tengamos nuestra carta core en la primera ronda de acuerdo a nuestro modelo anterior, y tenemos que para $r=1$

$$
p_1 \approx 0.419  \\
\hat q_1 = 1
$$

Vamos a utilizar $p_r$ y $\hat q_r$ para calcular $p^{\ast}_r$

$$
p^{\ast}_r = p_r \hat q_r
$$

Esto debido a que la probabilidad de que ocurra el evento $r$, es decir que en la ronda $r$ sea cuando tomamos nuestra carta core, es la probabilidad de que tomemos la carta ($p_r$) y no la hayamos tomado en las rondas anteriores a esta ($\hat q_r$). Las probabilidades se multiplican porque se trata de eventos independientes. ~~Pero este post se esta volviendo un poco más complicado de lo que esperaba entonces no voy a explicar independencia... aunque debería.~~

Finalmente, nuestro valor esperado se calcularía como:

$$
E(x) = \sum_{r}{r p_r \hat q_r }
$$

Y en forma de bonita tabla:

$r$|$n_r$|$p$|${1-p}$|$\hat q_r$|$r p \hat q_r$
-----|-----|-----|-----|-----|-----
1|33|0.419|0.581|1.0000|0.4194
2|24|0.042|0.958|0.5806|0.0484
3|23|0.043|0.957|0.5565|0.0726
4|22|0.045|0.955|0.5323|0.0968
5|21|0.048|0.952|0.5081|0.1210
6|20|0.050|0.950|0.4839|0.1452
7|19|0.053|0.947|0.4597|0.1694
8|18|0.056|0.944|0.4355|0.1935
9|17|0.059|0.941|0.4113|0.2177
10|16|0.063|0.938|0.3871|0.2419
11|15|0.067|0.933|0.3629|0.2661
12|14|0.071|0.929|0.3387|0.2903
13|13|0.077|0.923|0.3145|0.3145
14|12|0.083|0.917|0.2903|0.3387
15|11|0.091|0.909|0.2661|0.3629
16|10|0.100|0.900|0.2419|0.3871
17|9|0.111|0.889|0.2177|0.4113
18|8|0.125|0.875|0.1935|0.4355
19|7|0.143|0.857|0.1694|0.4597
20|6|0.167|0.833|0.1452|0.4839
21|5|0.200|0.800|0.1210|0.5081
22|4|0.250|0.750|0.0968|0.5323
23|3|0.333|0.667|0.0726|0.5565
24|2|0.500|0.500|0.0484|0.5806
25|1|1.000|0.000|0.0242|0.6048

$$
\sum_{r}{rp\hat q_r} \approx 8.2581
$$

De modo que, en promedio, **vamos a tomar nuestra carta core en la ronda 8.25**

Una vez más, programaticamente


```python
def RoundCore():
    R = 1
    ad = PlayerDeck([
            Card(name='Forbidden Knowledge', kind='asset'),
            Card(name='Holy Rosary', kind='asset'),
            Card(name='Shrivelling', kind='asset', core=True),
            Card(name='Scrying', kind='asset'),
            Card(name='Arcane Studies', kind='asset'),
            Card(name='Arcane Initiate', kind='asset'),
            Card(name='Drawn to the Flame', kind='event'),
            Card(name='Ward of Protection', kind='event'),
            Card(name='Blinding Light', kind='event'),
            Card(name='Fearless', kind='skill'),
            Card(name='Leather Coat', kind='asset'),
            Card(name='Scavenging', kind='asset'),
            Card(name='Baseball Bat', kind='asset'),
            Card(name='Rabbit\'s Foot', kind='asset'),
            Card(name='Stray Cat', kind='asset'),
            Card(name='Dig Deep', kind='asset'),
            Card(name='Cunning Distraction', kind='event'),
            Card(name='Look what I found!', kind='event'),
            Card(name='Lucky!', kind='event'),
            Card(name='Survival Instinct', kind='skill'),
            Card(name='Heirloom of Hyperborea: Artifact from Another Life', kind='asset'),
            Card(name='Dark Memory', kind='weakness'),
            Card(name='Haunted', kind='weakness'),
            Card(), Card(), Card(), Card(), Card(), Card(), Card(), Card(), Card(), Card(),
        ])
    for i in range(2):
        j = 0
        while j < 5:
            if ad.draw(initial=True).core:
                return R
            j+=1
    else:
        ad.mulligan(r=5)
        j = 0
        while j < 4:
            if ad.draw().core:
                return R
            j+=1

    while True:
        R += 1
        c = ad.draw()
        if c.core:
            return R
```


```python
rounds = 0
tries = 100000
for i in range(tries):
    rounds += RoundCore()

print("In avarage, the core card was drawed in the round:", rounds / tries)
```

    In avarage, the core card was drawed in the round: 8.26042


Que una vez más es bastante cercano a nuestro modelo

## ¿Qué valor de skill necesito para pasar un skill check?

![Part3](/assets/2019-05-02/part3.png)

La otra parte importante de Arkham es que haces _skill checks._ Hacer un _skill check_ implica tomar un token de la _chaos bag_ y sumar o restar su valor del skill value del personaje. Si se iguala o supera el valor objetivo se pasa el check.

Todos los personajes tienen 4 skills: Willpower, intellect, combat and agility. Entre más alto es el valor mejor es el personaje haciendo una acción.

La _chaos bag_ tiene diferentes tokens dependiendo del escenario y la dificultad. Y sus efectos pueden variar por lo mismo.

Por ejemplo, para combatir a un enemigo puede ser necesario pasar un _skill check_ de **4 combat** con un personaje que tiene **combat 3** como skill. Entonces se toma un **+1** de la _chaos bag_ subiendo el combat del personaje a 4, igulando el valor objetivo y pasando el check.

---

Para _Night of The Zealot_ la chaos bag se ve así:

- Easy Difficulty:
 - +1, +1, 0, 0, 0, -1, -1, -1, -2, -2, skull, skull, cultist, stone, tentacle, elder-sign
- Standard Difficulty:
 - +1, 0, 0, -1, -1, -1, -2, -2, -3, -4, skull, skull, cultist, stone, tentacle, elder-sign
- Hard Difficulty:
 - 0, 0, 0, -1, -1, -2, -2, -3, -3, -4, -5, skull, skull, cultist, stone, tentacle, elder-sign
- Expert Difficulty:
 - 0, -1, -1, -2, -2, -3, -3, -4, -4, -5, -6, -8, skull, skull, cultist, stone, tentacle, elder-sign

Los _tentacles_ son fallos automáticos y los _elder-signs_ hacen el personaje utilice su habilidad especial. Los skulls, cultists y stones son específicos a cada escenario.

Los modificadores de escenario son:

### The Gathering
#### Easy/Standard
- Skull: -X. X is the number of Ghoul enemies at your location.
- Cultist: -1. If you fail, take 1 horror.
- Stone: -2. If there is a Ghoul enemy at your location, take 1 damage.

#### Hard/Expert

- Skull: -2. If you fail, after this skill test, search the encounter deck and discard pile for a Ghoul enemy, and draw it. Shuffle the encounter deck.
- Cultist: Reveal another token. If you fail, take 2 horror.
- Stone: -4. If there is a Ghoul enemy at your location, take 1 damage and 1 horror.

### The Midnight Masks
#### Easy/Standard
- Skull: -X. X is the highest number of doom on a Cultist enemy in play.
- Cultist: -2 Place 1 doom on the nearest Cultist enemy.
- Stone: -3. If you fail, place 1 of your clues on your location.

#### Hard/Expert

- Skull: -X. X is the total number of doom in play.
- Cultist: -2. Place 1 doom on each Cultist enemy in play. If there are no Cultist enemies in play, reveal another token.
- Stone: -4. If you fail, place all your clues on your location.

### The Devourer Below
Durante este escenario se agrega un Calamar\[?\] al _Chaos Bag_ ~~no se si es un calamar.~~

#### Easy/Standard

- Skull: -X. X is the number of Monster enemies in play.
- Cultist: -2. Place 1 doom on the nearest enemy.
- Stone: -3 If there is a Monster enemy at your location, take 1 damage.
- Calamar: -5. If there is an Ancient One enemy in play, reveal another token.

#### Hard/Expert

- Skull: -3. If you fail, after this skill test, search the encounter deck and discard pile for a Monster enemy, and draw it. Shuffle the encounter deck.
- Cultist: -4. Place 2 doom on the nearest enemy.
- Stone: -5. If there is a Monster enemy at your location, take 1 damage and 1 horror.
- Calamar: -7. If there is an Ancient One enemy in play, reveal another token.

---

Lo que sigue son estimaciones porque es dificil modelar cuantos enemigos hay en juego. Lo importante de un _skill check_ es la diferencia entre el personaje y valor objetivo; por ejemplo **3 personaje - 4 objetivo = -1 diferencia**


Pero para The Gathering, con un enemigo en juego, en _easy_ si igualamos el valor objetivo tenemos un $37.50\%$ de probabilidad de pasar el check. Porque la bolsa efectivamente tiene:

$$
B = \{ 1, 1, 0, 0, 0, 0, -1, -1, -1, -1, -1, -1, -2, -2, -2, -100 \}
$$


Es un conjunto de 16 elementos de los cuales 6 son iguales o mayores que cero. Luego:

{% raw %}
$$
{{|\{x \in B : x \ge 0 \}|}\over{|B|}} = 0.357
$$
{% endraw %}

Realmente no hay muchas razones para hacer esto programáticamente pero si dejé un [Google Drive disponible](https://docs.google.com/spreadsheets/d/1TP8EczLHfiHUHYhk33vrgsGJ_n6C_yDpcPambtrD8iU/edit?usp=sharing) y tengo algunas notas que compartir.

---

Algunos tokens indican sacar otro token. Esto realmente no afecta las probabilidades del resto del chaos bag, es decir, si tenemos 16 tokens normales y 2 que jalan un siguiente token, la probabilidad de sacar un token específico sigue siendo $1/16$

Hay algunos tokens que simplemente agregan dificultad agregando daño u horror. Para The Gathering en easy/standard cada vez que haces un _skill check_ tomas en promedio 1/16 de horror.

Skids, Agnes y Roland tienen una muy ligera ventaja cuando no alcanzan los valores objetivo, debido a que pueden agregar valor al skill cuando sale un _elder sign._ En the Gathering (easy/expert) Daisy tiene probabilidad de $0\%$ de pasar un check si esta uno por debajo del valor objetivo, pero Skids tiene $6.25\%$. Si iguala o supera el valor objetivo ambos tienen la misma probabilidad. Para la estrategia que yo juego esto no es muy útil, y contar con ello es contar en algo que va a pasar solo una de cada dieciseis veces, pero esta bien tenerlo en cuenta.

---

Finalmente. Para los 3 escenarios y las 4 dificultades, esto es por cuando deberías de superar el valor objetivo para tener un 50% de probabilidad de tener éxito en un _skill check_ (Con uno enemigo en juego en todos los casos)

#### The Gathering

| Difficulty | Superar por | Probabilidad de éxito |
|------------|-------------|-----------------------|
| Easy | 1 | 75.00% |
| Standard | 1 | 62.50% |
| Hard | 2 | 62.50% |
| Expert | 3 | 58.82% |

#### The Midnight Masks

| Difficulty | Superar por | Probabilidad de éxito |
|------------|-------------|-----------------------|
| Easy | 1 | 52.94% |
| Standard | 2 | 70.59% |
| Hard | 3 | 66.67% |
| Expert | 3 | 52.63% |

#### The Devourer Below

| Difficulty | Superar por | Probabilidad de éxito |
|------------|-------------|-----------------------|
| Easy | 1 | 68.75% |
| Standard | 1 | 56.25% |
| Hard | 2 | 52.94% |
| Expert | 3 | 50.00% |
