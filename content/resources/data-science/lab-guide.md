---
title: "Data Science Lab Guide"
toc: true
description: "Four projects in Python, run in Google Colab."
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)
  toc: true  = show a contents list at the top

A LAB GUIDE: all the Data Science lessons on one page. It is built the same way as
resources/arduino/lab-guide.md: one ## heading per lesson with a fixed {#address}, ### headings
inside each lesson, and --- between lessons.
-->

Four projects in Python, run in Google Colab.

## Before you start {#before-you-start}

### Set up

1. Sign in to your school Google account in Chrome.
2. Go to colab.research.google.com.
3. Click New notebook. Click the title at the top and rename it, for example "DS1 - Sam".
4. The notebook has cells. Click a cell and type code. To run the cell, press <kbd>Shift+Enter</kbd> or click the play button on the left of the cell.
5. numpy, pandas, matplotlib and scipy are already installed. You don't need to install anything.

### Connections to other tools

- **Microcontrollers:** the log from M5 can be your data for DS1. Copy the numbers into a table.
- **Pure Data:** DS3 gives you the pitch numbers used in PD5.
- **Design:** your D3 box makes sounds you can record and measure in DS4.

### Good practice

- Run the cells in order from the top. If something breaks, run all of them again from the top.
- Read the error message at the bottom. It usually tells you the line that is wrong.
- Copy code by typing it so you learn it, but pasting is fine to check your work.
- Save with File, then Save a copy in Drive if you want to keep your own version.

### Terms

- **Cell:** a box where you type and run code.
- **Variable:** a name that holds a value, like data or freq.
- **DataFrame:** a table of data in pandas.
- **Mean:** the sum divided by the count. **Median:** the middle value when sorted.
- **Standard deviation:** how spread out the values are.
- **Outlier:** a value far from the others.
- **Hz (hertz):** cycles per second, the unit of pitch.


---

## DS1 Load and Summarize {#ds1-load-and-summarize}

### Goal

Load a small table of sensor readings into Python and find the smallest, largest, range, mean and median. Make a chart of it.

### What you need

Google Colab open in Chrome (see the Data Science page). Time: about 30 minutes. If you did M5 in Microcontrollers, you can use your own log instead of the sample below.

### Steps

#### 1. Open a notebook

Go to colab.research.google.com and click New notebook. Name it "DS1 - (your name)".

{{% checkpoint %}}
**Checkpoint:** you see an empty code cell.
{{% /checkpoint %}}

#### 2. Put the data in

Click the first cell, type the code below, and press <kbd>Shift+Enter</kbd> to run it. If you have your own M5 log, replace the rows with your own numbers (keep the first line, which names the columns).

```python
import io
import pandas as pd
import matplotlib.pyplot as plt
csv_text = """seconds,light,temp_c,humidity
2,538,23.0,50.0
4,541,23.0,50.0
6,545,23.1,49.0
8,95,23.1,49.0
10,102,23.1,49.0
12,530,23.2,49.0
14,534,23.2,48.0
16,538,23.2,48.0"""
data = pd.read_csv(io.StringIO(csv_text))
print(data)
```

{{% checkpoint %}}
**Checkpoint:** a table with 8 rows and 4 columns prints below the cell.
{{% /checkpoint %}}

#### 3. Find the summary numbers

Add a new cell (click +Code) and run:

```python
print("min:", data["light"].min())
print("max:", data["light"].max())
print("range:", data["light"].max() - data["light"].min())
print("mean:", data["light"].mean())
print("median:", data["light"].median())
```

{{% checkpoint %}}
**Checkpoint:** min 95, max 545, range 450, mean 377.375, median 534.
{{% /checkpoint %}}

#### 4. Draw a chart

Add a new cell and run:

```python
plt.plot(data["seconds"], data["light"], marker="o")
plt.xlabel("seconds")
plt.ylabel("light")
plt.title("Light over time")
plt.show()
```

{{% checkpoint %}}
**Checkpoint:** a line chart with two low points where the light dropped.
{{% /checkpoint %}}

#### 5. Describe it

Add a new cell and run: `data.describe()`

{{% checkpoint %}}
**Checkpoint:** a table of count, mean, std, min and quartiles for every column.
{{% /checkpoint %}}

### Try it

- Chart the temperature or humidity instead of light.
- Change one number in the table and see how the mean changes and how the median changes. Which one moves more?
- Use your own M5 log from the Microcontrollers pathway.

### What's happening

pandas reads a table and holds it in a DataFrame called data. Each column has built-in tools to find the smallest, largest, mean and median. The mean is pulled toward odd values. The median is not. Here the two dark readings (95 and 102) pull the mean down to 377, while the median stays at 534, which is more like a normal reading.

### If it doesn't work

- **NameError:** you skipped a cell. Run all cells in order from the top.
- **KeyError:** the name in the brackets must match the column name exactly, including capital letters.
- **Nothing shows up:** click the cell again and press <kbd>Shift+Enter</kbd>.
- **The chart is empty:** make sure the `plt.show()` line is the last line of the cell.

{{% admonition type="note" title="Note" %}}
The Python in this page was run and gave the numbers shown. The Colab screen and buttons were not tested. If a step doesn't match what you see, flag it so the page can be fixed.
{{% /admonition %}}


---

## DS2 Smooth and Spot Outliers {#ds2-smooth-and-spot-outliers}

### Goal

Clean up noisy data with a moving average, and find the readings that don't fit.

### What you need

Google Colab, and DS1 finished (you'll reuse the same table). Time: about 30 minutes.

### Steps

#### 1. Reopen your DS1 notebook

Open the DS1 notebook. Run all the cells from the top (Runtime menu, then Run all) so that the data table exists.

{{% checkpoint %}}
**Checkpoint:** the data table prints with 8 rows.
{{% /checkpoint %}}

#### 2. Add a moving average

A moving average replaces each value with the average of the value and its neighbors. Add a new cell and run:

```python
data["smooth"] = data["light"].rolling(3).mean()
print(data[["seconds", "light", "smooth"]])
```

{{% checkpoint %}}
**Checkpoint:** the first two smooth values say NaN (not enough neighbors yet). After that you see numbers, for example the third one is 541.33.
{{% /checkpoint %}}

#### 3. Chart both lines

Add a new cell and run:

```python
plt.plot(data["seconds"], data["light"], marker="o", label="raw")
plt.plot(data["seconds"], data["smooth"], marker="o", label="smooth")
plt.legend()
plt.xlabel("seconds")
plt.show()
```

{{% checkpoint %}}
**Checkpoint:** two lines. The smooth line is flatter and its dips are softer.
{{% /checkpoint %}}

#### 4. Find the spread

Standard deviation measures how spread out the numbers are. Add a new cell and run:

```python
avg = data["light"].mean()
spread = data["light"].std()
print("mean:", avg)
print("std:", spread)
```

{{% checkpoint %}}
**Checkpoint:** the mean is 377.375 and the std is about 222.93.
{{% /checkpoint %}}

#### 5. Flag the odd ones

Add a new cell and run:

```python
data["odd"] = (data["light"] - avg).abs() > spread
print(data[["seconds", "light", "odd"]])
```

{{% checkpoint %}}
**Checkpoint:** the readings 95 and 102 show True. All the others show False.
{{% /checkpoint %}}

#### 6. Try a bigger rule

Change the line in step 5 to use 2 * spread and run it again.

{{% checkpoint %}}
**Checkpoint:** now nothing shows True. With a small table, 2 spreads is too strict. Real scientists pick a rule that fits their data.
{{% /checkpoint %}}

### Try it

- Change `rolling(3)` to `rolling(5)`. What happens to the smooth line?
- Make up a new data value that is very large, such as 5000, and see if the odd column catches it.
- Smooth the temperature column instead.

### What's happening

Real sensors are noisy. A moving average cancels out small random jumps, so you can see the trend. The standard deviation gives you a ruler for "far from normal." A value more than one or two spreads from the mean is an outlier. Outliers can be mistakes, or they can be the most interesting part of the data. Here they are the moments the light was blocked.

### If it doesn't work

- **KeyError:** "smooth": run the step 2 cell first.
- **All values show NaN:** the moving average needs at least 3 rows of numbers.
- **Nothing is flagged:** the rule is too strict, so try 1 * spread.
- **The chart shows only one line:** check that both plt.plot lines are in the same cell.

{{% admonition type="note" title="Note" %}}
The Python in this page was run and checked. The Colab screen and buttons were not tested.
{{% /admonition %}}


---

## DS3 Scales {#ds3-scales}

### Goal

See why musical pitch is better drawn on a log scale, and make a list of 13 piano note frequencies with Python.

### What you need

Google Colab. Time: about 30 minutes. No data files needed.

### Steps

#### 1. Open a new notebook

Go to colab.research.google.com, click New notebook, and name it "DS3 - (your name)".

#### 2. Make the note numbers

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

#### 3. Plot on a straight (linear) scale

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

#### 4. Plot on a log scale

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

#### 5. Look at the ratio

Add a new cell and run:

```python
print(freq[1:] / freq[:-1])
```

{{% checkpoint %}}
**Checkpoint:** every number is about 1.0595. That is the same multiplier for each step.
{{% /checkpoint %}}

#### 6. Make your own scale

Add a new cell and run:

```python
major = [0, 2, 4, 5, 7, 9, 11, 12]
for step in major:
    print(step, round(440 * 2 ** (step / 12), 2))
```

{{% checkpoint %}}
**Checkpoint:** the 8 notes of a major scale starting from A440. Keep these numbers for the Pure Data pathway.
{{% /checkpoint %}}

### Try it

- Start from 220 instead of 440. What changes?
- Make a list for 24 steps (two octaves). On the log chart, is it still a straight line?
- Make a list of 8 loudness values where each is twice as strong as the one before, and plot it on a log scale.

### What's happening

Your ear hears ratios, not differences. Going from 220 to 440 Hz sounds like the same jump as 440 to 880, even though the second is twice as many Hz. A straight scale hides this. A log scale turns "multiply by the same amount" into "move the same distance." That is also why loudness is measured in decibels, which is a log scale.

### If it doesn't work

- **NameError:** you skipped a cell. Run all cells in order from the top.
- **SyntaxError:** check that every opening bracket has a closing bracket, and that the indented line after the for line starts with 4 spaces.
- **The chart doesn't change:** check that `plt.yscale("log")` is before `plt.show()`.
- **The numbers have a lot of decimals:** round them with `round(x, 2)`.

### Bridge

Take the major scale numbers into Pure Data PD2 and PD5 and play them as notes.

{{% admonition type="note" title="Note" %}}
The Python in this page was run and checked for the first numbers (440, 466.16, 493.88). The Colab screen and buttons were not tested.
{{% /admonition %}}


---

## DS4 Sound as Data {#ds4-sound-as-data}

### Goal

Make a sound file from numbers, read it back in as data, and measure it: its loudness and its pitch.

### What you need

Google Colab. Time: about 40 minutes. You will need headphones or speakers if you want to hear it.

### Steps

#### 1. Open a new notebook

Go to colab.research.google.com, click New notebook, and name it "DS4 - (your name)".

#### 2. Make a tone out of numbers

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

#### 3. Listen to it

Add a new cell and run:

```python
from IPython.display import Audio
Audio("tone.wav")
```

{{% checkpoint %}}
**Checkpoint:** a small player appears. Press play to hear a steady 440 Hz tone (the note A).
{{% /checkpoint %}}

#### 4. Read it back as data

Add a new cell and run:

```python
rate, samples = wavfile.read("tone.wav")
print(rate, samples.dtype, len(samples), len(samples) / rate)
```

{{% checkpoint %}}
**Checkpoint:** 22050 int16 22050 1.0 (the rate, the number type, the count, and the length in seconds).
{{% /checkpoint %}}

#### 5. Draw the wave

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

#### 6. Measure the loudness

Loudness can be found with RMS (root mean square), a kind of average of the wave. Add a new cell and run:

```python
rms = np.sqrt(np.mean(x ** 2))
print("RMS:", rms)
```

{{% checkpoint %}}
**Checkpoint:** about 0.3535.
{{% /checkpoint %}}

#### 7. Measure the pitch

A Fourier transform finds which frequencies are in a sound. Add a new cell and run:

```python
spec = np.abs(np.fft.rfft(x))
freqs = np.fft.rfftfreq(len(x), 1 / rate)
print("peak frequency:", freqs[np.argmax(spec)])
```

{{% checkpoint %}}
**Checkpoint:** the peak frequency is 440.0 Hz, which is exactly the tone you made.
{{% /checkpoint %}}

#### 8. See the spectrum

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

### Try it

- Change 440 in step 2 to 220 or 880 and run all cells again. The peak should follow.
- Make a two-note sound by adding two sines together: `tone = 0.3 * np.sin(2 * np.pi * 440 * t) + 0.3 * np.sin(2 * np.pi * 660 * t). How many spikes does the spectrum show?`
- Change the amplitude 0.5 to 0.25. What happens to the RMS?
- Use a recording from your D3 box: upload a .wav file with the folder icon on the left of Colab, then read it in step 4 with its name instead of "tone.wav".

### What's happening

Sound on a computer is a list of numbers. The sample rate is how many numbers per second. A pure tone is a sine wave. The RMS is how big the wave is overall, which is related to loudness. The Fourier transform splits a sound into its frequencies, which shows what pitches it contains. This is how tuners and music apps know what note you are playing.

### If it doesn't work

- **NameError:** you skipped a cell. Run all cells in order from the top.
- **The audio player doesn't show up:** make sure `Audio("tone.wav")` is the last line of its cell.
- **FileNotFoundError:** run the step 2 cell first. Colab erases its files when you disconnect, so you may have to make the file again.
- **The sound is too quiet or too loud:** change the 0.5 in step 2.

### Bridge

Compare this tone with the oscillator you build in Pure Data PD1. Do they have the same frequency peak?

{{% admonition type="note" title="Note" %}}
The Python in this page was run and checked: 22050 samples, RMS 0.3535, peak 440.0. The Colab screen and buttons, and the audio player, were not tested.
{{% /admonition %}}

