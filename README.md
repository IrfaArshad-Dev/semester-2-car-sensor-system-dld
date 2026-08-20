# 🚗 Car Sensor System – Digital Logic Design Project

![DLD](https://img.shields.io/badge/Course-Digital%20Logic%20Design-blue) ![Arduino](https://img.shields.io/badge/Hardware-Arduino%20UNO-teal) ![Semester](https://img.shields.io/badge/Semester-2nd-orange) ![Status](https://img.shields.io/badge/Status-Complete-brightgreen) ![University](https://img.shields.io/badge/University-Riphah-lightgrey)

---

## 📖 Project Overview

This project was developed as part of the **Digital Logic Design (DLD)** course during **Spring 2025 (2nd Semester of BS Software Engineering)** at **Riphah International University**.

It demonstrates real-world automation using digital logic principles, sensors, and microcontrollers — implemented as two independent hardware modules:

- 🌙 **Module 1** — Automatic Smart Street Light System
- 🚧 **Module 2** — Automatic Car Parking Toll Gate System

> **Supervisor:** Ma'am Nayyab Khalid

---

## 🎯 Problem Statement

Traditional street lighting and parking gate systems are inefficient, labor-intensive, and energy-consuming. This project presents cost-effective, sensor-based automated alternatives that reduce manual intervention and improve safety.

---

## 🌟 Objectives

- Design automated systems that solve real-world problems using digital logic.
- Implement sensor-based circuits for energy conservation and smart access control.
- Demonstrate working physical prototypes with potential for scalability.

---

## 🚀 Modules

### 🌙 Module 1 — Automatic Smart Street Light

Operates on **motion detection** using an IR proximity sensor.

| Condition | Result |
|---|---|
| Motion detected | LEDs turn ON |
| No motion | LEDs remain OFF |

Simulates a smart, energy-saving street lighting system that activates only when needed.

---

### 🚧 Module 2 — Automatic Car Parking Toll Gate

Automates a toll gate using an **Arduino UNO + Ultrasonic Sensor (HC-SR04) + Servo Motor (SG90)**.

| Condition | Gate State |
|---|---|
| Vehicle within 25 cm | Servo at 180° → Gate OPEN |
| No vehicle (> 25 cm) | Servo at 90° → Gate CLOSED |

The sensor polls every **500ms**, keeping gate state updated in real time. When a vehicle is detected, the gate stays open for **3 seconds** before rechecking.

---

## 🛠️ Components Used

| # | Component | Purpose |
|---|---|---|
| 1 | LDR (Light Dependent Resistor) | Detects ambient light levels |
| 2 | BC-547 Transistor | NPN switching transistor |
| 3 | Resistors (10kΩ) | Standard current limiting |
| 4 | IR Proximity Sensor | Detects motion or nearby objects |
| 5 | LEDs | Visual state indicators |
| 6 | 9V Battery | Circuit power supply |
| 7 | On/Off Switch | Manual power control |
| 8 | Jumper Wires | Component connections |
| 9 | Arduino UNO | Microcontroller for logic & control |
| 10 | Ultrasonic Sensor (HC-SR04) | Distance measurement via sound waves |
| 11 | Servo Motor (SG90) | Gate barrier operation |
| 12 | Breadboard | Solderless prototyping platform |

---

## 💻 Arduino Code (Module 2)

```cpp
#include <Servo.h>

Servo servo;
int trigPin = 11;
int echoPin = 12;

long duration;
float distance;

void setup() {
  Serial.begin(9600);
  servo.attach(13);
  servo.write(180);   // Gate open on start
  delay(2000);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH, 20000);
  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.println(distance);

  if (distance <= 25) {
    servo.write(180);   // Gate open
    delay(3000);
  } else {
    servo.write(90);    // Gate closed
  }

  delay(500);
}
```

---

## 📂 Repository Structure

```
semester-2-car-sensor-system-dld/
│
├── Documentation/
│   └── DLD_Final_Project_Report.pdf
│
├── Demo/
│   └── Car_Sensor_System.mp4
│
├── README.md
└── LICENSE
```

---

## 📊 Results

All modules performed their intended functions successfully during testing.

- ✅ **Module 1** — Lights activated only on motion detection, conserving energy.
- ✅ **Module 2** — Gate automated correctly based on vehicle proximity, reducing manual labor and improving vehicle flow.

---

## 🔮 Future Improvements

- 📡 Wireless technology integration (Wi-Fi / Bluetooth)
- ☁️ Cloud-based data logging and monitoring
- 🤖 AI-driven decision-making
- 📱 Mobile app control interface

---

## 🎓 Academic Context

| Field | Detail |
|---|---|
| Course | Digital Logic Design (DLD) |
| Program | BS Software Engineering |
| Semester | 2nd Semester |
| Session | Spring 2025 |
| Institution | Riphah International University |
| Submission Date | 20 May 2025 |

---

## 👩‍💻 Project Team

| Name | SAP ID | Email |
|---|---|---|
| Irfa Arshad | 63662 | irfaarshad98@gmail.com |
| Eman Zahid | 63906 | emanzahid.036@gmail.com |
| Alisha Muqadas | 62787 | alishamuqdas185@gmail.com |
| Amina Batool | 62461 | 62461@students.riphah.edu.pk |

---

## 🎥 Demo Video

📺 [Watch on Google Drive](https://drive.google.com/file/d/1zzrQSzyD-3wIL7z0GFH8Q2-Zy42sbiHm/view?usp=drive_link)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
