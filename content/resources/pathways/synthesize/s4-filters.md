---
title: "S4 Filters"
weight: 4
---

## Goal

Shape a bright, buzzy sound by cutting out some of its frequencies with a filter, and sweep the filter by hand to make the classic synth "wah" sound.

## What you need

Pure Data and headphones. Your saw wave from S3. Time: about 30 minutes.

## Steps

### 1. Build a saw wave patch

Place and wire these boxes, in order from top to bottom:

```text
phasor~ 110
-~ 0.5
*~ 0.1
dac~
```

Wire `*~ 0.1` into both inlets of `dac~`. Turn DSP on.

{{% checkpoint %}}
**Checkpoint:** a low buzzy tone.
{{% /checkpoint %}}

### 2. Add a low-pass filter

A low-pass filter lets low frequencies through and cuts the highs. Place a new box `lop~ 1000` between `-~ 0.5` and `*~ 0.1`. Wire `-~ 0.5` into `lop~ 1000`, and `lop~ 1000` into `*~ 0.1`.

{{% checkpoint %}}
**Checkpoint:** the tone sounds duller and softer. The number 1000 is the cutoff frequency in Hz.
{{% /checkpoint %}}

### 3. Change the cutoff

Place a number box (<kbd>Ctrl+3</kbd>) and connect it to the right inlet of `lop~`. Switch to run mode (<kbd>Ctrl+E</kbd>). Click and drag the number box between 100 and 5000.

{{% checkpoint %}}
**Checkpoint:** low numbers sound muffled, like it is behind a wall. High numbers sound bright again.
{{% /checkpoint %}}

### 4. Sweep it

Now make the sweep move on its own. Make this chain, and wire each to the next:

```text
osc~ 0.5
*~ 800
+~ 1000
```

The `lop~` cutoff only takes a plain number, so for a moving sweep use a filter whose cutoff can be a signal. Place a new box `vcf~ 3`. Send the saw wave from `-~ 0.5` into the left inlet of `vcf~ 3`. Send the output of `+~ 1000` into the middle inlet of `vcf~ 3`. Send the right outlet of `vcf~ 3` (the low-pass output) into `*~ 0.1` instead of `lop~`.

{{% checkpoint %}}
**Checkpoint:** the sound slowly opens and closes, twice every four seconds. This is the wah sound.
{{% /checkpoint %}}

### 5. Try a high-pass filter

A high-pass filter cuts the lows and lets the highs through. Replace `lop~ 1000` with `hip~ 1000`.

{{% checkpoint %}}
**Checkpoint:** the tone sounds thin and tinny.
{{% /checkpoint %}}

### 6. Try a band-pass filter

Replace `hip~` with `bp~ 1000 3`. The first number is the center frequency and the second is how narrow it is (Q).

{{% checkpoint %}}
**Checkpoint:** only a narrow slice of the sound passes. It sounds like a nasal voice.
{{% /checkpoint %}}

## Try it

- Change the base note to 55, 220 or 440, and listen to how the filter acts.
- Change `osc~ 0.5` to a faster number, such as `osc~ 5`.
- Try the filter on `noise~` instead of `phasor~`. A low-pass noise sounds like wind. A narrow band-pass noise sounds like a whistle.
- Try `vcf~` (a filter with a signal-controlled cutoff and resonance) in place of `lop~`. This one is more advanced, so read its help patch by right-clicking and choosing Help.

## What's happening

A saw wave is full of harmonics. A filter removes some of them. A low-pass filter takes out the high harmonics, so the sound is darker. Moving the cutoff over time makes the sound change in character. This is called subtractive synthesis: start with a rich sound and carve it away. The sweep uses the same LFO idea you built in S2, now controlling the filter.

## If it doesn't work

- **No sound:** check the wire from the filter to `*~ 0.1`.
- **The sound is too quiet with a low cutoff:** raise the volume a little (0.1 to 0.2).
- **The sweep isn't audible:** check that the `+~ 1000` output goes into the middle inlet of `vcf~ 3`, and that you take the sound from its right outlet.
- **The cutoff goes below zero:** keep `*~ 800` under the `+~` number (here 1000), or the cutoff gets negative.
- **A box has a dashed outline:** check spelling, including the ~.

{{% admonition type="note" title="Note" %}}
Pd steps are written from memory and have not been tested. Teacher: please try this once.
{{% /admonition %}}
