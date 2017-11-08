# Smart Cane
## Table of Contents
- [About](#about)
- [Requirements](#requirements)
- [How Does it Work?](#how-does-it-work)
- [Interfacing the Arduino](#interfacing-the-arduino)
- [Uploading the Sketch for the Arduino Smart Cane](#uploading-the-sketch-for-the-arduino-smart-cane)
- [Assembling the Arduino Smart Cane](#assembling-the-arduino-smart-cane)
- [Attaching the Components on the Smart Cane](#attaching-the-components-on-the-smart-cane)

## About
Smart Cane adalah sebuah tugas project dari Topik Khusus Arsitektur dan Jaringan Komputer (AJK). Tujuan dari project ini adalah untuk mempermudah orang - orang yang mengalami kecacatan mata.

## Requirements 
1. Arduino Uno
2. Ultrasonic Sensor (HCSR04)
3. Mini Breadboard
4. 9 volt battery
5. 9 volt battery connector
6. DC male  + female power jack
7. Buzzer
8. Jumper Wire
9. Toggle Switch
10. Tongkat dan Kotak untuk penyimpanan hardware

## How Does it Work?
Teknologi di balik Arduino Smart Cane cukup jelas. Ada tiga bagian dibalik Smart Cane: input, controller, dan output. Input terdiri dari *Ultrasonic Sensor* yang mampu mendeteksi hambatan di depannya pada kisaran hingga 400cm. Bagian ini dihubungkan ke controller: *Arduino Uno* yang menentukan apakah ada rintangan yang terlalu dekat dengan tongkat dan memicu output jika memang demikian. Outputnya terdiri dari buzzer.

Untuk lebih mudahnya, dapat dikatakan alur kerja **Smart Cane** adalah: Input dari Ultrasonic Sensor -> Controller Arduino -> Output suara Buzzer

##Interfacing the Arduino
Sekarang saatnya memasang *Arduino Uno*! Ini dapat dilakukan dengan mudah dan tidak memiliki pengaturan kabel yang rumit. Lihat skema di bawah ini dan dengan hati-hati menghubungkan semua bagian ke Arduino. Saya menggunakan *Mini Breadboard* untuk menghubungkan *Ultrasonic Sensor* ke *Arduino Uno* dengan menggunakan *Jumper Wire*. Bagian lain seperti *Buzzer* terhubung langsung ke Arduino. Anda bisa melihat diagram pengkabelan dari gambar di bawah ini.
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
```c
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

##Assembling the Arduino Smart Cane
Nah sekarang saatnya menggabungkan keseluruhan material sehingga Smart Cane akan terbentuk. Disini kita menggunakan pipa/pegangan dari payung (berukuran -+1,25m) karena di ujung pegangan payung sudah ada holder 'L' melengkung untuk pegangan tangan. Oke langsung ke step nya ya 

	1. Siapkan cane / tongkat yang akan digunakan (sekali lagi, kita menggunakan pegangan dari payung. Ukuran -+1,25m)
	2. Siapkan Box untuk menaruh Arduino, buzzer, dan material lainnya
	3. Lem, dan pastikan semua sudah menempel ke Box tersebut sehingga semua komponen aman
	4. Done :)

##Attaching the Components on the Smart Cane
Ini adalah bagian terberat dari project ini. Temukan kotak yang dapat digunakan untuk memasukkan semua perangkat keras. Buat dua lubang untuk pemasangan *Ultrasonic Sensor* di tutup kotak seperti yang ditunjukkan pada gambar. peletakkan *buzzer* di luar kotak agar terdengar lebih baik. Selanjutnya, pasang *toggle switch* (pasang di bagain tongkat yang kalian inginkan, sebagai contoh *toggle switch* dipasang pada bagian luar kotak). Pasang baterai di dalam kotak dan sambungkan *Power Jack* ke *Arduino Uno*.

Sekarang pasang kotak ke tongkat menggunakan sekrup atau lem. Dalam project ini menggunakan kabel zip karena cukup kuat. Setelah menempelkan kotak ke tongkat.

![Dokumentasi 1](/1.jpg)
![Dokumentasi 2](/114012.jpg)
![Dokumentasi 3](/114013.jpg)
![Dokumentasi 4](/114016.jpg)