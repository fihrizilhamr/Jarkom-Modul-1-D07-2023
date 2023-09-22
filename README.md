# Jarkom-Modul-1-D07-2023
## Pendahuluan

Repository ini dibentuk untuk menyelesaikan tugas praktikum Jaringan Komputer.

Anggota Kelompok D07:
| Nama | NRP |
| :---: | :---: |
| Danno Denis Dhaifullah | 5025211027 |
| Fihriz Ilham Rabbany | 5025211040 |

## Pembahasan

### Soal 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
##### Poin a)
Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 
##### Poin b)
Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
##### Poin c)
Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
##### Poin d)
Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

### Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

### Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
##### Poin a)
Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702? `21`
##### Poin b)
Protokol layer transport apa yang digunakan? `UDP`

###### Jawaban
Untuk menyelesaikan soal di atas, kita perlu memanggil paket yang sesuai dengan kriteria soal. Untuk memanggil paket yang ter_capture_ dengan IP _source_ maupun _destination_ `239.255.255.250` dengan port `3702`, kita dapat menggunakan perintah berikut:
```
(ip.src == 239.255.255.250 && udp.port == 3702) || (ip.dst == 239.255.255.250 && udp.port == 3702)
```
Periksa jumlah paket yang ter_capture_ pada bagian _Displayed Packets_. Setelah itu, kita bisa mendapatkan nilai **21**. Untuk mendapatkan nama protokol layer transport yang digunakan, periksa keterangan paket. Setelah itu, kita bisa mendapatkan jawaban **UDP**.

> ![No 3](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/10ad3c22-e045-45a2-9eeb-fae3cbd69f3f)



### Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130? `0x18e5`

###### Jawaban
Untuk menyelesaikan soal di atas, panggil paket nomor 130 menggunakan Wireshark. Untuk memanggilnya, kita dapat menggunakan perintah berikut:
```
frame.number == 130
```
Lalu, periksa nilai checksum pada bagian User Datagram Protocol (UDP). Setelah itu, kita bisa mendapatkan nilai **0x18e5**

> ![No 4](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/e3687ce8-269b-497c-a317-4e90d09f899b)

### Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
##### Poin a)
Berapa banyak packet yang berhasil di capture dari file pcap tersebut? `60`
##### Poin b)
Port berapakah pada server yang digunakan untuk service SMTP? `25`
##### Poin c)
Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP? `74.53.140.153`

###### Jawaban
Untuk menyelesaikan soal di atas, kita perlu mendapatkan `host` dan `port` yang tepat untuk melakukan netcat. Untuk itu, kita dapat menggunakan perintah berikut:
```
smtp.auth.password
```
Untuk melihat dan menganalisis paket yang ter_capture_, kita bisa `Follow TCP Stream` terhadapt paket yang telah ditemukan. Setelah itu, kitab isa menemukan string yang telah diencode menggunakan Base64, yaitu `NWltcGxlUGFzNXdvcmQ=`. Setelah kita decode, kitab isa mendapatkan passwordnya, yaitu `5implePas5word`. Kemudian, kita bisa buka text file menggunakan password tersebut. Dengan itu kita bisa mendapatkan `host` serta `port` yang dibutuhkan, yaitu `nc 10.21.78.111 11111`.
Untuk mendapatkan berapa banyak paket yang berhasil ter_capture_, kita dapat melihat pada bagian _Displayed Packets_. Setelah itu, kita bisa mendapatkan nilai **60**.
Untuk port pada server yang digunakan untuk service SMTP, kitab isa menjawab **25**. Karena Port 25 adalah port standar yang digunakan untuk mengirim email melalui protokol SMTP.
Untuk mendapatkan IP yang merupakan _public_ IP, kita bisa menghilangkan _private_ IP terlebih dahulu. Karena rentang alamat _public_ IP mencakup setiap nomor yang tidak dicadangkan untuk rentang _private_ IP. Ada tiga kelas rentang _private_ IP, yaitu: `Kelas A: 10.x.x.x`, `Kelas B: 172.16.x.x`, dan `Kelas C: 192.168.x.x`. Untuk itu, kita bisa menggunakan perintah berikut:
```
(ip.dst != 192.168.0.0/16 && ip.dst != 172.16.0.0/12 && ip.dst != 10.0.0.0/8)
```
Kemudian kita bisa melihat _Destination Address_ yang merupakan _public_ IP, yaitu **74.53.140.153**.

> ![No 5 Part 1](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/ff7c02e6-a319-43a8-9bf2-9b60e402079f)

> ![No 5 Part 2](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/8aa104c6-c06b-446a-bf9c-ce0291952374)

> ![No 5 Part 3](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/7179886f-f865-4c53-a869-096fef68c538)

> ![No 5 Part 4](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/c02ffa60-46a8-49a4-8583-99151f00c132)


### Soal 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

### Soal 7
Berapa jumlah packet yang menuju IP 184.87.193.88?

### Soal 8
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad). `tcp.dstport == 80 || udp.dstport == 80`

###### Jawaban
Untuk memanggil paket yang ter_capture_ dan menuju port `80`, kita dapat menggunakan perintah berikut:
```
tcp.dstport == 80 || udp.dstport == 80
```
Setelah itu, kita bisa mendapatkan kueri filter yang sesuai, yaitu **tcp.dstport == 80 || udp.dstport == 80**.

> ![No 8](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/81c9df5d-3b4a-497c-a1a6-c3eedf48071a)

### Soal 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34! `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`

###### Jawaban
Untuk memanggil paket yang ter_capture_ dan berasal dari alamat `10.51.40.1` tetapi tidak menuju ke alamat `10.39.55.34`, kita dapat menggunakan perintah berikut:
```
ip.src == 10.51.40.1 && ip.dst != 10.39.55.34
```
Setelah itu, kita bisa mendapatkan kueri filter yang sesuai, yaitu **ip.src == 10.51.40.1 && ip.dst != 10.39.55.34**.

> ![No 9]( https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/664b1c13-3401-46b7-b870-7f304b8e4ecd)



### Soal 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

## Kendala
Berikut adalah kendala yang dihadapi ketika mencoba menyelesaikan tugas praktikum Jaringan Komputer:
1. Ketidakstabilan jaringan yang menyebabkan keterlambatan dalam proses pengerjaan.
2. Batasan waktu pengerjaan yang cukup singkat.
3. Keterbatasan waktu untuk mengembangkan _proof of concept_ yang komprehensif.
