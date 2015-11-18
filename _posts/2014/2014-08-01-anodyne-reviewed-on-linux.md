---
layout: page
sidebar: right
title:  "Anodyne reviewed on Linux"
subheadline:  "Anodyne review, including a guide to actually run this thing on Linux."
teaser: "I'm not a big fan of Zelda-like super retro games, but I decided to give Anodyne a chance anyway."
categories:
    - "videogames"
tags:
    - anodyne
    - steam
    - linux
    - zelda
    - top down
image:
    title: 2014/anodyne0.png
    title: 2014/anodyne0.png
    homepage: 2014/anodyne0.png
    caption: ZOMG, a door with black bands on sides!
    caption_url: http://www.11bitstudios.com/games/13/anomaly-korea
header:
    image_fullwidth: "2014/jurassic-park-rampage-edition.png"
    caption: Still cooler than Anodyne
    caption_url: http://www.anodynegame.com/
---

Despite my will of trying the game, the authors made it in such a way that was a pain being able to use it. First, it depends on Adobe Air. Seriously guys? Adobe Air? You make a multiplatform, Linux-friendly game and you decide to depend on freaking Adobe Air? Meh! So, at first start, a console appears from steam, requesting you if you will to install Adobe Air. I replied "yes", the package was downloaded and the installation failed, or anyway the game did not start. OK, no problem. I use Sabayon, so I just installed Adobe Air from Entropy (note: # means that the command is issued as root, $ that the command is issued as user):

{% highlight bash %}
equo i adobe-air-runtime
{% endhighlight %}

it requires Nirvana Community Repo, but if you don't feel like using that repo, you can install it anyway through Portage:

{% highlight bash %}
emerge adobe-air-runtime
{% endhighlight %}

I tried again, and the request for installing Adobe Air did not appear anymore. Despite the fact that the package was installed correctly. Weird. I tried to figure out what was wrong, and after some search I discovered that Adobe Air requires you to accept a license by editing a god-only-knows-what file that stays well hidden in one of your home subfolders. Clearly, accepting the license when installing the package is not enough. Well played Adobe! Very user friendly! In order for you to avoid doing the same search, here is a command you can just throw in your shell that makes Adobe Air happy and lets Anodyne start:

{% highlight bash %}
echo 2 > ~/.appdata/Adobe/AIR/eulaAccepted
{% endhighlight %}

so, now that it started, let's comment the game.

## Plot

You are a guy called Young, that for no apparent reason is called to save the world by helping a guy called "Briar". In order for Young to meet Briar, he will need to visit and explore various locations, solving puzzles and beating enemies in order to find enough "cards" to open the gate leading to Briar. The cards are collectible representations of the characters of the game. During its adventure, Young will explore very different locations that I would define surreal, many of which brilliantly design under the aesthetical point of view: there is great variety of colours, ambients, music and atmosphere. The latter is improved a lot by dialogs with NPCs: they vary from funny to ironic to dramatic to philosophical; and there are often many little pieces of pure genius in them. Dialogs, despite being of little relevance for the gameplay, are one of the best aspects of this game. Young will improve its abilities exploring new parts of the world: he will find life-donating fairies, upgrades and its main tool, probably the most weid tool has ever been used as main tool in a videogame: a broom. Yes, a broom. Young will fight his enemies and solve its puzzles with the solely help of a broom. Nice touch.

## Gameplay

The game consists of visiting a sequence of rooms, and solving puzzles. Most puzzles are self contained, in the sense that you won't need to visit other rooms in order to complete them. Once completed, they give you access to previously unaccessible areas: new rooms or chests containing cards or keys. There are a number of stages with different themes, and each of them has various rooms. Some of the stages have a boss in the end that you will need to fight in order to complete the area. All the stages have direct access to a sort of hub stage called "Nexus". Once the player has discovered every card in a stage, a red stone appears on the stage portal located in Nexus. This way, you will not search over and over in areas you have already been. As I said in the previous section, Young's main tool is a broom. It can be used as a weapon against enemies, or (say what!) to move dust. Dust is a sort of magic substance in Anodyne: it floats, allowing the player to explore areas filled with water, it is able to stop lasers, and it enables mobile platforms. Now that I know dust is so useful, I will never clean my house again.

Most of the puzzles are nice and interesting: they require a few moments to think which the solution can be, then normally in few attempts it's possible to solve them. There are a few exceptions, though. One of the stages in particular requires Young to exhibit himself in a series of complicated jumps and timely moves. It is very easy to repeatedly fail, and some times this ends up really frustrating the player. A good game should always be challenging, interesting, and never ever ever frustrating.

Despite the variety of atmospheres and the nice dialogs that make every place interesting to explore, the gameplay after a while many of the puzzles end up being repetitive. I liked much more the approach of Antichamber, that gradually "teaches" new tricks to the player. Anodyne is much more rough under this point of view.

## Controls

Controls are cumbersome. By default, only the keyboard is supported, and the user is supposed to use directlional buttons, enter as a start button and X and C keys for jumping and making an action. I don't dislike simplicity... But I really hate technical issues. Gamepad support is sponsored, but once connected, my XBox 360 controller, that works in every damn game in Steam, was doing nothing. I had to search the Internet (again!) and found out what was the problem: under Linux, this game supports the controller through Joy2key. Joy2key is a nice software that allows to bind, within a single X window, your gamepad to a keyboard button. The point of my rant is that even my text editor have gamepad support through Joy2key! That is ridiculous! Moreover, configuring it is not trivial. You must first install Joy2key, then link SDL files where Anodyne thinks is the right place for them to be, then compiling a gamepad profile, then run Joy2key along with the game. Moreover, you need your gamepad to be connected and to be /dev/input/js0, because screw people with two controllers! Here the instructions:

{% highlight bash %}
su
equo i joy2key
cd /usr/include/x86_64-pc-linux-gnu/SDL/
ln -s /usr/include/SDL/SDL_platform.h SDL_platform.h
ln -s /usr/include/SDL/SDL_stdinc.h SDL_stdinc.h
ln -s /usr/include/SDL/SDL_endian.h SDL_endian.h
ln -s /usr/include/SDL/begin_code.h begin_code.h
ln -s /usr/include/SDL/close_code.h close_code.h
exit
cd cd ~/.steam/steam/SteamApps/common/Anodyne/linux_controller
./ccr.sh
{% endhighlight %}

once done, go to Steam, right click on "Anodyne" in your library, then ``Properties``, then ``Set Launch Options...`` and enter the following in the text area:

{% highlight bash %}
joy2key -rcfile ~/.steam/steam/SteamApps/common/Anodyne/linux_controller/anodyne.j2kconfig -config Anodyne | %command%
{% endhighlight %}

Now, once the game starts, your mouse will become a cross. Click on the Anodyne window to bind the gamepad to the keyboard when the window has focus. Despite your will, sooner or latetr Joy2key will decide to crash. You don't need to restart the game, just reduce it at icon, open a shell and issue:

{% highlight bash %}
joy2key -rcfile ~/.steam/steam/SteamApps/common/Anodyne/linux_controller/anodyne.j2kconfig -config Anodyne
{% endhighlight %}

Then click on the game window. Playing the game with a controller is way better than the experience you get out of a keyboard, altough even with a controller some puzzles that involve complex jumping are definitely irritating because stupidly difficult. I cannot stand games that instead of challenging your ability to understand the game challenge your ability to deal with a millimetric jump in a trivial scenario. If I wanted that, I'd have downloaded Flappy Bird instead.

If it is not clear, the controller part of Anodyne is way below the pass mark.

## Graphics and sound

Premise: I'm not a fan of the return of pixels. This extremely overrated mania that probably started with  [Minecraft](http://it.wikipedia.org/wiki/Minecraft) of making games look pixelated by design got out of control, and now I often hear people arguing that pixels require higher skills and stuff. Bitch, please. In some cases (Minecraft for instance, where the game is made out of blocks) I think it makes perfect sense to use pixelated, but nowadays seems like every indie game should be pixelated to be defined artistic. I think this thing is getting more and more hipster. Anyway, here is an example of a game room in Anodyne:

![a room]({{ site.urlimg }}/2014/anodyne1.png)

Nice, uh? Well... no. The game has a graphics similar to that of my old [Nokia 6630](http://en.wikipedia.org/wiki/Nokia_6630), screen dimension included. Can you see those two enormous black areas on the side of the screen? Exactly! Anodyne forces you to play with its rules. You have a classic Full HD screen? Well, rotate it! Uh, what are you saying? You cannot? Your fault! Get the black bars and live happy! By comparison, look at one of my old [Sega Mega Drive](http://it.wikipedia.org/wiki/Sega_Mega_Drive) games: [Jurassic Park Rampage Edition](http://en.wikipedia.org/wiki/Jurassic_Park:_Rampage_Edition).

![The amazing graphics of Jurassic Park: Rampage Edition]({{ site.urlimg }}/2014/jurassic-park-rampage-edition.png)

Impressive, huh? The game is twenty years old, but the graphics is still better than Anodyne's. Oh, yes, yes, this is pixel art and blah blah blah, but I'm not a hipster and I have my own taste, and moreover I hate games that are unable to rescale for adapting to different screens. Sounds to me like technical deficit, and this is bad.

<iframe width="560" height="315" src="https://www.youtube.com/embed/M3YfdhAhCds" frameborder="0" allowfullscreen></iframe>

The [soundtrack](http://www.youtube.com/watch?v=M3YfdhAhCds) is way better than the graphics, and it fits pretty well the various stages. Overall, however, the game is a Nokia 6630 level technical quality.

## Longevity

My Steam timer says that I've completed the game in eleven hours. Considering that there an achievement for those who do the same in three hours, I am a proven slow player. After having finished the game, the replayability is near zero, so expect realistically something in between three and ten hours of gameplay (I'm an outline I guess), which probably are more or less the same time you need to figure out how to run the game and how to use your gamepad if you have to do it alone without a guide.

## Conclusion
Anodyne is a below average game, and I do not recommend it. Authors are probably much more creative artists than game designers. The atmosphere of the game is nice, but it is technically too below the threshold of niceness, and the gameplay is not innovative nor addictive. If you find it for a very convenient price may be worth the money, but for sure I would never ever spend $9.99 to buy it at full price on Steam.
