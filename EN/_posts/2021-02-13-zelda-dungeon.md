---
layout: post
permalink: /:year/:month/:day/:title:output_ext
locale: en_GB
title: "How to make a Zelda style dungeon for TTRPGs"
image:
  path: /assets/2021-02-13/jordan-grider-lLP7s9Rpw7E-unsplash.jpg
  width: 1920
  height: 1436
description: "Dungeons! Probably the best ones come from The Legend of Zelda. How can we apply that knowledge to RPGs, specially D&D?"
---

<!--INTRO-->

Dungeons! ... can become a boring railroad, but they don't have to. Personally whenever I think of dungeons I don't actually think of TTRPGs, I think of The Legend of Zelda. Stone Tower, Water Temple, Fortress of Winds, Tower of the Gods... the list goes on. Is there a secret to a Zelda dungeon? Can we reverse engineer a Zelda style dungeon into our TTRPGs?

![A catacomb picture][postcover]

<!--more-->

_Cover photo by [Jordan Grider]_

<!--ABSTRACT-->
This article builds upon the research from the excellent [Boss Keys] series by [Mark Brown]. In this series Mark studied what makes a Zelda dungeon a _**Zelda Dungeon,**_ distilling it down to a very interesting graph language. Those graphs are the heart of the dungeon we will make together in this article. I fully recommend watching the series even if the graph system is not fully developed until episode 7; or at the very least check [Episode 7: The Minish Cap].

--------

I will break down the process in steps. We'll start with a randomly generated dungeon and end with a custom edit of the same with an understanding of how the characters will move trough it. And we'll make a lot of graphing in between. You can also read my advice on [Running the dungeon].

## A Random Dungeon

If we are making a new dungeon why are we starting with a random one? Well, starting from scratch is very hard and, trying to [justify] the layout, that is, coming up with reasons why this dungeon is the way it is, can be very fulfilling. Just looking at a map will spark ideas.

For this I use [DunGen]: it has several tile sets, you can download maps indifferent resolutions and it has a lot options including some interesting room shapes.

![Random map generated with dungen.app][randommap]
_You can generate this dungeon using the seed `42250252` at [DunGen]_

Some recommendations to generate a dungeon:
- Avoid long corridors, they aren't interesting and take a lot of map space.
- It's better to go small than to go big. Four or five rooms are probably enough to fill a session; and you can always add another level if needed.
- Keep in mind not every room will make it to the final map. So, if there's a zone that's not interesting but the rest is, remove it during the edits.

All of these things can be fixed later, but it's easier if you start with something interesting.

## Decide on important rooms

![Boss room][room_boss]{: .room} ![Central room][room_central]{: .room} ![Trap room][room_trap]{: .room} ![Treasure room][room_treasure]{: .room}
{: .rooms}

- Large room on the left, boss room?
- Room on the centre, bifurcations are an easy way to have backtracking
- Slanted room is saying "trap"
- Room on the right, could hold a `treasure` or a `key`

I already know some of these rooms are not making it in the same form to the final map. For example, a central room is usually a very open space with an interesting shape, so it will be edited to reflect that.

Finally I know the entrance is on the top and I'm undecided if there should be another entrance/exit

## Setup locks and graph it!

First. What is a lock? A lock is not only a closed door that can be picked. Going back to Zelda a lock takes the form of an inaccessible tall platform, a frozen door that requires fire arrows, an elevetor that needs to be turned on. All of these are **locks** and most of them bring more flexibility and engagement than a door.

It's not that locked doors are bad, it's that in TTRPGs they are delays rather than obstacles, since, often, they can be picked. Of course there's a time and a place to use locked doors, for example, they lend well to linear dungeons; and they are the most reasonable option for city buildings.

Another type of lock is a `One-way lock`. It's open on the way in, but closes behind the characters. This can even take the form of a pit from where the characters fall and then need to find a way out.

![Anotated dungeon][graph01]
_Dungeon with markers of where locks are located_

When choosing where to place locks I try to get a feeling for how the characters will go trough the dungeon. For example, if you need to pass a `one-way lock` to get to the `slanted H` then whatever is used to open the one-way lock has to be found in or after the `H`.

### The Graphs

The only way of familiarizing with the graphs is familiarizing with the graphs, so we'll jump right in.

For this dungeon I came up with the following _ideal path_. Keep in mind this is just _the flow_ of the dungeon. Details, how traps will work, treasure or even what kind of locks and keys are found here I'll leave for later ~~but I'm taking notes as I go~~. Right now I'm focusing making the dungeon worth exploring.

<div class="dungeon">
![Dungeon graph][graph02]

![Overlaid Dungeon][graph03]

_The abstracted dungeon flow_

_Graph overlaid on the dungeon_
</div>

These are the steps I expect the characters to take.

0. After entering the dungeon the PCs find:
  - locked `purple B`
  - locked `blue T`
  - open `orange one-way lock` characters are expected to enter here.
1. Crossing `orange one-way lock` they find:
  - trap room. I think the trap will be related with the doors here, but I'm not sure how yet
  - open door
  - locked `magenta Y`
  - locked `yellow z`
2. Behind the open door there's:
  - `blue Z key`
  - `yellow Z key` so the characters can go out and open `yellow Z lock`. They can't go back and open the `blue T` because of the `one-way lock`
3. Opening `yellow Z`:
  - `orange X key`
  - `mangenta Y key`. Now PCs can open `magenta Y` and `one-way lock`. However, I think, if they go trough the `one-way lock` and back in the trap will re-arm itself.
4. Opening `magenta Y lock`:
  - treasure hoard
  - disarming mechanism to `one-way lock`
  - `purple B key`
5. Locks `purple B` and `blue T`
    1. If the characters open `blue T` before the boss room they find another treasure hoard, maybe a weapons rack, and an exit. So they could bail right now.
    2. Thematically `purple B lock` and `purple B key` should be significant, they should be a Boss Door and a Boss Key.

### Using the graphs

There's a reason the graph has vertical lines, horizontal levels and many different icons.

Icons represent very specific points of interaction between the dungeon features and the characters; that's pulling, picking, pushing, etc. A corridor or an empty room does not require interaction, so they are not represented by icons.

Vertical lines mean things that need to be made in sequence one after the other. Lines without icons in the middle mean things that the characters can find at the same stage, but not necessarily interact with it. For example, after you enter the dungeon you'll see both `blue T lock` and `orange one-way lock` but you'll have to go and deal with other things before opening `blue T`.

Many parallel vertical lines mean there's a lot of backtracking in the dungeon.

Height level indicates the order in which something **can** be interacted with. The higher something is the earlier you can interact with. That's why keys are always higher in the graph than their respective locks. This also means if two things are at the same height they can be done in any order respective of each other.

![Dungeon graph][graph02]
_Full dungeon graph_

Vertical lines and height combined mean that the higher and the further right something is the easier it is to "solve" it. You can, almost, walk straight to `yellow Z key` but getting to the secondary exit will take some time.

Linear dungeons tend to have taller graphs. Dungeons with many optional content tend to have wider graphs. These parameters are not always related with architectural complexity. A clear example would be a garden maze: it only has a Entrance and Exit, and no other features to interact with, so it's graph would be two icons on a straight line.

Making this kind of diagram gives you a very clear idea of the complexity of the dungeon, it will also show the importance of rooms by focusing the backtracking points, ig, the points the lines branch out.

Most Zelda dungeons have a central room that you'll go back at least a few times, this gives players a good feeling of how a dungeon is laid out and reinforces the room's importance.

## Make it nice

Right now we have both a map and a way to turn it into a dungeon. However some of the map's rooms don't quite work, it's time for edits. I use [Dungeon Scrawl], it's a bit intimidating but I think the results speak for themselves.

![Final version of the dungeon map][final_map]
_Map's final version. I prefer to think of it as an in-universe map. Not a tactical map_

As far as edits go I personally prefer wider than taller maps. I also reorient many rooms and change the shape of important ones. In this case the central room is hexagonal and the boss room is directly facing that central room.

I don't really add furniture or other such things, these kind of maps don't make up for good tactical use. They are **Zelda dungeon maps,** the ones that display on the corner. They are meant to help characters navigate the dungeon. In combat most rooms can be run with theatre of the mind or an specific tactical map made for that purpose.

This being the case the map doesn't even has to be "accurate". Maybe that is a false wall and there's a secret room, maybe that corridor has collapsed and the map is outdated. There are many possibilities when we use maps as pure abstractions.

_If you are interested in this idea I made a whole [different blog post][Running the dungeon] with advice on running a dungeon in this style._

---

Before we go here's the full graph notation and the final version of the annotated map. Always a good idea to keep it on hand.

![Final version of the annotated map][final_map_annotated]
_The final annotated version of the map_

- ![Graph notation entrance][notation_entrance]{: .notation_icon} **Entrance:** the characters enter the dungeon trough here. This area should immediately present the "theme" of the dungeon.
- ![Graph notation exit][notation_exit]{: .notation_icon} **Exit:** an alternative entrance/exit. This is useful in case the characters get trapped (which is always an option) or if they want to bail with what they have and avoid the boss.
- ![Graph notation boss][notation_boss]{: .notation_icon} **Boss:** the boss should always be able to leave this room if it makes sense. A dragon might not but a bandit commander for sure.
- ![Graph notation lock][notation_lock]{: .notation_icon} **Lock:** when graphing think of it as the limit of an inaccessible area. Of course, in play, this can always change, and it often will if the players have the skills.
- ![Graph notation rat_lock][notation_rat_lock]{: .notation_icon} **one-way lock:** use this kind of lock whenever you want to restrict backtracking. Ideally it locks when characters are too far to do anything about it.
- ![Graph notation key][notation_key]{: .notation_icon} **Key:** literal keys, levers, items, pressure plates. All the things that open the next section in the dungeon.
- ![Graph notation trap][notation_trap]{: .notation_icon} **Trap:** traps are varied beyond the scope of this very long post, but consider if they are lethal, troublesome or delays. I recommend checking [Master The Dungeon's YouTube channel][master_the_dungeon] for some cool traps (and their take on the Zelda Dungeon as well)
- ![Graph notation treasure][notation_treasure]{: .notation_icon} **Treasure:** not all treasure belongs in the map, but hoards or particular items are worth taking note.
{: .list}

---

<!--OUTRO-->

If you'd liked this post and want to support me check out [Arcane Moon], a D&D adventure inspired by 90s Magical Girl anime, published at DMs Guild. Or download for free my Fiasco Classic Adventure [Busca Un Problema] at Itch.io!

You can also read [The Dwendalian War Inciting Incident] the encounter that started the war in my Wildemount campaign. And you should read the other part of this same article on [Advice to running a dungeon.][Running the dungeon]

Finally you can follow me [@darkade]! Thanks for reading!
<!--Custom CSS-->
<style>
.rooms {
    text-align: center;
    border-radius: 10%;
}

.room {
    display: inline;
    max-width: 20%;
    border-radius: 20px;
    height: 150px;
}

.notation_icon {
  display: inline;
  height: 1.5rem;
  vertical-align: bottom;
}

.list li {
  margin-top: 0.25rem;
}

.dungeon {
  display: grid !important;
  grid-template-columns: 1fr 1fr;
  align-items: end;
  cursor: zoom-in;
  margin-top: 1rem;
  margin-bottom: 1rem;
}

.dungeon p, .dungeon img {
  text-align: center;
  margin-top: auto;
  margin-bottom: auto;
}

.dungeon img:hover {
  transform: scale(2);
  border: solid #11b8f8;
  border-radius: 2%;
  border-width: 2px;
}

</style>

<!--Internal-Links-->
[The Dwendalian War Inciting Incident]: {% post_url EN/2020-12-29-inciting-incident %}
[Zelda Style Dungeons]: {% post_url EN/2021-02-13-zelda-dungeon %}
[Running the dungeon]: {% post_url EN/2021-02-13-dungeon-advice %}

<!--Self Promo-->
[@darkade]: https://twitter.com/darkade
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
[justify]: https://twitter.com/MortPhilippa/status/1344357808649756674
[Mark Brown]: https://twitter.com/gamemakerstk
[DunGen]: https://dungen.app/dungen/
[master_the_dungeon]: https://www.youtube.com/channel/UCrPmuq5_AJ_DvZ9OXQrFEFw
[Dungeon Scrawl]: https://probabletrain.itch.io/dungeon-scrawl
[Episode 7: The Minish Cap]: https://youtu.be/KEVJXqV7XMc
