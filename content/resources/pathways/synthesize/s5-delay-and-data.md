---
title: "S5 Delay and Data"
weight: 5
---

## Goal

Add an echo to your sound, then play a melody from a list of numbers. This is where data from the other pathways can drive your synthesizer.

## What you need

Pure Data and headphones. Your saw or sine patch from earlier. Optional: the scale numbers from DS3, or the log from M5. Time: about 45 minutes. Do it in two parts if needed.

## Part A: echo

### 1. Start with a short sound

Place and wire: `osc~ 440`, then `*~ 0.1`, then `dac~`. This is the same patch as S1.

Place a number box and connect it to the left inlet of `osc~ 440`. In run mode, change the number between 440 and 0 repeatedly to start and stop the sound. Zero makes a silent tone.

{{% checkpoint %}}
**Checkpoint:** you can make short tones by hand.
{{% /checkpoint %}}

### 2. Add the delay

Place two new boxes: `delwrite~ echo 1000` and `delread~ echo 300`. The first stores 1000 milliseconds of sound under the name "echo". The second reads it back 300 milliseconds later.

Wire the output of the `*~ 0.1` box to the input of `delwrite~ echo 1000` as well as to `dac~`.

Wire the output of `delread~ echo 300` to a new `*~ 0.4` box, and then to `dac~` (both inlets).

{{% checkpoint %}}
**Checkpoint:** when you play a short tone, you hear it again 0.3 seconds later, quieter.
{{% /checkpoint %}}

### 3. Feed the echo back

Also wire the output of `*~ 0.4` to the input of `delwrite~ echo 1000`.

{{% checkpoint %}}
**Checkpoint:** the echo repeats several times, getting quieter each time. Be careful: if the feedback number (0.4) is 1 or above, the echo never dies. Keep it below 0.7.
{{% /checkpoint %}}

## Part B: play numbers

### 4. Make a place to hold the numbers

Place an object box with `array define data 8`. This makes a list called data with 8 slots.

Place a message box (<kbd>Ctrl+2</kbd>) with this exact text:

```text
; data 0 440 494 523 587 659 587 523 494
```

Click it in run mode. (The semicolon at the start sends the numbers to the list named data. The first 0 is where to start. These are 8 note frequencies.)

{{% checkpoint %}}
**Checkpoint:** the list now holds eight pitches. Double-click the array define box to see them in a graph, if you want.
{{% /checkpoint %}}

### 5. Make a counter

Place these boxes and wire each to the next in a loop:

```text
metro 300
f
+ 1
mod 8
```

Wire the outlet of `mod 8` back into the right inlet of f. Also wire the outlet of f to `tabread data`.

Place a message box with 1 and another with 0, and wire both to the left inlet of `metro 300`. Clicking 1 starts the counter and 0 stops it.

{{% checkpoint %}}
**Checkpoint:** in run mode, the number coming out of f counts 0 to 7 and repeats.
{{% /checkpoint %}}

### 6. Read the numbers

Place `tabread data`. Wire the outlet of f to the inlet of `tabread data`. Wire the outlet of `tabread data` to the left inlet of `osc~ 440` (this replaces the number box).

{{% checkpoint %}}
**Checkpoint:** click the 1 message box. You hear a melody of 8 notes, repeating.
{{% /checkpoint %}}

## Try it

- Change the metro speed: `metro 150` is faster, `metro 600` is slower.
- Change the notes in the message box. Use the numbers from your DS3 scale (major scale from 440: 440, 493.88, 554.37, 587.33, 659.25, 739.99, 830.61, 880).
- Use data from M5: change the numbers in the message box to your own light readings, or scale them with * 2 so they fall in a pitch range you like. A sensor melody!
- Put the melody into your filter from S4, and into the echo from Part A.

## What's happening

`delwrite~` and `delread~` make an echo by storing sound and playing it back later. Feeding it back makes repeats. The counter loop makes the numbers 0 to 7 over and over. `tabread` reads the list at that position. So a plain list of numbers becomes a tune. Data that you collect (from the Microcontrollers pathway) or compute (in Data Science) can control sound this way. Turning data into sound is called sonification.

## If it doesn't work

- **No melody:** check that you clicked the 1 message box, and that DSP is on.
- **The same note repeats:** check that the outlet of `mod 8` goes back into the right inlet of f.
- **An error says "array:** no such array": check that the array is named exactly data, in both places.
- **The echo is too loud or doesn't stop:** lower the `*~ 0.4` number.
- **A box has a dashed outline:** check spelling.

{{% admonition type="note" title="Note" %}}
Pd steps are written from memory and have not been tested. Teacher: please build this once.
{{% /admonition %}}
