---
title: "S2 Pitch and Volume"
weight: 2
---

## Goal

Change the pitch and volume while the sound plays, then add vibrato (a wobbling pitch) and tremolo (a pulsing volume) using a slow oscillator, called an LFO.

## What you need

Your S1 patch (`osc~`, `*~`, `dac~`). Headphones. Time: about 30 minutes.

## Steps

### 1. Open your S1 patch

Open it and save a copy as "S2". Turn DSP on and check that you can hear the tone.

### 2. Add a pitch control

Place a number box (<kbd>Ctrl+3</kbd>) above the `osc~` box. Connect its outlet to the left inlet of `osc~`. Switch to run mode (<kbd>Ctrl+E</kbd>). Click and drag the number box up and down.

{{% checkpoint %}}
**Checkpoint:** the pitch changes as you drag. Try 220, 440 and 880.
{{% /checkpoint %}}

### 3. Add a volume control

Place a second number box above `*~`. Edit the `*~` box to be just `*~` with no number, then connect the new number box to the right inlet of `*~`. Switch to run mode and drag the number between 0 and 0.3.

{{% checkpoint %}}
**Checkpoint:** you control the volume with a number. Keep it below 0.5.
{{% /checkpoint %}}

### 4. Make vibrato

Switch back to edit mode. Make this chain of boxes to the left of your main patch, and wire each to the next:

```text
osc~ 5
*~ 10
+~ 440
```

Connect the `+~ 440` output to the left inlet of your main `osc~` (replace the pitch number box connection, or remove the number box for now).

{{% checkpoint %}}
**Checkpoint:** the pitch now wobbles around 440, 5 times a second, by about 10 Hz above and below. This is vibrato.
{{% /checkpoint %}}

### 5. Change the vibrato

Change `osc~ 5` to `osc~ 2` for slower, then to `osc~ 8` for faster. Change `*~ 10` to `*~ 30` for a deeper wobble.

{{% checkpoint %}}
**Checkpoint:** you hear the wobble change speed and depth.
{{% /checkpoint %}}

### 6. Make tremolo

Undo or delete the vibrato chain. Keep the pitch at `osc~ 440`. Now make this chain, with each box wired to the next:

```text
osc~ 4
*~ 0.5
+~ 0.5
```

Connect the `+~ 0.5` output to the right inlet of a new `*~` box (with no number) placed between your `osc~ 440` and your volume `*~ 0.1`. That is, `osc~ 440` goes into the left inlet of the new `*~`, and the new `*~` goes on to `*~ 0.1`.

{{% checkpoint %}}
**Checkpoint:** the volume pulses 4 times a second, which is tremolo.
{{% /checkpoint %}}

## Try it

- Do both at the same time.
- Use a number box to control the vibrato speed.
- Try an LFO at a very fast speed, like `osc~ 50`. It stops sounding like wobble and starts to change the tone color.

## What's happening

An LFO is just an oscillator that runs too slowly to hear as a note. Instead we use it to control another sound. For vibrato, the LFO moves the main pitch up and down. For tremolo, it moves the volume up and down. Here `*~` sets how strong the effect is, and `+~` sets the middle value it moves around. Most synthesizers are built this way: one wave controlling another.

## If it doesn't work

- **Sound goes silent:** check that the `+~ 0.5` chain output goes into the right inlet of the `*~`, not the left.
- **The pitch jumps or sounds like noise:** the LFO depth is too big. Lower `*~ 10` to `*~ 5`.
- **A new box has a dashed outline:** check the spelling, including the ~.
- **You can't change a number:** switch to run mode with <kbd>Ctrl+E</kbd>.

{{% admonition type="note" title="Note" %}}
Pd steps are written from memory and have not been tested. Teacher: please build this once to check the wiring in steps 4 and 6.
{{% /admonition %}}
