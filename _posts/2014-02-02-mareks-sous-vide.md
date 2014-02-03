---
layout: post
category : maker
tagline: "Expanding on the Adafruit Sous Vide Tutorial"
tags : (tutorial, arduino, cooking]
---
{% include JB/setup %}

[![Arduino Powered Sous Vide Machine](/images/sous-vide/thumb/full-setup.jpg)](/images/sous-vide/full-setup.jpg)

My dad asked for a Sous Vide machine for christmas this year and being the good son I am I obligded him by making one. This turned out to be quite a bit more work that I was expecting, but in the end it was fun and I both learned a great deal and leveled up my soudering skills.

I built it following the very well written and detailed [tutorial on Adafruit](http://learn.adafruit.com/sous-vide-powered-by-arduino-the-sous-viduino) by [Bill Earl](http://learn.adafruit.com/users/11). I wanted to make something more self contained, and I wanted to make it easier to plug and unplug the various parts. Below I'll outline the differences between my build and the Adafruit tutorial in case anyone wants to build something similar.

## Self Contained

To achive the first goal I found a great [little clear stacking box](http://www.containerstore.com/shop?productId=10035341) from the Container Store. It fit the Arduio, with the LCD Shield and a protoshield in the top compartment, and the wiring for the relay in the bottom compartment. Since you rarely need to make adjustments it seamed reasonble to require the top lid to change the temperature. Ideally the buttons would be operable from outside the box, but this would have required much more detailed cutting and fitting than i felt I could do without a laser cutter.

[![wiring](/images/sous-vide/thumb/wiring.jpg)](/images/sous-vide/wiring.jpg)
[![connections on back](/images/sous-vide/thumb/connections-on-back.jpg)](/images/sous-vide/connections-on-back.jpg)


## Relay

The Adafruit tutorial uses the really cool [Power Switch Tail](http://www.adafruit.com/products/268), but to make it more self contained I got the inexpensive and easy to work with [SainSmart 2-Channel Relay Module](http://www.amazon.com/SainSmart-2-CH-2-Channel-Relay-Module/dp/B0057OC6D8). I got a little flustered at first because the relay in the tutorial was activated by a HIGH signal and this module was activated by a LOW signal. This seams couter intuitive at first, but is apparently things are driven in the electronics world. It makes sense because most microcontrollers can "sink" more voltage than they can drive. This should make the circuit more reliable and also allows it to work with 3v logic. This required changing the code from the tutorial to accomodate this reversal in logic. It was pretty simple, just find and replace HIGH to LOW.

[![connections on back](/images/sous-vide/thumb/relay-compartment.jpg)](/images/sous-vide/relay-compartment.jpg)

## Additional Code changes.

After I had everything wired up I was having lots of trouble getting the device to work correctly. It would never settle at the right temperature. I assumed that the problem was a bad temperature prob, and ordered a new one. Turns out the code the tutorial refences needed some updating. Some searching on the Adafruit forums turned up some [updated code](http://forums.adafruit.com/viewtopic.php?f=22&t=47039&p=236468&hilit=sous+vide+sous+vide+sous+vide+tuning#p236468). The change in the code waits to start the PID Algorythm until it's near the desired temperature. After running this new code it worked really reliably.

You can find my modified code on [Github](https://github.com/mirzu/Mareks_Sous_Viduino).

## Take aways and next steps

I'm really happy with the results and I'm looking forward to making v2 for myself. I think I can really quickly cook up the curcuit and get everything together. The process introduced me to PID circuits and I already have plans to combine a small PC fan and this basic circuit to make a temperature control for my BBQ. Much fun would build again.

