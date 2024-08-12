+++
title = "ATH-M50x Headphone Repair"
weight = 1
+++

*Aug 1, 2024*

The saga of fixing my 8 year old headphones.

![Headphone Diagram from User Manual](/images/headphones/ath-m50x_repair_manual.png)
<!--more-->
[*[Diagram from a ATH-M50x User Manual](https://manuals.plus/audio-technica/audio-technica-ath-m50x-professional-studio-monitor-headphones)* ]


Audio Technica's ATH-M50x are my favorite headphones and the only pair that I've needed in my entire adult life. They have excellent sound, are comfortable, portable, and stylish. 

The only qualm  I have with the ATH-M50x headphones is the build quality: nearly every component on my headphones has been destroyed or has been broken (by me):
 * The faux leather on the headband and earpads has peeled off
 * The original 3 meter cable melted after being left over a candle
 * The left driver casing melted (also after being left over a candle)
 * The hinge notch on both the left and right hinge drums snapped, which is a common issue for these headphones, causing the ear pads to not fit properly on the head
 * The right driver wire frayed on the inside of the driver casing due to a sharp bend in the wire wrap rubbing on the injection molded plastic, causing fatigue failure in the casing and a shorted driver
 
The good thing is that all of those components are fixable or have cheap replacements online. Wires can be soldered and wrapped, ear pads are $30 on Amazon, and replacement hinges can be printed.

Working at the [Golisano Institute for Sustainability](https://www.rit.edu/sustainabilityinstitute/) has given me a newfound appreciation for reusing and repairing my things. It's far cheaper, waste friendly, and energy efficient to fix one part of a product than to completely replace the product - or in this case, many parts of the product. Repairability is a benefit to the consumer and the environment.

This is part of the reason why companies like Apple will always focus on replacing damaged components before handing you a new device. The other reason is money, of course. They won't sell new products if people just break them and the newest version is given to them for cheap. 

#### Repair Process:

![Headphone Driver Re-Soldering](/images/headphones/1_rounded.png)
*Finished Repair Procedure*

When the right driver died on my headphones, there was a priority of problems to fix that would determine how 'salvageable' my beloved ATH-M50xs were:
1. Repairing the right driver 
2. Design a permanent solution to fix the hinge
3. Purchase new ear pads
4. Re-wrap the headband

If I couldn't fix the right driver, the subsequent changes would be pointless, and I would be forced to buy a new pair.

#### Right Driver Problem:
![Right Driver PCB](/images/headphones/right_driver_wires_rounded.png)
*Right Driver PCB*

This black wire casing frayed over time due to fatigue, so I thought that I would cut the wire, split the copper & red connections, and call it a day. Foolish and incorrect. These wires are some type of [tinsel wire](https://en.wikipedia.org/wiki/Tinsel_wire) that contact inside of the casing (wrapped on themselves), meaning that there is a coating or plating that makes solder impossible to stick on, even with good flux. 

Folks on the internet recommended scraping at the wire casing with a knife to improve solderability, but these wires are too small for that. 

Instead, I had to completely disconnect and re-solder the left, right, and neutral driver wires that connect from the sound distribution PCB to the driver PCBs. 

![Sound Distribution PCB](/images/headphones/main_pcb_rounded.png)
*Sound Distribution PCB*

This PCB has three solder pad terminals: 
*  L (blue wire) pad for the left driver
*  R (red wire) pad for the right driver
*  Neutral (copper wires) pad that presents itself as two seperate pads, but only has one trace 

The neutral pads meet and go to the same ground pin, as seen in this picture:
![3.5 MM Audio Connector Diagram](/images/headphones/TRRS-Wiring-Diagram_rounded.png)

[*[3.5 MM Audio Connector Diagram from CircuitBasics](https://www.circuitbasics.com/how-to-hack-a-headphone-jack/)* ]

Those pads contact with the proprietary quick release connector that comes with the ATH-M50x.

I re-soldered all of the connections to the L and R drivers and tested it by adjusting the directional audio settings of my device between the L and R drivers to individually test each driver without the other playing noise. 

Thankfully, the solder job worked well enough. I just had one small problem: the wires I used were way too large to route through the original path, so the wires would be exposed between the drivers and the headband, where I would wrap the wire safely against the headband. 

I think the exposed wires look really cool, so this is a pro. It makes my headphones unique, as well. They're one of a kind. 

#### Hinge Fix Design:
![Original Hinge Design](/images/headphones/original_hinge_notch_rounded.png)

The yellow highlighted notch is what is supposed to keep the drivers and ear pads tight against the head, and is the problem part that broke. 

The solution is a small, 3D printed bracket that replaces the functionality of that notch. I modeled the solution in Fusion 360 and printed it on my Neptune 3. With M3 screws and a few grams of PLA, the notch should be restored. 

![New Hinge Design](/images/headphones/hinge_assembly_drawing_rounded.png)
*Hinge Redesign*

I printed a few sets of these, trying to dial in print settings, material, and the design. Failure on the left driver made it clear that a harder plastic like PLA was better suited to support the hinge. 

A wall thickness greater than 100 allows for 100% infill without the infill patern, creating a stronger matrix that resists deformation at the notch, which was a common problem, especially in the PETG parts.

#### Results:

![Final Repair Results](/images/headphones/final_repair_rounded.png)
*Completed Repair*

This is the finished product, a half melted, hacked together headset that allows me to give new life to my old headphones while making them look badass. It took about three or four hours to do all of the repair work by hand, and a few more idle hours for printing. 
