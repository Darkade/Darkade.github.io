---
layout: post
title: "How to make a Zelda dungeon for TTRPGs"
image:
  path: /assets/2020-12-29/gabriel-varaljay-TwP4GjKC_3w-unsplash.jpg
  width: 1920
  height: 1440
description: "Dungeons! Probably the best ones come from The Legend of Zelda. How can we apply that knowledge to RPGs, specially D&D?"
---

<!--INTRO-->

Dungeons! ... can be a boring railroad. But they don't have to! Myself whenever I think of dungeons I don't actually think of TTRPGs, I think of The Legend of Zelda, Stone Tower, Water, Earth Forest... the list goes on. Is there a secret to a Zelda dungeon? What can we do to reverse engineer a dungeon back into our TTRPGs?

![An Opera House][postcover]

<!--more-->

_Cover photo by [Gabriel Varaljay]_

<!--ABSTRACT-->
This article will draws heavily from the excellent [Boss Keys] series by Mark Brown. In this series Mark studied what makes a Zelda dungeon a _**Zelda Dungeon.**_ And he distilled it down to a very interesting graph abstraction. This graph is at the core of the dungeon we will make together in this article. I fully recommend watching the series even if the graph system is not fully developed until episode 7; at the very least do check Episode 7: The Minish Cap.

--------

So we will break this down in ____ steps. We'll start with a randomly generated dungeon, and ending with the dungeon re-maped in the tool of your preference with a lot of graphing in between.

## A Random Dungeon

If we are making a new dungeon why are we starting with a generated one? Well, starting fully from scratch is hard, and I'm a big believer in [justification], coming up with the reasons why this dungeon is the way it is can be very fulfilling.

So. My tool of choice is [DunGen]: it has several tile sets in case you want to directly use whats generated; you can download in many different resolutions and it has a lot of sizes and interesting room shapes.

![Random map generated with dungen.app][randommap]
_You can generate this dungeon using the seed `42250252` at [DunGen]_

Some recommendations:
- Avoid very long corridors, they aren't very interesting and take a lot of map space. Gegenerate accordingly.
- You are probably thinking too big. I know you think this dungeon is not big enough, but it probably is enough to fill a couple of sessions; and you can always add another level if needed.
- Not every room will make it to the final product. So if there's a zone that's not interesting but the rest is, keep it and cut that zone later.

All of these things can be fixed later, but it's easier if you start with something interesting.

## Decide on important rooms

![Boss room][room_boss]{: .room} ![Central room][room_central]{: .room} ![Trap room][room_trap]{: .room} ![Treasure room][room_treasure]{: .room}
{: .rooms}

- Large room on the left, boss room?
- Room on the centre, bifurcations are interesting if you plan to have backtracking
- Slanted room this says trap to me
- Room on the right, here there could be some `treasure` or a `key`

Even at this point I know some of these rooms are not making it in the same shape to the final map. For example, a central room should be a very open space, so it will be edited to reflect that.

Finally I know the entrance is on the top and I'm undecided if there should be another entrance/exit

## Decide on locks and graph it!

First, what is a lock? a lock is not only a locked door that can be picked, if we go back to Zelda a lock takes the form of an inaccessible tall platform, as a frozen door that requires an special item, an elevetor that needs to be turned on. All of these are locks and most of them are more flexible and engaging than a locked door.

It's not that lock doors are bad, it's that they are more delays than they are obstacles since often they can be picked. Of course there's a time and a place but locked doors tend to make up for linear dungeons.

Another type of lock is a Rat Lock. It's open on the way in, but closes behind the characters. This can take the form of a pit from where the characters need to find a way out.

![Anotated dungeon][graph01]
_Dungeon with markers of where locks and keys are located_

In this step I like to get the a feeling for how the Dungeon is laid out. For example, if the `H slanted` is a trap room with a `rat lock` then whatever the way is to open the rat lock can't be before crossing the lock. On the other hand if the key to `purple B lock` is before the `rat lock`  then the dungeon is just a boss fight, and everything else is optional.

### The Graphs

Now it's a matter of getting familiar with the graphs.

For this dungeon I came up with the following flow. Keep in mind this is "the flow" details of traps, treasure or even what kind of locks and keys are there I'll leave for later. As right now I'm focusing on wether the dungeon will be worth exploring and high concepts.

<div class="dungeon">
![Dungeon graph][graph02]

![Overlaid Dungeon][graph03]

_This graph abstracts the dungeon flow without showing all the rooms and literal backtracking_

_Graph overlaid on top of the dungeon map_
</div>

0. After entering the dungeon the characters find `purple B lock`, `blue T lock` and the opened `orange rat lock`.
1. Crossing `orange rat lock` the characters find themselves in a trap room. I think the trap will be related with the doors here, one of wich is open.
2. Behind the open door we find `blue Z key` and `yellow Z key`. So the characters can go out and open `yellow Z lock`. At this point they might realize the blue key opened the blue lock, but they have no way to backtrack there, because of the `rat lock`.
3. Opening `yellow Z lock` the characters find `orange X key` and `mangenta Y key`. So they can backtrack to `magenta Y lock` and the `rat lock` is open. However if they go trough the rat lock and in again the trap will re arm itself.
4. the `magenta Y lock` holds a treasure. The final disarming mechanism of the `rat lock` and `purple B key`. The boss key
5. Locks `purple B` and `blue T`
    1. If the characters open `blue T lock` before the boss room they find another treasure hoard, maybe a weapons rack, and an exit. So they could bail right now.
    2. Thematically `purple B lock` and `purple B key` should be significant, they should be a Boss door and a Boss key.

### Reading the graphs

To make sense of the graph notice each vertical line means backtracking. Immediately after you enter the dungeon you find `blue T lock` but you'll have to go and deal with other things before opening that door.

Height in the graph indicates the order something is designed to take place. So, keys are always higher in the graph than their respective doors even if they were in the same vertical line. On the other hand, if two things are at the same height then they can be done in any order espective of each other.

These two things mean that the higher and the further right something is the easier it is to "solve" it. You can walk straight to `yellow Z key` but getting to the second exit will take some time.

Finally notice that the taller a graph is then the dungeon tends to be more linear, the wider it tends to relay more on backtracking, just in this dungeon the characters have to backtrack at least 4 times. Going both tall and wide means the dungeon is a maze.

![Dungeon graph][graph02]

The advantage of making a dungeon in this fashion is that you'll get a very clear idea of complexity, order and, if I say so again, backtracking. It also gives you a lot of motivation to choose a central room. Most Zelda dungeons do have a central room that you'll keep going trough at least a few times, this gives players a good feeling of how a dungeon is laid out and reinforces the room's importance.

## Make it nice

Now we have a prototype of the dungeon. You could run a game with the generated dungeon but some rooms don't quite work, like the central room and that big negative space. For this I use [Dungeon Scrawl]. It's a bit intimidating but I think the results speak for themselves.

I don't really add furniture or other such things, and I send the map to the players. I don't think these kind of maps make up for good tactical ones. I think of them as Zelda dungeon maps. You find them and they help you navigate the dungeon. But most rooms can be run with theatre of the mind or a more detailed room map if needed.

I made a whole different blog post with advice on running a dungeon with this map.

## Some advice on running the dungeon

### Avoid corridor fights
These tend to turn in to wars of attrition, they go long and get boring. If you do find yourself running a fight in a corridor suddenly there can be a _pit trap._ Both the characters and the enemies fall into a pool of water (to reduce damage) now they are fighting in an open space and later they can climb back up.

### Somebody else might be here
If theres a door the characters aren't opening most times somebody can open it from the other side. This person can be an ally or an enemy and they have their own reasons to be in the dungeon, were they expecting the party? how long have they been down here? How did they got in?

This is one of the reasons why I recommend having two entrances/exits, it justifies having people coming from elsewhere.

### Use shapes and colours

That door is a Blue Hexagon, and the lever that opens it is blue and framed by an hexagonal tile. This seems obvious, because it is. But remember Zelda, dungeons sometimes have arrows! It's about making the experience fulfilling. If when you pull the blue lever there's a loud mechanical sound elsewhere in the dungeon it's clear that it came from the blue door.

However players forget colours immediately, so shapes can help. Maybe the first door is a rectangle, second a pentagon, third hexagon, octagon... make it sequential.

### Puzzles are breakable

A difference between Zelda and an RPG is that in the former you can't blow up this door, while in the latter it feels cheap when you can't blow it up.

If the characters attempt to destroy or bypass a puzzle that's fine, remember that players will engage with this content in the way they find most entertaining for themselves. Be ready for this and don't take it personally, the story is going where it wants to go.

If this happens consider if the puzzle backfires: maybe all the doors open at the same time but thre were enemies behind all of them. Just don't make it vengeful. Traps and puzzles don't backfire because the players don't engage with them in the intended way, they backfire because the characters get an staff stuck in the machine and now it's about to explode.

### Make the map a map

Consider having this map being just a map, that's an abstraction of the dungeon. Maybe the characters find it inside the dungeon, or maybe they find it elsewhere and that's why they are coming here. In any case having this being a map opens you to the possibility of there being other rooms not shown here, either because they are secret rooms, or because you needed to add them on the moment.

If you do need a tactical map you can make it out. Maybe there's a boss room, and that merits a detailed room. Another reason is in play masking in order to add fog of war is very tedious. And a final reason is players will just move to the next room when not in combat; which makes the map intrusive to play when you try to force it being used as a tactical map.

---

Here's the full graph notation.

- ![Graph notation entrance][notation_entrance]{: .notation_icon} **Entrance:** the characters enter the dungeon trough here. This area should immediately present the "theme" of the dungeon.
- ![Graph notation exit][notation_exit]{: .notation_icon} **Exit:** an alternative entrance/exit. This is useful in case the characters get trapped (which is always an option) or if they want to bail with what they have and avoid the boss.
- ![Graph notation boss][notation_boss]{: .notation_icon} **Boss:** the boss should always be able to leave this room if it makes sense. A dragon might not but a bandit commander for sure.
- ![Graph notation lock][notation_lock]{: .notation_icon} **Lock:** when graphing think of it as the limit of an inaccessible area. Of course, in play, this can always change, and it often will if the players have the skills.
- ![Graph notation rat_lock][notation_rat_lock]{: .notation_icon} **Rat Lock:** use this kind of lock whenever you want to restrict backtracking. Ideally it locks when characters are too far to do anything about it.
- ![Graph notation key][notation_key]{: .notation_icon} **Key:** literal keys, levers, items, pressure plates. All the things that open the next section in the dungeon.
- ![Graph notation trap][notation_trap]{: .notation_icon} **Trap:** traps are varied beyond the scope of this very long post, but consider they can be lethal, troublesome or delays. I recommend checking [Master The Dungeon's YouTube channel][master_the_dungeon] for some cool traps.
- ![Graph notation treasure][notation_treasure]{: .notation_icon} **Treasure:**not all treasure belongs in the map, but hoards or particular items are worth taking note.
{: .list}

---

<!--OUTRO-->

If you'd liked this and want to support me check out [Arcane Moon], a D&D adventure inspired by 90s Magical Girl anime, published at DMs Guild.

You can also read my take on [The Role of Dice in Role Playing Games] or about [Ironsworn], one of my favorite RPGs. And follow me [@darkade].

Thanks for reading!

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

<!--Credits-->

[Gabriel Varaljay]: https://unsplash.com/@gabrielvaraljay

<!--Internal-Links-->
[The Role of Dice in Role Playing Games]: {% post_url 2020-09-21-role-of-dice %}

[Bag of Holding]: {% post_url 2020-04-25-bag-of-holding %}
[D&D online]: {% post_url 2020-04-05-dnd-online %}
[Ironsworn]: {% post_url 2020-04-01-Ironsworn-pt1 %}
[veilpost]: {% post_url 2020-04-14-the-veil %}
[arcanemoonpost]: {% post_url 2020-09-05-adventure-writing %}

<!--Self Promo-->
[@darkade]: https://twitter.com/darkade
[#WarlockPixieland]: https://twitter.com/search?q=(%23warlockpixieland)&f=live
[Arcane Moon]: https://bit.ly/ArcaneMoon

<!--External-Links-->
[Boss Keys]: https://www.youtube.com/watch?v=ouO1R6vFDBo&list=PLc38fcMFcV_ul4D6OChdWhsNsYY3NA5B2
[justification]: https://twitter.com/MortPhilippa/status/1344357808649756674
[DunGen]: https://dungen.app/dungen/
[master_the_dungeon]: https://www.youtube.com/channel/UCrPmuq5_AJ_DvZ9OXQrFEFw
[Dungeon Scrawl]: https://probabletrain.itch.io/dungeon-scrawl
