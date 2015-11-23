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
    image_fullwidth: 2014/drupal-joomla.png
    caption: Drupal and Joomla logos
    caption_url: https://miami.wordcamp.org/2016/2015/10/21/special-invite-to-drupal-and-joomla-shops/
image:
    title: 2014/move-joomla-to-drupal.png
    thumb: 2014/drupal-joomla.png
    homepage: 2014/drupal-joomla.png
    caption: Joomla to Drupal
    caption_url: https://www.cms2cms.com/

---

In the end, I got bored of Joomla. It's not Joomla fault I think, it's just that keeping everything up-to-date was too time expensive, and in fact my old website got stuck with Joomla 1.5.something.

At a certain point I decided I had to update it. An important premise is that using only rolling-release distributions (Sabayon and Arch) I grow extremely lazy for what concerns manual updates: I am used to have daily / weekly updates done with a single command, and only rarely I have to look to what went wrong. I can accept a bit more effort for upgrading the kernel (namely: a couple more of commands to issue), but I really cannot spend a day for such operation as I was used to when I used Windows - I still remember I was formatting my system every four or five months, now I laugh at myself when it comes to my mind.

Anyway, I searched for instructions for the Joomla update. Updating between minor versions was quite easy: just unpack the patch archive and upload, done. Upgrading between major versions looked a much deeper pain. I also had the idea of seeking which version my favourite package managers propose:

{% highlight bash %}
equo s joomla
╠ @@ Searching...
╠ @@ Package: www-apps/joomla-1.5.25 branch: 5, [sabayon-weekly]
╠ Available: version: 1.5.25 ~ tag: NoTag ~ revision: 0
╠ Installed: version: Not installed ~ tag: n/a ~ revision: n/a
╠ Slot: 1.5.25
╠ Homepage: http://www.joomla.org/
╠ Description: Joomla is a powerful Open Source
╠ Content Management System.
╠ License: GPL-2
╠ Keywords: joomla
╠ Found: 1 entry
{% endhighlight %}

Meh!

{% highlight bash %}
pacman -Ss joomla
{% endhighlight %}

Super meh!

{% highlight bash %}
yaourt -Ss joomla
aur/akeeba-remote-control-64 4.0.8-2 (1)
Desktop application which allows you to backup multiple joomla sites (with Akeeba Backup) with a single click.
aur/joomla 3.3.0-1 (49)
A PHP-based content management platform
aur/joomla-es 1.6.0-1 (Out of Date) (2)
Sistema de Administracion de Contenidos
aur/joomscan 2012_03_10-1 (12)
Detects file inclusion, sql injection, command execution vulnerabilities of a target Joomla! web site.
{% endhighlight %}

The AUR is fantastic as usual!

Since I have not switched all my systems to Arch - I need a good reason to remove Sabayon, and I have none - I wanted something that was kept up-to-date also in my repository: my idea is that I can keep a local install up to date, and just regularly upload it to the server (and regularly backup it). So I looked around, searching for other CMSs. As everybody does, I evaluated Wordpress, Joomla and Drupal.

##### Wordpress
**Pros**: easy, available both in Pacman and Entropy

**Cons**: considered slow with respect to the others, I would lose my Joomla contents

##### Joomla
**Pros**: I already know how it works, I will not lose my current website content

**Cons**: I HATE HATE HATE doing upgrades, version 3 not available in Entropy

##### Drupal
**Pros**: require skills (so I will either prove myself valiant or learn more), available both in Pacman and Entropy, fast

**Cons**: I would lose my Joomla contents

Since I could in the end keep my legacy site in a subdirectory and redirect if needed, I decided to go for Drupal. And this is the result folks: I must admit I am rather satisfied of my choice.
