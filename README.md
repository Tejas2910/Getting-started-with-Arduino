# Getting-started-with-Arduino

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
`Serial.begin(9600);` : The argument is no. of bytes per second and usually is taken as 9600.

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
