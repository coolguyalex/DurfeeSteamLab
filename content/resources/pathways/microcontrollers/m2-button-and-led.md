---
title: "M2 Button and LED"
weight: 3
---

About 60 minutes. Digital input and output. Code with blanks to fill in.

## Goal

Make an LED light up while you hold down a button.

You'll learn: how a pin can listen (input) as well as act (output), how a breadboard connects parts, and why electricity needs a complete loop from power to ground.

## Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- 1 x LED
- 1 x 220 ohm resistor (red, red, brown)
- 1 x pushbutton
- 5 x jumper wires

## Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: button on pin 2, LED on pin 8.
{{% /admonition %}}

1. Unplug the board from the USB cable.
2. Connect a jumper wire from the Arduino GND pin to the blue (-) rail.
3. Push the LED into the breadboard so its two legs are in different rows. The longer leg is positive.
4. Connect the row of the shorter leg to the blue rail with a jumper wire.
5. Place the resistor from the row of the longer leg to an empty row. Connect that empty row to Arduino pin 8 with a jumper wire.
6. Press the button into the breadboard so it straddles the middle gap. Connect a jumper wire from one side to pin 2, and from the other side to the blue rail. **Checkpoint:** your wiring matches the diagram, row by row.

## Starter sketch (button_led.ino)

Three blanks are marked ____. Fill them in before you upload.

```cpp
const int buttonPin = 2;
const int ledPin = 8;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(ledPin, ____); // 1: is the LED an INPUT or an OUTPUT?
}

void loop() {
  int state = digitalRead(buttonPin);
  if (state == ____) { // 2: what does the pin read while the button is pressed?
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, ____); // 3: HIGH or LOW to turn the LED off?
  }
}
```

<details>
<summary>Answers (try first!)</summary>

1: `OUTPUT`. 2: `LOW`. 3: `LOW`.

The second one feels backwards. `INPUT_PULLUP` keeps the pin at `HIGH` when nothing happens. Pressing the button connects the pin to ground, so it reads `LOW`.

</details>

## Build it

1. Fill in the blanks, then plug in the board and click Verify.
2. Click Upload. **Checkpoint:** the LED lights while you hold the button and goes off when you let go.

## What's actually happening?

A pin set to `INPUT_PULLUP` listens. It reads `HIGH` or `LOW`, and nothing in between, which makes it a digital input. A pin set to `OUTPUT` acts. Your sketch asks one question over and over: is the button pressed? If it is, the LED gets power.

Electricity only flows in a complete loop. The LED's loop goes from pin 8, through the resistor and the LED, to the ground rail and back to GND. The resistor limits the current so the LED doesn't burn out.

## Try it

1. Flip it: make the LED stay on until you press the button.
2. Add a second LED on another pin that lights when the first one is off.
3. Challenge: make the LED switch on and off each time you press (a toggle). You'll need a variable that remembers the LED's state.

## If it doesn't work

- **The LED never lights:** the LED may be backwards. The longer leg goes toward the resistor. Also check that the blue rail is connected to GND.
- **The LED is always on:** both button wires may be on the same side of the gap, which keeps the button permanently connected. Move one to the other side.
- **The upload works but the button does nothing:** check that the button wire goes to pin 2, and that the sketch uses `buttonPin = 2`.
