👁️ Third Eye for Blind (Arduino-Based Obstacle Detection)
📌 Project Overview

This project helps visually impaired people detect obstacles using an ultrasonic sensor. When an object comes within a certain distance, a buzzer alerts the user. The system is simple, low-cost, and portable.

🧰 Components Required
Arduino Uno
Ultrasonic Sensor (HC-SR04)
Buzzer
9V Battery + Battery Clip
Breadboard
Jumper Wires
⚙️ Working Principle

The ultrasonic sensor sends sound waves and receives echoes. Based on the time taken, distance is calculated. If the object is too close, the buzzer turns ON.

🔌 Circuit Connections
🟢 Ultrasonic Sensor (HC-SR04)
VCC → 5V (Arduino)
GND → GND (Arduino)
TRIG → Digital Pin 9
ECHO → Digital Pin 10
🔴 Buzzer
Positive (+) → Digital Pin 8
Negative (–) → GND
🔋 Power Supply
9V Battery → Vin (Arduino)
Battery GND → Arduino GND
![image alt](https://github.com/sreejavanaparthy106/third-eye-for-blind-people/blob/46b846893b7c5ae55d54559ee7f8d076842549d6/circuit%20diagram.jpg)

🧠 Arduino Code
#define trigPin 9
#define echoPin 10
#define buzzer 8

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzer, OUTPUT);
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

  Serial.print("Distance: ");
  Serial.println(distance);

  if (distance < 100) {
    digitalWrite(buzzer, HIGH);
  } else {
    digitalWrite(buzzer, LOW);
  }

  delay(200);
}
📏 Distance Logic
< 100 cm → Buzzer ON (Obstacle detected)
≥ 100 cm → Buzzer OFF

👉 You can modify this threshold based on your requirement.

🛠️ Assembly Tips
Mount the ultrasonic sensor facing forward
Use a small box or wearable frame (like glasses or belt clip)
Secure wires properly to avoid loose connections
Keep battery lightweight for portability
🚀 Improvements (Optional)
Use vibration motor instead of buzzer
Add multiple sensors for wider coverage
Use rechargeable battery instead of 9V
Add voice alerts using speaker module
🎯 Final Output

When powered, the system continuously checks for obstacles. If something comes near, the buzzer alerts instantly, helping the user avoid collisions.
