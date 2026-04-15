Overview

This project is a motion detection system built using Arduino Uno and an ultrasonic sensor (HC-SR04). It detects the presence of an object based on distance and indicates the status using LEDs. The system provides real-time detection and is simple, cost-effective, and easy to implement.

Components Used
Arduino Uno
HC-SR04 Ultrasonic Sensor
Red LED
Green LED
220Ω Resistors
Jumper Wires
Breadboard
Connections
Ultrasonic Sensor:
VCC → 5V
GND → GND
TRIG → Pin 9
ECHO → Pin 10
LEDs:
Green LED → Pin 3 → Resistor → GND
Red LED → Pin 4 → Resistor → GND


Code
const int trigPin = 9;
const int echoPin = 10;
const int greenLED = 3;
const int redLED = 4;

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(redLED, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2;

  if (distance > 0 && distance < 10) {
    digitalWrite(redLED, HIGH);
    digitalWrite(greenLED, LOW);
  } else {
    digitalWrite(redLED, LOW);
    digitalWrite(greenLED, HIGH);
  }

  delay(500);
}


How It Works

The ultrasonic sensor measures the distance between the sensor and an object. If the object is within a set range, the system detects motion and turns ON the red LED. Otherwise, the green LED indicates no motion.

Features
Real-time motion detection
Simple and low-cost design
Easy to build and understand
LED-based indication system
Expandable to IoT applications

Future Scope
Add IoT for remote monitoring
Use multiple sensors for larger areas
Integrate mobile notifications
Implement smart automation systems
