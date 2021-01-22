```C++
//Johnny Krosby
//Servo spins faster the closer an object is to the sensor

#include <Servo.h>

Servo myServo;

int servoPin = 9;
int triggerPin = 2;
int echoPin = 3;
int distanceMax = 25; // 13cm
int distanceMin = 0;
int distance;
int duration;
int speed; //servo speed

void setup() {
  Serial.begin(9600);
  pinMode(triggerPin, OUTPUT);
  pinMode(echoPin, INPUT);
  myServo.attach(servoPin);
}

void loop() {
  distance = 0;
  duration = 0;
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  
  // Convert in CM
  distance = (duration / 2) / 29.1;
  
  if (distance >= distanceMax || distance <= distanceMin) {
    Serial.println("Target not found");

    myServo.write(90); // Puts in stop position

  } else {
    Serial.print(distance);
    Serial.println(" cm");

    //Convert distance into parameters of 0-90 for the servo
    speed = (distance * 4.5);
    
    if (speed > 85) { 
      myServo.write(85);
    } else {
      myServo.write(speed);
      
    }
  }
}

```
