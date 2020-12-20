---
layout: post
title: Así jugamos DnD online por primera vez en años
image: /assets/2020-04-05/dnd.jpg
description: Cuarentena, juegos de rol, convivencia, whatever. Hoy, mis amigos y yo, jugamos DnD online por primera vez en años y así es como lo hicimos.
---

![DnD][dnd]

Cuarentena, juegos de rol, convivencia, whatever. Hoy, mis amigos y yo, jugamos DnD online por primera vez en años y así es como lo hicimos.

<!--more-->

No creo tener que explicar por deberías o no jugar Dungeons & Dragons, si te llama la atención deberías jugarlo. Si no tuviste una buena experiencia prueba con un grupo diferente, pero dale un par de oportunidades; aunque D&D no es mi juego de rol favorito, si ha servido para introducir al hobby a miles de personas, algo esta haciendo bien.

### Qué usamos y cómo lo hicimos

Usamos [Discord](https://discordapp.com), Excel, [DnD Beyond](https://dndbeyond.com/) y [Avrae](https://avrae.io/) todo es gratis ~~excepto excel pero hablo de eso en un momento~~ y fácil de usar.

#### Discord

[Discord](https://discordapp.com) es un app de chat enfocada principalmente en gaming. La utilizamos para:

1. Tener un canal de voz dónde la gente puede entrar y salir cuando quiera
2. Tirar dados utilizando un _dicebot,_ en nuestro caso Avrae
3. Que el _Dungeon Master_ nos compartiera su pantalla
4. Compartir imágenes y cosas que nos ayudaran a contextualizar la partida.

![Nuestros Canales de Discord][discord]

Te recomiendo tener un canal para las cosas generales de la partida `#rol` y uno para tu _dicebot_ `#tirar_dados`.

### Excel

Excel no es gratis, pero seguramente lo tienes. Si no lo tienes baja [LibreOffice](https://www.libreoffice.org). Pero realmente creo que deberías usar [Google Sheets.](https://sheets.google.com) En nuestra partida el _DM_ nos compartió desde su pantalla una hoja de Excel con el mapa, nuestros nombres y los enemigos.

Hay herramientas muy avanzadas para hacer esto, como [Roll20](https://roll20.net/), [Fantasy Grounds](https://www.fantasygrounds.com/home/home.php) o [Astral](https://astraltabletop.com/). Todas son muy buenas pero: toma tiempo aprender a usarlas, requieren que el _DM_ pase tiempo preparando la sesión, y las versiones gratuitas tienen limitaciones.

![Nuestro mapa usando Google Sheets][sheets]

Usar Excel fue muy útil porque pudimos improvisar el mapa muy rápido, hay un grid y puedes asignarles colores especiales a las cosas. Te recomiendo usar Google Sheets porque todos pueden entrar y mover su propio personaje en vez de que haya una sola persona haciéndolo, pero supongo que es cosa de estilos y de cada grupo. Por ejemplo, en nuestro grupo no hacía sentido usar Sheets porque varios jugadores estaban desde sus teléfonos.

### DnD Beyond

Utilizamos [DnD Beyond](https://dndbeyond.com/) para crear nuestros personajes. Si, tomó 1.5~2 hrs hacer personajes... para los cinco jugadores, es lo más rápido que hemos hecho personajes en toda la historia. DnD Beyond es muy útil porque te muestra solo la información que necesitas ver para tu clase o raza y, paso por paso, terminas con un personaje exactamente a tu medida.

![Kynan: mi personaje para esta partida][kynan]

Si solo vas a utilizar las cosas de las [reglas básicas](https://www.dndbeyond.com/sources/basic-rules) no tienes que comprar ni pagar nada en DnD Beyond. El PDF de las reglas básicas de D&D esta disponible de forma [gratuita en el sitio de Wizards of the Coast](https://dnd.wizards.com/articles/features/basicrules). De modo que nadie tiene que gastar dinero si solo quieren probar el juego.

### Avrae

Es el _discordbot_ oficial de DnD Beyond y 50% de la razón por la cual creo que la partida fue tan fácil de llevar. [Avrae](https://avrae.io/) te permite importar tu personaje desde DnD Beyond, lleva seguimiento de las iniciativas y te permite hacer todas tus tiradas de forma semi-automática.

Esto significa que si alguien nunca ha jugado y el master dice
> Has un check de Acrobatics

El jugador solo tiene que escribir

> !check acrobatics

Y Avrae se va a encargar de hacer la tirada y decir cómo la hizo.

![Así se ven las iniciativas y algunas tiradas hechas con Avrae][avrae]

Tenía muchas dudas sobre el bot pero hace muchas más cosas de lo que esperaba y funciona de forma excelente. Si te preocupa que tus jugadores no aprendan a hacer sus tiradas... la verdad es algo que no te debería de preocupar. Piensa que Avrae te va a permitir invitar a tus amigos que solo quieren probar el juego sin abrumarlos con las mecánicas de las tiradas; y para tus amigos hardcore y try hard, el bot de todos modos dice cómo se hizo la tirada, entonces van a aprender.

Esta es una pequeña guía que hice de tiradas y comandos:

> _**Comandos de Avae**_
>
> **Para el DM**
>
> `!init begin` – Inicia combate  
> `!init end` – termina combate  
> `!init madd <nombre de mounstruo> -n 3 -name Arquero#` – Agrega 3 arqueros, llamados "Arquero1, Arquero2,Arquero3" Las mayúsculas y minúsculas si importan  
> `!init attack slam -t Kynan` – Hace un ataque de slam para el monstruo del cual es el turno  
> `!init attack list` – le manda como direct message los ataques del monstruo actual al DM  
>
> **Para los jugadores**
>
> `!init join` cuando empezó combate así tiran sus iniciativas  
> `!init attack dagger -t Arquero3` – Ataca al Arquero3, las mayusculas y minúsculas si importan  
> `!init attack dagger -t Arquero3 Arquero2` – Hace un ataque a ambos arqueros
>
> **Common Commands**
>
> `!init hp Kynan 1d4 + 1` – Helea a Kynan 1d4 +1  
> `!init next` – para marcar que terminaron su turno  
> `!init effect "Kim Donjuan" Grappled` – le agrega Grappled a Kim  
> `!init re "Kim Donjuan" Grappled` – Le quita grappled
>
> **Ejemplo complejo**
>
> `!init attack adv -d 4d6 -t Arquero3` – Hace un ataque con una daga, com 4d6 de bono de daño al Arquero3

Y aquí esta una [guía oficial](https://avrae.readthedocs.io/en/latest/aliasing/aliasing.html) y la [referencia de comandos](https://avrae.io/commands) de Avrae. Es muy fácil de aprender a usar el bot, después de la mitad de la partida todos estaban tirando sin que surgieran ~~muchas~~ dudas.

---

Y eso es todo. Es raro de decir pero, honestamente, no ha habido mejor momento para probar Dungeons & Dragons y que requiriera de tan poca inversión por parte de todos los involucrados. Solo recuerden siempre agradecerle su tiempo y esfuerzo a su Dungeon Master.

Muchas gracias por leer. En caso de que quieras leer más sobre RPGs recientemente empecé una serie de [reviews de Ironsworn]({% post_url 2020-04-01-Ironsworn-pt1 %})


[dnd]: {{ page.image }}
[discord]: /assets/2020-04-05/discord.png
[sheets]: /assets/2020-04-05/sheets.png
[kynan]: /assets/2020-04-05/kynan.png
[avrae]: /assets/2020-04-05/avrae.png
