# Building your own CoreIR transponder

Originally on https://blog.k3s.live/2016/10/12/building-your-own-coreir-transponder/, mirroring here for posterity.

[October 12, 2016](https://mrickert.com/building-your-own-coreir-transponder/) • [19 Comments](https://mrickert.com/building-your-own-coreir-transponder/#comments)

### Creating your own CoreIR transponder from off-the-shelf components…

#### [![coreirlogosmall](https://mrickert.com/wp-content/uploads/2016/10/coreirlogosmall.png)](https://mrickert.com/wp-content/uploads/2016/10/coreirlogosmall.png)What you’ll need:

*   [An NPN transistor](https://www.digikey.com/product-detail/en/fairchild-semiconductor/PN2222ATFR/PN2222AD26ZCT-ND/459004)
*   [A 4S balance lead connector](https://www.digikey.com/product-detail/en/jst-sales-america-inc/B5B-XH-A(LF)(SN)/455-2270-ND/1530483)
*   [Two 940nm IR led](https://www.digikey.com/product-detail/en/lumex-opto-components-inc/OED-EL-1L2/67-1001-ND/270797)
*   [A 9.1ohm resistor](https://www.digikey.com/product-detail/en/vishay-dale/CRCW25129R10JNEG/541-9.1XCT-ND/1178532)
*   [One Arduino pro micro](http://www.banggood.com/Pro-Micro-5V-16M-Mini-Leonardo-Microcontroller-Development-Board-For-Arduino-p-1077675.html?rmmds=buy)
*   [28guage silicon wire](http://www.banggood.com/1M-8101214161820222426-AWG-Silicone-Wire-SR-Wire-p-921159.html?rmmds=search)
*   A hot glue gun

Got all that? Great, let’s get started!

First, cut the wiring on your two LEDs like seen below, if you look closely, you should see two sets of notches on your led wires, the second set (further from the led itself) is where you want to cut with scissors. You’ll also want to bend the side that has the ‘smaller’ filliment inside the led bulb (we call that the anode) about 90 degrees out, why will be clear later on:

[![3](https://mrickert.com/wp-content/uploads/2016/10/3-1.jpg)](https://mrickert.com/wp-content/uploads/2016/10/3-1.jpg)
[![2](https://mrickert.com/wp-content/uploads/2016/10/2-1.jpg)](https://mrickert.com/wp-content/uploads/2016/10/2-1.jpg)

Next we take the 4S balance connector and cut off the back pins as close as we can to the plastic case, this will help keep potential shorts from occurring as we put everything together later on.

[![20](https://mrickert.com/wp-content/uploads/2016/10/20.jpg)](https://mrickert.com/wp-content/uploads/2016/10/20.jpg)

Ok, so we prepped our LEDs and our balance connector, lets prepare the transistor next. place the transistor so that the flat side is facing \*up\* and the ‘legs’ are facing tward you, then take the leg all the way to the right and bend it back tward the transistor until its flush with the plastic housing, creating an L shape, as seen below. You’ll also want to trim this bent leg a bit, so that it only has at most a few mm extending from the plastic transistor housing.

[![5](https://mrickert.com/wp-content/uploads/2016/10/5.jpg)](https://mrickert.com/wp-content/uploads/2016/10/5.jpg)
[![4](https://mrickert.com/wp-content/uploads/2016/10/4.jpg)](https://mrickert.com/wp-content/uploads/2016/10/4.jpg)

This next step is optional, but it’ll give you a much better end result… ‘tin’ (that is, put some flux and then solder on to) the pins on the arduino we’ll be using later. Pin 5, all ground pins, vcc, and raw.

[![1](https://mrickert.com/wp-content/uploads/2016/10/1.jpg)](https://mrickert.com/wp-content/uploads/2016/10/1.jpg)

Got it? Good! Keep that soldering iron nice and hot, and solder the 9.1ohm resistor (either direction, there is no wrong way) onto the VCC pin, while propping it up against the orange chip, the lower you can go here, the flatter your end result (transponder) will appear. Be sure not to touch the reset or A3 pins though!

[![6](https://mrickert.com/wp-content/uploads/2016/10/6.jpg)](https://mrickert.com/wp-content/uploads/2016/10/6.jpg)
[![7](https://mrickert.com/wp-content/uploads/2016/10/7.jpg)](https://mrickert.com/wp-content/uploads/2016/10/7.jpg)

So far so good, now its time to install the transistor we previously prepped. With the flat side still facing upwards, solder the leftmost leg to ground, and the middle leg to the 5 pin before bending the transistor down flat against the Arduino (but don’t touch any metal bits with those legs):

[![9](https://mrickert.com/wp-content/uploads/2016/10/9.jpg)](https://mrickert.com/wp-content/uploads/2016/10/9.jpg)
[![8](https://mrickert.com/wp-content/uploads/2016/10/8.jpg)](https://mrickert.com/wp-content/uploads/2016/10/8.jpg)

Remember that wire I made you buy, here’s where it goes… Attach two wires, one to RAW and one to GND, and make sure they are long enough to just come past the far end of the board (the end without the usb connector). Be sure to keep track of which goes where if you use the same color wire for both pins!

[![11](https://mrickert.com/wp-content/uploads/2016/10/11.jpg)](https://mrickert.com/wp-content/uploads/2016/10/11.jpg)
[![10](https://mrickert.com/wp-content/uploads/2016/10/10.jpg)](https://mrickert.com/wp-content/uploads/2016/10/10.jpg)

This next part may seem silly, but trust me, it matters. Place a small strip of electrical (or other kind, I prefer electrical) tape to the top of the usb connector, this will shield it from the wiring we will be soon placing on top of it, preventing shorts.

[![13](https://mrickert.com/wp-content/uploads/2016/10/13.jpg)](https://mrickert.com/wp-content/uploads/2016/10/13.jpg)
[![12](https://mrickert.com/wp-content/uploads/2016/10/12.jpg)](https://mrickert.com/wp-content/uploads/2016/10/12.jpg)

Nice! Things are going to start looking like a transponder soon… Now lets solder our first LED onto the board. You’ll want the anode (that’s the bit you bent outward, the smaller wire inside the led bulb side) to get soldered to the top of the resistor, while the cathode (the straight bit) to lay flat against the tape we just placed down. Aim the LED out at a 90deg angle as best you can for best results, and also note that the closer to the usb connector you get, the more crash resistant your transponder will be.

[![14](https://mrickert.com/wp-content/uploads/2016/10/14.jpg)](https://mrickert.com/wp-content/uploads/2016/10/14.jpg)
[![15](https://mrickert.com/wp-content/uploads/2016/10/15.jpg)](https://mrickert.com/wp-content/uploads/2016/10/15.jpg)

One more time… Now we attach the second LED in a similar fashion. Cathode to cathode and anode to anode, creating a triangle of awesome led power. Be careful here not to break your led’s off of your resistor, that solder point can get a bit fragile until we’re all done.

[![17](https://mrickert.com/wp-content/uploads/2016/10/17.jpg)](https://mrickert.com/wp-content/uploads/2016/10/17.jpg)
[![16](https://mrickert.com/wp-content/uploads/2016/10/16.jpg)](https://mrickert.com/wp-content/uploads/2016/10/16.jpg)

More silicone wire time! Take a very small amount of wire and solder the cathodes (the straight led pins at the top of the board) to the transistor (the black square thing with three legs). Be sure not to have the exposed parts of the wire touch anything else, as I know things are getting a bit cramped for space by now…

[![19](https://mrickert.com/wp-content/uploads/2016/10/19.jpg)](https://mrickert.com/wp-content/uploads/2016/10/19.jpg)
[![18](https://mrickert.com/wp-content/uploads/2016/10/18.jpg)](https://mrickert.com/wp-content/uploads/2016/10/18.jpg)

Let there be ligh….. I mean power! Connect the two wires you attached earlier, the ones going to RAW and GND pins, to your balance connector. (I found that tinning the pins on the balance connector made a huge impact here on ease of soldering). The RAW pin wire goes to the right-most pin if your looking at the balance connector from the back, as if it was facing away from you. The GND pin wire goes to the pin two to the left of that. If you have trouble just reference the pictures… A LOT! You don’t want to mix these two wires up, as that’ll fry the board and parts you so painstakingly installed earlier.

[![23](https://mrickert.com/wp-content/uploads/2016/10/23.jpg)](https://mrickert.com/wp-content/uploads/2016/10/23.jpg)
[![21](https://mrickert.com/wp-content/uploads/2016/10/21.jpg)](https://mrickert.com/wp-content/uploads/2016/10/21.jpg)

(Bonus wiring shot, just to make sure you don’t blow stuff up)

[![22](https://mrickert.com/wp-content/uploads/2016/10/22.jpg)](https://mrickert.com/wp-content/uploads/2016/10/22.jpg)

Almost there, only a few more steps… Place a small dab of hot glue on the back of the transponder, and then quickly press the balance connector into place, making sure the two ‘grooved’ bits in the white plastic case are facing upward tward you. If you can’t get it just right, don’t worry, this is just to help the next part get easier.

[![24](https://mrickert.com/wp-content/uploads/2016/10/24.jpg)](https://mrickert.com/wp-content/uploads/2016/10/24.jpg)

Glue ALL THE THINGS! (Ok, not really, be sure to leave the balance connector, leds, and usb connection exposed). Protip: I find the black hot glue to be much stronger and much stiffer than standard transparent glue. Don’t be afraid to really glob on the glue on the center of the board, the led’s should still shine through the balance connector, and you realllllly don’t want to have a short when you strap your first battery to this thing.

[![25](https://mrickert.com/wp-content/uploads/2016/10/25.jpg)](https://mrickert.com/wp-content/uploads/2016/10/25.jpg)

[Now grab yourself a copy of the software](https://github.com/RaceFPV/CoreIR) and get to flying!

(PS. A detailed write-up of installing/updating the software to follow soon)