---
layout: post
title: "How often to roll dice in Dungeons & Dragons"
featuredimage: /assets/2020-11-18/lucas-santos-XIIsv6AshJY-unsplash.jpg
description: "Have you wondered how often should you be rolling in your D&D game? Is it even possible to answer such question? Today we take a crack at it."
imagewidth: 1920
imageheight: 1280
---

![A couple of d20 dice. One black, landed on a one. The other one green, landed on a 15][postcover]

How often per D&D session do you roll dice? There's people who roll for everything and people who'd prefer never to roll at all. But, is there a sweet spot of how often should players roll?

If we think of rolling a success as a net positive for PCs, how many rolls can they expect to make before succeeding? If you've met that person who doesn't like rolling because they might fail, have you considered maybe they should roll more often instead of less?

Today we talk about statistics and give plenty of hot takes on how rolling works in Dungeons & Dragons.

<!--more-->

_Cover image by [Lucas Santos]_

This post is a successor to my [previous one][The Role of Dice in Role Playing Games], where I talk about some of this stuff in a more general perspective and compare rolling in D&D with rolling in PbtA, from a maths stand point.


---

## What's your chance of succeeding at this check?

This is simple right? you roll a `d20` add your `Bonus` and compare it to the `DC` of the task ahead. So, given a `DC 15` with no bonus your chance of succeeding is `6/20` that is `30%`. And for the same `DC 15` with a `+5 Bonus` the chance of success is `11/20 = 55%`.

In the first case it's becase, out of the numbers a `d20` can generate, `6` are equal or greater than `15`:

```
{1 , 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14} are bellow 15
{15, 16, 17, 18, 19, 20} are equal or greater than 15
```

The second case `d20 + 5`

```
{6, 7, 8, 9, 10, 11, 12, 13, 14} these nine numbers are bellow 15
{15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25} these eleven are equal or greater than 15
```

Using the same logic we can build the following table for Difficulty Class ranging from `10` to `30` and Bonus from `+0` to `+10`.

![A table showing the probability of success for a specific DC and a given Bonus][probability]
_Probability of success in a d20+Bonus against a certain DC_

The `0%` and `100%` are probably obvious. Given only a `+1 Bonus`  you can never expect to roll a `25` and given a `+9 Bonus` you are guaranteed to roll at least a `20` even if the dice lands on a one.

~~As a quick note. D&D 5e does not define critical failures in the core books. So rolling a one is mechanically meaningless beyond having rolled a one. And It only defines critical success for combat as rolling twice the number of damage dice.~~

If we disregard "scales of success" and think of a roll as pass/fail then this is a [Bernoulli Trial]. So, we can think of it as similar to a coin toss, except each of the two sides has different probabilities of landing, and the faces are pass & fail instead of heads & tails.

### A 10% chance is not a 0% chance

I think this is obvious when rolling a single `d20`, you know you can get a `20` on the roll with a `5%` probability. But as bonuses stack and probabilities shift this seems to be forgotten. Against a `DC 10` even with a `+7 bonus` the probability of success is `90%` in other words: you have a 10% chance of failing. **On average, you'll fail one out of every ten attempts.**

~~This is another reason not to do critical successes and failures. Always having a 5% chance of failing or 5% chance of success is terribly unbalanced and swingy~~

It's not whether if you will fail. It's a matter of **when** will you fail.

## When will you fail?

We can extend the concept of the [Bernoulli Distribution] to answer the following question: In average how many failures will I observe before observing a success?

That is to say: (in average) how many tails will land before the first heads land? or, more to our own interest, **how many times will I have to roll before succeeding at this task given my current Bonus at this DC?**

**Keep in mind that whenever I say "before" in this context it means _before and up to_** Meaning If you are expected to roll trice before seeing a success, then you would be expected to have a success in your third roll ~~on average.~~

In probability this number is described by the [Geometric Distribution]. Which can be thought of the probability distribution of as: the number of of Bernoulli Trials needed to get a success.

![A table showing expected number of rolls to succeed against a DC given a Bonus][expectedvalue]
_Expected number of rolls before succeeding for d20+Bonus against a certain DC_


The `1s` and empties should be clear, as well. Given a `+9 bonus` you'll always pass a `DC 10` because even a roll of `1` will result in a total of `10`. So it takes a single roll to pass a `DC 10` in those conditions. For all intents an purposes a `1` in this table is an auto success.

On the other hand, the empty values show there's no chance to succeed at all, no matter the number of trials. You can keep rolling that `d20` but with a `+0 bonus` you'll never pass a `DC 21`


Before explaining the rest of the table it's important to consider that these values are **on average.** Except for the `1`s and the empty cells, this is not certain. You could roll a `d20` a thousand times and not get a single `20` on the dice. It would be extremely odd, but it is possible. And if you are thinking "standard deviation" later I will explain the standard deviation of these values and how is it important.

### The expected rolls bands

So. Let's explain band by band. First the `2-band`. Whenever you have a `50%` or greater chance of success, you are expected to roll twice before seeing a success. And it makes sense. if you have an `80%` chance of success you are very likely to succeed, but it won't happen always; however it's so likely that it would only take two rolls most of the time.

> This is why [failing forwards] is important. If the DM keeps the `DC 15` and a the PC has a `+3 Bonus` most times they'll succeed by their third try.

Now. Where do this numbers come from? The _Expected number of Bernoulli Trials before a success is defined as `1 ÷ probability of success`_

So, if your probability of success if `50%` you are expected to do two trials. If it's `75%` you are expected to do `1.333` trials. But, of course, making a third of a trial is not possible, you cannot make a third of a dice roll. So we round up, since you have to make one trial and a bit, you effectively have to make two trials.

That's why the `2-band` is so large, whenever you have a `50%` or greater chance of success, you can expect to get a success by the second time.

---

It's important to reiterate that this does not mean it's more or less likely to succeed at first try; just that most of the times you will have succeeded by the second attempt.

---

The `3`, `4`, `5` and `7` bands make intuitive sense; as the probability of success gets lower, then you can expect more attempts before succeeding. However the `10` and `20` bands seem like really big jumps.

To understand, consider the `10-band` is the product of having just a `10%` chance of success, meaning ~~💖✨OnAvErAgE✨💖~~ you'll succeed once every ten trials. And for the `20-band` you are at `5%` chance of success, meaning you'll succeed once every twenty trials.

### And this all means?

As I said, it reinforces the importance of Failing Forwards during Skill Checks. Given that depending on the `DC` and `Bonus` you are likely to observe a success by the second or third try, then a single failed roll should probably not have a lasting impact on the game, a series of failed rolls, however, should.

Second, but most important: You now know how many rolls a player should make to get a success with their character!

If you are frustrated by your players, or yourself, rolling and failing maybe you aren't rolling often enough. Most likely a PC needs to make at least two rolls before succeeding. So, that's the minimum amount of rolls a character should make per session,  to get that _success high._

~~This is why advantage exists. Most checks would succeed on a second try.~~

Finally. If the session is expected to be hard or a PC is not particularly skilled at the task at hand, then the session must call for a lot more rolls.

## What about the standard deviation?

Ahhh yes! The [Standard Deviation]. Defining standard deviation without it taking an hour is kind of hard. So, I'll give you a definition that will be useful in game: **68% of trials will behave within the average, plus or minus the standard deviation.**

![A table showing the standard deviation of the number of rolls expected to succeed against a DC given a Bonus][standarddeviation]
_Standard Deviation of the number of rolls expected to roll before succeeding for d20+Bonus against a certain DC_

As I been saying: all these numbers are on average. But, as you probably know, average is not the same as your specific experience. However, according to our previous definition, 68% of roll-series will fall within the ranges derived from this table.

For example, for a `DC 15` and a `+1 Bonus`:
- On average you are expected to roll trice before a success. (Check previous section)
- And `68%` of trials you will have rolled a success after rolling between `1` and `5` times. That is `[3-2, 3+2]` given the stdev in this table.

Of course, for `+10 Bonus` and `DC 10` the standard deviation is zero because you'll always succeed.

---

So. How often should you be rolling in your session? Well that depends on the characters and the difficulty class.

For example: in combat, if PC has a `+4 Bonus` against an enemy `AC 16` then the PC who gets between `2` and `4` rolls would have landed _one_ hit `68%` of the times.

Is it a weird and convoluted way of thinking about this? Probably, but if you get nothing else:

> **Three times. Everyone should roll at least three times per session.**

---

If you'd like to play around with these tables you can find them [here][tables]

---

Thank you for reading this post! I occasionally write about maths in D&D, but I write about RPGs in general about once a month. Right now I'm writing an adventure for 5e: [Warlock Pixieland], it's inspired by the 90s anime classic Cowboy Bebop!

If you'd like to support me check [Arcane Moon] my previous adventure available at DMs guild, and you can read about the [process of creating it][arcanemoonpost] here in my blog.

You can also find me on Twitter [@darkade]. There you can find the most recent news about what am I working on. Let me know if you'd like to read more about dice, bonuses and this kind of thing, because I still have plenty of ideas on it ~~Binomial Distribution anyone?~~

Thank you for reading!

<!--Images-->
[postcover]: {{ page.featuredimage }}

[probability]: /assets/2020-11-18/p.png
[expectedvalue]: /assets/2020-11-18/e.png
[standarddeviation]: /assets/2020-11-18/s.png

<!--Credits-->

[Lucas Santos]: https://unsplash.com/@_staticvoid?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText

<!--Internal-Links-->
[The Role of Dice in Role Playing Games]: {% post_url 2020-09-21-role-of-dice %}

[Bag of Holding]: {% post_url 2020-04-25-bag-of-holding %}
[D&D online]: {% post_url 2020-04-05-dnd-online %}
[Ironsworn]: {% post_url 2020-04-01-Ironsworn-pt1 %}
[veilpost]: {% post_url 2020-04-14-the-veil %}
[arcanemoonpost]: {% post_url 2020-09-05-adventure-writing %}

<!--External-Links-->
[Bernoulli Trial]: https://en.wikipedia.org/wiki/Bernoulli_trial
[Bernoulli Distribution]: https://en.wikipedia.org/wiki/Bernoulli_distribution
[Geometric Distribution]: https://en.wikipedia.org/wiki/Geometric_distribution
[Standard Deviation]: https://en.wikipedia.org/wiki/Standard_deviation

[tables]: https://bit.ly/3pIbSYH

[@darkade]: https://twitter.com/darkade
[failing forwards]: https://youtu.be/l1zaNJrXi5Y
[Warlock Pixieland]: https://twitter.com/search?q=(%23warlockpixieland)&f=live

[Arcane Moon]: https://bit.ly/ArcaneMoon
