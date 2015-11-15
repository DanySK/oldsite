---
layout: page
sidebar: right
title:  "Version ranges resolution in Gradle is insane"
subheadline:  "No intersection, no party"

teaser: "Gradle is unable to analyze all the ranges for the transitive dependencies prior to choosing one. It resolves every range singularly, and then picks the latest (or fails)."
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

First of all, I think Gradle is great.
It does very well a lot of things.
One of the things it just does not get along with is version range resolution.
For how I understand it, this behaviour is inherited from Ivy, but it is nonetheless plain insane.

Suppose you are developing a project, which declares a dependency upon two libraries: `foo` and `bar`.
Both of those dependencies use Google Guava. `foo` declares compatibility with Guava `[14.0, 17.0]`. `bar` declares compatibility with Guava `[16.0, 18.0]`.
The most obvious behaviour is to pick the intersection of ranges and choose within, in this case, `[16.0. 17.0]` should be selected).

By default, the fucking insane way of Gradle of resolving the overlapped ranges is to just grab the newest version declared in both ranges.
In this case, Guava 18 would be used.
What does it mean?
It means that if there is at least one library that at some point partly breaks backwards compatibility, then your build will just break.
A less insane resolution strategy can be forced by specifying `failOnVersionConflict()` in `configurations.all`.
The new behaviour is: throw errors if the maximum declared version for a library is not always the same for all ranges in the dependency tree.
The "error" (which is not an error, since there is version overlapping) can then be solved manually, wasting time, efforts, and portability.
It is not possible, to the best of my knowledge, to force an automatic "select the highest version included in all ranges" strategy.
This destroys the primary purpose of version ranges.
If, by any chance, you know a way to tell Gradle to behave like it should, please let me know.

### All Posts about Gradle
{: .t60 }
{% include list-posts tag='gradle' %}
