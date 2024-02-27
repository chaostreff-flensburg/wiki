---
title: "Try me LEDs"
date: 2024-02-27T22:11:13Z
draft: false
categories: ["projekte"]
---

Mit den Try me LEDs kannst du spielerisch deine Fähigkeiten im Programmieren von LEDs ausprobieren.

Du kannst den "Arduino Programmierbar" einfach mit deinem Skript programmieren. Am besten verwendest du dazu die Fastled Bibliothek. Oben auf dem "Schalter" kannst du einstellen, welcher Arduino den LED-Streifen programmiert. Auf dem "Arduino Demo" läuft immer das Fastled Demo Script.


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

## Todos
- Verkabelung permanenter machen (z.B. alles relevante verlöten)
- An "Arduino Programmierbar" noch Sensoren anschließen
- Mehr Beispiel Anleitungen erstellen
