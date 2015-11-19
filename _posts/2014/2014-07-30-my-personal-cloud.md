---
layout: page
sidebar: right
title:  "My personal cloud"
subheadline:  "Safety and availability."
teaser: "I got a few requests to describe my personal cloud system."
categories:
    - information technology
tags:
    - cloud
    - nas
    - backup
    - crashplan
    - raspberry pi
    - linux
image:
    title: 2014/cloud.png
    title: 2014/cloud.png
    homepage: 2014/cloud.png
    caption: Graphical summary of my configuration
    caption_url: http://www.danilopianini.org
header:
    image_fullwidth: "2014/cloud.png"
    caption: Graphical summary of my configuration
    caption_url: http://www.danilopianini.org
---

I decided to build something more serious than an external hard drive for two reasons: comfort in data access and safety of my data. Too many times, in fact, I had to struggle with external hard drives, plug and unplug them here and there and continuously making sure that there was no inconsistency between the various place where I work. Too many times I had to waste time trying to recover as much data as possible from a broken disk.

I must say I've always kept three copies of all my non-regenerable data,  so I've never lost a byte of those data (before you ask: yes, a double disk failure happened once). But even if you only lose your backup, or gigabytes of experiment data you can regenerate, it may take days or week to get it back. If you are used to have a security copy of all your media, like I am, re-ripping all the DVDs would be an enormous pain in the ass.

After a period of many disk losses, I decided to build something a bit more reliable. Requirements:

* At least 3TB of available space
* I already have 1x2TB, 2x1TB and 1x500 hard drives I don't want to throw away
* Regenerable data must be resilient to one disk failure
* Non regenerable data must be resilient to two disk failures
* Geographical redundancy
* Streaming of my multimedia files in my local network
* Automatic synchronization of some of the files (not everything obviously, I do not have 3TB available in every single workstation I have)
* Everything *must run on Linux*, since I will never ever ever accept to be forced to use a Microsoft operating system, I'd rather develop my own solution

The requirement on space immediately killed any possibility for Dropbox, which is very Linux friendly but simply does not offer the required amount of space nor the flexibility I want. I decided to build my own solution, and here is the schema:

I bought my own NAS. I decided to go for a Netgear ReadyNAS 104. It is a four bay NAS, and the killer feature for me was the support to X-RAID. X-RAID is a very smart RAID system, that smartly combines RAID1 and RAID5 in order to obtain from any combination of disks of different sizes the largest possible amount of space available still maintaining resilience to one disk failure. The mechanism is not complex. Say that we have four disks, respectively, of 4, 3, 2 and 1TB each. X-RAID would use the first TB of each disk to build a RAID5 among those four 1TB virtual disks, let's call it ARRAY0. Then, it would use the second TB of the first three disks to build another RAID5 among three virtual 1TB devices, let it be ARRAY1. It would also build a RAID1 using the third TB of the first two disks, ARRAY2. Finally, the last TB of the first disk would be wasted. At this point, whichever of the four disk fails, every single array can be rebuilt based on data on the other three disks. Obviously, losing the smaller disk would mean to only rebuild ARRAY0, while losing one of the two biggest would lead to the need of rebuilding all three the arrays. Anyway, we would squeeze from a similar system a total of 6TB of usable space, which is a nice result compared to the 3TB that a plain RAID5 configuration would guarantee on the same configuration. X-RAID perfectly fits those like me who need to reuse disks of different sizes.

Using only the disks in my possess, however, I would have only got 2.5TB of usable space (3x500MB + 2x500MB). I decided to add another disk to the array, and I went for a Western Digital Green WD40EZRX 4TB. In my case, size, low noise and low power consumption were key factors, while the speed was not. Once the smallest disk had been substituted with the new one, I ended up with 4TB of space (3x1TB+1x1TB), wasting this way 2TB of disk space of the new disk, that will become available when I will have a disk failure on one of the small disks (that will get replaced by a 4TB drive) or when I finish this space and decide to upgrade. I recycled the 500GB drive as external drive where to periodically synchronize non regenerable data (so that I actually have two disk failures tolerance)

At this point, I met the requirement of space. I set up the HTTP service for in-home streaming (I have a XBMC box for multimedia stuf connected to the big screen in the living room), and SFTP for transferring data along a secure channel from anywhere. Since I cannot spend the time of my life manually using SFTP, I initally set up rsync with a cronjob for syncronising some of the folders. After a while, though, I tried [BitTorrent Sync](http://www.bittorrent.com/sync) and liked it very much. It is very fast, requires almost zero configurations, and it is very easy to set up multiple folders, set them read only or read write, and in case share them with other people. I dropped rsync at that point, and switched everything to BTSync. I still use Dropbox also, for the few data that I can stuff in the 40GB of space i got along these years. Still, I have a few hundreds GB of data synchronized through BitTorrent Sync.

At this point I had a concern about the electricity supply. I live in a mountain area, connected with euphemistically poor wires: before starting buyng some serious power suppliers, many of my components died of sudden death very easily. We also often experience shortages, expecially when there are thunderstorms or snowstorms. Since I invested good money for protecting my data, it would be a real pity if a discontinuity damaged my NAS leaving me with prefectly sane hard disk drives that I cannot read anymore. I decided to invest in a good UPS from APC, which would protect my NAS from electricity peaks and, considering the expected peak power consumption for my NAS of ~30W, would be able to keep it alive for a few hours even in case of shortage.

The only missink requirement, at this point, is geographical redundance. Geographical redundance is the answer to the question: what if an asteroid hits your NAS? A very nice solution would have been to just set up more NAS with similar configuration in different locations, possibly different continents. Well, I still have no house in the Caribbean, and use Cesena as a redundancy site for Pennabilli sounds... well, ridicolous. I went for an online storage service. I initially tried OnlineStorageSolutions (OLSCs), but
**the service is basically a scam**
, and I do not recommend it to anyone. I struggled for a while before finding something that looked suitable to me, and finally ran through [CrashPlan](http://www.code42.com/crashplan/). CrashPlan is a service that allows the user to synchronize an entire computer in the cloud for a continuous backup. Is similar to Dropbox, but offers unlimited space for 4$ per month per PC, offers a nice versioning system, and does not allow to download single files if bigger than 250MB: it is a pure disaster recovery system. There are many other similar services around, but CrashPlan has a key advantage over them all: runs on Linux, since it is written in Java. I only had to to hack into my NAS to install a JVM on the Marvell ARM system... but the risk of messing up with the original software and losing support scared me away from this way. I decided for something more conservative. I got a Raspberry PI (many thanks to REz that borrowed me his to make experiments), installed Arch Linux (I'm in love with rolling release, you know), and set up Java 8 on that platform. I have chosen the Raspberry PI because I wanted something with very low power consumption. Java 8 was still beta when I did the work (now it is stable), but Java 7 did not have support for hardware floating point operations, and I was really concerned worsening the performance of a board that it is itself very poorly equipped (you pay it 35$, of course is not a sky rocket). After [a bit of hacking](http://archlinuxarm.org/forum/viewtopic.php?f=31&t=5120) with library object files, CrashPlan settings and systemd service files, I got a headless instance of crashplan running. I just mounted the whole NAS as NFS mount read only (I don't trust very much closed software), and my backup started. It is going to be finished in around ten months (many have passed already), due to the mighty combination of many data and crappy Italian ADSL. I also setup the system to be able to forward data through SSH tunneling to a remote GUI in order to monitor the progress from wherever.

So right now, I'm in a transient but decently safe conditions: not regenerable data is resilient to three disk failures and already has geographic redundancy on multiple levels, and all the rest is resilient to one disk failure and is progressing with geographical redundancy. Moreover, I have automatic synchronization of shared folders with versioned backup and in-house streaming in all my home PCs. Although I still need to rely on classic cloud for redundancy, if you own at least two places at enough distance one from the other (at least in different countries for legal reasons I'd say, and even better different continents), you can just do everything with BitTorrent Sync saving you headaches, 4$/monh on CrashPlan and 35$ of RasPI... and also a lot of fun time figuring out how to configure the little board to behave as you desire.

Uh! And final touch: I keep Arch on the RasPI rolling automatically running ``pacman`` in a cronjob: I absolutely don't care if something breaks, since the SD card is periodically backed up with ``dd`` and versioned on the NAS, and I can always recover it to a previous stage. Anyway, in these first months there was no problem at all.

> RasPI image by Guitool (own work). Smartphone image by TheGoldenBox (original picture), modification: Mielon. [CC-BY-SA-3.0](http://creativecommons.org/licenses/by-sa/3.0), via Wikimedia Commons.
