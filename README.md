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
Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?
##### Poin b)
Protokol layer transport apa yang digunakan?

### Soal 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?
###### Jawaban
Untuk menyelesaikan soal di atas, dapat ikuti langkah berikut:
Pertama, panggil paket nomor 130 menggunakan Wireshark. Untuk memanggilnya, kita dapat menggunakan perintah berikut:
```
wireshark frame.number == 130
```
Kedua, periksa nilai checksum pada bagian User Datagram Protocol (UDP). Setelah itu, kita bisa mendapatkan Nilai *0x18e5*
![No 4](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/e3687ce8-269b-497c-a317-4e90d09f899b)

### Soal 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
##### Poin a)
Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
##### Poin b)
Port berapakah pada server yang digunakan untuk service SMTP?
##### Poin c)
Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

### Soal 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

### Soal 7
Berapa jumlah packet yang menuju IP 184.87.193.88?

### Soal 8
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

### Soal 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

### Soal 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

## Kendala
Berikut adalah kendala yang dihadapi ketika mencoba menyelesaikan tugas praktikum Jaringan Komputer:
1. Ketidakstabilan jaringan yang menyebabkan keterlambatan dalam proses pengerjaan.
2. Batasan waktu pengerjaan yang cukup singkat.
3. Keterbatasan waktu untuk mengembangkan _proof of concept_ yang komprehensif.
