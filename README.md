# Digital Timer
 
Include your responses to the bold questions below. Include snippets of code that explain what you did. Deliverables are due next Tuesday. Post your lab reports as README.md pages on your GitHub, and post a link to that on your main class hub page.

## Part A. Solder your LCD panel

![Soldered LCD](https://github.com/noelkonagai/interactive-devices/blob/master/Lab%202/lab2_soldering.jpeg "Soldered LCD")

## Part B. Writing to the LCD
 
**a. What voltage level do you need to power your display?**

According to the [fact sheet](https://cdn-shop.adafruit.com/product-files/181/p181.pdf) I need 5V to power the display.

**b. What voltage level do you need to power the display backlight?**

According to the same fact sheet, I need an adjustable voltage, for which I chose a 3V input.
   
**c. What was one mistake you made when wiring up the display? How did you fix it?**

I got everything right the first time.

**d. What line of code do you need to change to make it flash your name instead of "Hello World"?**

Changing `lcd.print()` alters what gets displayed.
```java
lcd.print("My name is Noel!");
```
 
**e. Include a copy of your Lowly Multimeter code in your lab write-up.**

In order to achieve this circuit, I changed the circuit design by integrating a 10kOhm resistor in lieu of the potentiometer that served to adjust the contrast of the LCD. Once I freed up the potentiometer, I integrated it again in the circuit with 5V as input, the middle pin connected to the A0 pin, and the GND pin to ground.

Here is a working [video](https://youtu.be/2GSZCz1kAis) of the voltmeter.


```java
// include the library code:
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

int sensorPin = A0;    // select the input pin for the potentiometer
int sensorValue = 0;  // variable to store the value coming from the sensor
float inputVoltage = 0.0;

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  lcd.print("Voltage:");
}

void loop() {
  // read the value from the sensor:
  sensorValue = analogRead(sensorPin);
  inputVoltage = (sensorValue * 5.0) / 1024.0; // converting the 10-bit reading to actual volts
  lcd.setCursor(0,1);
  lcd.print(inputVoltage);
  delay(300); // to enhance readability
}
```

## Part C. Using a time-based digital sensor

[Working Rotary Encoder Video](https://youtu.be/vdCoxvCP6rs)

## Part D. Make your Arduino sing!

**a. How would you change the code to make the song play twice as fast?**

I changed the following bit of the code, where I doubled the numbers to play the song twice as fast.

```java
int noteDurations[] = {
  8, 16, 16, 8, 8, 8, 8, 8
};
```
 
**b. What song is playing?**

Star Wars

## Part E. Make your own timer

**a. Make a short video showing how your timer works, and what happens when time is up!**

I decided to combine the three circuits that I made during this lab into this Digital Timer. I used the LCD to display instructions and the time left. I used the rotary encoder to enable the user to set a time from which the user may wish to count backwards from. Once time is up, I use the speaker to play a melody to indicate to the user that time is up. Then I use the LCD to display instructions how to resume a new session.

[link to video](https://youtu.be/31LO1Nfyvyg)

**b. Post a link to the completed lab report your class hub GitHub repo.**
