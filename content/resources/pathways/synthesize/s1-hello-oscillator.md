---
title: "S1 Hello Oscillator"
weight: 1
---

## Goal

Make your first sound: a steady tone from an oscillator, with a volume control that keeps it safe for your ears.

## What you need

Pure Data open in your browser (see the Synthesize page for the link), and headphones. Time: about 20 minutes.

## Steps

### 1. Turn the volume down

Turn your Chromebook volume low. Put on headphones.

### 2. Open a new patch

Open a new empty patch in Pure Data. Click on the patch so it has focus.

{{% checkpoint %}}
**Checkpoint:** you see a blank patch window.
{{% /checkpoint %}}

### 3. Make the oscillator

Press <kbd>Ctrl+1</kbd> to place an object box. Type `osc~ 440` and click on an empty part of the patch.

{{% checkpoint %}}
**Checkpoint:** a box that says `osc~ 440` with one outlet at the bottom and two inlets on top.
{{% /checkpoint %}}

### 4. Make the volume control

Press <kbd>Ctrl+1</kbd> again and place a second box under the first. Type `*~ 0.1` and click on an empty space.

{{% checkpoint %}}
**Checkpoint:** a box that says `*~ 0.1`. This multiplies the sound by 0.1, which makes it much quieter.
{{% /checkpoint %}}

### 5. Make the speaker box

Press <kbd>Ctrl+1</kbd> once more and place a third box at the bottom. Type `dac~` and click on an empty space.

{{% checkpoint %}}
**Checkpoint:** a box that says `dac~`. It has two inlets: the left speaker and the right speaker.
{{% /checkpoint %}}

### 6. Connect them

Drag a wire from the outlet of `osc~ 440` (bottom left) to the left inlet of `*~ 0.1`. Then drag a wire from the outlet of `*~ 0.1` to the left inlet of `dac~`, and another wire from the same outlet to the right inlet of `dac~`.

{{% checkpoint %}}
**Checkpoint:** three wires. The sound goes oscillator, then volume, then both speakers.
{{% /checkpoint %}}

### 7. Turn the sound on

Turn DSP on (the checkbox or button labeled DSP or "audio on").

{{% checkpoint %}}
**Checkpoint:** you hear a steady quiet tone. It is the note A.
{{% /checkpoint %}}

### 8. Change the volume

Turn DSP off. Double-click on the `*~ 0.1` box while in edit mode, change 0.1 to 0.3, click away, and turn DSP on again.

{{% checkpoint %}}
**Checkpoint:** the tone is louder. Be careful. Do not go above 0.5.
{{% /checkpoint %}}

## Try it

- Change 440 to 220 and then 880. Which is higher? Which is lower?
- Place a number box (<kbd>Ctrl+3</kbd>) and connect it to the left inlet of `osc~`. In run mode, click and drag it up and down to change the pitch while the sound plays.
- Place a second `osc~` and send it to the same `*~` box. Listen to two tones at once.

## What's happening

`osc~` makes a sine wave at the frequency you give it. The number after `osc~` is the frequency in Hz. The wave is a list of numbers made 44,100 times each second. The `*~` multiplies each number, so a smaller number gives a smaller wave and a quieter sound. `dac~` (digital to analog converter) sends the numbers to your speakers.

## If you hear nothing

- **DSP isn't on:** turn it on.
- **The volume is too low:** raise the `*~` number a little, or turn up the Chromebook volume.
- **A wire is missing:** check that all three wires are there.
- **The browser is blocking sound:** click once on the page, and check the site's sound permission in Chrome.
- **A box has a dashed border:** Pd doesn't know that word. Check your spelling, including the ~.

{{% admonition type="note" title="Note" %}}
Pd steps are written from memory and have not been tested. The browser version of Pd may use different menu names. Teacher: please try this once.
{{% /admonition %}}
