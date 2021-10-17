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

Define variable name LED_PIN and pin number it represents pin number 12
