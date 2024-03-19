---
title: "Try me LEDs"
date: 2024-02-27T22:11:13Z
draft: false
categories: ["projekte"]
---

{{< info name="Try me LEDs" img="/try-me-leds/try-me-leds-2024-03-12_low.jpg" contact="scammo" >}}


Mit den Try me LEDs kannst du spielerisch deine Fähigkeiten im Programmieren von LEDs ausprobieren.

Du kannst den "Arduino Programmierbar" einfach mit deinem Skript programmieren. Am besten verwendest du dazu die Fastled Bibliothek. Oben auf dem "Schalter" kannst du einstellen, welcher Arduino den LED-Streifen programmiert. Auf dem "Arduino Demo" läuft immer das Fastled Demo Script.

## Weitere Resourcen

- [LED Matrix Display - OER Jugendhackt(PDF)](https://cloud.okfn.de/s/qzJcxZf8WF97EKb?dir=undefined&openfile=79765)

## Beispiel Code zwei Durchlaufende LEDs

```
#include <FastLED.h>

// How many leds in your strip?
#define NUM_LEDS 300
#define BRIGHTNESS  55


#define DATA_PIN 3
// Define the array of leds
CRGB leds[NUM_LEDS];

void setup() { 
    // Uncomment/edit one of the following lines for your leds arrangement.
    // ## Clockless types ##
    FastLED.addLeds<NEOPIXEL, DATA_PIN>(leds, NUM_LEDS);  // GRB ordering is assumed
      FastLED.setBrightness(BRIGHTNESS );

}

void loop() { 
  // Turn the LED on, then pause
    for (int i = 0; i <= NUM_LEDS; i++) {

      leds[i-2] = CRGB::Black;
      leds[i-1] = CRGB::Black;
      leds[i] = CRGB::Green;
      leds[i+1] = CRGB::Green;
      FastLED.show();
      delay(50);
    }
}
```

## Verbindung

![Schaltverbindung try me leds](/try-me-leds/try-me-leds_Steckplatine.png)

[Fritzing Datei](
![Schaltverbindung try me leds](/try-me-leds/try-me-leds.fzz))

## Historie

Aller erste Version:
![Aller erste Version Try me leds](/try-me-leds/try_me_leds_1.jpg)