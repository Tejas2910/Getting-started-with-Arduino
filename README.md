# Getting-started-with-Arduino
## Refer this Doc : 
## Example 1
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

`delay()` : function will block the program for a given amount of time (in milliseconds).

## Example 2
```
#define LED_PIN 11

void setup()
{
  pinMode(LED_PIN, OUTPUT);
}

void loop()
{
  for (int i = 0; i <= 255; i++) {
    analogWrite(LED_PIN, i);
    delay(10);
  }
  
  for (int i = 255; i >= 0; i--) {
    analogWrite(LED_PIN, i);
    delay(10);
  }
}
```
## Example 3
```
int j = 1;
int wait = 500;

void setup() {
  // put your setup code here, to run once:
Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
Serial.println(j);
j = j+1;
delay(wait);
}
```
`Serial.begin(9600);` : Begin the serial data transmission at the rate of 9600 bits per second.

`Serial.println(j);` : print on next line.

## Exmaple 4
```
int numblinks;
int wait = 500;
int LED_pin = 12;
int i ;
String msg ="Howm many times LED should blink"; 

void setup() {
  // put your setup code here, to run once:
Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
Serial.println(msg);
while(Serial.available()==0){
}
numblinks = Serial.parseInt();
for(i=1;i<=numblinks;i++){
  digitalWrite(LED_pin, HIGH);
  delay(wait);
  digitalWrite(LED_pin, LOW);
  delay(wait);
}
i = 1;
}
```
`while(Serial.available()==0){
}` : Loop will be execute again and again till we type on serial monitor.

`numblinks = Serial.parseInt();` : Takes the input we type in serial monitor.

## Example 5 
### Part 1
Arduino code without interrupts 
```
#define LED_PIN 9
#define BUTTON_PIN 3

byte ledState = LOW;

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT);
}

void loop() {
  if (digitalRead(BUTTON_PIN), HIGH) {
    ledState = !ledState;
  }

  digitalWrite(LED_PIN, ledState);
}
```
We initialize the pin of the LED as OUTPUT and the pin of the button as INPUT. In the if loop() we monitor the button state and modify the LED state accordingly. When the button is pressed ledstate gets changed.

### Part 2
```
#define LED_PIN 9
#define BUTTON_PIN 3

volatile byte ledState = LOW;

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT);

  attachInterrupt(digitalPinToInterrupt(BUTTON_PIN), blinkLed, RISING);
}

void loop() {
  digitalWrite(LED_PIN, ledState);
}

void blinkLed() {
  ledState = !ledState;
}
```
`attachInterrupt(digitalPinToInterrupt(BUTTON_PIN), blinkLed, RISING);` : When the signal on the button pin is rising – which means that push button is pressed, the current program execution – loop() function – will be stopped and the blinkLed() function will be called. Once blinkLed() has finished, the loop() can continue.

` attachInterrupt();` : This function takes 3 parameters: the interrupt pin, the function to call, and the type of interrupt.

`volatile byte ledState = LOW;` : variable is defined as volatile as it is used both inside and outside the interrupt function.
