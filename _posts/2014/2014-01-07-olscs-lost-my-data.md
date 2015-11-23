---
layout: page
sidebar: right
title:  "How OLScs (onlinestoragesolution.com) lost my data"
subheadline:  "Want to lose data and money?"
teaser: "Beware of this service: it is just a scam."
categories:
    - information technology
tags:
    - cloud
    - onlinestoragesolutions
    - scam
header:
    image_fullwidth: 2014/scm.jpg
    caption: Here is a scam
    caption_url: http://www.donotlink.com/hg12
image:
    title: 2014/broken-cloud.png
    homepage: 2014/scm.jpg
    caption: A broken cloud
    caption_url: http://www.danilopianini.org
---

A few months ago I've written about Sabayon Frozen being moved to a real hosting platform, OLScs. They do advertise on their website a very cheap ($48 for two years of service) and feature rich unlimited cloud storage, but they forget to mention they are totally unreliable. I am now writing this message to let others know and maybe save some data loss.

As you can imagine, hosting Sabayon Frozen requires a large amount of space, about 150GB per snapshot. Moreover, since the service is "unlimited", I've decided to store there a copy of my personal data, which is floating around 3TB in total.

While I was uploading, after having reached the limit of 1.5TB, I was notified that my usage was "well above average". Well, they offer the service as unlimited, I use it as they advertise. They decided to "move" me on another server. Here I started having some doubts: how is it possible that they have to run it manually? Don't they have an automated system to gracefully and seamlessly move data around in their own data center?

Anyway, after several hours I got moved on the new server. Here is where all the problems started. First, **I could see the directory structure, but no file**. Then, I could see some of my files, but not all of them. I was unable to delete some directories (permission denied) and the public folder was no longer accessible from http. They tried to fix it, and ended up switching on **two versions of my data**, one with some files and working public directory, the other with other files and no public directory. In every case, part of my data was lost.

No big deal till this moment anyway, since I had a copy of everything, and I just re-uploaded the whole stuff. A very annoying thing is that their FTP server limits the number of listed files to 10000, while in Sabayon Frozen directories I have much more: this ended up in a useless re-upload of hundreds of GBs.

Another problem started while uploading: my files were truncated at some point, and the upload was continuously interrupted:

``Response: 226-Error during write to file``

To me, it appears to be a clear sign of the server ran out of disk space. I opened a ticked, and they replied they have to move me. This was on December 16th. They started the move giving me an ETA of approximately 24 hours, and said it was completed on December 19th. At this point, I checked, and I've seen a HUGE amount of data was missing, more than 2TB. From this moment on, they continued telling me they were re-syncing, changing permissions, and so on and so forth. When I asked why it was taking so long, I got this answer:

> I  can't really say. You have so much stuff I should have never moved you in the first place. The chances of you getting everything back in the same manor are looking slim

What? Are they serious? I kept on waiting for them to fix their mess until today, then I've lost my patience when they came up with:

> As far as I can tell I don't think data has been lost.  Are you missing something?

This is **RIDICULOUS**. First, they basically admit they've done something wrong, and say that there is little possibility of having everything back as it was (no reason for the loss, obviously). Then, **they feign ignorance** and ask if I am missing something when it is WEEKS that I keep contacting them telling that **YES, I DO MISS 2TB OF DATA**.

So, dear netizens searching for a reliable online backup service, stay away from onlinestoragesolutions.com. It is very cheap, but **totally unreliabile**, and with irritating support service.

I am now looking elsewhere for an unlimited online backup service supporting FTP (rsync would work even better), if you have any suggestion, please contact me!
