---
title: "Try me LEDs"
date: 2024-02-27T22:11:13Z
draft: false
categories: ["projekte"]
---

{{< info name="Try me LEDs" img="/try-me-leds/try-me-leds-2024-03-12_low.jpg" contact="scammo" >}}


Mit den Try me LEDs kannst du spielerisch deine Fähigkeiten im Programmieren von LEDs ausprobieren.

Du kannst den "Arduino Programmierbar" einfach mit deinem Skript programmieren. Am besten verwendest du dazu die Fastled Bibliothek. Oben auf dem "Schalter" kannst du einstellen, welcher Arduino den LED-Streifen programmiert. Auf dem "Arduino Demo" läuft immer das Fastled Demo Script.

Das Netzteil hat einen Output von 5V 10A

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

[Schaltverbindung try me leds](/try-me-leds/try-me-leds.fzz))

## Historie

Aller erste Version:
![Aller erste Version Try me leds](/try-me-leds/try_me_leds_1.jpg)

## LEDs mit Potentiometer

Schließe einen Potentiometer an den A0 (Analog 0) Pin und ändere dann folgenden Code:

```
void loop() { 
    for (int i = 0; i <= NUM_LEDS; i++) {
      leds[i-2] = CRGB::Black;
      leds[i-1] = CRGB::Black;
      leds[i] = CRGB::Green;
      leds[i+1] = CRGB::Green;
      FastLED.show();
      // map(value, fromLow, fromHigh, toLow, toHigh)
      delay(map(analogRead(A0), 0, 255, 0, 400));
      Serial.println(A0);
    }
}
```

[map() infos in der Arduino Doku](https://www.arduino.cc/reference/en/language/functions/math/map/)

## DemoReel 100 auf dem "Arduino DEMO"

```
/// @file    DemoReel100.ino
/// @brief   FastLED "100 lines of code" demo reel, showing off some effects
/// @example DemoReel100.ino

#include <FastLED.h>

FASTLED_USING_NAMESPACE

// FastLED "100-lines-of-code" demo reel, showing just a few 
// of the kinds of animation patterns you can quickly and easily 
// compose using FastLED.  
//
// This example also shows one easy way to define multiple 
// animations patterns and have them automatically rotate.
//
// -Mark Kriegsman, December 2014


#define DATA_PIN    3
//#define CLK_PIN   4
#define LED_TYPE    WS2812
#define COLOR_ORDER GRB
#define NUM_LEDS    300
CRGB leds[NUM_LEDS];

#define BRIGHTNESS          96
#define FRAMES_PER_SECOND  120

void setup() {
  delay(3000); // 3 second delay for recovery
  
  // tell FastLED about the LED strip configuration
  FastLED.addLeds<LED_TYPE,DATA_PIN,COLOR_ORDER>(leds, NUM_LEDS).setCorrection(TypicalLEDStrip);
  //FastLED.addLeds<LED_TYPE,DATA_PIN,CLK_PIN,COLOR_ORDER>(leds, NUM_LEDS).setCorrection(TypicalLEDStrip);

  // set master brightness control
  FastLED.setBrightness(BRIGHTNESS);
  FastLED.setMaxPowerInVoltsAndMilliamps(5,8000); 

}


// List of patterns to cycle through.  Each is defined as a separate function below.
typedef void (*SimplePatternList[])();
SimplePatternList gPatterns = { rainbow, rainbowWithGlitter, confetti, sinelon, juggle, bpm };

uint8_t gCurrentPatternNumber = 0; // Index number of which pattern is current
uint8_t gHue = 0; // rotating "base color" used by many of the patterns
  
void loop()
{
  // Call the current pattern function once, updating the 'leds' array
  gPatterns[gCurrentPatternNumber]();

  // send the 'leds' array out to the actual LED strip
  FastLED.show();  
  // insert a delay to keep the framerate modest
  FastLED.delay(1000/FRAMES_PER_SECOND); 

  // do some periodic updates
  EVERY_N_MILLISECONDS( 20 ) { gHue++; } // slowly cycle the "base color" through the rainbow
  EVERY_N_SECONDS( 10 ) { nextPattern(); } // change patterns periodically
}

#define ARRAY_SIZE(A) (sizeof(A) / sizeof((A)[0]))

void nextPattern()
{
  // add one to the current pattern number, and wrap around at the end
  gCurrentPatternNumber = (gCurrentPatternNumber + 1) % ARRAY_SIZE( gPatterns);
}

void rainbow() 
{
  // FastLED's built-in rainbow generator
  fill_rainbow( leds, NUM_LEDS, gHue, 7);
}

void rainbowWithGlitter() 
{
  // built-in FastLED rainbow, plus some random sparkly glitter
  rainbow();
  addGlitter(80);
}

void addGlitter( fract8 chanceOfGlitter) 
{
  if( random8() < chanceOfGlitter) {
    leds[ random16(NUM_LEDS) ] += CRGB::White;
  }
}

void confetti() 
{
  // random colored speckles that blink in and fade smoothly
  fadeToBlackBy( leds, NUM_LEDS, 10);
  int pos = random16(NUM_LEDS);
  leds[pos] += CHSV( gHue + random8(64), 200, 255);
}

void sinelon()
{
  // a colored dot sweeping back and forth, with fading trails
  fadeToBlackBy( leds, NUM_LEDS, 20);
  int pos = beatsin16( 13, 0, NUM_LEDS-1 );
  leds[pos] += CHSV( gHue, 255, 192);
}

void bpm()
{
  // colored stripes pulsing at a defined Beats-Per-Minute (BPM)
  uint8_t BeatsPerMinute = 62;
  CRGBPalette16 palette = PartyColors_p;
  uint8_t beat = beatsin8( BeatsPerMinute, 64, 255);
  for( int i = 0; i < NUM_LEDS; i++) { //9948
    leds[i] = ColorFromPalette(palette, gHue+(i*2), beat-gHue+(i*10));
  }
}

void juggle() {
  // eight colored dots, weaving in and out of sync with each other
  fadeToBlackBy( leds, NUM_LEDS, 20);
  uint8_t dothue = 0;
  for( int i = 0; i < 8; i++) {
    leds[beatsin16( i+7, 0, NUM_LEDS-1 )] |= CHSV(dothue, 200, 255);
    dothue += 32;
  }
}

```

## Sonstiges

[USB B dust cover stl](https://www.printables.com/de/model/473014-usb-b-port-cap)