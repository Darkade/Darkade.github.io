---
layout: post
permalink: /:year/:month/:day/:title:output_ext
locale: en_GB
title: "How to run a Zelda style dungeon"
image:
  path: /assets/2021-02-13/jordan-grider-M6e-9wzHto8-unsplash.jpg
  width: 1920
  height: 2567
description: "We previously made a Zelda style dungeon map and now it's time to run it. Don't let yourself be intimidated by it, here's a couple things to keep in mind."
---

<!--INTRO-->

Zelda Dungeons are the gold standard to me. In a previous post I showed you how to design a dungeon in the style of those games. Here's some advice on how to run that dungeon!

![An Opera House][postcover]

<!--more-->

_Cover photo by [Jordan Grider]_

<!--ABSTRACT-->
If you haven't read the previous post you can do so [here][Running the dungeon]. There I covered how to go from a randomly generated map to an edited map and a graph method on how to layout the things that go in the dungeon. Again, I recommend checking the [Boss Keys] series by [Mark Brown].


## Avoid corridor fights
They almost always turn into wars of attrition, long and boring. If you do find yourself running a corridor fight suddenly there could be a _pit trap._ Both the characters and the enemies fall into a pool of water (to reduce damage) now they are fighting in an open space and later they can climb back up.

## Somebody else might be here
If theres a door the characters aren't opening most times somebody can open it from the other side. This person could be an ally or an enemy who has their own reasons to be in the dungeon, were they expecting the party? how long have they been down here? How did they got in?

This is another reason to have two entrances/exits, it justifies having people coming from elsewhere.

## Use shapes and colors

A door could be shaped like a Blue Hexagon, and the lever that opens it is blue and it's framed by an hexagonal tile. This is meant to make things clear to the players. If when you pull the blue lever there's a loud mechanical sound elsewhere in the dungeon it's clear that it came from the blue door. Zelda, dungeons sometimes have arrows!

Just keep in mind that players forget colors immediately, that's where shapes come in. Maybe the first door is a rectangle, second a pentagon, third hexagon, octagon... make it colorful and sequential.

## Puzzles are breakable

A difference between Zelda and TTRPGs is that in the former you can't blow up doors, while in the latter it feels like a cheat when you can't blow doors up.

If the characters attempt to destroy or bypass a puzzle that's fine, remember that players will engage with this content in the way they find most entertaining for themselves. Be ready for this and don't take it personally, the story is going where it wants to go.

When that happens think if the puzzle should backfire. Maybe all the doors open at the same time but there are enemies behind all of them. Just don't make it vengeful. Traps and puzzles don't backfire because the players don't engage with them in the intended way, they backfire because the characters get an staff stuck in the machine and now it's about to explode.

## Make the map a map

Treat this map as a map, that is to say **an abstraction of the dungeon.** Maybe the characters find it inside the dungeon, or maybe they find it elsewhere and that's why they are coming here. In any case this opens the possibility to have secret rooms or other content that you add in the heat of the moment.

Another reason not to use this as a tactical map is that it's large! You'll probably want to have fog of war and managing it on a large map get's harder. A final reason is that players will just move to the next room when the PCs are not in combat, they don't require a grid to navigate.

If you do need a tactical map, make it. Maybe there's a boss room that you'd like to show a lot of detail. For this I recommend [DungeonDraft] it's a very capable tool, you can follow [@TheAbeilQueen] to see some cool examples.

---

<!--OUTRO-->

If you liked this post and want to support me check out [Arcane Moon], a D&D adventure inspired by 90s Magical Girl anime, published at DMs Guild. Or download for free my Fiasco Classic Adventure [Busca Un Problema] at Itch.io!

You can also read [The Dwendalian War Inciting Incident] the encounter that started the war in my Exandria campaign. And you should read the other part of this same article on [How to make a Zelda Style Dungeon.][Zelda Style Dungeons]

Finally you can follow me [@darkade]! Thanks for reading!

<!--Internal-Links-->
[The Dwendalian War Inciting Incident]: {% post_url EN/2020-12-29-inciting-incident %}
[Zelda Style Dungeons]: {% post_url EN/2021-02-13-zelda-dungeon %}
[Running the dungeon]: {% post_url EN/2021-02-13-dungeon-advice %}

<!--Self Promo-->
[@darkade]: https://dice.camp/@darkade
[#WarlockPixieland]: https://twitter.com/search?q=(%23warlockpixieland)&f=live
[Arcane Moon]: https://bit.ly/ArcaneMoon
[Busca Un Problema]: https://bit.ly/BuscaUnProblema
<!--Images-->

[postcover]: {{ page.image.path }}
[randommap]: /assets/2021-02-13/DunGen_42250252_original_small.jpg
[room_boss]: /assets/2021-02-13/room_boss.jpg
[room_central]: /assets/2021-02-13/room_central.jpg
[room_trap]: /assets/2021-02-13/room_trap.jpg
[room_treasure]: /assets/2021-02-13/room_treasure.jpg

[notation_exit]: /assets/2021-02-13/notation_exit.png
[notation_entrance]: /assets/2021-02-13/notation_entrance.png
[notation_lock]: /assets/2021-02-13/notation_lock.png
[notation_rat_lock]: /assets/2021-02-13/notation_rat_lock.png
[notation_key]: /assets/2021-02-13/notation_key.png
[notation_trap]: /assets/2021-02-13/notation_trap.png
[notation_treasure]: /assets/2021-02-13/notation_treasure.png
[notation_boss]: /assets/2021-02-13/notation_boss.png

[graph01]: /assets/2021-02-13/dungeon_graph_01.jpg
[graph02]: /assets/2021-02-13/dungeon_graph_02.jpg
[graph03]: /assets/2021-02-13/dungeon_graph_03.jpg
[final_map]: /assets/2021-02-13/final_map.png
[final_map_annotated]: /assets/2021-02-13/final_map_annotated.jpg

<!--Credits-->

[Jordan Grider]: https://unsplash.com/@jordangrider

<!--External-Links-->
[Boss Keys]: https://www.youtube.com/watch?v=ouO1R6vFDBo&list=PLc38fcMFcV_ul4D6OChdWhsNsYY3NA5B2
[justification]: https://twitter.com/MortPhilippa/status/1344357808649756674
[Mark Brown]: https://twitter.com/gamemakerstk
[DunGen]: https://dungen.app/dungen/
[master_the_dungeon]: https://www.youtube.com/channel/UCrPmuq5_AJ_DvZ9OXQrFEFw
[Dungeon Scrawl]: https://probabletrain.itch.io/dungeon-scrawl
[Episode 7: The Minish Cap]: https://youtu.be/KEVJXqV7XMc
[DungeonDraft]: https://dungeondraft.net/
[@TheAbeilQueen]: https://twitter.com/TheAbeilQueen
