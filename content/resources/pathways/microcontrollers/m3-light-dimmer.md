---
title: "M3 Light Dimmer"
weight: 4
---

About 75 minutes. Analog input. Working code to change.

## Goal

Use a light sensor to control how bright an LED glows, and watch the sensor's numbers in the Serial Monitor.

You'll learn: how an analog sensor differs from a button, how to read a number from a sensor, and how to print it.

## Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- 1 x LED and 1 x 220 ohm resistor
- 1 x light sensor (LDR)
- 1 x 10 kilohm resistor (brown, black, orange)
- Jumper wires

## Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: LED on pin 9, LDR and 10 kilohm divider on A0.
{{% /admonition %}}

1. Unplug the board. Rebuild the LED circuit from M2, but connect the resistor's empty row to pin 9 this time.
2. Connect Arduino 5V to the red (+) rail.
3. Put the light sensor in the breadboard with its legs in two different rows. Connect the first row to the red rail.
4. Place the 10 kilohm resistor from the sensor's second row to the blue rail.
5. Connect a jumper wire from the sensor's second row (where the sensor and the resistor meet) to Arduino pin A0. **Checkpoint:** your wiring matches the diagram, row by row.

## Starter sketch (light_dimmer.ino)

This one already works. You'll change it in the Try it section.

```cpp
const int sensorPin = A0;
const int ledPin = 9;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int light = analogRead(sensorPin); // a number from 0 to 1023
  int brightness = map(light, 0, 1023, 255, 0); // flip it: dark room = bright LED
  analogWrite(ledPin, brightness); // 0 is off, 255 is full
  Serial.println(light);
  delay(50);
}
```

## Build it

1. Paste the sketch, Verify, then Upload. **Checkpoint:** the LED gets brighter when you cover the sensor with your hand.
2. Open the Serial Monitor tab in the editor and set the speed to 9600. **Checkpoint:** numbers scroll past, and they change when you cover the sensor.
3. Cover the sensor, then shine a phone flashlight on it. Write down the lowest and highest numbers you see.

## What's actually happening?

analogRead measures the voltage on a pin and gives you a number from 0 (0 volts) to 1023 (5 volts). The button in M2 had only two states. A light sensor can give any number in between, which makes it an analog sensor.

The sensor changes its resistance with light, and the 10 kilohm resistor turns that change into a voltage your board can measure. analogWrite sends the LED a fast on-off pulse pattern, and the more time it spends on, the brighter the LED looks. `map()` converts a number from one range to another.

## Try it

1. Your real lowest and highest readings probably aren't 0 and 1023. Put your own numbers into `map()` so the LED uses its full range.
2. Change the sketch so the LED is brighter in the light and dimmer in the dark.
3. Challenge: make the LED blink faster as the room gets darker. Hint: use the reading to set the `delay()`.

## If it doesn't work

- **The numbers are stuck at 0 or 1023:** check that the 10 kilohm resistor is connected, and that the A0 wire is in the row where the sensor and the resistor meet.
- **The Serial Monitor shows garbled text:** the speed must match the sketch. Set the monitor to 9600 to match `Serial.begin(9600)`.
- **The LED doesn't change:** make sure the LED wire goes to pin 9, not pin 8. Only some pins can dim an LED.
