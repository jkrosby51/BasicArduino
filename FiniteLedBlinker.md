```C++
//  Johnny Krosby
//  Blinks 5 times and then stops

int counter = 0;
int ledPin = 8;

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, INPUT);
  digitalWrite(ledPin,LOW);
}

void loop() {
  if (counter < 5) {
    counter++;
    Serial.println(counter);
    digitalWrite(ledPin, HIGH);
    delay(100);
    digitalWrite(ledPin, LOW);
    delay(100);
  }
}
```
