---
title: "M1 Blink"
weight: 2
---

About 30 minutes. Nothing to wire. Full code provided.

## Goal

Upload your first sketch and make the light on the board blink.

You'll learn: what a sketch is, what `setup()` and `loop()` do, and how to change a number and upload again.

## Parts

- 1 x Arduino Uno
- 1 x USB data cable

## Starter sketch (blink.ino)

```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH); // LED on
  delay(1000); // wait 1000 milliseconds
  digitalWrite(LED_BUILTIN, LOW); // LED off
  delay(1000);
}
```

## Build it

1. Open a new sketch in the Cloud Editor and name it Blink.
2. Delete everything in the editor, then paste in the starter sketch.
3. Click Verify. **Checkpoint:** no red error messages appear.
4. Click Upload and wait for it to finish. **Checkpoint:** the small light marked L on the board blinks.
5. Change both 1000s to 200 and upload again. **Checkpoint:** it blinks faster.

## What's actually happening?

Every sketch has two parts. `setup()` runs once when the board starts. `loop()` runs again and again, forever.

digitalWrite sets a pin to `HIGH` (5 volts, on) or `LOW` (0 volts, off). `delay(1000)` waits 1000 milliseconds, which is one second. `LED_BUILTIN` is a nickname for the pin that the small light on the board is wired to.

## Try it

1. Make the light stay on for 100 milliseconds and off for 900.
2. Make a heartbeat: two quick blinks, then a pause.
3. Challenge: blink out S.O.S. in Morse code (three short, three long, three short).

## If it doesn't work

- **The upload fails:** check that your cable carries data (some only charge) and that a light is on at the board. Unplug it, plug it back in, and choose the port again.
- **Red error text appears:** read the line number in the message. The usual causes are a missing semicolon ; or a missing curly brace }. Compare your sketch with the starter, character by character.
- **The upload worked but nothing blinks:** look for the small light marked L, not the steady power light.
