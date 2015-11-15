---
layout: page
sidebar: right
title:  "SmarTrRR: a transitive dependency range resolver for Gradle"
subheadline:  "Smarter dependency resolution"

teaser: "The transitive dependency ranges resolution in Gradle is crazy. I believe I got it fixed."
categories:
    - "information technology"
tags:
    - gradle
    - dependency management
    - development
    - build systems
    - continuous integration
image:
   thumb: "texture-reduced.jpg"
header:
    image_fullwidth: "texture-reduced.jpg"
    caption: Blog of Danilo Pianini
    caption_url: http://danilopianini.org/
---

I am very happy to announce [SmarTrRR][SmarTrRR], that reads "smarter" and it's an acronym for "Smarter Transitive Range Resolver".
In a previous post I have already discussed how the transitive ranges resolution in Gradle is flawed.
The issue was so annoying that I have decided to write a plugin to work it around.

## Algorithm

The plugin overrides the project's dependency resolution strategy and behaves as follow:

* Apply the substitutions (in case you want to rename some transitive dependencies and point them elsewhere, e.g. to translate ``com.google.guava:guava:14.0.1`` into ``com.google.guava:guava-jdk5:14.0.1``)

* In case of range overlap, compute the intersection range. Force the intersection range to the current and all the previously scanned dependencies

* In case of pointwise intersection (namely, a single version is compatible), pick such version

* In case of actual version conflict, pick the highest lower-compatible version. For instance, if there is a conflict between ``[2.0, 3[`` and ``[3.0, 5[``, then ``3.0`` is selected. As another example, in case of conflict between ``1.2`` and ``1.3``, ``1.3`` is selected (this is similar to the default Gradle behavior).

## Usage

### Use SmarTrRR to resolve transitive dependency ranges

Very little effort is required to enable SmarTrRR in your Gradle build:

{% highlight groovy %}
buildscript {
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath 'org.danilopianini:smartrrr:0.0.0'
    }
}
apply plugin: 'org.danilopianini.smartrrr'
{% endhighlight %}

That's it: the plugin will be downloaded from Central, brought in into your build classpath, and used for dependency resolution. Yay!

### Configure dependency substitutions

Substitutions are used to point **all** the instances of some artifact *up to certain version* to another artifact, or to another version of the same one. A ``substitutions`` section in your ``build.gradle`` will do the job.

Here is an example:
{% highlight groovy %}

substitutions {
	substitute 'asm:asm' up_to '6' with 'org.ow2.asm:asm' at '+'
	substitute 'com.google.guava:guava' up_to '14.0.1' with 'com.google.guava:guava-jdk5' at '+'
}
{% endhighlight %}


This configuration substitutes any artifact matching ``asm:asm:[0, 6]`` with ``org.ow2.asm:asm:+`` and any artifact matching ``com.google.guava:guava:[0, 14.0.1]``  with ``com.google.guava:guava-jdk5:+``

### All Posts about Gradle
{: .t60 }

{% include list-posts tag='gradle' %}

[SmarTrRR]: https://github.com/DanySK/SmarTrRR
