---
layout: page
sidebar: right
title:  "Automatically switch screen configuration when a new monitor is connected in Sabayon Linux"
subheadline:  "Plug and view"
teaser: "It is easy to configure Linux to switch the configuration automatically when a new monitor gets connected."
categories:
    - "information technology"
tags:
    - linux
    - screen configuration
    - automatic
    - script
    - udev
header:
    image_fullwidth: 2012/xinerama.jpg
    caption: Xinerama modern 4 monitor setup by Kazymjir
    caption_url: https://commons.wikimedia.org/wiki/File:Xinerama_modern_4_monitor_setup.jpg#/media/File:Xinerama_modern_4_monitor_setup.jpg
image:
    title: 2012/xinerama.jpg
    homepage: 2012/xinerama.jpg
    thumb: 2012/xinerama.jpg
    caption: Xinerama modern 4 monitor setup by Kazymjir
    caption_url: https://commons.wikimedia.org/wiki/File:Xinerama_modern_4_monitor_setup.jpg#/media/File:Xinerama_modern_4_monitor_setup.jpg
---

Using often my laptop for presentations, I really got bored of manual switching the graphics every time a new monitor is connected. Thou KDE offers a functional utility in its control panel for that, I prefer my computer to switch automagically as soon as a screen connector is plugged in or removed. The following instructions will work for both Sabayon and Gentoo, and possibly under other Linux distributions like Ubuntu, Mint, SUSE, depending on where the configuration files are placed.

To see if you can trigger udev events related to monitor connected, run:
{% highlight bash %}
udevadm monitor --property
{% endhighlight %}

Now, if you try to plug and unplug a new monitor, you should see some events on your console, something like:

{% highlight bash %}
KERNEL[1303765357.560848] change /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV_LOG=0
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0
SUBSYSTEM=drm
HOTPLUG=1
DEVNAME=dri/card0
DEVTYPE=drm_minor
SEQNUM=2943
MAJOR=226
MINOR=0
{% endhighlight %}

If you can see that, you will be able to configure your monitor for the automatic switch. First:
{% highlight bash %}
cd /etc/udev/rules.d/
{% endhighlight %}
here are stored the `udev` rules. Let's create a new one. I will use nano, but every editor is ok.
{% highlight bash %}
nano 80-vga.rules
{% endhighlight %}
in the file, write the following, to intercept the monitor events:
{% highlight bash %}
ACTION=="change", SUBSYSTEM=="drm", HOTPLUG=="1", RUN+="/root/hotplug.sh"
{% endhighlight %}

The ``RUN`` variable will contain the path to a script which will be run when a new event is detected. I placed it in ``/root/hotplug.sh``, but you may want to place it somewhere else.
Now, the script. I will quote mine, then explain:

{% highlight bash %}
#!/bin/sh
read STATUS < /sys/class/drm/card0-VGA-1/status
export DISPLAY=:0
export XAUTHORITY=/home/danysk/.Xauthority
if [ "$STATUS" = "connected" ]
  then
    xrandr --output VGA1 --right-of LVDS1 --auto --screen 0
  else
    xrandr --output VGA1 --off --screen 0
fi
{% endhighlight %}

So, this is what this simple script does:
read the current status of the VGA connector (can be either ``"connected"`` or ``"disconnected"``);
export the variables required in order to access the current running X (remember to change ``danysk`` to your user name!);
verify the current status of the VGA connector and use ``xrandr`` to properly set it (i like to the right of my main screen, but you may set clone or whatever you like.


That's it. If you did it well, now your system reacts to plug and unplug operations automatically switching to the right configuration. Have fun :)
