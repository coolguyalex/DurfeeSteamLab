---
title: "Pure Data Lab Guide"
toc: true
description: "Five projects that build a synthesizer out of boxes and wires."
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)
  toc: true  = show a contents list at the top

A LAB GUIDE: all the Pure Data lessons on one page. It is built the same way as
resources/arduino/lab-guide.md: one ## heading per lesson with a fixed {#address}, ### headings
inside each lesson, and --- between lessons.
-->

Five projects that build a synthesizer out of boxes and wires.

## Before you start {#before-you-start}

### Basics of Pure Data

Pd has two kinds of things you place on the page. An object box does a job, like making a sine wave. A message box sends a number or word when you click it.

Objects ending in a tilde (~) work with audio, like `osc~`. Objects without a tilde work with plain numbers.

You connect boxes with wires: drag from the outlet (small dark rectangle at the bottom of a box) to the inlet (top of the next box).

Shortcuts on the Pd patch: <kbd>Ctrl+1</kbd> makes an object box. <kbd>Ctrl+2</kbd> makes a message box. <kbd>Ctrl+3</kbd> makes a number box. After you place the box, type in it and click on an empty part of the patch to finish it.

To make the audio work, turn on DSP (audio processing). In many versions this is a checkbox or a button labeled DSP or "audio on".

Edit mode lets you move boxes and draw wires. Run mode lets you click and change numbers. <kbd>Ctrl+E</kbd> switches between them.

### Good practice

- Keep the volume low when you start. Put on headphones, and turn the volume down before turning DSP on.
- Never connect a new thing to `dac~` without a `*~` in front of it to turn the volume down.
- Save often and give your patch a clear name.

### Connections to other tools

- **Microcontrollers:** the log from M5 can be sent into PD5 as data.
- **Data Science:** DS3 gives you pitch numbers to use in PD5, and DS4 lets you measure the sounds you build here.
- **Design:** D3 shows how the shape of a box changes its sound.

### Terms

- **Oscillator:** something that makes a repeating wave, and so a tone.
- **Frequency:** how many waves per second, in Hz. It sets the pitch.
- **Amplitude:** how big the wave is. It sets the loudness.
- **Waveform:** the shape of the wave (sine, saw, square).
- **Filter:** something that removes some of the frequencies.
- **LFO:** low frequency oscillator, a slow wave that controls another sound.
- **DSP:** digital signal processing, the switch that turns audio on in Pd.


---

## PD1 Hello Oscillator {#pd1-hello-oscillator}

### Goal

Make your first sound: a steady tone from an oscillator, with a volume control that keeps it safe for your ears.

### What you need

Pure Data open in your browser (see the Sound tools page for the link), and headphones. Time: about 20 minutes.

### Steps

#### 1. Turn the volume down

Turn your Chromebook volume low. Put on headphones.

#### 2. Open a new patch

Open a new empty patch in Pure Data. Click on the patch so it has focus.

{{% checkpoint %}}
**Checkpoint:** you see a blank patch window.
{{% /checkpoint %}}

#### 3. Make the oscillator

Press <kbd>Ctrl+1</kbd> to place an object box. Type `osc~ 440` and click on an empty part of the patch.

{{% checkpoint %}}
**Checkpoint:** a box that says `osc~ 440` with one outlet at the bottom and two inlets on top.
{{% /checkpoint %}}

#### 4. Make the volume control

Press <kbd>Ctrl+1</kbd> again and place a second box under the first. Type `*~ 0.1` and click on an empty space.

{{% checkpoint %}}
**Checkpoint:** a box that says `*~ 0.1`. This multiplies the sound by 0.1, which makes it much quieter.
{{% /checkpoint %}}

#### 5. Make the speaker box

Press <kbd>Ctrl+1</kbd> once more and place a third box at the bottom. Type `dac~` and click on an empty space.

{{% checkpoint %}}
**Checkpoint:** a box that says `dac~`. It has two inlets: the left speaker and the right speaker.
{{% /checkpoint %}}

#### 6. Connect them

Drag a wire from the outlet of `osc~ 440` (bottom left) to the left inlet of `*~ 0.1`. Then drag a wire from the outlet of `*~ 0.1` to the left inlet of `dac~`, and another wire from the same outlet to the right inlet of `dac~`.

{{% checkpoint %}}
**Checkpoint:** three wires. The sound goes oscillator, then volume, then both speakers.
{{% /checkpoint %}}

#### 7. Turn the sound on

Turn DSP on (the checkbox or button labeled DSP or "audio on").

{{% checkpoint %}}
**Checkpoint:** you hear a steady quiet tone. It is the note A.
{{% /checkpoint %}}

#### 8. Change the volume

Turn DSP off. Double-click on the `*~ 0.1` box while in edit mode, change 0.1 to 0.3, click away, and turn DSP on again.

{{% checkpoint %}}
**Checkpoint:** the tone is louder. Be careful. Do not go above 0.5.
{{% /checkpoint %}}

### Try it

- Change 440 to 220 and then 880. Which is higher? Which is lower?
- Place a number box (<kbd>Ctrl+3</kbd>) and connect it to the left inlet of `osc~`. In run mode, click and drag it up and down to change the pitch while the sound plays.
- Place a second `osc~` and send it to the same `*~` box. Listen to two tones at once.

### What's happening

`osc~` makes a sine wave at the frequency you give it. The number after `osc~` is the frequency in Hz. The wave is a list of numbers made 44,100 times each second. The `*~` multiplies each number, so a smaller number gives a smaller wave and a quieter sound. `dac~` (digital to analog converter) sends the numbers to your speakers.

### If you hear nothing

- **DSP isn't on:** turn it on.
- **The volume is too low:** raise the `*~` number a little, or turn up the Chromebook volume.
- **A wire is missing:** check that all three wires are there.
- **The browser is blocking sound:** click once on the page, and check the site's sound permission in Chrome.
- **A box has a dashed border:** Pd doesn't know that word. Check your spelling, including the ~.

{{% admonition type="note" title="Note" %}}
Pd steps were written from memory and have not been tested. The browser version of Pd may use different menu names. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## PD2 Pitch and Volume {#pd2-pitch-and-volume}

### Goal

Change the pitch and volume while the sound plays, then add vibrato (a wobbling pitch) and tremolo (a pulsing volume) using a slow oscillator, called an LFO.

### What you need

Your PD1 patch (`osc~`, `*~`, `dac~`). Headphones. Time: about 30 minutes.

### Steps

#### 1. Open your PD1 patch

Open it and save a copy as "PD2". Turn DSP on and check that you can hear the tone.

#### 2. Add a pitch control

Place a number box (<kbd>Ctrl+3</kbd>) above the `osc~` box. Connect its outlet to the left inlet of `osc~`. Switch to run mode (<kbd>Ctrl+E</kbd>). Click and drag the number box up and down.

{{% checkpoint %}}
**Checkpoint:** the pitch changes as you drag. Try 220, 440 and 880.
{{% /checkpoint %}}

#### 3. Add a volume control

Place a second number box above `*~`. Edit the `*~` box to be just `*~` with no number, then connect the new number box to the right inlet of `*~`. Switch to run mode and drag the number between 0 and 0.3.

{{% checkpoint %}}
**Checkpoint:** you control the volume with a number. Keep it below 0.5.
{{% /checkpoint %}}

#### 4. Make vibrato

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

#### 5. Change the vibrato

Change `osc~ 5` to `osc~ 2` for slower, then to `osc~ 8` for faster. Change `*~ 10` to `*~ 30` for a deeper wobble.

{{% checkpoint %}}
**Checkpoint:** you hear the wobble change speed and depth.
{{% /checkpoint %}}

#### 6. Make tremolo

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

### Try it

- Do both at the same time.
- Use a number box to control the vibrato speed.
- Try an LFO at a very fast speed, like `osc~ 50`. It stops sounding like wobble and starts to change the tone color.

### What's happening

An LFO is just an oscillator that runs too slowly to hear as a note. Instead we use it to control another sound. For vibrato, the LFO moves the main pitch up and down. For tremolo, it moves the volume up and down. Here `*~` sets how strong the effect is, and `+~` sets the middle value it moves around. Most synthesizers are built this way: one wave controlling another.

### If it doesn't work

- **Sound goes silent:** check that the `+~ 0.5` chain output goes into the right inlet of the `*~`, not the left.
- **The pitch jumps or sounds like noise:** the LFO depth is too big. Lower `*~ 10` to `*~ 5`.
- **A new box has a dashed outline:** check the spelling, including the ~.
- **You can't change a number:** switch to run mode with <kbd>Ctrl+E</kbd>.

{{% admonition type="note" title="Note" %}}
Pd steps were written from memory and have not been tested. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## PD3 Waveforms {#pd3-waveforms}

### Goal

Hear how three wave shapes (sine, saw, square) sound different at the same pitch, and learn to build each one from simple boxes.

### What you need

Pure Data and headphones. Time: about 30 minutes. You can start a fresh patch.

### Steps

#### 1. Start with the safe output

Place these two boxes, with the `*~` above the `dac~`, and wire `*~ 0.1` to both inlets of `dac~`:

```text
*~ 0.1
dac~
```

Turn DSP on later, only after the oscillator is connected.

#### 2. Sine wave

Place `osc~ 220` above the `*~ 0.1` box and wire it in. Turn DSP on.

{{% checkpoint %}}
**Checkpoint:** a smooth, pure, soft tone. Turn DSP off.
{{% /checkpoint %}}

#### 3. Saw wave

Place a new box `phasor~ 220` off to the side and wire its outlet to the left inlet of `*~ 0.1`. Take the sine wire out first. A `phasor~` counts from 0 up to 1 and then drops back to 0, over and over, so it makes a saw wave. Turn DSP on.

{{% checkpoint %}}
**Checkpoint:** a buzzy, bright tone at the same pitch. Same note, different color. That color is called timbre.
{{% /checkpoint %}}

#### 4. Center the saw

Between `phasor~ 220` and `*~ 0.1` insert a new box `-~ 0.5`, and wire `phasor~` into `-~ 0.5` and then into `*~ 0.1`.

{{% checkpoint %}}
**Checkpoint:** it sounds almost the same, but the wave now goes below and above zero, like the sine did. The speaker moves evenly in both directions.
{{% /checkpoint %}}

#### 5. Square wave

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

#### 6. Compare the three

Wire all three oscillators into three separate `*~` boxes with a different volume each, and mix them into `dac~`, or simply swap the wire from one to another as you listen. Say out loud what each one sounds like.

{{% checkpoint %}}
**Checkpoint:** you can describe each: sine (smooth), saw (buzzy and bright), square (hollow).
{{% /checkpoint %}}

#### 7. Try the same on a higher and lower note

Change 220 to 110 and then to 440 in each of the oscillators.

{{% checkpoint %}}
**Checkpoint:** the timbre stays the same, but the pitch changes.
{{% /checkpoint %}}

### Try it

- Place a number box (<kbd>Ctrl+3</kbd>) and connect it to the left inlet of the `phasor~` so you can change the pitch while it plays.
- Make a triangle wave: `phasor~ 220`, then `-~ 0.5`, then `abs~`. Is it closer to a sine or a saw?
- Make noise: place `noise~` and send it to `*~ 0.1`. What does it sound like?
- Add two sine waves with `osc~ 220` and `osc~ 330`.

### What's happening

Every sound is a wave, and the shape of the wave is its timbre. A sine wave has only one frequency in it. A saw or square wave is made of the main frequency plus many higher ones (harmonics) added together, which is why they sound brighter. In Data Science DS4 you can measure this: record or build the tones, and compare their spectra. A sine has a single spike. A saw has many.

### If it doesn't work

- **No sound:** DSP is off, or a wire is missing between the oscillator, `*~ 0.1` and `dac~`.
- **It is too loud:** lower the 0.1 in the `*~` box.
- **A box has a dashed border:** check spelling. Look for the ~ after phasor and osc.
- **A clicking sound:** that is the wave jumping when you change a number or wire. Turn DSP off before you change things.

{{% admonition type="note" title="Note" %}}
Pd steps were written from memory and have not been tested. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## PD4 Filters {#pd4-filters}

### Goal

Shape a bright, buzzy sound by cutting out some of its frequencies with a filter, and sweep the filter by hand to make the classic synth "wah" sound.

### What you need

Pure Data and headphones. Your saw wave from PD3. Time: about 30 minutes.

### Steps

#### 1. Build a saw wave patch

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

#### 2. Add a low-pass filter

A low-pass filter lets low frequencies through and cuts the highs. Place a new box `lop~ 1000` between `-~ 0.5` and `*~ 0.1`. Wire `-~ 0.5` into `lop~ 1000`, and `lop~ 1000` into `*~ 0.1`.

{{% checkpoint %}}
**Checkpoint:** the tone sounds duller and softer. The number 1000 is the cutoff frequency in Hz.
{{% /checkpoint %}}

#### 3. Change the cutoff

Place a number box (<kbd>Ctrl+3</kbd>) and connect it to the right inlet of `lop~`. Switch to run mode (<kbd>Ctrl+E</kbd>). Click and drag the number box between 100 and 5000.

{{% checkpoint %}}
**Checkpoint:** low numbers sound muffled, like it is behind a wall. High numbers sound bright again.
{{% /checkpoint %}}

#### 4. Sweep it

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

#### 5. Try a high-pass filter

A high-pass filter cuts the lows and lets the highs through. Replace `lop~ 1000` with `hip~ 1000`.

{{% checkpoint %}}
**Checkpoint:** the tone sounds thin and tinny.
{{% /checkpoint %}}

#### 6. Try a band-pass filter

Replace `hip~` with `bp~ 1000 3`. The first number is the center frequency and the second is how narrow it is (Q).

{{% checkpoint %}}
**Checkpoint:** only a narrow slice of the sound passes. It sounds like a nasal voice.
{{% /checkpoint %}}

### Try it

- Change the base note to 55, 220 or 440, and listen to how the filter acts.
- Change `osc~ 0.5` to a faster number, such as `osc~ 5`.
- Try the filter on `noise~` instead of `phasor~`. A low-pass noise sounds like wind. A narrow band-pass noise sounds like a whistle.
- Try `vcf~` (a filter with a signal-controlled cutoff and resonance) in place of `lop~`. This one is more advanced, so read its help patch by right-clicking and choosing Help.

### What's happening

A saw wave is full of harmonics. A filter removes some of them. A low-pass filter takes out the high harmonics, so the sound is darker. Moving the cutoff over time makes the sound change in character. This is called subtractive synthesis: start with a rich sound and carve it away. The sweep uses the same LFO idea you built in PD2, now controlling the filter.

### If it doesn't work

- **No sound:** check the wire from the filter to `*~ 0.1`.
- **The sound is too quiet with a low cutoff:** raise the volume a little (0.1 to 0.2).
- **The sweep isn't audible:** check that the `+~ 1000` output goes into the middle inlet of `vcf~ 3`, and that you take the sound from its right outlet.
- **The cutoff goes below zero:** keep `*~ 800` under the `+~` number (here 1000), or the cutoff gets negative.
- **A box has a dashed outline:** check spelling, including the ~.

{{% admonition type="note" title="Note" %}}
Pd steps were written from memory and have not been tested. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## PD5 Delay and Data {#pd5-delay-and-data}

### Goal

Add an echo to your sound, then play a melody from a list of numbers. This is where data from the other tools can drive your synthesizer.

### What you need

Pure Data and headphones. Your saw or sine patch from earlier. Optional: the scale numbers from DS3, or the log from M5. Time: about 45 minutes. Do it in two parts if needed.

### Part A: echo

#### 1. Start with a short sound

Place and wire: `osc~ 440`, then `*~ 0.1`, then `dac~`. This is the same patch as PD1.

Place a number box and connect it to the left inlet of `osc~ 440`. In run mode, change the number between 440 and 0 repeatedly to start and stop the sound. Zero makes a silent tone.

{{% checkpoint %}}
**Checkpoint:** you can make short tones by hand.
{{% /checkpoint %}}

#### 2. Add the delay

Place two new boxes: `delwrite~ echo 1000` and `delread~ echo 300`. The first stores 1000 milliseconds of sound under the name "echo". The second reads it back 300 milliseconds later.

Wire the output of the `*~ 0.1` box to the input of `delwrite~ echo 1000` as well as to `dac~`.

Wire the output of `delread~ echo 300` to a new `*~ 0.4` box, and then to `dac~` (both inlets).

{{% checkpoint %}}
**Checkpoint:** when you play a short tone, you hear it again 0.3 seconds later, quieter.
{{% /checkpoint %}}

#### 3. Feed the echo back

Also wire the output of `*~ 0.4` to the input of `delwrite~ echo 1000`.

{{% checkpoint %}}
**Checkpoint:** the echo repeats several times, getting quieter each time. Be careful: if the feedback number (0.4) is 1 or above, the echo never dies. Keep it below 0.7.
{{% /checkpoint %}}

### Part B: play numbers

#### 4. Make a place to hold the numbers

Place an object box with `array define data 8`. This makes a list called data with 8 slots.

Place a message box (<kbd>Ctrl+2</kbd>) with this exact text:

```text
; data 0 440 494 523 587 659 587 523 494
```

Click it in run mode. (The semicolon at the start sends the numbers to the list named data. The first 0 is where to start. These are 8 note frequencies.)

{{% checkpoint %}}
**Checkpoint:** the list now holds eight pitches. Double-click the array define box to see them in a graph, if you want.
{{% /checkpoint %}}

#### 5. Make a counter

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

#### 6. Read the numbers

Place `tabread data`. Wire the outlet of f to the inlet of `tabread data`. Wire the outlet of `tabread data` to the left inlet of `osc~ 440` (this replaces the number box).

{{% checkpoint %}}
**Checkpoint:** click the 1 message box. You hear a melody of 8 notes, repeating.
{{% /checkpoint %}}

### Try it

- Change the metro speed: `metro 150` is faster, `metro 600` is slower.
- Change the notes in the message box. Use the numbers from your DS3 scale (major scale from 440: 440, 493.88, 554.37, 587.33, 659.25, 739.99, 830.61, 880).
- Use data from M5: change the numbers in the message box to your own light readings, or scale them with * 2 so they fall in a pitch range you like. A sensor melody!
- Put the melody into your filter from PD4, and into the echo from Part A.

### What's happening

`delwrite~` and `delread~` make an echo by storing sound and playing it back later. Feeding it back makes repeats. The counter loop makes the numbers 0 to 7 over and over. `tabread` reads the list at that position. So a plain list of numbers becomes a tune. Data that you collect (from the Microcontrollers pathway) or compute (in Data Science) can control sound this way. Turning data into sound is called sonification.

### If it doesn't work

- **No melody:** check that you clicked the 1 message box, and that DSP is on.
- **The same note repeats:** check that the outlet of `mod 8` goes back into the right inlet of f.
- **An error says "array:** no such array": check that the array is named exactly data, in both places.
- **The echo is too loud or doesn't stop:** lower the `*~ 0.4` number.
- **A box has a dashed outline:** check spelling.

{{% admonition type="note" title="Note" %}}
Pd steps were written from memory and have not been tested. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}

