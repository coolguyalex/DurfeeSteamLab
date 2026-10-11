---
title: "Reference"
weight: 7
---

Quick answers to keep open while you build.

## Code you'll use

- `pinMode(pin, OUTPUT)` - makes a pin send signals out. Use `INPUT_PULLUP` to listen.
- `digitalWrite(pin, HIGH)` - turns a pin on (5 V). `LOW` turns it off.
- `digitalRead(pin)` - reads a pin as `HIGH` or `LOW`.
- `analogRead(pin)` - reads a voltage as a number from 0 to 1023.
- `analogWrite(pin, value)` - dims an LED. The value runs from 0 to 255.
- `map(x, a, b, c, d)` - converts x from the range a to b into the range c to d.
- `delay(ms)` - waits for that many milliseconds.
- `Serial.begin(9600)` - starts the connection to the Serial Monitor.
- `Serial.println(x)` - prints x and starts a new line.

## Parts at a glance

- **220 ohm resistor:** red, red, brown bands.
- **10 kilohm resistor:** brown, black, orange bands.
- **LED:** the longer leg is positive. The flat edge of the rim is on the negative side.
- **Pushbutton:** four legs. Legs on the same side are always connected. Pressing connects the two sides.

## Nothing works? Check in this order

1. Is a light on at the board?
2. Is the right board and port selected in the editor?
3. Does Verify pass with no red errors?
4. Does your wiring match the diagram, row by row?
5. Is the ground rail connected to GND?
6. Unplug the board, plug it back in, and upload again.
7. Read your wiring out loud to a classmate and ask them to follow it on the diagram.
