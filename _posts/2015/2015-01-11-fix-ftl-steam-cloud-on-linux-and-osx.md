---
layout: page
sidebar: right
title:  "How to fix FTL: Faster Than Light Steam Cloud sync on Linux and MacOS X"
subheadline:  "Lose your progress never again"
teaser: "FTL does not play well with Steam Cloud. Here is a possible solution."
categories:
    - "videogames"
tags:
    - ftl
    - steam
    - linux
    - mac os x
    - steam cloud
image:
   thumb: "texture-reduced.jpg"
header:
    image_fullwidth: "texture-reduced.jpg"
    caption: Blog of Danilo Pianini
    caption_url: http://danilopianini.org/
---

![FTL Snapshot]({{ site.urlimg }}/2015/ftlsnap.png)

I love FTL.
And I am sure you love it too.
However, this game has a bug when ran upon Steam: despite it claims support for Steam Cloud, such a feature does not work correclty under \*nix, and this afflicts Linux and MacOS users who cannot sync their saves across multiple systems.

The root of the issue is in a case problem for the FTL saved games folder.
When creating folders on Unix, Steam ignores case, and creates a ``fasterthanlight`` folder. The game, however, reads from a ``FasterThanLight`` folder.
I
 personally suspect this is a Steam problem, probably due to its Windows-centric origins.
Windows file systems, in fact, are case insensitive, and on that platform the bug cannot be reproduced.

Despite the fact that it would be nice from Valve to fix this, here is a simple manual solution.
I've tested it on [Antergos Linux][Antergos], but it should work also on every other Linux and on OSX, if FTL uses the same directory structure under the latter (which is likely, otherwise just tune the commands to match the correct ones, or leave a comment below).

Be warned: by executing this procedure, you will use the saved games you currently have on Steam Cloud.
Your local progress will be moved in ``~/.local/share/FasterThanLight.backup``. These steps must be run on every \*nix system that you want to be cloud synced.
Fire up a terminal and issue:

{% highlight bash %}
mv ~/.local/share/FasterThanLight ~/.local/share/FasterThanLight.backup
ln -s ~/.local/share/fasterthanlight ~/.local/share/FasterThanLight
{% endhighlight %}

Now open the game, and enjoy a working Steam Cloud.

### All Posts about FTL
{: .t60 }

{% include list-posts tag='ftl' %}

[Antergos]: https://antergos.com/
