---
title: "M4 Raw vs Library"
weight: 5
---

About 90 minutes. Digital sensor and libraries. You write the second sketch.

## Goal

See what a digital sensor actually sends, then use a library to read temperature and humidity the easy way.

You'll learn: how a digital sensor sends numbers as 1s and 0s, why that raw data is useless until it's decoded, and what a library is.

## Parts

- 1 x Arduino Uno and USB cable
- 1 x breadboard
- 1 x DHT11 temperature and humidity sensor
- 3 x jumper wires
- Check your sensor: a DHT11 on a small circuit board has three pins (+, OUT, -). A bare sensor has four and needs a 10 kilohm resistor between the data pin and 5V. Ask your teacher if you aren't sure which one you have.

## Wire it

{{% admonition type="diagram" title="Diagram (to be added)" %}}
Wiring diagram: DHT11 + to 5V, - to GND, OUT to pin 2.
{{% /admonition %}}

1. Unplug the board. Connect the sensor's + to 5V, its - to GND, and its OUT (data) to pin 2. **Checkpoint:** your wiring matches the diagram.

## Part 1: look at the raw data

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

## Part 2: let a library do it

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

## What's actually happening?

The light sensor in M3 gave a voltage that could be anywhere in a range. That's analog. The DHT11 is digital: it sends a message made only of on and off pulses, and the pattern of pulses carries the numbers.

That raw message is useless unless you know the sensor's language. The first byte is humidity, the third is temperature, and so on. A library is code that someone else wrote and shared. This one already knows the DHT11's language, so you call `dht.readTemperature()` and get a number. `#include` is how your sketch pulls the library in.

## Try it

1. Print the temperature in F. Hint: multiply C by 9, divide by 5, and add 32.
2. Warm the sensor with your fingers and watch both numbers change.
3. Challenge: add the LED from M2, and light it when the temperature goes above the room's normal reading.

## If it doesn't work

- **"No answer from the sensor":** check all three wires, and make sure OUT is on pin 2. The sensor can take a second after power-up before it answers.
- **The values show "nan":** the reading failed. The DHT11 can only be read about once every two seconds, so keep the 2000 millisecond delay.
- **The compiler can't find DHT.h:** the library isn't added to this sketch yet. Open the Libraries panel and add it.
