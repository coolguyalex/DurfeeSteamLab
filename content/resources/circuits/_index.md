---
title: "Circuits"
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)

A foundations page: ideas to learn before using the tools. The five-minute version is
written here by the lab; the suggested progression sends students to better interactive
material elsewhere. Page layout notes are in resources/arduino/_index.md.
-->

What a circuit is and how it behaves, before touching an Arduino or a patch cable. A few hours here makes the [Arduino](/resources/arduino/) and [synthesis](/resources/sound/) material much easier to follow.

## The five-minute version

- **Circuit:** a complete loop. Current only flows if there is an unbroken path from the power source, through the parts, and back.
- **Voltage:** the electrical push between two points, measured in volts. A battery supplies it.
- **Current:** the flow of charge around the loop, measured in amps.
- **Resistance:** how much a part opposes current, measured in ohms. Ohm's law ties the three together: voltage = current × resistance.
- **Switch:** a gap in the loop that can be closed. Open means no current. Closed means current can flow.
- **+, − and GND:** + is the higher-voltage side of a supply and − is the lower side. GND (ground) is the reference point that every other voltage is measured from. On the boards used here it is the same as the − side. Connecting + straight to GND with nothing in between is a short circuit.
- **LEDs** only work one way round, and always need a resistor in series to limit the current.

## Suggested progression

1. **Build and break circuits.** *Interactive* · [Circuit Construction Kit: DC](https://phet.colorado.edu/en/simulations/circuit-construction-kit-dc) - University of Colorado's PhET simulation. Add batteries, switches and bulbs, measure with a voltmeter and ammeter, and compare series with parallel. Runs in the browser, including on Chromebooks.
2. **Read the explanations.** *Read* · [What is Electricity?](https://learn.sparkfun.com/tutorials/what-is-electricity) then [Voltage, Current, Resistance, and Ohm's Law](https://learn.sparkfun.com/tutorials/voltage-current-resistance-and-ohms-law) - SparkFun.
3. **Read a diagram.** *Read* · [How to Read a Schematic](https://learn.sparkfun.com/tutorials/how-to-read-a-schematic) - SparkFun.
4. **Build one for real.** *Read* · [How to Use a Breadboard](https://learn.sparkfun.com/tutorials/how-to-use-a-breadboard) - SparkFun. Then go to the [Arduino Lab Guide](/resources/arduino/lab-guide/).

## Next

- [Arduino](/resources/arduino/) - put circuits under software control.
- [VCV Rack](/resources/sound/#vcv-rack) - the same idea of signals flowing through connected modules, applied to sound.
