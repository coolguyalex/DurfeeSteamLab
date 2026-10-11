---
title: "DS1 Load and Summarize"
weight: 1
---

## Goal

Load a small table of sensor readings into Python and find the smallest, largest, range, mean and median. Make a chart of it.

## What you need

Google Colab open in Chrome (see the Data Science page). Time: about 30 minutes. If you did M5 in Microcontrollers, you can use your own log instead of the sample below.

## Steps

### 1. Open a notebook

Go to colab.research.google.com and click New notebook. Name it "DS1 - (your name)".

{{% checkpoint %}}
**Checkpoint:** you see an empty code cell.
{{% /checkpoint %}}

### 2. Put the data in

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

### 3. Find the summary numbers

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

### 4. Draw a chart

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

### 5. Describe it

Add a new cell and run: `data.describe()`

{{% checkpoint %}}
**Checkpoint:** a table of count, mean, std, min and quartiles for every column.
{{% /checkpoint %}}

## Try it

- Chart the temperature or humidity instead of light.
- Change one number in the table and see how the mean changes and how the median changes. Which one moves more?
- Use your own M5 log from the Microcontrollers pathway.

## What's happening

pandas reads a table and holds it in a DataFrame called data. Each column has built-in tools to find the smallest, largest, mean and median. The mean is pulled toward odd values. The median is not. Here the two dark readings (95 and 102) pull the mean down to 377, while the median stays at 534, which is more like a normal reading.

## If it doesn't work

- **NameError:** you skipped a cell. Run all cells in order from the top.
- **KeyError:** the name in the brackets must match the column name exactly, including capital letters.
- **Nothing shows up:** click the cell again and press <kbd>Shift+Enter</kbd>.
- **The chart is empty:** make sure the `plt.show()` line is the last line of the cell.

{{% admonition type="note" title="Note" %}}
The Python in this page was run and gave the numbers shown. The Colab screen and buttons were not tested; teacher: please try it once.
{{% /admonition %}}
