---
layout: page
sidebar: right
title:  "Anomaly Korea reviewed on Linux"
subheadline:  "The other side of tower defense (maybe the boring one)"
teaser: "I bought this game as I did for many others, namely it accidentally appeared on my Steam library because I hit an Humble Bundle containing something else I was interested in. In my effort to try to complete as much games for Linux as possible, I also completed this one."
categories:
    - "videogames"
tags:
    - anomaly korea
    - steam
    - linux
    - tower attack
image:
    title: 2014/2014-07-31_00001.jpg
    title: 2014/2014-07-31_00001.jpg
    homepage: 2014/2014-07-31_00002.jpg
    caption: Oh, f**k!
    caption_url: http://www.11bitstudios.com/games/13/anomaly-korea
header:
    image_fullwidth: "2014/2014-07-31_00002.jpg"
    caption: Anomaly Korea screenshot
    caption_url: http://www.11bitstudios.com/games/13/anomaly-korea
---

## Plot

We are in (guess!) future and (guess!) bad alien guys have invaded our beloved planet. Their exact plan is unknown, but apparently those aliens called "Machines" take the form of towers and invade some areas. In the role of an American general called Evans, we will lead a small group of troops along invaded scenarios, trying to wipe out the aliens. As you may have noticed, the plot is dramatically trivial. The only element of interest is that, despite their love for Tokyo and United States, this time aliens have invaded Korea. This is nice news (except for you, my dear Korean fellows), and probably the only element of originality in the game's plot. The location, however, is pretty irrelevant: you will see nothing "Korean" enough that will trigger you a "look, we are in Korea!". If they used the exact same scenario for "Anomaly Argentina" you would probably barely notice it. Moreover, dialogs are somewhere between boooooring and irritating. There is poor Lt. Park that tells you what you are supposed to do, and Gen. Morris that is the classic stereotype of American Mr. Smartass General that comes out with poor jokes. Meh.

## Gameplay

The authors define the game as "tower offense". I bet you know tower defense: enemies spawn from a point and follow a route, and you must displace your towers along that route in such a way that the enemies cannot reach their goal. Flip that: you spawn from a point and you must follow a route towards some other point. Along all the possible routes, enemy defensive towers (of various kind) are waiting for you with their weapons loaded. I must admit that the gameplay brings some original contribution, do not know any other game proposing something similar. The player starts its mission is a sort of tactical view, that allows to see the whole scenario and to plan a route towards the goal. The tactical view can be re opened at any time during the mission, in order to face different conditions and events.

![Tactical screen]({{ site.urlimg }}/2014/2014-07-30_00003.jpg)

Before starting the mission, the player can spend some money to buy a pack of vehicles, up to six. There are various types of vehicles that differ for resistance, firing range and power, armor and abilities. By spending money, every vehicle can be upgraded to a better version up to three times. Money can be refilled in game by destroying towers and collecting resources. Collecting resource means (I'm not kidding) leading the convoy near them and being able to fire on them.

Once the mission starts, the convoy will move along the path decided by the player, and the vehicles will automatically fire whenever an enemy is in range. Unfortunately, the enemy towers will do exactly the same with you. There are many different enemies with very different abilities. The strategic part of the game consists in finding a good path that allows to hit the enemies without being subject to lethal counter attack. I was expecting the strategy part to be dominant in the game, but it actually is not: the game is much more action that one may suppose, and I think is no good. You are provided with a set of "abilities", namely with bonuses enabled in some area for a short amount of time. Those bonus include repairing, enhanced attack, decoys for enemies and defensive bonus. Usage of such bonuses is fundamental and cannot be done in the tactic view or when the game is paused: this requires the player to be quick in deploying the correct ability in the correct point at the right time and, in complicated situations, changes the face of the game from strategy to fast paced point-and-click mess. I would have really preferred a more tactical approach.

During the game, if you have enough money, you can buy new units or upgrade those you have. I have personally found that buying more units is almost useless, since they remain at the end of the group and never fire: it is much more efficient to have highly upgraded units on the front lines, firing on enemies before they can really counter attack and quickly wiping out wide areas in short time with the "boost" ability that greatly improves attack power and rate. Alternatively, with many vehicles, the player can continuously switch them from front to back, ensuring that more damaged units remain more protected. This way, though, the user passes more time re-ordering the units queue than doing anything else: it really destroys the sense of the game.

Another gaming problem is the difficulty level. Main campaign scenarios are boringly trivial at "casual" and totally out of my reach at "advanced". I never tested myself to the third level of difficulty. I would really have appreciated that magic something in between bore and irritation that is called "challenge". Another feature that I don't like is that saves are made by checkpoints. Those checkpoints are pretty dense, so it only rarely happens that you have to replay entire zones, but still it can happen if you make a stupid move just before getting access to the checkpoint. It is even worse if it happens because of an imprecision in your clicking rage instead of a planning error. another bad consequence of a strategy game turned action.

## Controls
The whole game is played by using a mouse. The only useful keyboard shortcut I've found is the space bar for accessing the units menu. This is not a problem in all strategy games, but it is if you make it so fast paced as Anomaly Korea is. An irritating thing happens in the tactical view: when you click for moving the visual, very often the direction you gave in a turn near the point where you clicked flip. If you are not wary, you may end up with you convoy heading towards the wrong directions, often right in the cold embrace of death.

## Graphics and sound
I found Anomaly Korea to be suprisingly pleasant under the graphical point of view.

![Scenario]({{ site.urlimg }}/2014/2014-07-30_00001.jpg)

It is a 3D game, models and shadows are nice, textures are too, it is not a masterpiece but looks pretty nice. Moreover, it's very lightweight: I have played with my usual GeForce GT 630M, definitely not a performance champion, and with the penalty introduced by Bumblebee (through Primusrun). I played the game ad full detail with no anti aliasing without any slowdown at 1080p. The game has shown absolutely no problem running on Linux, it is very stable and this in my point of view is a big plus. If you are a Linux user with Optimus graphics like me, install Bumblebee and a OpenGL offloader (optirun or primusrun) and then go to your Steam library, right click on Anomaly Korea, choose properties and in "Set launch options..." insert:

{% highlight bash %}
primusrun %command%
{% endhighlight %}

or optirun if that is your offloader. This command is universal, and can be applied to any game you want to run using your discrete video card. I personally like this approach, because it allows to fine-tune your power consumption on a per-game basis.

![Things explode]({{ site.urlimg }}/2014/2014-07-30_00002.jpg)

Unfortunately, the audio is less good than video. The whole soundtrack is about fifteen minutes of music, ending up being repetitive. But what's worse are the dialogs with fucking Morris. It makes me feel like cheering for Machines to destroy the Earth. If they are attacking there must be a reason, uh? Well, Morris is probably part of that reason.

## Longevity
The game contains a twelve-levels campaign mode and a "art of war" mode. In the former, you are gradually introduced to new vehicles and enemies, and you must save the world. In the second category you play scenarios that test how good you are with abilities. Needless to say, the crazily steep difficult curve has very negative impact on replayability. At the time I am writing the review, my Steam time counter says that I spent six hours with this game. I still have some "art of war" missions to complete, but I got tired of them: if I lose five times in a row and I cannot adjust the difficult to cope with my reduced mental abilities, I prefer to quit the game rather than growing angry.

## Conclusion

![Let's save the world]({{ site.urlimg }}/2014/2014-07-31_00002.jpg)

I liked the idea of "tower offense". It is something new and unexplored. I liked much less the frivolousness of the plot and, more important, the strong focus on action. I would have preferred the game to take a more strategic approach. The good point for the game is the technical realisation, with a nice graphics and a very stable and neat product. What a pity the game itself is not a milestone.
