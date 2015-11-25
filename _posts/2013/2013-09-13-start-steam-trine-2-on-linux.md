---
layout: page
sidebar: right
title:  "Solution for Trine 2 on Steam not starting on Sabayon Linux"
subheadline:  "Let's fix the game on Sabayon Linux."
teaser: "The Steam version of Trine 2 was not starting on Linux. Here is a possible solution."
categories:
    - videogames
tags:
    - trine 2
    - steam
    - linux
    - sabayon
    - fix
    - start
header:
    image_fullwidth: 2013/trine2-screen.jpg
    caption: Trine 2 start screen
    caption_url: http://trine2.com/site/
image:
    title: 2013/trine2.png
    homepage: 2013/trine2-screen.jpg
    caption: Trine 2
    caption_url: http://trine2.com/site/
---

I've recently bought the games on the Indie Humble Bundle 9, and among them there is the very nice puzzle-solving platform Trine 2. Since I am a Steam user, I relied on the Valve's platform for download and installation. Till there, everything went smooth.

When I've tried Trine 2, however, I was disappointed: the game just refused to start. I've browsed the game files and started check the various init scripts, and I finally found a solution. Go in the game's installation directory (by default ``~.local/share/Steam/SteamApps/common/Trine 2/``) and open up ``trine2.sh``.

You'll see in the end of the file:

{% highlight bash %}
nohup ./bin/trine2_linux_launcher_32bit >/dev/null &
{% endhighlight %}

A solution to get the game started is just to replace it with:

{% highlight bash %}
nohup ./bin/trine2_linux_32bit "-RenderingModule:DetectedFullscreenWidth=$FB_FULLSCREEN_WIDTH" "-RenderingModule:DetectedFullscreenHeight=$FB_FULLSCREEN_HEIGHT" >/dev/null &
{% endhighlight %}

Now it works! Yes, but the graphics is really poor, as you surely have noticed. One the most appealing features of the game is the fancy colorful graphics, and I obviously want it to be shiningly rendered. Fortunately, there is an option file that can be manually modified to fine tune the graphics. It's located in ``~/.frozenbyte/Trine2/`` and there are a few relevant options but these:

{% highlight bash %}
setOption(renderingModule, "ScreenWidth", 1920)
setOption(renderingModule, "ScreenHeight", 1080)
{% endhighlight %}

are the most important ones. Fill them up with your own screen resolution. If your screen is full hd, just copy my settings. Play around with the other options if you like, just restore their value to default if something goes badly wrong.
