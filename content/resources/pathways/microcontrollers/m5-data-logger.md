---
title: "M5 Data Logger"
weight: 6
---

About 90 minutes. Logging and CSV. You write most of the code.

## Goal

Record light, temperature and humidity over time, then turn it into a chart in Google Sheets.

You'll learn: how to print readings as a table, how a CSV is laid out, and how to get your data into a spreadsheet. You can use the data you collect in the Data Science and Synthesize pathways (DS1 and S5).

## Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- The light sensor circuit from M3
- The DHT11 from M4

## Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: M3 light sensor on A0 plus M4 DHT11 on pin 2. The LED is not needed.
{{% /admonition %}}

Wire it exactly like M3 and M4, both on the same breadboard. You can leave the LED out.

## Starter sketch (data_logger.ino)

The sketch is mostly written. Five lines are left for you, marked TODO.

```cpp
#include <DHT.h>
DHT dht(2, DHT11);
const int lightPin = A0;

void setup() {
  Serial.begin(9600);
  dht.begin();
  // The first line is the header row of the table:
  Serial.println("seconds,light,temp_c,humidity");
}

void loop() {
  int light = analogRead(lightPin);
  float tempC = dht.readTemperature();
  float humidity = dht.readHumidity();
  // TODO 1: print the seconds since the board started: millis() / 1000
  // TODO 2: print a comma
  // TODO 3: print light, then a comma
  // TODO 4: print tempC, then a comma
  // TODO 5: print humidity, and END the line with println
  delay(2000);
}
```

<details>
<summary>The five missing lines (try first!)</summary>

```cpp
Serial.print(millis() / 1000);
Serial.print(",");
Serial.print(light);
Serial.print(",");
Serial.print(tempC);
Serial.print(",");
Serial.println(humidity);
```

</details>

## Build it

1. Finish the sketch, Verify, then Upload. **Checkpoint:** the Serial Monitor shows lines like 12,538,23.00,50.00.
2. Let it run for about 20 rows. While it runs, change something: cover the light sensor and breathe on the DHT11.
3. Select all the text in the Serial Monitor and copy it.
4. Open a new Google Sheet, click cell A1 and paste. Everything landed in one column? Select the column, then choose Data, then Split text to columns, and pick Comma. **Checkpoint:** you have four columns with a header row.
5. Select the columns, then choose Insert, then Chart. Make a line chart of light over time. **Checkpoint:** you can see on the chart when you covered the sensor.
6. Name the sheet "M5 log" with your name, and keep it. You'll use it again later.

## What's actually happening?

Logging means measuring again and again and saving the results. The sketch prints one line per reading, with commas between the values. That layout is called a CSV (comma-separated values). Any spreadsheet or program can read it, and each line becomes a row.

The header row names each column so the data still makes sense a week from now.

## Try it

1. Log for ten minutes while something in the room changes, such as the lights going off or a window opening.
2. Change the delay to log faster or slower. What happens to your chart?
3. Challenge: add a column in Sheets that says "dark" or "light" depending on the reading. Hint: `=IF(B2<300,"dark","light")`, and pick your own number instead of 300.

## If it doesn't work

- **The temperature column says "nan":** the sensor didn't answer. Check the wiring and keep at least two seconds between readings.
- **The header row is missing:** the header only prints when the board starts. Press the reset button on the board, then copy again.

## Optional extension: M5+

At a lab computer with Python, you can save the readings straight to a CSV file without copying and pasting. Ask your teacher when a station is free.
