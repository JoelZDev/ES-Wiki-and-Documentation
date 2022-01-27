**Using the LED Module on ESP32**

LED.h:

This module is designed to be used via Platform.io. Place the header file inside your src directory and use the implemented methods in your code. To use the LED.h header you need to make sure the Adafruit NeoPixel library and the Arduino.h are installed in your project.
Make sure the LED Stripe is connected to PIN 2 on your board and you initialize your Pin 2 as a digital output inside your setup method.
This library works staticly with one connected LED stripe and you dont need to create any objects whatsoever.

Use the following methods to control a LED stripe:

LEDInit() - needs to be called in the the setup method of the main to initialize all pixels on the LED stripe.

LEDGlow(start, end, R, G, B) - expects a starting pixel, an ending pixel and red, green and blue color values and turns on all corresponding pixels in the chosen color.

LEDOff(start, end) - turns off all pixels between the starting and ending pixels (including the start and end pixel)

LEDOffAll() - turns off all pixels.

LEDGlowStart(start) - turns on one selected start LED to help indicate position of marker whilst setting up the size of a cabinet.

LEDGlowNext() - turns on the next LED in the row after the in the previous method selected starting point. (LED Nr = start+1)
