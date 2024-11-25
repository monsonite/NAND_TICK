# NAND_TICK
A 16-bit Serial CPU in NAND Logic

NAND TICK is one of a family of experimental bit-serial CPUs, intended for home construction from common parts.

It was designed as a follow-on to the earlier TICK, which was built from 74HCxx logic devices.

It began with the idea, that if a "ficticious" 16-bit universal shift  register (Parallel to Serial, and Serial to latching patallel) was available in a 40 pin DIL package, then this would gratly reduce the complexity and inventrory required to build a 16-bit bit-serial machine.

Such a device was created using H.Neemann's "Digital" simulator (here on Github) entirely using NAND gates. This means tht such a device could be built using whichever logic is available, be it 74HCxx, discrete DTL, LED-DTL, or discrete CMOS.

The device has both parallel inputs, and latching parallel outputs, plus serial in and out. It can therfore be used as an Accumulator, a general purpose register or a Program Counter. When fully populated with all functionality, it uses just less than 200, three-input NAND gates, mostly arranged as D-type flipflops.

As it mostly resembles a double length 74xx595, I have called it the KB595. A simpler version without the parallel latched outputs is the KB165, as it is similar to a double length 74xx165 PISO shift register.

Two other custom circuits are used in the design. The KB74 provides a clock-sequencer and timing pulse generator, consisting of a 4 bit counter and a chain of 4 flipflops. It is the equivalent of 53 NAND gates, mostly 3-input, but some 2 and 4 input too.

The last of the parts is called "Combo".  It consists of a bit-serial ALU, a half-adder incrementer circuit for the Program Counter and some instruction decoding logic. It is the equivalent of 62 NAND gates, a mix of 2, 3 inputs and some inverters.

A minimal design would typically be three of the shift registers, (Accumulator, B-Register and Program Counter), a KB74 clock sequencer and a Combo. Such a circuit would be approximately 700 transistors if using DTL or LED-DTL gates.

Any of these "chips"  can be opened - so the underlying logic and functionality can be inspected.

If converted to disctete LED DTL logic, using through hole components the shift register woyld be about 240mm x100 mm. Combo and the KB74 plus ROM and RAM would fit on a similar sized board. These could be rack mounted with a simple bus running between them.

NAND_TICK_13 is a half-way house to a working CPU.  It require the ROM to drive the instruction inputs on the Combo chip, and RAMs with read-write control logic to be added. It would probably be a good idea to provide an Input/Output register so that data can be passed in and out via SPI transfers. These additions would complete a working design in fewer than 1000 discrete transistors.



