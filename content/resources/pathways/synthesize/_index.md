---
title: "Synthesize"
---

{{% admonition type="draft" title="Draft" %}}
DRAFT v0.1 - first pass, not yet tested. Pick and test a browser version of Pure Data on a Chromebook and put its link below. If none works well, this pathway can switch to Sonic Pi or SuperCollider or may require a local installation.
{{% /admonition %}}

Five starter projects that teach you to make sound from nothing. You'll build a synthesizer out of boxes and wires, with no typing code. You use Pure Data (Pd), a free visual sound program. You don't need any experience.

{{% admonition type="todo" title="To add" %}}
LINK TO THE PURE DATA EDITOR: (to add)
{{% /admonition %}}

## The five projects

- [S1 Hello Oscillator](/resources/pathways/synthesize/s1-hello-oscillator/) - make a steady tone and control how loud it is.
- [S2 Pitch and Volume](/resources/pathways/synthesize/s2-pitch-and-volume/) - change the note, and add wobble (vibrato) and pulsing (tremolo).
- [S3 Waveforms](/resources/pathways/synthesize/s3-waveforms/) - hear how sine, saw and square waves sound different.
- [S4 Filters](/resources/pathways/synthesize/s4-filters/) - shape the sound by cutting highs and lows.
- [S5 Delay and Data](/resources/pathways/synthesize/s5-delay-and-data/) - add echo, then play a melody from a list of numbers.

## Basics of Pure Data

Pd has two kinds of things you place on the page. An object box does a job, like making a sine wave. A message box sends a number or word when you click it.

Objects ending in a tilde (~) work with audio, like `osc~`. Objects without a tilde work with plain numbers.

You connect boxes with wires: drag from the outlet (small dark rectangle at the bottom of a box) to the inlet (top of the next box).

Shortcuts on the Pd patch: <kbd>Ctrl+1</kbd> makes an object box. <kbd>Ctrl+2</kbd> makes a message box. <kbd>Ctrl+3</kbd> makes a number box. After you place the box, type in it and click on an empty part of the patch to finish it.

To make the audio work, turn on DSP (audio processing). In many versions this is a checkbox or a button labeled DSP or "audio on".

Edit mode lets you move boxes and draw wires. Run mode lets you click and change numbers. <kbd>Ctrl+E</kbd> switches between them.

## Ground rules

- Keep the volume low when you start. Put on headphones, and turn the volume down before turning DSP on.
- Never connect a new thing to `dac~` without a `*~` in front of it to turn the volume down.
- Save often and give your patch a clear name.

## Bridges to other pathways

- **Microcontrollers:** the log from M5 can be sent into S5 as data.
- **Data Science:** DS3 gives you pitch numbers to use in S5, and DS4 lets you measure the sounds you build here.
- **Design:** D3 shows how the shape of a box changes its sound.

## Words you'll meet

- **Oscillator:** something that makes a repeating wave, and so a tone.
- **Frequency:** how many waves per second, in Hz. It sets the pitch.
- **Amplitude:** how big the wave is. It sets the loudness.
- **Waveform:** the shape of the wave (sine, saw, square).
- **Filter:** something that removes some of the frequencies.
- **LFO:** low frequency oscillator, a slow wave that controls another sound.
- **DSP:** digital signal processing, the switch that turns audio on in Pd.
