---
title: "S3 Waveforms"
weight: 3
---

## Goal

Hear how three wave shapes (sine, saw, square) sound different at the same pitch, and learn to build each one from simple boxes.

## What you need

Pure Data and headphones. Time: about 30 minutes. You can start a fresh patch.

## Steps

### 1. Start with the safe output

Place these two boxes, with the `*~` above the `dac~`, and wire `*~ 0.1` to both inlets of `dac~`:

```text
*~ 0.1
dac~
```

Turn DSP on later, only after the oscillator is connected.

### 2. Sine wave

Place `osc~ 220` above the `*~ 0.1` box and wire it in. Turn DSP on.

{{% checkpoint %}}
**Checkpoint:** a smooth, pure, soft tone. Turn DSP off.
{{% /checkpoint %}}

### 3. Saw wave

Place a new box `phasor~ 220` off to the side and wire its outlet to the left inlet of `*~ 0.1`. Take the sine wire out first. A `phasor~` counts from 0 up to 1 and then drops back to 0, over and over, so it makes a saw wave. Turn DSP on.

{{% checkpoint %}}
**Checkpoint:** a buzzy, bright tone at the same pitch. Same note, different color. That color is called timbre.
{{% /checkpoint %}}

### 4. Center the saw

Between `phasor~ 220` and `*~ 0.1` insert a new box `-~ 0.5`, and wire `phasor~` into `-~ 0.5` and then into `*~ 0.1`.

{{% checkpoint %}}
**Checkpoint:** it sounds almost the same, but the wave now goes below and above zero, like the sine did. The speaker moves evenly in both directions.
{{% /checkpoint %}}

### 5. Square wave

Take the `-~ 0.5` box out for a moment. Make this chain and wire each to the next:

```text
phasor~ 220
>~ 0.5
-~ 0.5
```

Send the end of the chain into `*~ 0.1`.

{{% checkpoint %}}
**Checkpoint:** a hollow, nasal tone. A square wave is made by turning the saw into either 0 or 1 depending on whether it is above 0.5.
{{% /checkpoint %}}

### 6. Compare the three

Wire all three oscillators into three separate `*~` boxes with a different volume each, and mix them into `dac~`, or simply swap the wire from one to another as you listen. Say out loud what each one sounds like.

{{% checkpoint %}}
**Checkpoint:** you can describe each: sine (smooth), saw (buzzy and bright), square (hollow).
{{% /checkpoint %}}

### 7. Try the same on a higher and lower note

Change 220 to 110 and then to 440 in each of the oscillators.

{{% checkpoint %}}
**Checkpoint:** the timbre stays the same, but the pitch changes.
{{% /checkpoint %}}

## Try it

- Place a number box (<kbd>Ctrl+3</kbd>) and connect it to the left inlet of the `phasor~` so you can change the pitch while it plays.
- Make a triangle wave: `phasor~ 220`, then `-~ 0.5`, then `abs~`. Is it closer to a sine or a saw?
- Make noise: place `noise~` and send it to `*~ 0.1`. What does it sound like?
- Add two sine waves with `osc~ 220` and `osc~ 330`.

## What's happening

Every sound is a wave, and the shape of the wave is its timbre. A sine wave has only one frequency in it. A saw or square wave is made of the main frequency plus many higher ones (harmonics) added together, which is why they sound brighter. In Data Science DS4 you can measure this: record or build the tones, and compare their spectra. A sine has a single spike. A saw has many.

## If it doesn't work

- **No sound:** DSP is off, or a wire is missing between the oscillator, `*~ 0.1` and `dac~`.
- **It is too loud:** lower the 0.1 in the `*~` box.
- **A box has a dashed border:** check spelling. Look for the ~ after phasor and osc.
- **A clicking sound:** that is the wave jumping when you change a number or wire. Turn DSP off before you change things.

{{% admonition type="note" title="Note" %}}
Pd steps are written from memory and have not been tested. Teacher: please try this once, especially steps 4 to 6.
{{% /admonition %}}
