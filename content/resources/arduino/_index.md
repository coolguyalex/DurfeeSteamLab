---
title: "Arduino"
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)

A LANDING PAGE FOR ONE TOOL. The other tool pages (circuits, music, sound, data-science,
design) follow the same pattern, so that students know where to look:
  1. a short introduction
  2. "Get set up": how to get the tool
  3. "Suggested progression": a numbered order that mixes outside tutorials and our own lab guide
  4. "Connections to other tools"
Each progression item starts with a type in italics (*Interactive*, *Read*, *Video*, *Lab guide*)
so a student can see at a glance what kind of material it is.
Prefer the official tutorial or the one the wider community recommends. Don't write a new one
unless nothing good exists. Links go in Markdown like this: [words](https://address).
Links to pages on this site start with a slash: [Circuits](/resources/circuits/).
-->

An Arduino is a small programmable board that reads sensors and controls lights, motors and sound. It is the usual starting point for anything in the lab that senses or moves. Code is written in the Arduino Cloud Editor, in the browser.

New to electronics? Start with [Circuits](/resources/circuits/) first.

## Get set up

- **Editor:** [app.arduino.cc](https://app.arduino.cc), free. Ask in room 3106 which account to use.
- **Runs:** in the Chrome browser. Chrome asks permission to talk to the board over USB.
- **No board handy?** Try circuits and code in a simulator first:
  - [Wokwi](https://docs.wokwi.com/) simulates Arduino and other boards in the browser. Free for personal use. Try the [Arduino Uno "Hello World"](https://wokwi.com/projects/322062421191557714).
  - [Tinkercad Circuits](https://www.tinkercad.com/circuits) is Autodesk's browser simulator.

## Suggested progression

1. **Know what a circuit is.** *Interactive* · [Circuits](/resources/circuits/) - batteries, switches, voltage and current, before any code.
2. **First sketches.** *Lab guide* · [Arduino Lab Guide](/resources/arduino/lab-guide/) - setup, then M1 Blink through M5 Data Logger: blink an LED, read a button, read a sensor, log data to a chart.
3. **Try variations in a simulator.** *Interactive* · Wokwi or Tinkercad Circuits, from above.
4. **Look things up.** *Read* · [Arduino documentation](https://docs.arduino.cc/learn/) and its [built-in examples](https://docs.arduino.cc/built-in-examples/) - short, tested sketches for most basic jobs.
5. **Go deeper on a specific part.** *Read* · [Adafruit Learning System](https://learn.adafruit.com) and [SparkFun tutorials](https://learn.sparkfun.com) - detailed guides for individual sensors and boards.

<span class="todo">[no interactive beginner Arduino course has been chosen yet; the lab guide stands in until one is]</span>

## Connections to other tools

The log from M5 can be analyzed in [Data Science](/resources/data-science/) (DS1) and played as sound with the [sound tools](/resources/sound/) (PD5 in Pure Data). A box for an Arduino can be designed in [Design](/resources/design/) (D3).
