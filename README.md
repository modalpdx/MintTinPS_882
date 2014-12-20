#MintTinPS_882

A simple power supply board for "standard" mint tins. Examples: Altoids,
Penguin Mints, Mintz. The board is sized/shaped to fit in the tin while
still allowing enough room for up to three AA batteries in an open holder
and a mini-toggle to switch the power supply on/off.

[*Note: There are current limitations with this design that drove me to
design a more powerful board: the MintTinPS_604 which uses a MAX604
regulator instead of a MAX882 regulator. I recommend you skip this board
and go with that one instead. I'll leave these files here because why
not...*]

This version of the mint tin power supply uses a [**Maxim MAX882 linear voltage regulator**](http://www.maximintegrated.com/en/products/power/linear-regulators/MAX882.html "MAX882 Info"), which gives us the following output voltage options:

* Default voltage: 3.3V
* Adjustable voltage: 1.25V to 11V

The adjustable voltage is activated by setting a jumper (ADJV). If the
jumper is open, you get 3.3V.

##Parts
* Maxim MAX882 voltage regulator (8 pin DIP)
* 8 pin DIP socket (optional, but smart)
* 0.1uF capacitor (ceramic, C2 on the board)
* 2.2uF capacitor (polarized, C1 on the board)
* 10k Bourns trimmer potentiometer (3306)
* 2-pin male header (2.54mm/0.1") & jumper

Optional for power connection:
* 2 x 2 male header (2.54mm/0.1"), right-angled 
* Two 1 x 2 female headers (2.54mm/0.1") for power wires

Other:
* "Standard" size mint tin (ex: large Altoids/Mintz/Penguin Mints tin)
* .125" spacers (I'm guessing adhesive, nylon) if spacers are your thing
* Something else to fully insulate the bottom of the board

##Setting the adjustable voltage

The level of the adjustable voltage is set with a trimmer potentiometer on
the board. Connect the output power wires (POW|out) to a multimeter, set
the multimeter to read DC voltage, then turn the potentiometer until you
have your desired voltage. You are limited by the voltage that is put out
by your batteries (there is no boost circuitry in this power supply).
Also, make sure you are not powering any components with the power supply
when you adjust the voltage.

##Implementation

I intentionally left the power connections (POW|in/out) generic so you can
connect whatever battery you wish to connect in the manner in which you'd
like to connect it, *as long as you keep in mind that your power source
has to be between 2.7V and 11.5V*. 

Until 5V goes out of fashion, I'm using a 9V battery with this. No
combination of inline AA or AAA batteries will get high enough voltage to
provide >5V and still fit in a mint tin.  When 5V goes away, three AA
batteries should work.

The use of a jumper for switching voltages was intentional. Anything that
can switch from a lower to a higher voltage should involve some user
experience "friction." If the voltage switch is exposed on the outside of
the tin, it could be accidentally bumped. Depending on what voltage was
switched to, this could result in fried components. Keeping the voltage
switching experience inside the tin makes more sense.

There are no LEDs for power status, either. Feel free to add them if you
like. I wanted all power to go to the circuit I'm designing, not
blinkenlights.

##Limitations

* Input voltage range: 2.7V to 11.5V
* Output voltage range: 1.25V to 11V (input voltage limits upper value)
* Non-adjustable voltage: 3.3V
* No voltage boost capabilities
* Maximum current: 200mA
* Linear regulators are not the most efficient

This is a perfectly capable power supply for breadboarding. If you need a
power supply for something else, this isn't it. 

##Motivation

I wanted to have a small breadboard/power supply combo that would be
compact, self-contained, and offer two voltages. There are projects on the
Internet that do this already but they either skimp on the voltages (only
offer one, typically 5V) or they default to 5V and 9V (I have never needed
9V on a breadboard before, and I probably never will). 

I also wanted to future-proof the power supply.
Right now the common component voltages seem to be 3.3V and 5V, but 5V
components are becoming less common. It makes more sense to have a power
supply that offers 3.3V plus one adjustable voltage, so when 5V goes away,
I'll still have 3.3V and one other up-and-coming voltage (looks like 2.5V
may be the next one).

##Miscellaneous Notes

If you want the power supply to default to 5V instead of 3.3V, the Maxim
MAX883 should be a drop-in replacement for the MAX882. This chip would
give you everything the MAX882 offers but the non-adjustable voltage would
be 5V. The adjustable voltage is handled identically to the MAX882.

The first run of PCBs from DirtyPCBs has been tested and they work fine.
With the jumper out I get 3.3V and with the jumper in I get my adjustable,
dialed-in voltage.

##VERSIONS

0.1 - Initial version.

0.2 - Fixed arrangement of power pins, mount holes now .125", fixed silk
on bottom, fixed C1 on schematic.

