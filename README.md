# Kaleidoscope-LEDEffect-FunctionalColor



This plugin automatically colors groups of keys per the user's preference
based on the current function of the key on the active layer.

## Using the extension

To use the plugin, include the header, declare an effect using the
`LEDFunctionalColor` class, and tell the firmware to use the new effect.
Configure your own colors for groups of keys inside setup():

```c++
// Automatically sets key's LED on active layer based on the function of the key
#include <Kaleidoscope-LEDEffect-FunctionalColor.h>

// You can make multiple variations of the theme.
// Warning: having several versions consumes a lot of memory!
kaleidoscope::LEDFunctionalColor FunColor;
kaleidoscope::LEDFunctionalColor FunColorMedium;
kaleidoscope::LEDFunctionalColor FunColorLow;

void setup() {
  Kaleidoscope.use(&FunColor, &FunColorMedium, &FunColorLow);

  Kaleidoscope.setup(

    // Optionally Make things more human readable by naming your colors
    cRGB antiquewhite = CRGB(250, 235, 215);
    cRGB blue = CRGB(0, 0, 255);
    cRGB cyan = CRGB(0, 255, 255);
    cRGB green = CRGB(0, 128, 0);
    cRGB lightskyblue = CRGB(135, 206, 250);
    cRGB lime = CRGB(0, 255, 0);
    cRGB mintcream = CRGB(245, 255, 250);
    cRGB orange = CRGB(255, 165, 0);
    cRGB orangered = CRGB(255, 100, 0);
    cRGB palegreen = CRGB(152, 251, 152);
    cRGB pink = CRGB(255, 192, 203);
    cRGB red = CRGB(255, 0, 0);
    cRGB skyblue = CRGB(135, 206, 235);
    cRGB slateblue = CRGB(106, 90, 205);
    cRGB purple = CRGB(150, 50, 255);
    cRGB violet = CRGB(238, 130, 238);
    cRGB white = CRGB(255, 255, 255);
    cRGB yellow = CRGB(255, 255, 0);
    cRGB yellowgreen = CRGB(154, 205, 50);

    // If your FUNCTION layer is not the default, you must set it here
    FunColor.functionLayer = FUNCTION;

    // Here we can set custom colors for your FunctionalColor instance.
    // You can optionally specify a brightness value, 0-255 to dim your lights.

    // Set this first to provide a "default" color for all keys, then override with the other settings.
    FunColor.all(CRGB(250, 235, 215));

    // Set this second to change all modifiers (non-alphabet/numeric/punctuation keys)
    FunColor.allModifiers(CRGB(250, 235, 215));

    // Set this before individual mouse settings to change all mouse-related keys
    FunColor.allMouse(CRGB(0, 200, 200));

    //Set individual groups of colors. You may delete any lines you don't need.
    FunColor.escape(red, 170);
    FunColor.numbers(orange, 160);
    FunColor.letters_top_row(yellow, 100);
    FunColor.letters_home_row(yellowgreen, 100);
    FunColor.letters_bottom_row(green, 100);
    FunColor.punctuation(cyan, 100);
    FunColor.brackets(blue, 200);
    FunColor.backslash(red, 170);
    FunColor.pipe(cyan, 170);
    FunColor.tab(blue, 170);
    FunColor.backspace(red, 170);
    FunColor.del(red, 170);
    FunColor.enter(lime, 190);
    FunColor.arrows(green, 170);
    FunColor.nav(cyan, 170);
    FunColor.insert(green, 170);
    FunColor.shift(purple, 190);
    FunColor.ctrl(blue, 170);
    FunColor.alt(violet, 200);
    FunColor.cmd(violet, 200);
    FunColor.app(CRGB(250, 235, 215));
    FunColor.printscreen(CRGB(250, 235, 215));
    FunColor.pause(CRGB(250, 235, 215));
    FunColor.scrolllock(CRGB(250, 235, 215));
    FunColor.capslock(CRGB(250, 235, 215));
    FunColor.fkeys(red, 170);
    FunColor.fn(CRGB(250, 235, 215));
    FunColor.media(CRGB(250, 235, 215));
    FunColor.led(blue, 190);
    FunColor.mousemove(cyan, 170);
    FunColor.mousebuttons(lightskyblue, 170);
    FunColor.mousewarp(cyan, 100);
    FunColor.mousescroll(lightskyblue, 100);

    //Copy new settings to the dimmed versions
    FunColorMedium = FunColor;
    FunColorLow = FunColor;

    // You could make adjustments to your other versions' groups here, if desired.

    // Adjust the brightness of dimmed versions here from 0-255
    FunColorMedium.brightness(210);
    FunColorLow.brightness(170);


  );
}
```

## Dependencies

* [Kaleidoscope-LEDControl](https://github.com/keyboardio/Kaleidoscope-LEDControl)
