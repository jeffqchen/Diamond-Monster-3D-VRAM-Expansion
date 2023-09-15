# Diamond Monster 3D 3Dfx Voodoo 1 VRAM Expansion Mod

<img src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/2f89a707-f807-459f-97b8-f3c880af92d2" width=600>

## Introduction

The Diamond Monster 3D card is a 3Dfx Voodoo 1.

The Voodoo 1 normally comes with 4MB of RAM in total - 2MB for each of the main chip on the card - FBI (frame buffer interface) and TMU (texture mapping unit).

However, according to 3Dfx documentation, these chips support more RAM than just 2MB. Expecially for the FBI, 2MB and 4MB means big differences in capabilities, including higher resolution (800x600x16bit) with hardware-accelerated depth-buffering. Therefore, it makes sense to mod the card for the better.

<img src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/79b56bfa-d721-4157-8559-4019badfd301" width=600>

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/93f330f9-7383-4b24-9a43-68d8e4455c12">

Thanks to BitsUndBolts, Voodoo 1 cards with socket-spacing RAM chips can be modded with his [3Dfx Voodoo Memory Mod](https://github.com/BitsUndBolts/3Dfx-Voodoo-Memory-Mod).

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/b01b0e8b-c419-4c95-bd59-a764ce6469fb">

On the Diamond card, the FBI RAM chips were spaced too close to each others. The TMU chips also appear to be spaced slightly closer than the socketable one. Luckily, pin definition on the 3Dfx chips were the same. So I only had to design a solution to lead the signals off of the main board and interface with expansion RAM modules.

-----------

## Design

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/6a78ae95-489d-4c7f-a864-04bf8df0e8be">

The adapter boards have castellated holes to solder to the EDO RAM chip footprints on the main board. The female pin header is a 2x20 1.27mm pitched double-row SMD one. I made a cutout for the pin header to be mounted from the bottom of the board. This is to adapt to a more appropreate height, as well as making sure the adapter can't be easily ripped off of the adapter board when installing & removing RAM modules.

chttps://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/472ba2db-8931-4ce2-8bc3-ea0ea687fb51">

The RAM modules are tiny 4-layer PCBs with one EDO RAM chip on each side. The male pin header is a double-row 1.27mm-pitched one. You will need to build a total of eight RAM modules to complete the 8MB build.

This project is created with cost and availability in mind. Both pin headers are very common and cheap. The PCBs are relatively cheap to order. The EDO RAM chips are consistently in stock on eBay.

-----------

## Justification (or the lack of it)

Please be reminded that extra RAM does not bring any significant performance gain to the Voodoo 1 in most use cases. This is a pure functionality expansion, and the performance in that expanded scenario is miserable. There are very good reasons why 3Dfx ended up going with the 2+2 RAM configuration instead of more.

To complete this mod you will be soldering the following number of joints:
- FBI & TMU Board (2x)
  - Castellated Holes: (40-4)*4
  - SMD Headers: 40*4
  - SMD Resistors:2*2
- RAM Modules (8x)
  - J-pins: 40*2
  - Pin Headers: 40
- Main Chip Jumpers
  - Tiny Bodge Wires: 3
  - PCB Pads: 3
 
Total: 1582

I made about 3 errors out of 1582 pins in my personal attempt.

You will gain almost no extra performance out of this mod. But you will get a lot of practice soldering various types of joints!

BitsUndBolts [made a video](https://www.youtube.com/watch?v=zTUwuydDcZQ) benchmarking the cards before and after the RAM expansion.

-----------

## Parts

- PCB (Gerber files provided)
  - [1x] FBI Board - [Link]()
  - [1x] TMU Board - [Link]()
  - [8x] RAM Module Board - [Link]()
 
<img height="160" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/b8b9205b-0107-44e7-aa3c-269755408aeb"><img height="160" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/1109f469-fe2c-4502-8276-6e1dd250ec52"><img height="160" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/0df5e0c1-fc22-4932-b990-2e1e8559e8a3">
  
- Pin Headers  
  - [8x] Pin header, 2x20, male, 1.27mm pitched, double row, through hole - [Link]()
  - [8x] Pin header, 2x20, female, 1.27mm pitched, double row, SMD - [Link]()
 
<img height="160" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/725b7665-eebc-48eb-8a09-9cd296d3b2f1"><img height="160" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/b441ea16-a727-4f3f-bd0b-2f033d770f22">

  
- EDO RAM chip, 256K X 16 bit. Choices:
  - EliteMT M11B416256A-25J (also compatible with Voodoo 2)
  - Mosel Vitelic V53C16258HK30(or 45)
  - G-Link GLT44016-40J4-12 (or 15)
  - EtronTech Em614163A-50
  
- [4x] SMD Resistors, 47 Ohm, imperial 0805 size
- Very thin wire for extra signals. I used 30AWG enameled wire.

-----------

## Preparation

### Diamond Card

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/28a0d7db-5df0-41e3-a0df-c2632be3df03">

*Finished preparation on one bank*

Obviously the original RAM chips need to be desoldered from the card.

However, BEFORE doing so, test the card and make sure it runs fine.

My suggestion is to tin all the joints with small amounts of low-temperature solder (my choice is the "ChipQuik SMD1 Leaded Low Temperature Removal Kit"), and then remove with hot air. 

When low-temp solder is applied, hot air can be set to as low as 380ºC and still complete the job. Use circular motion and a nozzle that's not too small to apply the hot air.

Do NOT use prying action when removing the chip. Instead, stab the chips from the side until it moves, then quickly remove it with lateral action, instead of trying to lift it off.

After removing all the RAM chips, clean up all the residual solder from the board with soldering wick. Then, tin very small amounts of leaded solder to all the pads, so that they are easier to solder to the adapter boards.

Clean up the board with IPA.

Cut pieces of Kepton tape that are 6mm wide. Put them in the middle of the footprints where the female pin header would sit on. If your tape is too wide, cut a long piece and then use a ruler to cut the entire length to the width you want, instead of doing it piece by piece.

### Adapter Board

#### Cleaning Up Castellated Holes

The adapter boards have many castellated holes. Since the option to prep them costs A LOT of money, I suggest you do the cleaning on your own.

<img width="400" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/44d35ac7-a43c-4703-9651-675a875d929a"><img width="400" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/05bd24ff-efb5-44a5-8063-da71af1d6b0b">

*Before cleanup*

Start by using a very sharp & pointy tool, such as a pair of sharp tweezers, or a dental pick. Note all the castellated holes are in a state that the extra copper from the via is crushed and pushed into or swept to the sides.

Insert the pointy end of your tool into the center of the via and unfold/expand the hole back, so the extra copper that was supposed to be gone is sticking out side of the PCB. Check carefully and make sure no copper is folded onto the gap between the vias.

Then, using a very sharp blade, cut downwards along the edge of the PCB, to remove all the extra copper.

<img width="400" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/d48dc519-559e-4c36-ad26-84ee4f41477e"><img width="400" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/50492fda-cd41-4b2a-a8b1-94b161d8124a">

*After cleanup*

Finally, check all vias again and make sure no extra copper is folded into the gap between vias. If small amount of copper is sticking outwards, you can fold it into the via.

#### Solder On Signal Attenuation Resistors

Solder on the 47 Ohm resistor onto the adapter boards. Don't screw this one up.

#### Solder On Female Pin Headers

Check the connector with a thin needle and make sure all holes are open properly (you never know...)

Insert the pin headers through the slots from the bottom side of the board. Line up the legs with the SMD pads and solder them in. Make sure the connect is all the way in and there's no space between. Don't make big & blobby solder joints, since it will create unnecessary height and jack the board off of the main board.

<img width="400" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/349bd380-9dd0-44e0-a8b2-9dc24496b285"><img width="400" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/a7b15777-1146-458c-90bc-4211caebdc0d">

Double check all connections with a multimeter and magnifying glass.

**This step must be verified 100%. Mistakes in this step will be very difficult to fix once the adapter board is installed.**

### RAM Modules

Solder on the RAM chips first. Note the orientation on the silk screen. The pin 1 end is marked with a dot or a white line.

Do NOT mix different RAM chips. Make sure the two RAM chips on a module are of the exact same kind.

Locate the chip slightly away from the pin header side so they don't conflict with the headers.

Lastly, solder in the pin headers with the mating contacts (business end) towards the bottom side.

#### J-Pins Soldering Tips

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/c54c0f3d-772b-4f65-bbd3-5fd0f7dcc317">


- Jam the tip of your iron into the corner where the J-pin and the pad meets. Make sure the tip touches both of them
- Add sufficient solder from the side.
- Pull tip away/out along the SMD pad

#### Pin Header Soldering Tips

- Place male header over a female header.
- Push the male header into the female with the holes on a RAM module PCB

The following technique will make sure the pins are soldered straight. Otherwise rows of pins might buckle under heat and the row spacing becoming too tight.

- Start by soldering pins on two ends of the headers first. Adjust if it looks crooked from the side
- Drag solder all pins in with the help of flux.
- The pin headers take a lot of solder. Be prepared to feed a lot.
- Drag any excessive solder to the end with the help of flux, and wick off any that's left from the end.
- Remove the female header with finger nails from the two ends instead of the sides. When the gaps is big enough, use a ruler instead since it's easier.

-----------

## Installation

### Soldering Adapter Boards

Line up the adapter board with the RAM chip footprints on the card. Make sure everything looks symmetrical. Take a good look from the side to make sure the board is overall level. If not, you might have to check the bottom of the adapter board for solder blobs.

Tack down diagonal pins on the out-most edges. Then start soldering the pins one by one with some amounts of solder (they need quite a bit more than you would think). Make sure all joints appear full and healthy.

#### Castellated Holes Soldering Tip

<img width="300" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/57a5ab40-a3e0-4a25-9b84-a26413d2111e"><img width="300" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/b3d057e4-a2b7-4e1d-a1ae-ad56ffb37a3d"><img width="300" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/5b202a6d-6e22-43a3-b3ac-ff73b4b771f8">

Insert the tip of your iron in between the via and the pad. Make sure both are being heated.

Add solder from the top of the via. A considerable amount is needed.

Move the tip outwards along the SMD pad to form a full joint.

If the joint appears to be disconnected or not full, repeat the entire action and add a bit more solder.

The 1.27mm pitch may sound tight but they actually don't tend to bridge easily.

### Soldering FBI/TMU Pins To Adapter Boards

Extra pins have to be soldered to the respective pads on the adapter boards.

FBI Pin 180 & 199:

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/10bd17cc-03d2-4370-83c3-bb03dd7c5495">

TMU Pin 130:

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/a900492e-e65c-47ec-98c1-8905765aefd8">

Pin location marked with green dots in the pictures.

<img width="600" src="https://github.com/jeffqchen/Diamond-Monster-3D-VRAM-Expansion/assets/25773768/b99e9b84-2407-4c7a-b0ed-65d2043a7856">

After finishing, tack down the floating wires with tape.

#### Soldering tip

Add flux to the pin(s) to solder. With a clean tip, reflow the pin first. The motion should be along the direction of the pin, not sideways.

Add the tiniest amount of solder to your iron tip, then transfer it to the pin with the help of flux.

Tin the tip of the copper wire with solder, but make sure there is no solder blob on the wire.

Join the wire to the pin with your iron. A simple tap should do the job. Do NOT rub the pin & wire sideways since you might bend the pin.

### Insert RAM Modules

The easiest step.

Make sure the entire bank are of the same kind of chips. Mixing chips will introduce issues.

If the pin header does not want to go in, check the male pins first. Do not force it.

For the FBI bank, adding modules from right to left make it easier.

-----------

## Verification

Run the 3Dfx diagnostic utility called mojo. You should be seeing 4MB for both FBI and TMU.

The Diamond official driver info page does not reflect the actual amount of RAM and always shows 2MB and 2MB.

Run Unreal in Glide mode and set the resolution to 800x600. The game should run. If you see glitches, it's possible you are having some bad solder joints, or you might have overclocked the chip too much.

### Over-Clocking

The Diamond driver has that one slider that toggles between the stock 50MHz and overclocked 57MHz.

I have noticed that an 8MB card can't run at the full 57MHz anymore. However it runs fine at 55MHz with heatsinks on the main chips.

### Heat

I have the impression that the main chips generate more heat with more RAM installed. The TMU is the hottest and the attached heatsink reaches 58ºC under load at 55MHz. This is no joke and I suggest adding a heatsink and maybe even active cooling options such as an extra fan towards the heatsink.

-----------

# Special Thanks

BitsUndBolts
- [Twitter](https://twitter.com/BitsUndBolts)
- [YouTube](https://www.youtube.com/@bitsundbolts/)

-----------

Shield: [![CC BY-SA 4.0][cc-by-sa-shield]][cc-by-sa]

This work is licensed under a
[Creative Commons Attribution-ShareAlike 4.0 International License][cc-by-sa].

[![CC BY-SA 4.0][cc-by-sa-image]][cc-by-sa]

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-image]: https://licensebuttons.net/l/by-sa/4.0/88x31.png
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
