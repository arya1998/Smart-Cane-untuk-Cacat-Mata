# Smart Cane
## Table of Contents
- [About](#about)
- [Requirements](#requirements)
- [How Does it Work?](#how-does-it-work)
- [Interfacing the Arduino](#interfacing-the-arduino)
- [Uploading the Sketch for the Arduino Smart Cane](#uploading-the-sketch-for-the-arduino-smart-cane)

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

##Interfacing the Arduino
Sekarang saatnya memasang *Arduino Uno*! Ini dapat dilakukan dengan mudah dan tidak memiliki pengaturan kabel yang rumit. Lihat skema di bawah ini dan dengan hati-hati menghubungkan semua bagian ke Arduino. Saya menggunakan *Mini Breadboard* untuk menghubungkan *Ultrasonic Sensor* ke *Arduino Uno* dengan menggunakan *Jumper Wire*. Bagian lain seperti *Buzzer*terhubung langsung ke Arduino. Anda bisa melihat diagram pengkabelan dari gambar di bawah ini.
![Skema Smart Cane](https://301o583r8shhildde3s0vcnh-wpengine.netdna-ssl.com/wp-content/uploads/2016/08/conn-min.jpg)
Berikut adalah koneksi untuk setiap bagian:
- Ultrasonic VCC to Arduino 5v.
- Ultrasonic GND to Arduino GND.
- Ultrasonic TRIG to Arduino D13.
- Ultrasonic ECHO to Arduino D12.


- Buzzer RED to Arduino D6.
- Buzzer BLACK to Arduino GND.

- 9 volt battery RED to Toggle switch pin 1.
- 9 volt battery BLACK to DC male power jack(-).
- Toggle switch pin 2 to DC male power jack (+).

## Uploading the Sketch for the Arduino Smart Cane
Sekarang saatnya meng-*upload sketch*. *sketch* untuk Arduino diberikan di bawah ini, salinlah ini ke dalam IDE Arduino, lalu *upload* ke papan Arduino Anda.
```python
#define trigPin 13
#define echoPin 12
#define motor 7
#define buzzer 6

void setup()
{ pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
pinMode(motor, OUTPUT);
pinMode(buzzer,OUTPUT);
}

void loop()
{ long duration, distance;
digitalWrite(trigPin, LOW); 
delayMicroseconds(2); 
digitalWrite(trigPin, HIGH);
delayMicroseconds(10); 
digitalWrite(trigPin, LOW);

duration = pulseIn(echoPin, HIGH);
distance = (duration/2) / 29.1;

if (distance < 70) // Checking the distance, you can change the value
{ 
digitalWrite(motor,HIGH); // When the the distance below 100cm
digitalWrite(buzzer,HIGH);
} else
{
digitalWrite(motor,LOW);// when greater than 100cm
digitalWrite(buzzer,LOW); 
} delay(500);
}
```