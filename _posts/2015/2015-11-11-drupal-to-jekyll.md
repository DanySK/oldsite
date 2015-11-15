---
layout: page
sidebar: right
title:  "Drupal to Jekyll"
subheadline:  "I was shooting a canary with a cannon"

teaser: "How I decided to drop hyper-fancy content manager systems for a generated static website."
categories:
    - "information technology"
tags:
    - website
    - cms
    - jekyll
    - feeling responsive
    - github
    - git
header:
    image_fullwidth: "texture-reduced.jpg"
    caption: Blog of Danilo Pianini
    caption_url: http://danilopianini.org/
image:
    title: 2015/jekyll-logo.png
    thumb: 2015/jekyll-logo.png
    homepage: 2015/jekyll-logo.png
    caption: Jekyll is absolutely cool
    caption_url: https://jekyllrb.com/
---

I started building my website with Joomla first. Then I wanted something better, and I tried Drupal. They both, however, require more maintaining than I like, and with tools that I don't like.

In particular, here is what really made me think about sailing away from those technologies:

* The "you don't need to code" metaphor is a double edged sword. On the one hand, if you [know nothing][Jon Snow] about programming, you may be able to get a website up and running. On the other hand, if you know how to code instead, getting very simple things done is *painful*.

* Joomla and Drupal are systems meant to offer support for websites that have forums, login systems, and that are in general **way** more complicated than a blog. Using them for a simpler task really pulls in a lot of unwanted complexity, starting from the need of a SQL database.

* Writing a post requires you being online. I found no easy way to write a post e.g. in Markdown, wait for a connection, then upload it, and having my website updated. No posts from planes (no Internet in planes in EU yet), no posts when travelling, because there is a high risk of losing what I am writing if I don't press the "save" button before losing the connection. With Jekyll

* Deploying on a normal host is a pain in the neck. I don't know about other hosts, I am using [Aruba.it][Aruba]. They offer two interaction modes toward your web space, from the less painful:
  1. uploading through FTP (yes, FTP on port 21, not through SSH);
  2. use their super-fancy web interface.


* Maintaining a CMS is done by hand.
There is no package management that does upgrades for you.
This was not a problem eight years ago, when I was still using Windows as primary operating system, and also was probably not such a big deal up until six years ago, because I kept using it from time to time.
Right now, my only Windows installation is on an external USB drive, and it only serves to play [Dragon Age Origins][DAO] (it is the last game started but not yet finished that I have left to play before switching completely to Steam for Linux).
Having a package manager, I grew intolerant to having to upgrade manually.
Downloading files from the Internet, unpacking them, installing by hand, are all operations that make me mad.
Especially since when I started using rolling release distributions ([Sabayon][Sabayon] first, and [Arch][Arch]/[Antergos][Antergos] then), i just can not tolerate anymore upgrading things manually, unless I am the developer.
CMS require you to download a zip file, uncompress it, then paste it to your installation, then pray your god of choice that there are no regressions, test it locally, then upload the whole thing through FTP again.
OK, it is super-easy with respect to other procedures, but *still*.
The final result was: I just gave up upgrading. I have little time to write, no time left to maintain.

* Writing some code in a box is not that hard.
Doing it consistently among posts is much harder, highlighting the code is out of the human reach.
Now, a relevant amount of the stuff I write includes bash commands, sometimes scripts, and sometimes code.
Having automatic code highlighting is a big, big plus.

I have recently worked to some very exciting projects, e.g. the language [Protelis][Protelis], that require a public website to be available.
Since the project is hosted on GitHub, it seemed like a good idea to exploit the [GitHub Pages][GH Pages] machinery for producing the project website.
That was the reason behind my will to learn how to build a website on GitHub.
There is some learning curve for [Jekyll][Jekyll], but it's nothing that people used to write code cannot overtake.
The beautiful part is that you don't have to write in HTML any more, nor you have to edit your staff online: just write in Markdown, and your website will be generated automatically.

Moreover, once the basics have been worked out, there is something grand waiting for you: [Jekyll][Jekyll] has some **fantastic** support for theming, and there are a whole lot of free themes around, that cover more or less any need.
In particular, I fell in love with [Feeling Responsive][Feeling Responsive].
It has out of the box support for anything I needed, it is nice to look at, and easy to configure.

The idea of maintaining the website through git, use GitHub for hosting, writing posts from wherever (it is just Markdown) on my hard disk, test them launching a single command, uploading them with a single command, and being able to edit everything with any text editor I liked was almost enough to make me switch.

There was only one major issue: I have big binary files hosted on my current website.
In particular, I give away my saved games once I finish playing: it happened to me sometime to hit a bug in a videogame, maybe towards the end, and having to search for somebody else that got past that point and could provide a way to get me there too.
My solution is: use torrents. I have configured my PCs to run [Deluge][Deluge], automatically fetching torrents from a folder and seeding them.
Yes, for sure I won't have the same bandwidth of a host, but... who cares? I am pretty sure those files get few downloads per year anyway, and in case they get famous, well... P2P users should share and help others.

The bad part of this work is that I'll need to manually port the old posts from my previous website.
It will take time.
Once done, I'll redirect danilopianini.org here.

### All Posts about this website
{: .t60 }

{% include list-posts tag='website' %}

[Antergos]: https://antergos.com/
[Arch]: https://www.archlinux.org/
[Aruba]: https://www.aruba.it
[DAO]: https://en.wikipedia.org/wiki/Dragon_Age:_Origins
[Deluge]: http://deluge-torrent.org/
[Feeling Responsive]: https://github.com/Phlow/feeling-responsive
[GH Pages]: https://pages.github.com
[Jekyll]: https://jekyllrb.com/
[Jon Snow]: https://en.wikipedia.org/wiki/Jon_Snow_(character)
[Protelis]: http://protelis.org
[Sabayon]: https://www.sabayon.org/
