---
title: "Arduino Lab Guide"
toc: true
description: "Step-by-step projects from a first blinking LED to a data logger, plus a cheat sheet at the end."
---

<!--
FRONT MATTER: the block between the two --- lines above. It is settings for this page, not page text.
  title:  the page title (the heading, the browser tab, and links that point to it)
  toc:    true  = show a contents list at the top (see layouts/_default/single.html)
  description: a one-line summary used by search engines

HOW THIS PAGE IS BUILT: all the Arduino lessons are on this one page. Each lesson is a
level-two heading (##) with a fixed address in curly braces, for example  ## M1 Blink {#m1-blink}.
The contents list shows the ## headings only (the setting is in hugo.toml). Inside a lesson,
### headings are the parts of that lesson. A line with --- is a horizontal rule between lessons.
Other pages link to a lesson with /resources/arduino/lab-guide/#m1-blink.

The green boxes are the checkpoint shortcode, and the coloured note boxes are the admonition
shortcode. Both are defined in layouts/shortcodes/.
-->

Step-by-step projects from a first blinking LED to a data logger, plus a cheat sheet at the end.


---

## Start Here {#start-here}

A microcontroller is a tiny computer that can sense the world and act on it. Your Arduino can read a button or a light sensor, and it can switch an LED on and off. You'll write the instructions in a program called a sketch.

### Your kit

- 1 x Arduino Uno
- 1 x USB data cable
- 1 x breadboard
- Jumper wires
- LEDs
- 220 ohm resistors
- 10 kilohm resistors
- 1 x pushbutton
- 1 x light sensor (LDR)
- 1 x DHT11 sensor

{{% admonition type="note" title="Note" %}}
This list is a guess. Match it to your actual kit.
{{% /admonition %}}

### Set up on your Chromebook

You'll use the Arduino Cloud Editor in the Chrome browser. There is nothing to install.

1. Open app.arduino.cc and sign in. Ask in room 3106 which account to use.
2. Open the Cloud Editor and start a new sketch.
3. Plug your board in with a data USB cable. A light on the board turns on. **Checkpoint:** a light is on at the board.
4. Choose your board and port in the editor. Chrome asks to connect to a serial port. Pick your board in the list and click Connect. **Checkpoint:** the editor shows your board's name. Not sure which port is yours? Unplug the board and look at the list. Plug it back in and see which entry comes back. That one is yours.
5. To send a sketch to the board, click Verify (the check mark) first, then Upload (the arrow).
6. Keep the board plugged in until the upload finishes. Unplugging in the middle cancels it.

### The breadboard in four rules

- Holes in the same short row are connected to each other.
- The long rails along the sides carry power (+) or ground (-) the whole way down.
- The gap in the middle keeps the left and right halves apart.
- Unplug the board before you change any wiring.

### Good practice

- Never connect 5V directly to GND.
- Every LED gets a resistor.
- Ask before you touch someone else's board.

### Terms

- **Sketch:** a program for an Arduino.
- **Upload:** sending your sketch from the computer to the board.
- **Pin:** a metal socket on the board where you connect a wire. Each pin has a number or a name like A0.
- **Digital and analog:** a digital signal has only two states, on (HIGH) or off (LOW). An analog signal can be anywhere in a range, like a dimmer switch.
- **Serial Monitor:** a window in the editor that shows messages your board sends back to the computer.
- **Library:** code that someone else wrote and shared, so you don't have to write it yourself.
- **CSV:** a plain text table where commas separate the columns and each line is a row. Spreadsheets can open it.


---

## M1 Blink {#m1-blink}

About 30 minutes. Nothing to wire. Full code provided.

### Goal

Upload your first sketch and make the light on the board blink.

Covers: what a sketch is, what `setup()` and `loop()` do, and how to change a number and upload again.

### Parts

- 1 x Arduino Uno
- 1 x USB data cable

### Starter sketch (blink.ino)

```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH); // LED on
  delay(1000); // wait 1000 milliseconds
  digitalWrite(LED_BUILTIN, LOW); // LED off
  delay(1000);
}
```

### Build it

1. Open a new sketch in the Cloud Editor and name it Blink.
2. Delete everything in the editor, then paste in the starter sketch.
3. Click Verify. **Checkpoint:** no red error messages appear.
4. Click Upload and wait for it to finish. **Checkpoint:** the small light marked L on the board blinks.
5. Change both 1000s to 200 and upload again. **Checkpoint:** it blinks faster.

### What's actually happening?

Every sketch has two parts. `setup()` runs once when the board starts. `loop()` runs again and again, forever.

digitalWrite sets a pin to `HIGH` (5 volts, on) or `LOW` (0 volts, off). `delay(1000)` waits 1000 milliseconds, which is one second. `LED_BUILTIN` is a nickname for the pin that the small light on the board is wired to.

### Try it

1. Make the light stay on for 100 milliseconds and off for 900.
2. Make a heartbeat: two quick blinks, then a pause.
3. Challenge: blink out S.O.S. in Morse code (three short, three long, three short).

### If it doesn't work

- **The upload fails:** check that your cable carries data (some only charge) and that a light is on at the board. Unplug it, plug it back in, and choose the port again.
- **Red error text appears:** read the line number in the message. The usual causes are a missing semicolon ; or a missing curly brace }. Compare your sketch with the starter, character by character.
- **The upload worked but nothing blinks:** look for the small light marked L, not the steady power light.


---

## M2 Button and LED {#m2-button-and-led}

About 60 minutes. Digital input and output. Code with blanks to fill in.

### Goal

Make an LED light up while you hold down a button.

Covers: how a pin can listen (input) as well as act (output), how a breadboard connects parts, and why electricity needs a complete loop from power to ground.

### Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- 1 x LED
- 1 x 220 ohm resistor (red, red, brown)
- 1 x pushbutton
- 5 x jumper wires

### Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: button on pin 2, LED on pin 8.
{{% /admonition %}}

1. Unplug the board from the USB cable.
2. Connect a jumper wire from the Arduino GND pin to the blue (-) rail.
3. Push the LED into the breadboard so its two legs are in different rows. The longer leg is positive.
4. Connect the row of the shorter leg to the blue rail with a jumper wire.
5. Place the resistor from the row of the longer leg to an empty row. Connect that empty row to Arduino pin 8 with a jumper wire.
6. Press the button into the breadboard so it straddles the middle gap. Connect a jumper wire from one side to pin 2, and from the other side to the blue rail. **Checkpoint:** your wiring matches the diagram, row by row.

### Starter sketch (button_led.ino)

Three blanks are marked ____. Fill them in before you upload.

```cpp
const int buttonPin = 2;
const int ledPin = 8;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(ledPin, ____); // 1: is the LED an INPUT or an OUTPUT?
}

void loop() {
  int state = digitalRead(buttonPin);
  if (state == ____) { // 2: what does the pin read while the button is pressed?
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, ____); // 3: HIGH or LOW to turn the LED off?
  }
}
```

<details>
<summary>Answers (try first!)</summary>

1: `OUTPUT`. 2: `LOW`. 3: `LOW`.

The second one feels backwards. `INPUT_PULLUP` keeps the pin at `HIGH` when nothing happens. Pressing the button connects the pin to ground, so it reads `LOW`.

</details>

### Build it

1. Fill in the blanks, then plug in the board and click Verify.
2. Click Upload. **Checkpoint:** the LED lights while you hold the button and goes off when you let go.

### What's actually happening?

A pin set to `INPUT_PULLUP` listens. It reads `HIGH` or `LOW`, and nothing in between, which makes it a digital input. A pin set to `OUTPUT` acts. Your sketch asks one question over and over: is the button pressed? If it is, the LED gets power.

Electricity only flows in a complete loop. The LED's loop goes from pin 8, through the resistor and the LED, to the ground rail and back to GND. The resistor limits the current so the LED doesn't burn out.

### Try it

1. Flip it: make the LED stay on until you press the button.
2. Add a second LED on another pin that lights when the first one is off.
3. Challenge: make the LED switch on and off each time you press (a toggle). You'll need a variable that remembers the LED's state.

### If it doesn't work

- **The LED never lights:** the LED may be backwards. The longer leg goes toward the resistor. Also check that the blue rail is connected to GND.
- **The LED is always on:** both button wires may be on the same side of the gap, which keeps the button permanently connected. Move one to the other side.
- **The upload works but the button does nothing:** check that the button wire goes to pin 2, and that the sketch uses `buttonPin = 2`.


---

## M3 Light Dimmer {#m3-light-dimmer}

About 75 minutes. Analog input. Working code to change.

### Goal

Use a light sensor to control how bright an LED glows, and watch the sensor's numbers in the Serial Monitor.

Covers: how an analog sensor differs from a button, how to read a number from a sensor, and how to print it.

### Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- 1 x LED and 1 x 220 ohm resistor
- 1 x light sensor (LDR)
- 1 x 10 kilohm resistor (brown, black, orange)
- Jumper wires

### Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: LED on pin 9, LDR and 10 kilohm divider on A0.
{{% /admonition %}}

1. Unplug the board. Rebuild the LED circuit from M2, but connect the resistor's empty row to pin 9 this time.
2. Connect Arduino 5V to the red (+) rail.
3. Put the light sensor in the breadboard with its legs in two different rows. Connect the first row to the red rail.
4. Place the 10 kilohm resistor from the sensor's second row to the blue rail.
5. Connect a jumper wire from the sensor's second row (where the sensor and the resistor meet) to Arduino pin A0. **Checkpoint:** your wiring matches the diagram, row by row.

### Starter sketch (light_dimmer.ino)

This one already works. You'll change it in the Try it section.

```cpp
const int sensorPin = A0;
const int ledPin = 9;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int light = analogRead(sensorPin); // a number from 0 to 1023
  int brightness = map(light, 0, 1023, 255, 0); // flip it: dark room = bright LED
  analogWrite(ledPin, brightness); // 0 is off, 255 is full
  Serial.println(light);
  delay(50);
}
```

### Build it

1. Paste the sketch, Verify, then Upload. **Checkpoint:** the LED gets brighter when you cover the sensor with your hand.
2. Open the Serial Monitor tab in the editor and set the speed to 9600. **Checkpoint:** numbers scroll past, and they change when you cover the sensor.
3. Cover the sensor, then shine a phone flashlight on it. Write down the lowest and highest numbers you see.

### What's actually happening?

analogRead measures the voltage on a pin and gives you a number from 0 (0 volts) to 1023 (5 volts). The button in M2 had only two states. A light sensor can give any number in between, which makes it an analog sensor.

The sensor changes its resistance with light, and the 10 kilohm resistor turns that change into a voltage your board can measure. analogWrite sends the LED a fast on-off pulse pattern, and the more time it spends on, the brighter the LED looks. `map()` converts a number from one range to another.

### Try it

1. Your real lowest and highest readings probably aren't 0 and 1023. Put your own numbers into `map()` so the LED uses its full range.
2. Change the sketch so the LED is brighter in the light and dimmer in the dark.
3. Challenge: make the LED blink faster as the room gets darker. Hint: use the reading to set the `delay()`.

### If it doesn't work

- **The numbers are stuck at 0 or 1023:** check that the 10 kilohm resistor is connected, and that the A0 wire is in the row where the sensor and the resistor meet.
- **The Serial Monitor shows garbled text:** the speed must match the sketch. Set the monitor to 9600 to match `Serial.begin(9600)`.
- **The LED doesn't change:** make sure the LED wire goes to pin 9, not pin 8. Only some pins can dim an LED.


---

## M4 Raw vs Library {#m4-raw-vs-library}

About 90 minutes. Digital sensor and libraries. You write the second sketch.

### Goal

See what a digital sensor actually sends, then use a library to read temperature and humidity the easy way.

Covers: how a digital sensor sends numbers as 1s and 0s, why that raw data is useless until it's decoded, and what a library is.

### Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- 1 x DHT11 temperature and humidity sensor
- 3 x jumper wires
- Check your sensor: a DHT11 on a small circuit board has three pins (+, OUT, -). A bare sensor has four and needs a 10 kilohm resistor between the data pin and 5V. Ask in the lab if you aren't sure which one you have.

### Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: DHT11 + to 5V, - to GND, OUT to pin 2.
{{% /admonition %}}

1. Unplug the board. Connect the sensor's + to 5V, its - to GND, and its OUT (data) to pin 2. **Checkpoint:** your wiring matches the diagram.

### Part 1: look at the raw data

This sketch listens to the sensor and prints exactly what it sends. You don't need to understand every line yet.

*dht_raw.ino*

```cpp
const int dataPin = 2;

void setup() {
  Serial.begin(9600);
}

// Wait until the pin reads 'level'. Give up after timeoutUs microseconds.
bool waitFor(int level, unsigned long timeoutUs) {
  unsigned long start = micros();
  while (digitalRead(dataPin) != level) {
    if (micros() - start > timeoutUs) return false;
  }
  return true;
}

void loop() {
  byte data[5] = {0, 0, 0, 0, 0};
  // 1. Ask the sensor to talk: pull the line LOW for 20 ms, then let go.
  pinMode(dataPin, OUTPUT);
  digitalWrite(dataPin, LOW);
  delay(20);
  pinMode(dataPin, INPUT_PULLUP);
  // 2. The sensor answers with a short signal, then sends 40 bits.
  bool ok = waitFor(HIGH, 200) && waitFor(LOW, 200) && waitFor(HIGH, 200) && waitFor(LOW, 200);
  // 3. Each bit is a HIGH pulse. Short (about 27 us) is a 0. Long (about 70 us) is a 1.
  for (int i = 0; ok && i < 40; i++) {
    ok = waitFor(HIGH, 200);
    if (!ok) break;
    unsigned long start = micros();
    ok = waitFor(LOW, 200);
    if (!ok) break;
    if (micros() - start > 40) {
      data[i / 8] |= (1 << (7 - (i % 8)));
    }
  }
  // 4. Print the raw bits as five groups of eight.
  if (ok) {
    for (int b = 0; b < 5; b++) {
      for (int bit = 7; bit >= 0; bit--) {
        Serial.print(bitRead(data[b], bit));
      }
      Serial.print(" ");
    }
    Serial.println();
  } else {
    Serial.println("No answer from the sensor. Check your wiring.");
  }
  delay(2000);
}
```

1. Upload the sketch and open the Serial Monitor at 9600. **Checkpoint:** every two seconds a line of 40 ones and zeros appears.
2. Breathe on the sensor and watch the line change.
3. The 40 bits are five groups of eight. Group 1 is the humidity, group 3 is the temperature in C, and group 5 is a check number. Groups 2 and 4 are always zero on a DHT11. Convert group 3 to a normal number by hand. **Checkpoint:** you decoded the temperature by hand.

<details>
<summary>How to read the bits (try first!)</summary>

Each position in a group of eight is worth: 128, 64, 32, 16, 8, 4, 2, 1. Add up the positions that hold a 1.

Example: 00110010 00000000 00010111 00000000 01001001

Group 1 is 32 + 16 + 2 = 50, so the humidity is 50%. Group 3 is 16 + 4 + 2 + 1 = 23, so it's 23 C. Group 5 is 64 + 8 + 1 = 73, which is 50 + 0 + 23 + 0. The sensor sends it so the board can check that the message arrived correctly.

</details>

### Part 2: let a library do it

1. In the Cloud Editor, open the Libraries panel and search for DHT sensor library. Add it to your sketch. The sketch says a library is missing? This library may need a second one called Adafruit Unified Sensor. Search for it the same way and add it too.
2. Make a new sketch with the code below, then upload it.

*dht_library.ino*

```cpp
#include <DHT.h>
#define DHTPIN 2
#define DHTTYPE DHT11
DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  float humidity = dht.readHumidity();
  float tempC = dht.readTemperature();
  Serial.print("Humidity: ");
  Serial.print(humidity);
  Serial.print(" % Temperature: ");
  Serial.print(tempC);
  Serial.println(" C");
  delay(2000);
}
```

{{% checkpoint %}}
**Checkpoint:** the temperature matches the number you decoded by hand.
{{% /checkpoint %}}

### What's actually happening?

The light sensor in M3 gave a voltage that could be anywhere in a range. That's analog. The DHT11 is digital: it sends a message made only of on and off pulses, and the pattern of pulses carries the numbers.

That raw message is useless unless you know the sensor's language. The first byte is humidity, the third is temperature, and so on. A library is code that someone else wrote and shared. This one already knows the DHT11's language, so you call `dht.readTemperature()` and get a number. `#include` is how your sketch pulls the library in.

### Try it

1. Print the temperature in F. Hint: multiply C by 9, divide by 5, and add 32.
2. Warm the sensor with your fingers and watch both numbers change.
3. Challenge: add the LED from M2, and light it when the temperature goes above the room's normal reading.

### If it doesn't work

- **"No answer from the sensor":** check all three wires, and make sure OUT is on pin 2. The sensor can take a second after power-up before it answers.
- **The values show "nan":** the reading failed. The DHT11 can only be read about once every two seconds, so keep the 2000 millisecond delay.
- **The compiler can't find DHT.h:** the library isn't added to this sketch yet. Open the Libraries panel and add it.


---

## M5 Data Logger {#m5-data-logger}

About 90 minutes. Logging and CSV. You write most of the code.

### Goal

Record light, temperature and humidity over time, then turn it into a chart in Google Sheets.

Covers: how to print readings as a table, how a CSV is laid out, and how to get your data into a spreadsheet. You can use the data you collect in Data Science and Pure Data (DS1 and PD5).

### Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- The light sensor circuit from M3
- The DHT11 from M4

### Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: M3 light sensor on A0 plus M4 DHT11 on pin 2. The LED is not needed.
{{% /admonition %}}

Wire it exactly like M3 and M4, both on the same breadboard. You can leave the LED out.

### Starter sketch (data_logger.ino)

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

### Build it

1. Finish the sketch, Verify, then Upload. **Checkpoint:** the Serial Monitor shows lines like 12,538,23.00,50.00.
2. Let it run for about 20 rows. While it runs, change something: cover the light sensor and breathe on the DHT11.
3. Select all the text in the Serial Monitor and copy it.
4. Open a new Google Sheet, click cell A1 and paste. Everything landed in one column? Select the column, then choose Data, then Split text to columns, and pick Comma. **Checkpoint:** you have four columns with a header row.
5. Select the columns, then choose Insert, then Chart. Make a line chart of light over time. **Checkpoint:** you can see on the chart when you covered the sensor.
6. Name the sheet "M5 log" with your name, and keep it. You'll use it again later.

### What's actually happening?

Logging means measuring again and again and saving the results. The sketch prints one line per reading, with commas between the values. That layout is called a CSV (comma-separated values). Any spreadsheet or program can read it, and each line becomes a row.

The header row names each column so the data still makes sense a week from now.

### Try it

1. Log for ten minutes while something in the room changes, such as the lights going off or a window opening.
2. Change the delay to log faster or slower. What happens to your chart?
3. Challenge: add a column in Sheets that says "dark" or "light" depending on the reading. Hint: `=IF(B2<300,"dark","light")`, and pick your own number instead of 300.

### If it doesn't work

- **The temperature column says "nan":** the sensor didn't answer. Check the wiring and keep at least two seconds between readings.
- **The header row is missing:** the header only prints when the board starts. Press the reset button on the board, then copy again.

### Optional extension: M5+

At a lab computer with Python, you can save the readings straight to a CSV file without copying and pasting. Ask in the lab when a station is free.


---

## Reference {#reference}

Quick answers to keep open while you build.

### Code you'll use

- `pinMode(pin, OUTPUT)` - makes a pin send signals out. Use `INPUT_PULLUP` to listen.
- `digitalWrite(pin, HIGH)` - turns a pin on (5 V). `LOW` turns it off.
- `digitalRead(pin)` - reads a pin as `HIGH` or `LOW`.
- `analogRead(pin)` - reads a voltage as a number from 0 to 1023.
- `analogWrite(pin, value)` - dims an LED. The value runs from 0 to 255.
- `map(x, a, b, c, d)` - converts x from the range a to b into the range c to d.
- `delay(ms)` - waits for that many milliseconds.
- `Serial.begin(9600)` - starts the connection to the Serial Monitor.
- `Serial.println(x)` - prints x and starts a new line.

### Parts at a glance

- **220 ohm resistor:** red, red, brown bands.
- **10 kilohm resistor:** brown, black, orange bands.
- **LED:** the longer leg is positive. The flat edge of the rim is on the negative side.
- **Pushbutton:** four legs. Legs on the same side are always connected. Pressing connects the two sides.

### Nothing works? Check in this order

1. Is a light on at the board?
2. Is the right board and port selected in the editor?
3. Does Verify pass with no red errors?
4. Does your wiring match the diagram, row by row?
5. Is the ground rail connected to GND?
6. Unplug the board, plug it back in, and upload again.
7. Read your wiring out loud to a classmate and ask them to follow it on the diagram.

