---
title: "Start Here"
weight: 1
---

A microcontroller is a tiny computer that can sense the world and act on it. Your Arduino can read a button or a light sensor, and it can switch an LED on and off. You'll write the instructions in a program called a sketch.

## The five projects

- [M1 Blink](/resources/pathways/microcontrollers/m1-blink/) - upload your first sketch.
- [M2 Button and LED](/resources/pathways/microcontrollers/m2-button-and-led/) - inputs, outputs and the breadboard.
- [M3 Light Dimmer](/resources/pathways/microcontrollers/m3-light-dimmer/) - read an analog sensor and watch the numbers.
- [M4 Raw vs Library](/resources/pathways/microcontrollers/m4-raw-vs-library/) - see what a digital sensor really sends.
- [M5 Data Logger](/resources/pathways/microcontrollers/m5-data-logger/) - save your readings and chart them.

## Your kit

- 1 x Arduino Uno
- 1 x USB data cable
- 1 x breadboard
- Jumper wires
- LEDs
- 220 ohm resistors
- 10 kilohm resistors
- 1 x pushbutton
- 1 x light sensor (LDR)
- 1 x DHT11 sensor

{{% admonition type="note" title="Note" %}}
Teacher to confirm: this list is a guess. Match it to your actual kit.
{{% /admonition %}}

## Set up on your Chromebook

You'll use the Arduino Cloud Editor in the Chrome browser. There is nothing to install.

1. Open app.arduino.cc and sign in. Your teacher will tell you which account to use.
2. Open the Cloud Editor and start a new sketch.
3. Plug your board in with a data USB cable. A light on the board turns on. **Checkpoint:** a light is on at the board.
4. Choose your board and port in the editor. Chrome asks to connect to a serial port. Pick your board in the list and click Connect. **Checkpoint:** the editor shows your board's name. Not sure which port is yours? Unplug the board and look at the list. Plug it back in and see which entry comes back. That one is yours.
5. To send a sketch to the board, click Verify (the check mark) first, then Upload (the arrow).
6. Keep the board plugged in until the upload finishes. Unplugging in the middle cancels it.

## The breadboard in four rules

- Holes in the same short row are connected to each other.
- The long rails along the sides carry power (+) or ground (-) the whole way down.
- The gap in the middle keeps the left and right halves apart.
- Unplug the board before you change any wiring.

## Ground rules

- Never connect 5V directly to GND.
- Every LED gets a resistor.
- Ask before you touch someone else's board.

## Words you'll meet

- **Sketch:** a program for an Arduino.
- **Upload:** sending your sketch from the computer to the board.
- **Pin:** a metal socket on the board where you connect a wire. Each pin has a number or a name like A0.
- **Digital and analog:** a digital signal has only two states, on (HIGH) or off (LOW). An analog signal can be anywhere in a range, like a dimmer switch.
- **Serial Monitor:** a window in the editor that shows messages your board sends back to the computer.
- **Library:** code that someone else wrote and shared, so you don't have to write it yourself.
- **CSV:** a plain text table where commas separate the columns and each line is a row. Spreadsheets can open it.
