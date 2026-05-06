# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 10

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 10 (IP/ Internet Protocol)

## Tujuan Praktikum
- Memahami konsep dasar Internet Protocol (IP) dalam jaringan komputer.
- Memahami fungsi dan struktur IP Address sebagai identitas perangkat dalam jaringan.
- Mempelajari perbedaan antara IPv4 dan IPv6.
- Memahami konsep subnetting dalam pembagian jaringan.
- Mampu menampilkan dan mengidentifikasi IP Address pada sistem operasi (Windows/Linux).
- Memahami penggunaan perintah jaringan seperti ipconfig, ping, dan tracert.
- Menganalisis jalur pengiriman paket menggunakan traceroute.
- Memahami fungsi ICMP dalam pengujian konektivitas jaringan.
- Memahami konsep fragmentasi paket dalam IP.
- Mampu melakukan analisis paket jaringan menggunakan Wireshark.
- Memahami proses komunikasi data dalam jaringan berbasis IP.

**IP (Internet Protocol)**
Internet Protocol (IP) merupakan protokol utama dalam jaringan komputer yang berfungsi untuk mengatur proses pengiriman data dari satu perangkat ke perangkat lain. Setiap perangkat yang terhubung ke jaringan akan memiliki alamat khusus yang disebut IP Address, sehingga data dapat dikirim ke tujuan yang tepat. Dengan adanya IP Address, setiap perangkat dapat diidentifikasi secara unik dalam suatu jaringan.

**Jenis IP Address**
Secara umum, terdapat dua versi IP yang digunakan dalam jaringan komputer:

- **IPv4 (Internet Protocol version 4)**
    Menggunakan panjang alamat 32-bit yang terdiri dari empat bagian (oktet) yang dipisahkan oleh tanda titik.
    Contoh: 192.168.1.1

- **IPv6 (Internet Protocol version 6)**
    Menggunakan panjang alamat 128-bit yang ditulis dalam format heksadesimal dan dipisahkan dengan tanda titik dua.
    Contoh: 2001:db8::1

IPv6 dikembangkan untuk mengatasi keterbatasan jumlah alamat pada IPv4.

**Struktur dan Perhitungan IP Address**
IP Address IPv4 tersusun atas 4 bagian yang disebut oktet, dimana setiap oktet terdiri dari 8 bit. Karena setiap oktet memiliki 8 bit, maka nilai yang dapat ditampung berada pada rentang 0 hingga 255.

Perhitungan dasarnya:
- 1 oktet = 8 bit
- 1 oktet = 2⁸ = 256 kemungkinan nilai
- Total IPv4 = 4 oktet × 8 bit = 32 bit

Struktur ini memungkinkan kombinasi alamat yang cukup besar untuk digunakan dalam jaringan.

**Subnetting**
Subnetting adalah teknik pembagian jaringan besar menjadi beberapa jaringan yang lebih kecil (subnet). Tujuan utama dari subnetting adalah untuk meningkatkan efisiensi dan pengelolaan jaringan.

Manfaat subnetting antara lain:
- Mengurangi lalu lintas broadcast dalam jaringan
- Meningkatkan performa dan keamanan jaringan
- Mempermudah pengelolaan dan pengaturan alamat IP

Dengan subnetting, penggunaan alamat IP menjadi lebih terorganisir dan optimal sesuai kebutuhan Jaringan.

## 1. Apa itu IP Address?
IP Address (Internet Protocol Address) adalah alamat unik yang diberikan kepada setiap perangkat yang terhubung dalam jaringan komputer. Alamat ini berfungsi sebagai identitas sehingga perangkat dapat saling berkomunikasi dan bertukar data dengan tepat.
IP Address bekerja sebagai penunjuk lokasi dalam jaringan, sehingga setiap data yang dikirim memiliki tujuan yang jelas. Dalam proses komunikasi, IP Address digunakan untuk menentukan perangkat pengirim (source) dan perangkat penerima (destination).
Secara umum, terdapat dua jenis IP Address, yaitu:
- IPv4 (32-bit), contoh: 192.168.1.1
- IPv6 (128-bit), contoh: 2001:db8::1

**Langkah Pengerjaan**
1. Tekan tombol Windows + R
2. Ketik cmd, lalu tekan Enter
3. Pada Command Prompt (CMD), Ketik:
```bash
ipconfig
```
4. Tekan Enter

![Tampilan Hasil IP Address](../assets/image/tampilan%20apa%20itu%20ip%20address.png)

Perangkat menggunakan IP 192.168.1.14 yang termasuk dalam kelas C private. Subnet mask 255.255.255.0 (/24) digunakan untuk membagi bagian network dan host.
Network ID dari alamat tersebut adalah 192.168.1.0, dengan jumlah host yang dapat digunakan dalam jaringan sebanyak 254 perangkat.
Default gateway 192.168.1.1 berfungsi sebagai penghubung antara jaringan lokal dengan jaringan lain (internet).
Selain itu, perangkat juga memiliki beberapa IP Address tambahan dari adapter virtual seperti 192.168.56.1, 192.168.249.1, dan 192.168.198.1 yang digunakan untuk kebutuhan virtual machine.
Perangkat juga mendukung IPv6, yang ditunjukkan dengan adanya alamat IPv6 global dan link-local.

## 2. Traceroute dari suatu website
Traceroute adalah tool jaringan yang digunakan untuk mengetahui jalur (rute) yang dilewati oleh paket data dari perangkat sumber menuju server tujuan. Traceroute bekerja dengan mengirim paket secara bertahap ke setiap router (hop) yang dilewati dan mencatat waktu tempuhnya.

Dengan traceroute, pengguna dapat:
- Mengetahui jalur pengiriman data
- Mengidentifikasi jumlah hop
- Menganalisis keterlambatan jaringan
- Mendeteksi gangguan koneksi

**Langkah Pengerjaan**
1. Tekan tombol Windows + R
2. Ketik cmd, lalu tekan Enter
3. Pada Command Prompt (CMD), Ketik:
```bash
tracert google.com
```
4. Tekan Enter
5. Tunggu hingga proses selesai
![Tampilan Hasil Traceroute](../assets/image/Tampilan%20Hasil%20Traceroute.png)

Traceroute berhasil menunjukkan jalur pengiriman data dari perangkat menuju server Google. Paket data melewati jaringan lokal, jaringan ISP, hingga jaringan publik sebelum mencapai tujuan.
Adanya beberapa “Request timed out” merupakan kondisi normal yang disebabkan oleh pembatasan jaringan, dan tidak mempengaruhi koneksi secara keseluruhan.

- Paket data tidak langsung menuju server tujuan, melainkan melewati beberapa router (hop).
- IP seperti 10.x.x.x dan 172.x.x.x menunjukkan jaringan internal ISP (Telkomsel).
- IP publik seperti 142.x.x.x dan 209.x.x.x menunjukkan jaringan eksternal (Google).
- Adanya “Request timed out” disebabkan oleh router yang tidak merespons ICMP.
- Meskipun terdapat timeout, koneksi tetap berjalan dengan baik karena paket tetap sampai ke tujuan.

## 3. Apa itu ICMP, MTU, TTL?
**1. ICMP (Internet Control Message Protocol)**
ICMP adalah protokol jaringan yang digunakan untuk mengirimkan pesan kontrol dan informasi kesalahan dalam proses komunikasi data. ICMP tidak digunakan untuk mengirim data utama, tetapi untuk membantu proses diagnosis jaringan.

**Fungsi ICMP:**
- Menguji koneksi jaringan (menggunakan perintah ping)
- Memberikan pesan error (misalnya destination unreachable)
- Membantu proses traceroute

**Contoh penggunaan:**
```bash
ping google.com
```
**2. MTU (Maximum Transmission Unit)**
MTU adalah ukuran maksimum paket data (dalam byte) yang dapat dikirim dalam satu kali transmisi melalui jaringan. Jika ukuran data melebihi MTU, maka paket akan dipecah menjadi beberapa bagian (fragmentasi).

**Fungsi MTU:**
- Menentukan batas ukuran paket data
- Mencegah terjadinya kegagalan pengiriman data
- Mempengaruhi performa jaringan

**Contoh:**
- MTU umum Ethernet = 1500 byte

**3. TTL (Time To Live)**
TTL adalah nilai yang menunjukkan batas jumlah hop (lompatan router) yang dapat dilalui oleh sebuah paket sebelum paket tersebut dibuang.
Setiap kali paket melewati satu router, nilai TTL akan berkurang 1. Jika TTL mencapai 0, maka paket akan dihentikan untuk mencegah looping di jaringan.

**Fungsi TTL:**
- Mencegah paket berputar tanpa batas
- Membantu proses traceroute
- Mengontrol umur paket dalam jaringan

**Contoh:**
- TTL awal biasanya 64, 128, atau 255

**Langkah Pengerjaan:**
- Buka Command Prompt (CMD)
- Jalankan:
```bash
ping 8.8.8.8 -l 2000
```
- Filter ke wireshark
```bash
icmp
```
![Tampilan Hasil ICMP,MTU,TTL](../assets/image/tampilan%20hasil%20icmp%20mtu%20ttl.png)

Berdasarkan hasil Wireshark, terlihat paket ICMP (ping) dari 192.168.1.14 ke 8.8.8.8 mengalami fragmentasi, yang ditandai dengan adanya “Fragmented IP protocol” dan “Reassembled”. Hal ini terjadi karena ukuran paket (1514 bytes) melebihi batas MTU (1500 bytes), sehingga paket dipecah menjadi beberapa bagian.
Fragmen tersebut berhasil dikirim dan disusun kembali di sisi penerima. Terdapat juga keterangan “No response found”, yang menunjukkan tidak adanya balasan dari tujuan, kemungkinan karena pembatasan jaringan.

## 4. Cari contoh Fragmentasi di Wireshark kalian
Fragmentasi IP adalah proses pemecahan paket data menjadi beberapa bagian (fragmen) ketika ukuran paket melebihi batas maksimum yang diizinkan oleh jaringan, yaitu MTU (Maximum Transmission Unit). Proses ini bertujuan agar paket tetap dapat dikirim melalui jaringan dengan kapasitas terbatas. Setiap fragmen akan dikirim secara terpisah dan kemudian disusun kembali (reassembly) di sisi penerima.

**Langkah-langkah Percobaan:**
- Membuka aplikasi Wireshark
- Memilih interface jaringan yang aktif
- Memulai proses capture paket
- Membuka Command Prompt (CMD)
- Menjalankan perintah:
```bash
ping 8.8.8.8 -l 2000
```
- Kembali ke Wireshark
- Menggunakan filter:
```bash
ip.flags.mf == 1 || ip.frag_offset > 0
```
![Tampilan hasil contoh fragmentasi di wireshark](../assets/image/tampilan%20hasil%20fragmentasi%20di%20wireshark.png)

Berdasarkan hasil Wireshark dengan filter ip.flags.mf == 1 || ip.frag_offset > 0, terlihat paket dari 10.218.9.14 ke 8.8.8.8 mengalami fragmentasi. Hal ini ditandai dengan adanya keterangan “Fragmented IP protocol” serta “Reassembled in #...”.
Ukuran paket sebesar 1514 bytes menunjukkan bahwa paket melebihi batas MTU (1500 bytes), sehingga dipecah menjadi beberapa fragmen. Fragmen tersebut memiliki ID yang sama dan dikirim secara terpisah, kemudian berhasil disusun kembali (reassembly).
Selain itu, terdapat paket ICMP Echo Request dengan ukuran 562 bytes dan TTL = 128, yang menunjukkan proses ping. Meskipun terdapat keterangan “no response found”, proses fragmentasi tetap berhasil terjadi

## 5. Carilah IPV6 di Wireshark yang kalian lakukan
IPv6 adalah protokol jaringan yang digunakan untuk mengidentifikasi perangkat di internet dengan kapasitas alamat yang lebih besar dibanding IPv4. Pada hasil analisis di Wireshark, paket IPv6 menunjukkan komunikasi antara client dan server menggunakan protokol TCP dan SSL/TLS (HTTPS). Adanya keterangan “TCP Retransmission” menandakan terjadi pengiriman ulang paket akibat gangguan jaringan, namun komunikasi tetap berjalan.

**Langkah-langkah Percobaan:**
- Membuka aplikasi Wireshark
- Memilih menu File → Open
- Membuka file dari asisten praktikum bernama ipv6_sample.pcap
- Setelah file terbuka, masukkan filter:
```bash
ipv6
```
- Menekan Enter untuk menampilkan paket IPv6
- Mengamati detail paket seperti alamat source, destination, dan protokol
- Menganalisis hasil yang ditampilkan di Wireshark
![Tampilan hasil IPV6 di Wireshark](../assets/image/Tampilan%20hasil%20IPV6%20di%20Wireshark.png)

Berdasarkan hasil Wireshark dengan filter ipv6, terlihat bahwa terjadi komunikasi jaringan menggunakan protokol IPv6 dari alamat 2001:db8:1::10 menuju 2a00:1450:4009:80b::200e. Hal ini menunjukkan bahwa perangkat melakukan koneksi ke server eksternal (kemungkinan besar server Google) menggunakan jaringan IPv6.

Pada kolom protokol, terlihat paket menggunakan TCP dan SSL/TLS, yang menandakan bahwa komunikasi berlangsung melalui koneksi HTTPS (port 443). Hal ini diperkuat dengan adanya tujuan port 443, yang merupakan port standar untuk komunikasi aman.

Selain itu, terdapat banyak keterangan “TCP Retransmission”, yang menunjukkan bahwa beberapa paket dikirim ulang. Hal ini biasanya terjadi karena adanya gangguan jaringan seperti packet loss, delay, atau koneksi yang tidak stabil, sehingga paket sebelumnya tidak diterima dengan baik oleh tujuan.

Ukuran paket yang bervariasi (sekitar 900–1400 bytes) menunjukkan adanya proses pertukaran data yang cukup aktif antara client dan server. Di bagian detail juga terlihat bahwa data berada pada layer Transport Layer Security, yang berarti isi data telah dienkripsi dan tidak dapat dibaca secara langsung.

Secara keseluruhan, hasil capture menunjukkan bahwa jaringan berhasil menggunakan IPv6 untuk komunikasi internet, menggunakan protokol aman (HTTPS), namun terdapat indikasi ketidakstabilan jaringan yang ditandai dengan banyaknya retransmission.
