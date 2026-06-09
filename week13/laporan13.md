# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 13

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 13 (Ethernet and ARP)

## Tujuan Praktikum
1. Memahami konsep dasar Ethernet sebagai teknologi komunikasi pada jaringan lokal (LAN).
2. Memahami fungsi dan mekanisme kerja Address Resolution Protocol (ARP) dalam proses komunikasi jaringan.
3. Mengetahui hubungan antara alamat logis (IP Address) dan alamat fisik (MAC Address) pada jaringan komputer.
4. Mengamati proses ARP Request dan ARP Reply menggunakan aplikasi Wireshark.
5. Menganalisis struktur frame Ethernet serta informasi yang terkandung di dalamnya.
6. Memahami mekanisme broadcast dan unicast yang digunakan dalam komunikasi ARP.
7. Menggunakan Wireshark untuk melakukan capture, filter, dan analisis paket jaringan.
8. Mengetahui proses pemetaan alamat IP ke alamat MAC sebelum terjadinya komunikasi data pada jaringan Ethernet.

---

## Dasar Teori
1. Ethernet

Ethernet merupakan teknologi jaringan yang digunakan untuk menghubungkan perangkat-perangkat dalam jaringan lokal (Local Area Network/LAN). Ethernet bekerja pada Layer 2 (Data Link Layer) dalam model OSI dan berfungsi untuk mengatur proses pengiriman data antar perangkat dalam jaringan.

Pada jaringan Ethernet, setiap perangkat memiliki alamat fisik yang disebut MAC Address (Media Access Control Address). Alamat ini bersifat unik dan digunakan sebagai identitas perangkat saat proses komunikasi berlangsung.

Frame Ethernet terdiri dari beberapa bagian utama, yaitu:

- Destination MAC Address
- Source MAC Address
- EtherType
- Payload (Data)
- Frame Check Sequence (FCS)

EtherType digunakan untuk menunjukkan jenis protokol yang dibawa oleh frame Ethernet.

|EtherType | Protokol |
|----------|----------|
|0x0800    | IPv4     |
|0x0806    | ARP      |
|0x86DD    | IPv6     |

Ethernet menjadi salah satu teknologi jaringan yang paling banyak digunakan karena memiliki kecepatan tinggi, biaya implementasi yang relatif rendah, serta mudah dikembangkan sesuai kebutuhan jaringan.

---

2. MAC Address

MAC Address (Media Access Control Address) merupakan alamat fisik unik yang dimiliki oleh setiap perangkat jaringan. MAC Address terdiri dari 48 bit dan biasanya dituliskan dalam format heksadesimal yang dipisahkan oleh tanda titik dua (:).

Contoh:

70:08:94:ac:7a:09

MAC Address digunakan untuk mengidentifikasi perangkat pada jaringan lokal dan menjadi tujuan utama dalam proses pengiriman frame Ethernet.

---

3. Address Resolution Protocol (ARP)

Address Resolution Protocol (ARP) adalah protokol yang digunakan untuk menerjemahkan alamat IP menjadi alamat MAC Address pada jaringan IPv4. ARP diperlukan karena komunikasi pada jaringan Ethernet menggunakan MAC Address, sedangkan pengguna umumnya mengenali perangkat berdasarkan IP Address.

Ketika sebuah perangkat mengetahui alamat IP tujuan tetapi belum mengetahui alamat MAC tujuan, perangkat tersebut akan mengirimkan ARP Request untuk memperoleh informasi alamat fisik yang sesuai.

ARP bekerja di antara Layer 2 (Data Link Layer) dan Layer 3 (Network Layer), sehingga berfungsi sebagai penghubung antara protokol IP dan Ethernet.

---

4. Cara Kerja Ethernet dan ARP

Ethernet dan ARP bekerja secara bersamaan dalam proses komunikasi jaringan. Ethernet bertugas mengirimkan frame berdasarkan MAC Address, sedangkan ARP bertugas mencari dan menerjemahkan alamat IP menjadi MAC Address yang sesuai.

Proses komunikasi berlangsung melalui beberapa tahapan sebagai berikut:

1. Menentukan Alamat Tujuan

Ketika sebuah perangkat ingin mengirim data ke perangkat lain, perangkat tersebut terlebih dahulu mengetahui alamat IP tujuan yang akan dihubungi.

2. Memeriksa ARP Cache

Sebelum mengirim data, sistem akan memeriksa ARP Cache untuk mengetahui apakah pasangan IP Address dan MAC Address tujuan sudah tersimpan sebelumnya.

Jika informasi tersebut tersedia, perangkat dapat langsung mengirimkan frame Ethernet tanpa melakukan proses ARP kembali.

3. Mengirim ARP Request

Jika alamat MAC tujuan belum ditemukan dalam ARP Cache, perangkat akan mengirimkan ARP Request ke seluruh perangkat dalam jaringan menggunakan alamat broadcast:

ff:ff:ff:ff:ff:ff

Contoh pesan ARP Request:

Who has 10.106.84.254? Tell 10.106.84.59

Pesan tersebut berarti perangkat dengan IP Address 10.106.84.59 meminta informasi MAC Address milik perangkat dengan IP Address 10.106.84.254.

4. Menerima ARP Reply

Perangkat yang memiliki alamat IP yang dicari akan mengirimkan ARP Reply sebagai balasan.

ARP Reply berisi informasi alamat MAC perangkat tersebut dan dikirim langsung (unicast) kepada perangkat yang meminta informasi.

Contoh:

10.106.84.254 is at xx:xx:xx:xx:xx:xx

5. Menyimpan Informasi ke ARP Cache

Setelah menerima ARP Reply, perangkat akan menyimpan pasangan IP Address dan MAC Address tersebut ke dalam ARP Cache.

Penyimpanan ini bertujuan agar komunikasi berikutnya dapat berlangsung lebih cepat tanpa perlu mengirim ARP Request kembali.

6. Mengirim Frame Ethernet

Setelah alamat MAC tujuan diketahui, perangkat dapat membuat frame Ethernet yang berisi:

- Destination MAC Address
- Source MAC Address
- EtherType
- Payload Data

Frame Ethernet kemudian dikirim menuju perangkat tujuan melalui jaringan lokal.

7. Data Diterima oleh Tujuan

Perangkat tujuan menerima frame Ethernet berdasarkan Destination MAC Address yang sesuai. Selanjutnya data diproses oleh lapisan jaringan yang lebih tinggi hingga mencapai aplikasi yang dituju.

---

5. Hubungan Ethernet dan ARP

Ethernet dan ARP memiliki hubungan yang sangat erat dalam komunikasi jaringan lokal. Ethernet bertugas mengirimkan frame berdasarkan MAC Address, sedangkan ARP bertugas mencari dan menerjemahkan alamat IP menjadi MAC Address yang sesuai.

Tanpa ARP, perangkat tidak dapat mengetahui alamat MAC tujuan sehingga frame Ethernet tidak dapat dikirimkan dengan benar. Oleh karena itu, ARP menjadi salah satu protokol penting yang mendukung komunikasi pada jaringan Ethernet.

Secara sederhana, ARP berfungsi sebagai penghubung antara alamat logis (IP Address) dan alamat fisik (MAC Address), sedangkan Ethernet berfungsi sebagai media pengiriman data antar perangkat dalam jaringan lokal.

---

## Analisis ARP pada Wireshark

Pada praktikum ini dilakukan pengamatan terhadap proses kerja Address Resolution Protocol (ARP) menggunakan aplikasi Wireshark. ARP digunakan untuk menerjemahkan alamat IP menjadi alamat MAC Address sehingga perangkat dapat berkomunikasi pada jaringan Ethernet.

Sebelum proses capture dilakukan, ARP Cache dihapus terlebih dahulu agar komputer melakukan proses pencarian alamat MAC kembali. Dengan demikian paket ARP Request dan ARP Reply dapat diamati secara langsung pada hasil capture Wireshark.

---

1. Menghapus ARP Cache

Gambar 1. Penghapusan ARP Cache Menggunakan Command Prompt

![Tampilan CMD yang menjalankan perintah arp -d](../assets/image/Tampilan%20CMD%20yang%20menjalankan%20perintah%20arp%20-d.png)

Pada tahap awal praktikum dilakukan penghapusan ARP Cache menggunakan Command Prompt dengan hak akses Administrator.

Perintah yang digunakan:

```bash
arp -d *
```
Perintah tersebut berfungsi untuk menghapus seluruh pasangan IP Address dan MAC Address yang tersimpan pada ARP Cache. Setelah cache dihapus, komputer harus melakukan proses ARP kembali saat berkomunikasi dengan perangkat lain sehingga paket ARP dapat terlihat pada Wireshark.

---

2. Pencarian Protokol IPv4

Gambar 2. Pencarian IPv4 pada Wireshark

![Tampilan Search IPv4](../assets/image/tampilan%20Search%20IPv4.png)

Pada tahap ini dilakukan pencarian protokol IPv4 pada menu Enabled Protocols di Wireshark. Langkah ini bertujuan untuk memastikan bahwa protokol IPv4 dapat dikonfigurasi sesuai kebutuhan praktikum.

Proses pencarian dilakukan dengan memasukkan kata kunci "IPv4" pada kolom pencarian sehingga protokol dapat ditemukan dengan lebih mudah.

---

3. Menonaktifkan Protokol IPv4

Gambar 3. Menonaktifkan IPv4 pada Wireshark

![tampilan Disable IPv4](../assets/image/tampilan%20Disable%20IPv4.png)

Setelah protokol IPv4 ditemukan, dilakukan penonaktifan sementara sesuai petunjuk praktikum.

Tujuan langkah ini adalah untuk mempermudah proses pengamatan paket ARP sehingga paket yang ditampilkan menjadi lebih fokus dan tidak bercampur dengan banyak paket IPv4 lainnya.

---

4. Mengakses Website Target

Gambar 4. Halaman Website yang Diakses

![Tampilan Halaman Website yang Diakses](../assets/image/Tampilan%20Halaman%20Website%20yang%20Diakses.png)

Setelah proses capture dimulai, dilakukan akses ke halaman web berikut:

http://gaia.cs.umass.edu/wireshark-labs/HTTP-ethereal-lab-file3.html

Akses terhadap website tersebut bertujuan untuk menghasilkan aktivitas jaringan sehingga Wireshark dapat menangkap paket-paket yang terjadi selama proses komunikasi berlangsung.

---

5. Menampilkan Paket ARP

Gambar 5. Hasil Filter ARP pada Wireshark

![Tampilan Hasil filter arp](../assets/image/Tampilan%20hasil%20filter%20arp.png)

Setelah proses capture selesai, dilakukan penyaringan paket menggunakan filter:

```bash
arp
```

Hasil filter menunjukkan adanya paket ARP Request dan ARP Reply yang terjadi pada jaringan lokal.

Pada kolom Info terlihat informasi seperti:

Who has 10.106.84.254? Tell 10.106.84.59

Informasi tersebut menunjukkan bahwa host dengan IP Address 10.106.84.59 sedang mencari alamat MAC dari perangkat yang memiliki IP Address 10.106.84.254.

---

6. Analisis Paket ARP

Gambar 6. Analisis Paket ARP Request

![Tampilan Analisis Paket ARP Request](../assets/image/Tampilan%20Analisis%20Paket%20ARP%20Request.png)

Berdasarkan hasil pengamatan diperoleh informasi sebagai berikut:

|Parameter               | Nilai             |   
|------------------------|-------------------|
|Protocol                | ARP               |
|Opcode                  | Request (1)       |
|Sender IP Address       | 10.106.84.59      |
|Sender MAC Address      | 70:08:94:ac:7a:09 |
|Target IP Address       | 10.106.84.254     |
|Target MAC Address      | 00:00:00:00:00:00 |
|Destination MAC Address | ff:ff:ff:ff:ff:ff |
|EtherType               | 0x0806            |

Pada kolom Info terlihat informasi:

Who has 10.106.84.254? Tell 10.106.84.59

Analisis

Paket yang diamati merupakan ARP Request yang dikirim oleh host dengan alamat IP 10.106.84.59 untuk mencari alamat MAC dari perangkat dengan alamat IP 10.106.84.254.

Karena alamat MAC tujuan belum diketahui, paket dikirim menggunakan alamat broadcast ff:ff:ff:ff:ff:ff sehingga seluruh perangkat dalam jaringan lokal menerima permintaan tersebut.

Target MAC Address masih bernilai 00:00:00:00:00:00 karena informasi alamat fisik tujuan belum diperoleh. Setelah perangkat tujuan menerima ARP Request, perangkat tersebut akan mengirimkan ARP Reply yang berisi alamat MAC miliknya.

Informasi tersebut kemudian disimpan ke dalam ARP Cache sehingga komunikasi berikutnya dapat berlangsung lebih cepat tanpa perlu melakukan proses ARP kembali.

---

## Kesimpulan

1. Ethernet merupakan teknologi jaringan yang bekerja pada Layer 2 (Data Link Layer) model OSI dan menggunakan MAC Address sebagai identitas fisik perangkat dalam proses komunikasi jaringan.

2. Address Resolution Protocol (ARP) berfungsi untuk menerjemahkan alamat IP menjadi alamat MAC Address sehingga komunikasi antar perangkat pada jaringan Ethernet dapat berlangsung dengan baik.

3. Paket ARP Request dikirim secara broadcast menggunakan alamat MAC ff:ff:ff:ff:ff:ff untuk mencari alamat fisik dari suatu IP Address yang belum diketahui.

4. Paket ARP Reply dikirim secara unicast sebagai balasan yang berisi informasi MAC Address dari perangkat yang memiliki IP Address yang dicari.

5. Hasil pengamatan pada Wireshark menunjukkan adanya proses pencarian alamat MAC dari IP Address 10.106.84.254 oleh host dengan IP Address 10.106.84.59.

6. Informasi pasangan IP Address dan MAC Address yang diperoleh melalui ARP akan disimpan pada ARP Cache sehingga proses komunikasi berikutnya dapat berlangsung lebih cepat dan efisien.

7. Wireshark dapat dimanfaatkan untuk mengamati serta menganalisis paket Ethernet dan ARP secara detail sehingga mekanisme komunikasi pada jaringan komputer dapat dipahami dengan lebih baik.