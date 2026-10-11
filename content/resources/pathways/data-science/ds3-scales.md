---
title: "DS3 Scales"
weight: 3
---

## Goal

See why musical pitch is better drawn on a log scale, and make a list of 13 piano note frequencies with Python.

## What you need

Google Colab. Time: about 30 minutes. No data files needed.

## Steps

### 1. Open a new notebook

Go to colab.research.google.com, click New notebook, and name it "DS3 - (your name)".

### 2. Make the note numbers

Each step up the piano keyboard (one semitone) multiplies the pitch by the same amount. Twelve steps up doubles it, which is one octave. Type this in the first cell and run it:

```python
import numpy as np
import matplotlib.pyplot as plt
n = np.arange(0, 13)
freq = 440 * 2 ** (n / 12)
print(freq)
```

{{% checkpoint %}}
**Checkpoint:** 13 numbers starting 440, 466.16, 493.88 and ending 880 (A to the next A).
{{% /checkpoint %}}

### 3. Plot on a straight (linear) scale

Add a new cell and run:

```python
plt.plot(n, freq, marker="o")
plt.xlabel("semitones above A440")
plt.ylabel("frequency (Hz)")
plt.title("Linear scale")
plt.show()
```

{{% checkpoint %}}
**Checkpoint:** a curve that bends upward. Equal steps in pitch do not look equal.
{{% /checkpoint %}}

### 4. Plot on a log scale

Add a new cell and run:

```python
plt.plot(n, freq, marker="o")
plt.yscale("log")
plt.xlabel("semitones above A440")
plt.ylabel("frequency (Hz)")
plt.title("Log scale")
plt.show()
```

{{% checkpoint %}}
**Checkpoint:** a straight line. Equal steps in pitch now look equal, which is how your ear hears them.
{{% /checkpoint %}}

### 5. Look at the ratio

Add a new cell and run:

```python
print(freq[1:] / freq[:-1])
```

{{% checkpoint %}}
**Checkpoint:** every number is about 1.0595. That is the same multiplier for each step.
{{% /checkpoint %}}

### 6. Make your own scale

Add a new cell and run:

```python
major = [0, 2, 4, 5, 7, 9, 11, 12]
for step in major:
    print(step, round(440 * 2 ** (step / 12), 2))
```

{{% checkpoint %}}
**Checkpoint:** the 8 notes of a major scale starting from A440. Keep these numbers for the Synthesize pathway.
{{% /checkpoint %}}

## Try it

- Start from 220 instead of 440. What changes?
- Make a list for 24 steps (two octaves). On the log chart, is it still a straight line?
- Make a list of 8 loudness values where each is twice as strong as the one before, and plot it on a log scale.

## What's happening

Your ear hears ratios, not differences. Going from 220 to 440 Hz sounds like the same jump as 440 to 880, even though the second is twice as many Hz. A straight scale hides this. A log scale turns "multiply by the same amount" into "move the same distance." That is also why loudness is measured in decibels, which is a log scale.

## If it doesn't work

- **NameError:** you skipped a cell. Run all cells in order from the top.
- **SyntaxError:** check that every opening bracket has a closing bracket, and that the indented line after the for line starts with 4 spaces.
- **The chart doesn't change:** check that `plt.yscale("log")` is before `plt.show()`.
- **The numbers have a lot of decimals:** round them with `round(x, 2)`.

## Bridge

Take the major scale numbers into Synthesize S2 and S5 and play them as notes.

{{% admonition type="note" title="Note" %}}
The Python in this page was run and checked for the first numbers (440, 466.16, 493.88). The Colab screen and buttons were not tested.
{{% /admonition %}}
