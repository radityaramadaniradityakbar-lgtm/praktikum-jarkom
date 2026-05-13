# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 11

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 11 (DHCP / Dynamic Host Configuration Protocol)

## Tujuan Praktikum
1. Memahami konsep dasar Dynamic Host Configuration Protocol pada jaringan komputer.
2. Mengetahui fungsi DHCP dalam pemberian alamat IP secara otomatis.
3. Mengamati proses pertukaran paket DHCP antara client dan server.
4. Mempelajari tahapan DORA (Discover, Offer, Request, Acknowledge).
5. Menggunakan Wireshark untuk melakukan capture dan analisis paket DHCP.
6. Menganalisis informasi jaringan yang diperoleh client dari DHCP Server.

## 1. Apa itu DHCP?
Dynamic Host Configuration Protocol adalah protokol jaringan yang digunakan untuk memberikan konfigurasi jaringan secara otomatis kepada perangkat yang terhubung pada suatu jaringan komputer. Konfigurasi tersebut meliputi alamat IP, subnet mask, default gateway, dan DNS server.

DHCP bekerja dengan bantuan DHCP Server yang bertugas membagikan alamat IP kepada setiap client yang terhubung ke jaringan. Dengan adanya DHCP, administrator jaringan tidak perlu melakukan pengaturan IP secara manual pada setiap perangkat sehingga proses konfigurasi jaringan menjadi lebih cepat dan efisien.

Penggunaan DHCP sangat membantu pada jaringan yang memiliki banyak perangkat, seperti laboratorium komputer, sekolah, kampus, kantor, maupun jaringan hotspot. Selain mempermudah pengelolaan jaringan, DHCP juga dapat mengurangi terjadinya konflik IP karena pembagian alamat IP dilakukan secara otomatis oleh server.

DHCP memiliki proses komunikasi yang disebut DORA, yaitu Discover, Offer, Request, dan Acknowledge. Melalui proses tersebut, client dapat memperoleh alamat IP secara otomatis dari DHCP Server sehingga perangkat dapat terhubung ke jaringan dan mengakses internet.

**Langkah-Langkah Konfigurasi DHCP**

**1. Membuka View Network Connections**

![Tampilan Membuka View Network Connections](../assets/image/Membuka%20View%20Network%20Connections.png)

- Penjelasan:
Langkah pertama yang dilakukan adalah membuka menu View Network Connections pada sistem operasi Windows. Menu ini digunakan untuk melihat seluruh koneksi jaringan yang tersedia pada komputer, baik koneksi WiFi maupun Ethernet.

Untuk membuka menu tersebut dapat dilakukan melalui Control Panel atau melalui fitur pencarian Windows dengan mengetik “View Network Connections”. Setelah menu terbuka, pengguna dapat melihat daftar adapter jaringan yang sedang aktif maupun yang tidak aktif.

Tahap ini penting karena seluruh konfigurasi jaringan dilakukan melalui halaman Network Connections.

**2. Tampilan Beranda Network Connections**

![Hasil Tampilan Beranda Network Connections](../assets/image/Tampilan%20Beranda%20Network%20Connections.png)

- Penjelasan:
Pada halaman Network Connections akan ditampilkan berbagai jenis koneksi jaringan yang tersedia pada komputer. Koneksi tersebut dapat berupa WiFi, Ethernet, Bluetooth Network, maupun Virtual Adapter.

Pada praktikum ini digunakan koneksi WiFi sebagai media jaringan yang akan dikonfigurasi menggunakan DHCP. Dari tampilan ini pengguna dapat mengetahui status koneksi jaringan apakah sedang terhubung atau tidak.

Selain itu, halaman ini juga digunakan untuk melakukan pengaturan jaringan melalui menu properties pada adapter yang dipilih.

**3. Memilih Koneksi WiFi**

![Tampilan Memilih Koneksi WiFi](../assets/image/Tampilan%20Memilih%20Koneksi%20WiFi.png)

- Penjelasan:
Langkah berikutnya adalah memilih koneksi WiFi yang sedang digunakan. Pemilihan koneksi dilakukan dengan cara klik kanan pada adapter WiFi yang aktif.

Tahap ini bertujuan agar konfigurasi DHCP diterapkan pada jaringan WiFi yang digunakan oleh komputer. Jika pengguna menggunakan koneksi Ethernet maka adapter yang dipilih dapat disesuaikan dengan jenis koneksi yang digunakan.

Pemilihan adapter jaringan yang benar sangat penting agar pengaturan DHCP dapat berjalan dengan baik pada koneksi yang digunakan.

**4. Membuka Properties WiFi**

![Tampilan Membuka Properties WiFi](../assets/image/Tampilan%20Membuka%20Properties%20WiFi.png)

- Penjelasan:
Setelah memilih koneksi WiFi, langkah selanjutnya adalah membuka menu Properties. Menu ini berisi berbagai pengaturan jaringan yang digunakan oleh adapter WiFi.

Pada menu properties terdapat beberapa layanan jaringan seperti:

- Client for Microsoft Networks
- File and Printer Sharing
- Internet Protocol Version 4 (TCP/IPv4)
- Internet Protocol Version 6 (TCP/IPv6)

Melalui menu inilah pengguna dapat melakukan konfigurasi alamat IP secara otomatis menggunakan DHCP maupun secara manual menggunakan static IP.

**5. Memilih Internet Protocol Version 4 (TCP/IPv4)**

![Tampilan Memilih Internet Protocol Version 4 (TCP/IPv4)](../assets/image/Tampilan%20Memilih%20Internet%20Protocol%20Version%204%20TCPIPv4.png)

- Penjelasan:
Pada langkah ini dipilih menu Internet Protocol Version 4 (TCP/IPv4) kemudian klik tombol Properties.

Pengaturan TCP/IPv4 digunakan untuk mengatur alamat IP pada jaringan IPv4. Di dalam pengaturan ini pengguna dapat memilih apakah alamat IP akan diberikan secara otomatis oleh DHCP Server atau diatur secara manual.

Karena praktikum menggunakan DHCP, maka pengaturan akan diarahkan agar komputer memperoleh IP secara otomatis dari server DHCP.

**6. Tampilan Pengaturan Internet Protocol Version 4 (TCP/IPv4)**

![Tampilan Pengaturan Internet Protocol Version 4 (TCP/IPv4)](../assets/image/Tampilan%20Pengaturan%20Internet%20Protocol%20Version%204%20TCPIPv4.png)

- Penjelasan:
Pada tampilan ini terdapat dua pilihan utama yaitu:

- Obtain an IP address automatically
- Use the following IP address

Karena menggunakan DHCP, maka dipilih opsi Obtain an IP address automatically serta Obtain DNS server address automatically. Pengaturan tersebut memungkinkan komputer menerima konfigurasi jaringan secara otomatis dari DHCP Server.

Setelah pengaturan selesai dan tombol OK ditekan, komputer akan melakukan proses komunikasi DHCP untuk memperoleh alamat IP. Proses ini dilakukan melalui tahapan DORA yaitu Discover, Offer, Request, dan Acknowledge.

Dengan konfigurasi ini, perangkat dapat langsung terhubung ke jaringan tanpa perlu memasukkan alamat IP secara manual sehingga proses konfigurasi jaringan menjadi lebih mudah dan efisien.

## 2. Kelebihan dan Kekurangan DHCP
**Kelebihan DHCP**

1. Pemberian alamat IP dilakukan otomatis

> Dynamic Host Configuration Protocol memungkinkan perangkat memperoleh alamat IP tanpa perlu pengaturan manual dari pengguna. Selain IP address, DHCP juga memberikan subnet mask, gateway, dan DNS secara otomatis.

2. Mempermudah pekerjaan administrator jaringan

> Administrator jaringan tidak perlu mengatur konfigurasi IP satu per satu pada setiap komputer karena seluruh pengaturan dapat dikontrol melalui DHCP Server.

3. Mengurangi terjadinya konflik IP

> DHCP membagikan alamat IP yang berbeda kepada setiap perangkat sehingga kemungkinan dua perangkat menggunakan IP yang sama dapat diminimalkan.

4. Proses koneksi perangkat menjadi lebih cepat

> Ketika perangkat baru terhubung ke jaringan, perangkat dapat langsung menerima konfigurasi jaringan otomatis sehingga pengguna tidak perlu melakukan setting tambahan.

5. Penggunaan alamat IP lebih terorganisir

> DHCP memiliki sistem lease time yang membuat alamat IP yang sudah tidak digunakan dapat dipakai kembali oleh perangkat lain.

6. Cocok digunakan pada jaringan besar

> Pada lingkungan seperti sekolah, laboratorium, kantor, dan kampus yang memiliki banyak perangkat, DHCP sangat membantu karena pengelolaan jaringan menjadi lebih praktis.

7. Mendukung perpindahan perangkat antar jaringan

> Laptop atau smartphone yang berpindah tempat dapat langsung memperoleh konfigurasi IP baru secara otomatis sesuai jaringan yang digunakan.

8. Mempermudah perubahan konfigurasi jaringan

> Jika terdapat perubahan gateway atau DNS server, administrator cukup mengganti konfigurasi pada DHCP Server tanpa perlu mengatur ulang seluruh perangkat client.

9. Mengurangi kesalahan konfigurasi manual

> Pengaturan IP secara manual sering menyebabkan kesalahan penulisan alamat IP atau subnet mask. DHCP membantu mengurangi kesalahan tersebut.

10. Memudahkan pemantauan jaringan

> Administrator dapat memantau penggunaan alamat IP yang sedang aktif melalui DHCP Server sehingga pengelolaan jaringan lebih mudah dilakukan.

**Kekurangan DHCP**

1. Bergantung pada DHCP Server

> Jika DHCP Server mengalami gangguan atau mati, perangkat client tidak dapat memperoleh alamat IP otomatis sehingga jaringan menjadi terganggu.

2. Alamat IP dapat berubah sewaktu-waktu

> IP yang diberikan DHCP bersifat dinamis sehingga alamat IP perangkat dapat berubah sesuai lease time yang berlaku.

3. Kurang sesuai untuk perangkat tertentu

> Perangkat seperti server, printer jaringan, CCTV, dan access point biasanya memerlukan IP statis agar lebih stabil dan mudah diakses.

4. Memerlukan pengelolaan server yang baik

> DHCP Server harus dikonfigurasi dengan benar agar pembagian alamat IP berjalan normal dan tidak terjadi masalah jaringan.

5. Risiko keamanan jaringan

> Perangkat asing yang terhubung ke jaringan dapat memperoleh IP secara otomatis apabila tidak ada pembatasan akses jaringan.

6. Lease time yang tidak tepat dapat menimbulkan masalah

> Lease time yang terlalu singkat dapat membuat proses pembaruan IP terlalu sering, sedangkan lease time yang terlalu lama dapat menyebabkan pemborosan alamat IP.

7. Sulit melakukan identifikasi perangkat tertentu

> Karena IP dapat berubah-ubah, administrator terkadang kesulitan mengenali perangkat tertentu dalam jaringan.

8. Gangguan pada server memengaruhi seluruh client

> Apabila DHCP Server mengalami error, banyak perangkat client dalam jaringan dapat kehilangan akses koneksi secara bersamaan.

9. Membutuhkan perangkat server tambahan

> Pada jaringan tertentu, DHCP memerlukan server khusus sehingga membutuhkan biaya dan pengelolaan tambahan.

10. Tidak semua jaringan cocok menggunakan DHCP penuh

> Beberapa jaringan yang membutuhkan keamanan tinggi atau pengaturan khusus lebih cocok menggunakan kombinasi DHCP dan IP statis.

## 3. DORA
Dynamic Host Configuration Protocol menggunakan proses komunikasi yang disebut DORA untuk melakukan pemberian alamat IP secara otomatis kepada perangkat client yang terhubung ke jaringan.

**DORA merupakan singkatan dari:**

- Discover
- Offer
- Request
- Acknowledge (ACK)

Proses ini terjadi ketika sebuah perangkat pertama kali terhubung ke jaringan dan belum memiliki alamat IP. DHCP Server kemudian membantu client memperoleh konfigurasi jaringan seperti IP address, subnet mask, default gateway, dan DNS server secara otomatis.

Pada praktikum ini, proses DORA diamati menggunakan Wireshark dengan melakukan capture paket DHCP yang terjadi antara client dan server. Dari hasil capture tersebut dapat dilihat bagaimana proses pertukaran paket berlangsung secara berurutan hingga client berhasil memperoleh alamat IP.

Analisis paket DHCP pada Wireshark sangat membantu untuk memahami cara kerja DHCP dalam jaringan komputer, terutama proses komunikasi antara client dan server pada saat pemberian alamat IP otomatis.

**Langkah - Langkah:**

1. Membuka file dhcp-ethereal-trace-1 pada aplikasi Wireshark.

![Tampilan File dhcp-ethereal-trace-1](../assets/image/Tampilan%20file%20%20dhcp-ethereal-trace-1.png)

2. Menjalankan proses analisis paket jaringan DHCP.
3. Mengetik filter dhcp pada kolom filter Wireshark untuk menampilkan paket DHCP saja.

![Tampilan dhcp-ethereal-trace-1](../assets/image/tampilan%20dhcp-ethereal-trace-1.png)

![Tampilan filter dhcp (dhcp-ethereal-trace-1)](../assets/image/Tampilan%20filter%20dhcp%20dhcp-ethereal-trace-1.png)

**Penjelasan:**

Berdasarkan hasil filter DHCP pada Wireshark, terlihat beberapa paket DHCP yang muncul secara berurutan. Paket tersebut menunjukkan proses komunikasi antara client dan DHCP Server dalam memperoleh alamat IP otomatis.

**Pada hasil capture terlihat paket:**

- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP ACK

Urutan paket tersebut menandakan bahwa proses DORA berjalan dengan baik.

Client yang belum memiliki alamat IP menggunakan source address 0.0.0.0 dan mengirim paket broadcast ke 255.255.255.255 agar DHCP Server dapat menerima permintaan tersebut. DHCP Server dengan alamat 192.168.1.1 kemudian merespon dan memberikan konfigurasi jaringan kepada client.

Selain paket utama DORA, pada hasil capture juga terlihat paket DHCP Release yang menunjukkan client melepaskan alamat IP sebelumnya sebelum meminta alamat IP baru kembali.

**Tahapan DORA**

**1. DHCP Discover**
> Tahap pertama dimulai ketika client mengirimkan paket DHCP Discover untuk mencari DHCP Server yang tersedia pada jaringan. Karena perangkat belum memiliki alamat IP, paket dikirim menggunakan alamat broadcast agar seluruh DHCP Server dapat menerima permintaan tersebut. Tahap ini menjadi langkah awal client meminta konfigurasi jaringan secara otomatis.

**2. DHCP Offer**
> Setelah menerima paket Discover, DHCP Server merespon dengan mengirimkan DHCP Offer kepada client. Pesan Offer berisi penawaran alamat IP beserta informasi jaringan lainnya seperti subnet mask, gateway, DNS server, dan lease time. Tahap ini menunjukkan bahwa server siap memberikan alamat IP kepada client.

**3. DHCP Request**
> Client kemudian memilih alamat IP yang ditawarkan lalu mengirimkan DHCP Request kepada server. Pesan Request digunakan sebagai tanda bahwa client menerima penawaran alamat IP tersebut dan ingin menggunakannya. Tahap ini juga memberitahukan server lain bahwa penawaran mereka tidak dipilih oleh client.

**4. DHCP ACK (Acknowledgement)**
> Tahap terakhir adalah DHCP ACK yang dikirim oleh DHCP Server sebagai konfirmasi akhir. Server menyatakan bahwa alamat IP telah resmi diberikan kepada client sehingga perangkat dapat mulai menggunakan jaringan dengan normal. Selain alamat IP, server juga mengirimkan konfigurasi jaringan lain yang diperlukan oleh client.