---
title: "DS2 Smooth and Spot Outliers"
weight: 2
---

## Goal

Clean up noisy data with a moving average, and find the readings that don't fit.

## What you need

Google Colab, and DS1 finished (you'll reuse the same table). Time: about 30 minutes.

## Steps

### 1. Reopen your DS1 notebook

Open the DS1 notebook. Run all the cells from the top (Runtime menu, then Run all) so that the data table exists.

{{% checkpoint %}}
**Checkpoint:** the data table prints with 8 rows.
{{% /checkpoint %}}

### 2. Add a moving average

A moving average replaces each value with the average of the value and its neighbors. Add a new cell and run:

```python
data["smooth"] = data["light"].rolling(3).mean()
print(data[["seconds", "light", "smooth"]])
```

{{% checkpoint %}}
**Checkpoint:** the first two smooth values say NaN (not enough neighbors yet). After that you see numbers, for example the third one is 541.33.
{{% /checkpoint %}}

### 3. Chart both lines

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

### 4. Find the spread

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

### 5. Flag the odd ones

Add a new cell and run:

```python
data["odd"] = (data["light"] - avg).abs() > spread
print(data[["seconds", "light", "odd"]])
```

{{% checkpoint %}}
**Checkpoint:** the readings 95 and 102 show True. All the others show False.
{{% /checkpoint %}}

### 6. Try a bigger rule

Change the line in step 5 to use 2 * spread and run it again.

{{% checkpoint %}}
**Checkpoint:** now nothing shows True. With a small table, 2 spreads is too strict. Real scientists pick a rule that fits their data.
{{% /checkpoint %}}

## Try it

- Change `rolling(3)` to `rolling(5)`. What happens to the smooth line?
- Make up a new data value that is very large, such as 5000, and see if the odd column catches it.
- Smooth the temperature column instead.

## What's happening

Real sensors are noisy. A moving average cancels out small random jumps, so you can see the trend. The standard deviation gives you a ruler for "far from normal." A value more than one or two spreads from the mean is an outlier. Outliers can be mistakes, or they can be the most interesting part of the data. Here they are the moments the light was blocked.

## If it doesn't work

- **KeyError:** "smooth": run the step 2 cell first.
- **All values show NaN:** the moving average needs at least 3 rows of numbers.
- **Nothing is flagged:** the rule is too strict, so try 1 * spread.
- **The chart shows only one line:** check that both plt.plot lines are in the same cell.

{{% admonition type="note" title="Note" %}}
The Python in this page was run and checked. The Colab screen and buttons were not tested.
{{% /admonition %}}
