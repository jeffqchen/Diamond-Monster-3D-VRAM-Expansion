# Diamond Monster 3D 3Dfx Voodoo 1 VRAM Expansion Mod

## Introduction

[IMAGE]

The Diamond Monster 3D card is a 3Dfx Voodoo 1.

The Voodoo 1 normally comes with 4MB of RAM in total - 2MB for each of the main chip on the card - FBI (frame buffer interface) and TMU (texture mapping unit).

However, according to 3Dfx documentation, these chips support more RAM than just 2MB. Expecially for the FBI, 2MB and 4MB means big differences in capabilities, including higher resolution (800x600x16bit) with hardware-accelerated depth-buffering. Therefore, it makes sense to mod the card for the better.

[IMAGE]

Thanks to BitsUndBolts, Voodoo 1 cards with socket-spacing RAM chips can be modded with his [3Dfx Voodoo Memory Mod](https://github.com/BitsUndBolts/3Dfx-Voodoo-Memory-Mod).

[IMAGE]

On the Diamond card, the FBI RAM chips were spaced too close to each others. The TMU chips also appear to be spaced slightly closer than the socketable one. Luckily, pin definition on the 3Dfx chips were the same. So I only had to design a solution to lead the signals off of the main board and interface with expansion RAM modules.

-----------

## Design

[IMAGES]

The adapter boards have castellated holes to solder to the EDO RAM chip footprints on the main board. The female pin header is a 2x20 1.27mm pitched double-row SMD one. I made a cutout for the pin header to be mounted from the bottom of the board. This is to adapt to a more appropreate height, as well as making sure the adapter can't be easily ripped off of the adapter board when installing & removing RAM modules.

[IMAGE]

The RAM modules are tiny 4-layer PCBs with one EDO RAM chip on each side. The male pin header is a double-row 1.27mm-pitched one. You will need to build a total of eight RAM modules to complete the 8MB build.

This project is created with cost and availability in mind. Both pin headers are very common and cheap. The PCBs are relatively cheap to order. The EDO RAM chips are consistently in stock on eBay.

-----------

## Justification

Please be reminded that extra RAM does not bring any significant performance gain to the Voodoo 1 in most use cases. This is a pure functionality expansion, and the performance in that expanded scenario is miserable. There are very good reasons why 3Dfx ended up going with the 2+2 RAM configuration instead of more.

BitsUndBolts [made a video](https://www.youtube.com/watch?v=zTUwuydDcZQ) benchmarking the cards before and after the RAM expansion.

-----------

## Parts

- PCB (Gerber files provided)
  - [1x] FBI Board - [Link]()
  - [1x] TMU Board - [Link]()
  - [8x] RAM Module Board - [Link]()
  
- Pin Headers  
  - [8x] Pin header, 2x20, male, 1.27mm pitched, double row, through hole - [Link]()
  - [8x] Pin header, 2x20, female, 1.27mm pitched, double row, SMD - [Link]()
  
- EDO RAM chip, 256K X 16 bit. Choices:
  - EliteMT M11B416256A-25J (also compatible with Voodoo 2)
  - Mosel Vitelic V53C16258HK30(or 45)
  - G-Link GLT44016-40J4-12 (or 15)
  - EtronTech Em614163A-50
  
- [4x] SMD Resistors, 47 Ohm, imperial 0805 size
- Very thin wire for extra signals

-----------

## Preparation

### Diamond Card

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

Start by using a very sharp & pointy tool, such as a pair of sharp tweezers, or a dental pick. Note all the castellated holes are in a state that the extra copper from the via is crushed and pushed into or swept to the sides.

Insert the pointy end of your tool into the center of the via and unfold/expand the hole back, so the extra copper that was supposed to be gone is sticking out side of the PCB. Check carefully and make sure no copper is folded onto the gap between the vias.

Then, using a very sharp blade, cut downwards along the edge of the PCB, to remove all the extra copper.

Finally, check all vias again and make sure no extra copper is folded into the gap between vias. If small amount of copper is sticking outwards, you can fold it into the via.

#### Solder On Signal Attenuation Resistors

Solder on the 47 Ohm resistor onto the adapter boards. Don't screw this one up.

#### Solder On Female Pin Headers

Check the connector with a thin needle and make sure all holes are open properly (you never know...)

Insert the pin headers through the slots from the bottom side of the board. Line up the legs with the SMD pads and solder them in. Make sure the connect is all the way in and there's no space between. Don't make big & blobby solder joints, since it will create unnecessary height and jack the board off of the main board.

Double check all connections with a multimeter and magnifying glass.

**This step must be verified 100% since mistakes in this step will be very difficult to fix once installed.**

### RAM Modules

Solder on the RAM chips first. Note the orientation on the silk screen. The pin 1 end is marked with a dot or a white line.

Do NOT mix different RAM chips. Make sure the two RAM chips on a module are of the exact same kind.

Locate the chip slightly away from the pin header side so they don't conflict with the headers.

Lastly, solder in the pin headers with the mating contacts (business end) towards the bottom side.

#### J-Pins Soldering Tips

- Jam the tip of your iron into the corner where the J-pin and the pad meets. Make sure the tip touches both of them
- Add sufficient solder from the side.
- Pull tip away/out along the SMD pad

#### Pin Header Soldering Tips

- Place male header over a female header.
- Push the male header into the female with the holes on a RAM module PCB


- Solder the header onto the populated RAM module PCB
  - Start by soldering two ends of the headers first. Adjust if it looks crooked from the side
  - Drag solder all pins in with the help of flux.
  - The pin headers take a lot of solder. Be prepared to feed a lot.
  - Drag any excessive solder to the end with the help of flux, and wick off any that's left from the end.

-----------

## Installation

### Soldering Adapter Boards

Line up the adapter board with the RAM chip footprints on the card. Make sure everything looks symmetrical. Take a good look from the side to make sure the board is overall level. If not, you might have to check the bottom of the adapter board for solder blobs.

Tack down diagonal pins on the out-most edges. Then start soldering the pins one by one with some amounts of solder (they need quite a bit more than you would think). Make sure all joints appear full and healthy.

#### Castellated Holes Soldering Tip

Insert the tip of your iron in between the via and the pad. Make sure both are being heated.

Add solder from the top of the via. A considerable amount is needed.

Move the tip outwards along the SMD pad to form a full joint.

If the joint appears to be disconnected or not full, repeat the entire action and add a bit more solder.

The 1.27mm pitch may sound tight but they actually don't tend to bridge easily.

### Soldering FBI/TMU Pins To Adapter Boards

Extra pins have to be soldered to the respective pads on the adapter boards.

Pin location shown as in the pictures

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