# Smart Cane
## Table of Contents
- [About](#about)
- [Requirements](#requirements)
- [How Does it Work?](#how-does-it-work)
- [Interfacing the Arduino](#interfacing-the-arduino)

## About
Smart Cane adalah sebuah tugas project dari Topik Khusus Arsitektur dan Jaringan Komputer (AJK). Tujuan dari project ini adalah untuk mempermudah orang - orang yang mengalami kecacatan mata.

## Requirements
1. Arduino Uno
2. Ultrasonic Sensor (HCSR04)
3. Mini Breadboard
4. 9 volt battery
5. 9 volt battery connector
6. DC male power jack
7. Buzzer
8. Jumper Wire
9. Toggle Switch
10. Tongkat dan Kotak untuk penyimpanan hardware

## How Does it Work?
Teknologi di balik Arduino Smart Cane cukup jelas. Ada tiga bagian dibalik Smart Cane: input, controller, dan output. Input terdiri dari *Ultrasonic Sensor* yang mampu mendeteksi hambatan di depannya pada kisaran hingga 400cm. Bagian ini dihubungkan ke controller: *Arduino Uno* yang menentukan apakah ada rintangan yang terlalu dekat dengan tongkat dan memicu output jika memang demikian. Outputnya terdiri dari buzzer.

Interfacing the Arduino