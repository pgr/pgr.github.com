---
layout: post
title: Monome / Arduinome
---

{{ page.title }}
================

<p class="meta">2009 - 2012</p>
<p class="meta">Filed under: Electrical, Music, Hardware</p>

After seeing the beautiful work coming out of the Catskills, New York, from the folks at http://monome.org, I set about constructing two monome interface devices of my own.

Building two grids of eight by eight leds - which also respond to button presses, and which runs over USB, gives a minimalist, sixteen by eight interface device, which can be adapted to whatever is needed.

The 128 leds are a deep red (618nm), crisp and bright (1300mcd) and multiplexed to minimise the power required, allowing them to run solely off of USB.

Building these by hand based off the work by Brian Crabtree and Kelli Cain, as well as those on the monome community forums resulted in the following.

<a href="https://s3.amazonaws.com/github_image_storage/monome.jpg">
<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/monome.jpg" width="500" height="264" alt="" />
</a>

<a href="https://s3.amazonaws.com/github_image_storage/monome_2.jpg">
<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/monome_2.jpg" width="500" height="264" alt="" />
</a>

specs:
70x 5mm LEDs 30degree angle, 618nm, 1300mcd at 20mA. You’ll need to buy a single resistor match your led choice. 1300mcd is a nice brightness - so I’m limiting the leds to about 20mA. So I need one single resistor around 25-30kohms. I settled on 26.8kohms as that’s what I had on hand. For more info: check here:

1x Arduino Duemilanova
