---
layout: post
title: How to install adxv?
published: true
tag: x-ray crystallography
---


## What is ADXV?
Adxv can be used to display and analyze 2-D area detector data. It is optimized to display X-Ray crystallography diffraction images. The data may be displayed as a 1-D cross section, a 2-D image or a 3-D surface.

From [here](https://www.scripps.edu/tainer/arvai/adxv.html).

## Installation
Installation **per se** is not needed.You download a binary and put it in the `$PATH`. I usually download the CentOS7 version, which works just fine in Fedora. Be sure that it has proper permissions and then move it into `/usr/local/bin`, preferably with a shorter name `adxv`.

## Example

![adxv2]({{ site.url }}/assets/images/adxv2.png)

The image above shows that the 'reflections' at high resolution shells are weaker than the 'reflections' at low resolution shells.

> Ps. You can also create wicked cool movies, information for doing that is in the manual.
