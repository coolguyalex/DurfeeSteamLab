---
title: "DS4 Sound as Data"
weight: 4
---

## Goal

Make a sound file from numbers, read it back in as data, and measure it: its loudness and its pitch.

## What you need

Google Colab. Time: about 40 minutes. You will need headphones or speakers if you want to hear it.

## Steps

### 1. Open a new notebook

Go to colab.research.google.com, click New notebook, and name it "DS4 - (your name)".

### 2. Make a tone out of numbers

A sound is a long list of numbers: how far the speaker moves at each tiny moment. Type this in the first cell and run it:

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.io import wavfile
sr = 22050
t = np.linspace(0, 1, sr, endpoint=False)
tone = 0.5 * np.sin(2 * np.pi * 440 * t)
wavfile.write("tone.wav", sr, (tone * 32767).astype(np.int16))
print("made", len(tone), "numbers")
```

{{% checkpoint %}}
**Checkpoint:** it prints "made 22050 numbers". That is one second of sound at 22050 samples per second.
{{% /checkpoint %}}

### 3. Listen to it

Add a new cell and run:

```python
from IPython.display import Audio
Audio("tone.wav")
```

{{% checkpoint %}}
**Checkpoint:** a small player appears. Press play to hear a steady 440 Hz tone (the note A).
{{% /checkpoint %}}

### 4. Read it back as data

Add a new cell and run:

```python
rate, samples = wavfile.read("tone.wav")
print(rate, samples.dtype, len(samples), len(samples) / rate)
```

{{% checkpoint %}}
**Checkpoint:** 22050 int16 22050 1.0 (the rate, the number type, the count, and the length in seconds).
{{% /checkpoint %}}

### 5. Draw the wave

Add a new cell and run:

```python
x = samples / 32767
plt.plot(x[:200])
plt.title("First 200 samples")
plt.show()
```

{{% checkpoint %}}
**Checkpoint:** a smooth wave that goes up and down about twice. The height is 0.5.
{{% /checkpoint %}}

### 6. Measure the loudness

Loudness can be found with RMS (root mean square), a kind of average of the wave. Add a new cell and run:

```python
rms = np.sqrt(np.mean(x ** 2))
print("RMS:", rms)
```

{{% checkpoint %}}
**Checkpoint:** about 0.3535.
{{% /checkpoint %}}

### 7. Measure the pitch

A Fourier transform finds which frequencies are in a sound. Add a new cell and run:

```python
spec = np.abs(np.fft.rfft(x))
freqs = np.fft.rfftfreq(len(x), 1 / rate)
print("peak frequency:", freqs[np.argmax(spec)])
```

{{% checkpoint %}}
**Checkpoint:** the peak frequency is 440.0 Hz, which is exactly the tone you made.
{{% /checkpoint %}}

### 8. See the spectrum

Add a new cell and run:

```python
plt.plot(freqs[:1000], spec[:1000])
plt.xlabel("Hz")
plt.title("Spectrum")
plt.show()
```

{{% checkpoint %}}
**Checkpoint:** one tall spike at 440.
{{% /checkpoint %}}

## Try it

- Change 440 in step 2 to 220 or 880 and run all cells again. The peak should follow.
- Make a two-note sound by adding two sines together: `tone = 0.3 * np.sin(2 * np.pi * 440 * t) + 0.3 * np.sin(2 * np.pi * 660 * t). How many spikes does the spectrum show?`
- Change the amplitude 0.5 to 0.25. What happens to the RMS?
- Use a recording from your D3 box: upload a .wav file with the folder icon on the left of Colab, then read it in step 4 with its name instead of "tone.wav".

## What's happening

Sound on a computer is a list of numbers. The sample rate is how many numbers per second. A pure tone is a sine wave. The RMS is how big the wave is overall, which is related to loudness. The Fourier transform splits a sound into its frequencies, which shows what pitches it contains. This is how tuners and music apps know what note you are playing.

## If it doesn't work

- **NameError:** you skipped a cell. Run all cells in order from the top.
- **The audio player doesn't show up:** make sure `Audio("tone.wav")` is the last line of its cell.
- **FileNotFoundError:** run the step 2 cell first. Colab erases its files when you disconnect, so you may have to make the file again.
- **The sound is too quiet or too loud:** change the 0.5 in step 2.

## Bridge

Compare this tone with the oscillator you build in Synthesize S1. Do they have the same frequency peak?

{{% admonition type="note" title="Note" %}}
The Python in this page was run and checked: 22050 samples, RMS 0.3535, peak 440.0. The Colab screen and buttons, and the audio player, were not tested.
{{% /admonition %}}
