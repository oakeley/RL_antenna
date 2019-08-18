# Waterproof swim-compliant RileyLink with wireless charging (in three steps, by @Edward) #

Some things to keep in mind... 3D parts are not waterproof. You can think of them as a sieve and under water the pressure is very high even at relatively low depths. This is sufficient to force water into most 3D designs. First off, you can paint the surface with acetone (nail varnish remover) and this will melt it just a tiny bit but enough to seal the plastic. 

## 1) MAKE A BETTER AERIAL
It is also important to remember that radio waves and water do not play nicely (this is why submarines use sonar not radar and drag their aerials hundreds of metres behind for morse code communications). Google "signal attenuation". Basically the higher the frequency, the worse it gets. 

Bluetooth uses 2.4GHz which for most CGM/phone combos gives a maximum range of about 5cm in fresh water and about 1cm in salt water. I use the Unihertz Atom (https://www.unihertz.com/atom) because it is waterproof and has an arm strap so you can strap the phone directly on top of the CGM (so long as you wear it on your arm). I tested this with a G6 and a Miaomiao/Libre with no problems in either a fresh water lake in Finland or the Atlantic ocean.

The omnipod uses 433MHz so the range "should" be 5.5x better than Bluetooth at the same number of decibels. Unfortunately the RL antenna is not very good and struggles to keep contact even in air sometimes. Radio theory tells us a few things to help: thicker aerial wires have less resistance which means more broadcast power; longer aerials work better than shorter ones.

The length of the aerial is very important (think tuning an analogue radio into a radio station, small movements of the dial - which change the aerial length - cause the station to quickly degrade into static). The aerial is normally either 1 wavelength, 1/2 wavelength or 1/4 wavelength.

Unfortunately the speed of light (radio is a kind of light) is also really important. 
The "optimum" aerial length in metres is (Speed of light in m/s)/(Frequency in Hz or "waves per second") so "metres/s" / "waves/s" = "metres * waves". To get the length, we make waves = 1, 0.5, 0.25 depending on the fraction of a wavelength we want...

Speed of light is 299'792'458 m/s, pod is 433 MHz which is 433'000'000 waves/s (does anyone know the real pod frequency?): 299'792'458/433'000'000 = 0.692361335 metre.waves which gives 69.24cm; 34.62cm; 17.31cm

The main issue is that these aerials are rather long so the solution used in the default RL aerial is to take a 1/4 wavelength aerial and wrap it in a tight coil. Unfortunately this coil is very directional in its signal so the risk of data loss is high if the aerial is not pointing at the pod. Bad data quality/signal strength = error 49 pod death and AAPS/SMB can have a lot of chatter with the pod.

I started experimenting using a very thin wire and a hybrid between a helix and a straight antenna.
![](http://oakeley.com/wiki/prototype_1.JPG). However for water communication, a straight aerial made of thick copper wire is best. Unfortunately, the best length design I am unable to explain as it came from 1) a mistake I made with the maths followed by a day of trial-and-error optimising the winding pattern for the "wrong" length. 2) The observation that with a "correct" length wire it didn't work nearly as well! 

For this project you will need the following things
1) Some 1.5mm2 single core mains electrical wire; 2) a 5x90 screw or a small screwdriver wwith a 2mm diameter shaft; 3) some string; 4) a ruler; 5) wire cutters; 6) a potato peeler: 7) some tape; 8) some epoxy resin; 9) a Qi-mobile phone wireless charger; 10) some acetone; 11) a 3D printed case (see below)

Measuring wire accurately is almost impossible because it is very hard to keep straight. Take some string and measure that to 26cm in length. Tape it every few cm to the wire. Add 5 mm to the end (you will have lost this much in tension errors) and cut.
![Bought at https://www.obi.ch/](http://oakeley.com/wiki/string.JPG)

Next you need to remove the plastic insulation. The easiest method I found was to use a standard home potato peeler and cut the plastic insulation off by just slicing parallel to the wire away from your body like peeling potatoes (the plastic does not burn or melt because mains wire is fire resistant and it is too long to pull off easily).
![strip away plastic](http://oakeley.com/wiki/wirestrip.JPG)
![](http://oakeley.com/wiki/wirestrip2.JPG)

![](http://oakeley.com/wiki/screws.JPG)

Measure 2cm from the end of the wire and put a mark with a pen. Measure an additional 17.3cm from the mark and put another mark, wrap the the wire tightly around the thread of a 5x90 screw. You then need to squash the loops together to make them effective (I don't know why) but it also takes up less space if you do this.
![](http://oakeley.com/wiki/withscrew.JPG)

Alternatively, if you have a 2mm diameter small screwdriver then you can wrap the wire around that instead. It is easier to make tight coils on a screwdriver. Coil until you reach the mark. Your coil should be 17.3cm (1/4 wavelength).
![](http://oakeley.com/wiki/withoutscrew.JPG)

Measure the length of the wire below the coil and trim it to 1.73cm (1/40 wavelength). Measure the long end of the wire and trim it to 6.9cm (1/10 wavelenght): 1.73 + 17.3 + 6.9 = 25.93cm (like I said, a stupid length)
![](http://oakeley.com/wiki/aerial26.JPG)

Press a kitchen knife gently between each loop of the helix and wiggle just a bit. Check that none of the turns in the coil actually touch each other using a bright light behind the coil (this is important or you get a bad signal again).
![](http://oakeley.com/wiki/wiggle.JPG)
![](http://oakeley.com/wiki/post-wiggle.JPG)

Remove the aerial from the RL either by melting the solder (best) or using nail clippers (if it is stuck and really won't budge).
![](http://oakeley.com/wiki/noaerial.JPG)

Then solder the new aerial onto the same spot (put a small bit of flux on the copper wire to ensure it sticks before you apply the solder)
![](http://oakeley.com/wiki/best_position.JPG)

**Tune the aerial with nail clippers** checking the signal strength all around it is as strong as possible. You need to check along the sides and end-on. Check the signal strength at 1m, 5m, in the next room, upstairs. An oscilloscope is safest but you can try with a real pod also (but it may fail). The optimum length will be somewhere between **5.6cm-6.4cm** (seems to depend on the the coil density but it may also be that the best total length is 1/3 wavelength for this design (17.3+5.7 = 23cm which is about 1/3 of 69.2cm) again, no idea why... you can bend the long wire and force it into a box 
![](http://oakeley.com/wiki/bent.JPG)
or for a longer range. Melt a small hole in the box using a soldering iron and have the copper stick out (much better range)
![](http://oakeley.com/wiki/longaerial.JPG)

Does it work? Yes!
![](http://oakeley.com/wiki/prim_good2.JPG)

I put the phone/pi/hacked RL on the side of the bath, put a test pod in the bath stuck to the bottom using insulet pad under pod and started sending 2 unit bolus commands at different depths in open loop mode (via omnipy). Each tested twice with a five minute wait). Number is water depth

0 cm: obviously works
10 cm: instant response
20 cm: instant response
30 cm: delivery took 30 seconds for first attempt, adjusted RL position and second completed after 20 seconds
~40 cm: bolus not received, error 49 on second attempt (30cm ruler so exact measurement hard, this is the limit of my bath also!)

Obviously, your mileage may vary but unobstructed error free comms for at least 20cm underwater is a huge improvement.
![](http://oakeley.com/wiki/bath_test_10cm.JPG)

## 2) ADD A WIRELESS CHARGING LOOP
If you look on the underside of the RL, you will see two holes which are labelled "Alt.PWR" on the top side. These can be used for direct charging of the RL battery. Note carefully the + and -.
![](http://oakeley.com/wiki/wirelessRL2.JPG)
The charging loop has a top and a bottom. The plug will wrap up to the side that should be away from the charger. Note the + and -. These refer to the two outer most wires on a microUSB charger (the cheapest). Cut off the plug and carefully solder the + on the charger to the + on the underside of the RL. Solder the - to the -. It may be easier to use a bridging wire.
![](http://oakeley.com/wiki/wirelessSheet.JPG)
If all goes well you will have something like this. If you place it on a Qi charger the red LED should come on. You may have to move it about to find the best position (*note picture shows a less good earlier aerial design. Don't bend the aerial back on the itself, it must point away from the RL*)
![](http://oakeley.com/wiki/charge.JPG)

## 3) MAKE A BOX AND WATERPROOF EVERYTHING
I made a rectangular box with a lid at the narrow end in Fusion-360. It is best to use not more than a 1mm thickness of plastic or it will make the charging less effective. White plastic enables the LEDs to be visible.
The STL file can be downloaded from here: http://oakeley.com/wiki/RL_big_aerial_Swim.stl
![](http://oakeley.com/wiki/box0.JPG)

This is what it looks like for real:
![](http://oakeley.com/wiki/box1.JPG)
![](http://oakeley.com/wiki/box2.JPG)
![](http://oakeley.com/wiki/box3.JPG)
It was printed in "Standard PETG (FDM)", Colour: White, 20% infill, 100μm

To waterproof "properly" paint all the electronics with epoxy. For a "good enough effort", paint the entire box inside and out with acetone (nail varnish remover). When it is dry put the electronics inside and epoxy the lid shut.
