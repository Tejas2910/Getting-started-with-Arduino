# Getting-started-with-Arduino

### Example 1
```     
#define LED_PIN 12

void setup()
{
  pinMode(LED_PIN, OUTPUT);
}

void loop()
{
  digitalWrite(LED_PIN, HIGH);
  delay(500);
  digitalWrite(LED_PIN, LOW);
  delay(500); 
}
```       
Let's break down this code line by line

`#define LED_PIN 12` 

Define variable name LED_PIN and it represents pin number 12.

```
void setup()
{
  pinMode(LED_PIN, OUTPUT);
}
```
 `void setup()`: This function is executed once at the beginning of the program.
 `pinMode(Pin number, Mode)` : Before we can actually use a digital pin, we need to set a mode. Basically you have 2 modes: output (if you want to control a component), or input (if you want to read some information from a component). Here, we want to control the LED, so we choose output.

Here, digital pin 12 will be set as output, and we can control the LED.
```
void loop()
{
  digitalWrite(LED_PIN, HIGH);
  delay(500);
  digitalWrite(LED_PIN, LOW);
  delay(500); 
}
```
`void loop()` : This function is executed again and again, until you power off the Arduino.
`digitalWrite(Pin number, State)` : Represent state (HIGH or LOW) of pin.
