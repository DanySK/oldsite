---
layout: page
sidebar: right
title:  "Corsair Hydro H100i v2 under Linux"
subheadline:  "And probably also other Corsair AIO water coolers such as the H115i"

teaser: "Corsair does not support us, we do support ourselves."
categories:
    - "information technology"
tags:
    - linux
    - corsair
    - water cooling
header:
    image_fullwidth: 2017/aio-cooling.jpeg
    caption: Blog of Danilo Pianini
    caption_url: http://danilopianini.org/
image:
    title: 2017/Corsair_logo_horizontal.png
    thumb: 2017/Corsair_logo_horizontal.png
    homepage: 2017/aio-cooling.jpeg
    caption: Now also working under Linux!
    caption_url: https://github.com/audiohacked/OpenCorsairLink
---

I recently upgraded my rig, and decided to buy a pretty hot processor: the 8th gen Intel Core i7-8700K.
Intel has the very unfortunate habit of not soldering the processor die to the lid, but rather use a thermal compound whose performance are not comparable.
Some like to delid, I don't like very much the idea of voiding the warranty of a few days old processor.

Anyway, I decided to buy a water cooler in order to keep the CPU temperatures under control.
My choice was the Corsair H100i v2.
This system's suggested mounting expects the user to connect a cable to the waterblock and to a USB 2 header on the motherboard.
Once done, the all-in-one liquid cooler can be finely tuned using the "Corsair Link" application.
Sounds great, right? No it does not, as Corsair is not supporting Linux.

## Open Corsair Link: preparation

Fortunately though, the community helped itself.
[This project](https://github.com/audiohacked/OpenCorsairLink) allows Linux users to read data from the AIO (e.g. the water temperature and the fan speed), and to adjust the settings to their preference (led color, fan curves, pump performance).

### Building the application

That's rather easy. You'll need `git`, a C compiler, and `libusb` installed. They are all likely already on your system.

{% highlight bash %}
git clone git@github.com:audiohacked/OpenCorsairLink.git
cd OpenCorsairLink
make
{% endhighlight %}

Once the compilation is done, you'll find a `OpenCorsairLink.elf` file on the folder. That's the application. Everything's packed inside such file, and you can just put it in your `PATH` and have it accessible. Also, I suggest renaming it to just `OpenCorsairLink`

### Installing on Arch

Since I am an Arch Linux user, I decided to provide (myself and others) with a mean to do the above procedure quickly.
To do so, [I published an AUR package](https://aur.archlinux.org/packages/opencorsairlink-git/) that automatizes the compilation and installation procedure, that can be done in a single shot.
Assuming you are using [yaourt](https://archlinux.fr/yaourt-en) as AUR helper, just issue:

{% highlight bash %}
yaourt -Sy opencorsairlink-git
{% endhighlight %}

Once done, `OpenCorsairLink` will be an executable readily accessible from your command line.

## Using OpenCorsairLink

Here it comes the most difficult part: understanding how to use the application.
I could find no decent resource online explaining how to use it, and the help file is vague.

{% highlight bash %}
$ sudo OpenCorsairLink --help
OpenCorsairLink [options]
Options:
        --help                          :Prints this Message
        --version                       :Displays version.
        --debug                         :Displays enhanced Debug Messages.
        --dump                          :Implies --debug. Dump the raw data recieved from the device.
        --device <Device Number>        :Select device.

        LED:
        --led <HTML Color Code>                 :Define Color for LED.
        --led-warn <HTML Color Code>            :Define Color for Warning Temp.
        --led-temp <Temperature in Celsius>     :Define Warning Temperature.

        Fan:
        --fan-temps <CSV of Temperatures>       :Define Comma Separated Values of Temperatures for Fan.
        --fan-speeds <CSV of Speed Percentage>  :Define Comma Separated Values of RPM Percentage for Fan.

        Pump mode:
        --pump-mode <mode>      :set to 3 for quiet, and 5 for performance

 Without options, OpenCorsairLink will show the status of any detected Corsair Link device.
Dev=0, CorsairLink Device Found: H100i V2!
{% endhighlight %}

OK, some things are rather straightforward.
Selecting the device is easy, setting the pump is too.
Honestly, also the led part is not a problem.
The problem is how to tune the fans!
The help does not explain very well how many values should be provided.
I've tried several combination, that had no effect on the fan speed whatsoever, so I took a read of the source code: the magic number is **six**.
You must provide six values.
Temperatures are measured in Celsius, and they refer to the *water* temperature, not the CPU temperature.
So do not set your fans to get to a high speed when the temperature is 70°C or so, as it would be *way* too late.

### Valid configuration example

Here is my configuration line:
{% highlight bash %}
$ sudo OpenCorsairLink --device 0 --pump-mode 3 --fan-temps 0,20,25,30,35,40 --fan-speeds 0,10,30,60,80,100

Vendor: Corsair
Product: H100i V2
Firmware: 2.8.0.0
Temperature 0: 22.20
Fan Speed 0: 840
Pump Speed: 2820
{% endhighlight %}

The difference between the two pump settings is minimal, so maybe when the hot summer comes I might decide to use the performance mode for the pump.
I want the fans to be very quiet  when there is little or no load, but I want them to get aggressive when the water temperatures get too close to 40°C.
I don't really care about the led instead (my case window faces a pieces of furniture).

Once the settings are saved, the AIO should register them and be set.
However, I'm not entirely sure it works.
As such, just to be on the safe side, I reapply the configuration on boot.

So, dear Linux users, you can now enjoy your high performance water cooling system!

### All Posts about Linux
{: .t60 }

{% include list-posts tag='linux' %}
