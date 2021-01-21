```C++
//Johnny Krosby
//LED uses analog input to move from no brightness to full brightness

int ledValue = 5;
int ledPin = 9;
int analogDirection = 0; //0 is 100->0, 1 is 0->100

void setup() {
    Serial.begin(9600);
    pinMode(ledPin, OUTPUT);
}

void loop() {
  //Gives parameters to ledValue
  if(ledValue==100){
    analogDirection=0;
    Serial.println("going down");
  }
  else if(ledValue==0){
    analogDirection=1;
    Serial.println("going up");
  }
  //Actually writes to the LED
  if(analogDirection==0){
    
    ledValue--;
    delay(20);
    analogWrite(ledPin, ledValue);
    Serial.println(ledValue);
  }
  else if(analogDirection==1){
    ledValue++;
    delay(20);
    analogWrite(ledPin, ledValue);
    Serial.println(ledValue);
  }
}

```
