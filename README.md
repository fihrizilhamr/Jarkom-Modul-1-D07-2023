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

a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? `258040667`
##### Jawaban
Untuk mendapatkan sequence number (raw) pada packet yang menunjukkan aktivitas tersebut adalah dengan memasukkan filter seperti di bawah ini:

```
ftp.request.command == "STOR"
```
Lalu sistem akan menampilkan _source address_, yaitu 192.168.254.129. Sistem juga akan menampilkan _destination address_, yaitu 10.21.78.111. Kemudian menunjukkan sequence number beserta acknowledge number pada soal poin b.
<img width="931" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/961463e4-5d39-4061-8e34-f98f8e5bd6f4">


b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? `1044861039`

c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut? `1044861039`
##### Jawaban
Untuk mendapatkan sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut adalah dengan memasukkan filter seperti di bawah ini:

```
ftp.response.arg contains "c75"
```
Lalu sistem akan menampilkan _source address_, yaitu 192.168.254.129. Sistem juga akan menampilkan _destination address_, yaitu 10.21.78.111. Kemudian menunjukkan sequence number beserta acknowledge number pada soal poin d.
<img width="1034" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/ca68d467-4235-478c-b020-ff521f3ac6cb">


d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut? `258040696`

<img width="1020" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/fafb2f7a-e2ec-45de-8404-890a052e73ee">



### Soal 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer! `gunicorn`
##### Jawaban
Untuk mendapatkan web server yang digunakan pada portal praktikum ini adalah dengan memasukkan filter seperti di bawah ini:

```
http contains "www"
```

Lalu sistem akan menampilkan 3 _source address_ yang sama, yaitu 10.21.78.111. Sistem juga akan menampilkan 3 _destination address_ yang sama, yaitu 192.168.254.129. Masing-masing address adalah milik VPN ITS. Kemudian sistem akan menunjukkan web server dengan tampilan sebagai berikut.

<img width="1065" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/d5600df9-8a74-410b-a5d2-f683492c7634">



### Soal 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702? `21`

b. Protokol layer transport apa yang digunakan? `UDP`

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

a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut? `60`

b. Port berapakah pada server yang digunakan untuk service SMTP? `25`

c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP? `74.53.140.153`

###### Jawaban
Untuk menyelesaikan soal di atas, kita perlu mendapatkan `host` dan `port` yang tepat untuk melakukan `netcat`. Untuk itu, kita dapat menggunakan perintah berikut:
```
smtp.auth.password
```
Untuk melihat dan menganalisis paket yang telah ditangkap, kita dapat menggunakan fungsi `Follow TCP Stream` terhadap paket yang telah ditemukan. Setelah itu, kita dapat menemukan string yang telah diencode menggunakan Base64, yaitu `NWltcGxlUGFzNXdvcmQ=`. Setelah kita mendecode string tersebut, kita akan mendapatkan passwordnya, yaitu `5implePas5word`.

Selanjutnya, kita dapat membuka file teks menggunakan password tersebut. Dengan cara ini, kita dapat menemukan host dan port yang diperlukan, yaitu `nc 10.21.78.111 11111`.

Untuk mengetahui berapa banyak paket yang berhasil ditangkap (captured), kita dapat melihat pada bagian `Displayed Packets`. Setelah diperiksa, kita dapat mengetahui bahwa jumlah paket yang berhasil ditangkap adalah sebanyak **60**.

Adapun untuk mengetahui port yang digunakan oleh server untuk layanan SMTP, jawabannya adalah port **25**. Port **25** adalah port standar yang digunakan untuk mengirim email melalui protokol SMTP.

Terakhir, untuk mendapatkan alamat IP publik, kita perlu menghilangkan alamat IP pribadi terlebih dahulu. Rentang alamat IP publik mencakup semua nomor IP yang tidak dicadangkan untuk rentang alamat IP pribadi. Terdapat tiga kelas rentang alamat IP pribadi, yaitu:

- Kelas A: 10.x.x.x
- Kelas B: 172.16.x.x
- Kelas C: 192.168.x.x

Untuk menghilangkan alamat IP pribadi, kita dapat menggunakan perintah berikut:
```
(ip.dst != 192.168.0.0/16 && ip.dst != 172.16.0.0/12 && ip.dst != 10.0.0.0/8)
```
Kemudian kita bisa melihat _Destination Address_ yang merupakan _public_ IP, yaitu **74.53.140.153**.

> ![No 5 Part 1](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/ff7c02e6-a319-43a8-9bf2-9b60e402079f)

> ![No 5 Part 2](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/8aa104c6-c06b-446a-bf9c-ce0291952374)

> ![No 5 Part 3](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/7179886f-f865-4c53-a869-096fef68c538)

> ![No 5 Part 4](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/c02ffa60-46a8-49a4-8583-99151f00c132)
 
> ![No 5 Part 5](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/75eb931c-a196-430d-91ec-5dd14b7c3262)


### Soal 6 ``Revisi``


### Soal 7
Berapa jumlah packet yang menuju IP 184.87.193.88? `6`
##### Jawaban
Untuk mengetahui jumlah packet yang menuju ke IP 184.87.193.88 adalah dengan memasukkan filter sebagai berikut.

```
ip.dst == 184.87.193.88
```
Lalu sistem akan menampilkan jumlah packetnya, yaitu 6.

<img width="1215" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/65f09bb6-4e09-46ad-aacc-e429e301de83">
<img width="1213" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/30b152a6-c488-4c83-a5ce-29bfae21aab8">



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
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet! `dhafin:kesayangank0k0`
##### Jawaban
Untuk mengetaui kredensial ketika _user_ mencoba login menggunakan Telnet adalah dengan memasukkan filter sebagai berikut:

```
telnet && frame contains "Login"
```

Lalu sistem akan menampilkan dengan format **[userame][password]** dan didapatkan jawabannya adalah **dhafin:kesayangank0k0**

<img width="1024" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/3fff3316-8ed9-4a2c-8e56-2b09cd4aa8c6">
<img width="1028" alt="image" src="https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/105486369/120c6eff-b364-41eb-845d-5421af934ee3">



## Revisi
### Soal 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut. `JDRNJA`

###### Jawaban
Untuk menyelesaikan soal di atas, kita perlu perhatikan kembali dengan cermat soal tersebut. Ada beberapa hal penting yang dapat dicatat:
- `server SOURCE ADDRESS 7812 is invalid`
- `a1 e5 u21` 
- Huruf inisial beberapa kata yang dapat dirangkai menjadi `SUBSTITUSI`

Dengan menggunakan data diatas, kita dapat tarik beberapa kesimpulan, yaitu:
- _`Source Address`_ pada paket `7812` merupakan hal yang penting
- Kita perlu mendecode sesuatu dengan menggunakan `a1z26`

Panggil paket nomor `7812` menggunakan Wireshark. Untuk memanggilnya, kita dapat menggunakan perintah berikut:
```
frame.number == 7812
```
Setelah itu, kita bisa dapatkan _Source Address_ yang bernilai `104.18.14.101`. Dengan membaginya menjadi integer berdigit dua dan satu, kita bisa mendapatkan `10`, `4`, `18`, `14`, `10`, dan `1`. 
| A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |:---: |:---: |:---: |:---: |:---: |:---: |:---: |:---: |:---: |
|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|26|

Dengan menggunakan tabel di atas, kita bisa menerjemahkannya menjadi **`JDRNJA`**.

> ![No 6](https://github.com/fihrizilhamr/Jarkom-Modul-1-D07-2023/assets/116176265/2ab6fda9-cf07-4961-9736-056efa47cc1e)

## Kendala
Berikut adalah kendala yang dihadapi ketika mencoba menyelesaikan tugas praktikum Jaringan Komputer:
1. Ketidakstabilan jaringan yang menyebabkan keterlambatan dalam proses pengerjaan.
2. Batasan waktu pengerjaan yang cukup singkat.
3. Keterbatasan waktu untuk mengembangkan _proof of concept_ yang komprehensif.
