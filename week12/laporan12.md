# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 12

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 12 (ICMP / Internet Control Message Protocol)

## Tujuan Praktikum
1. Memahami konsep dasar Internet Control Message Protocol (ICMP) sebagai protokol yang digunakan untuk proses pengendalian dan diagnosis pada jaringan komputer.
2. Menjelaskan hubungan antara protokol ICMP dan protokol IP dalam proses komunikasi serta pengiriman paket data pada jaringan.
3. Mengetahui fungsi dan cara kerja program Ping dalam melakukan pengujian konektivitas antara host sumber dan host tujuan menggunakan pesan ICMP.
4. Mengidentifikasi dan menganalisis jenis pesan ICMP yang dihasilkan oleh program Ping, khususnya Echo Request dan Echo Reply.
5. Memahami fungsi program Traceroute (Tracert) untuk menelusuri jalur (route/hop) yang dilalui paket dari perangkat pengirim menuju perangkat tujuan.
6. Mengidentifikasi dan menganalisis pesan ICMP yang dihasilkan oleh Traceroute, terutama pesan Time Exceeded (TTL Exceeded).
7. Menggunakan aplikasi Wireshark untuk melakukan proses capture, filter, dan analisis paket ICMP yang berjalan pada jaringan.
8. Memahami struktur serta format paket ICMP yang terdiri dari Type, Code, Checksum, Identifier, Sequence Number, dan Payload.
9. Mampu membaca informasi hasil capture paket untuk mengetahui kondisi komunikasi dan kemungkinan terjadinya gangguan jaringan.
10. Menganalisis hasil pengamatan praktikum dan menyusun laporan berdasarkan data paket ICMP yang diperoleh.

## Dasar Teori
**1. Pengertian ICMP**

Internet Control Message Protocol (ICMP) merupakan protokol komunikasi yang berada pada lapisan jaringan (Network Layer) dan digunakan untuk mendukung proses pengelolaan serta pemantauan komunikasi data pada jaringan berbasis Internet Protocol (IP). ICMP menjadi bagian penting dalam sistem jaringan karena berfungsi sebagai media pertukaran informasi terkait kondisi pengiriman paket.

Berbeda dengan protokol yang digunakan untuk membawa data utama pengguna seperti TCP atau UDP, ICMP tidak digunakan untuk mengirim isi komunikasi, melainkan untuk memberikan informasi mengenai status koneksi, proses diagnostik jaringan, dan pelaporan kesalahan (error reporting) selama proses pengiriman paket berlangsung.

ICMP bekerja dengan cara mengirimkan pesan tertentu antar perangkat jaringan ketika terjadi kondisi tertentu, misalnya paket tidak dapat mencapai tujuan, waktu pengiriman habis (Time To Live/TTL exceeded), atau ketika perangkat ingin mengecek apakah host tujuan masih aktif dan dapat dijangkau.

Dalam implementasinya, ICMP dikirim di dalam payload paket IP, sehingga protokol ini memiliki hubungan yang erat dengan IP. Ketika suatu perangkat mengirim paket melalui jaringan, ICMP dapat memberikan respon yang membantu pengguna atau administrator memahami kondisi komunikasi yang sedang terjadi.

ICMP banyak digunakan dalam aktivitas administrasi jaringan karena mampu memberikan informasi mengenai:

- Ketersediaan perangkat pada jaringan.
- Kualitas dan kondisi koneksi.
- Jalur yang dilewati paket.
- Deteksi gangguan atau kegagalan komunikasi.
- Evaluasi performa jaringan.

**2. Fungsi ICMP**

ICMP memiliki beberapa fungsi utama dalam jaringan komputer, yaitu:

**a. Melakukan diagnosis jaringan**

Digunakan untuk mengetahui apakah suatu perangkat atau host dapat diakses melalui jaringan.

**b. Memberikan informasi kesalahan (Error Reporting)**

ICMP mengirim pemberitahuan apabila terjadi kegagalan pengiriman paket, misalnya tujuan tidak dapat dijangkau (Destination Unreachable).

**c. Menguji konektivitas jaringan**

Membantu memastikan komunikasi antar perangkat berjalan dengan baik.

**d. Menentukan jalur pengiriman paket**

Digunakan untuk mengetahui router atau hop yang dilewati paket sebelum mencapai tujuan.

**e. Membantu proses pemantauan jaringan**

Administrator dapat menggunakan ICMP untuk mengevaluasi performa serta mendeteksi gangguan komunikasi.

**f. Menampilkan kondisi respon jaringan**

ICMP dapat memberikan informasi waktu respon atau keterlambatan komunikasi (delay/latency).

**3. Contoh Penggunaan ICMP**

**A. Ping**

Ping digunakan untuk menguji apakah host tujuan aktif dan dapat dijangkau.

Contoh perintah:
```bash
ping www.google.com
```

Cara kerja:

- Komputer mengirim ICMP Echo Request (Type 8).
- Server tujuan membalas ICMP Echo Reply (Type 0).
- Hasil pengujian menampilkan informasi waktu respon dan status koneksi.

Contoh penggunaan:

- Mengecek apakah internet tersambung.
- Menguji koneksi ke server.
- Mengetahui keterlambatan jaringan.

**B. Traceroute / Tracert**

Traceroute digunakan untuk mengetahui jalur atau hop yang dilewati paket menuju tujuan.

Contoh perintah:

Windows:
```bash
tracert www.google.com
```

Linux:
```bash
traceroute www.google.com
```

Cara kerja:

- Paket dikirim dengan nilai TTL tertentu.
- Router yang menerima paket akan mengurangi nilai TTL.
- Ketika TTL habis, router mengirim ICMP Time Exceeded (Type 11).
- Hasil akhir menunjukkan jalur yang dilalui paket.

Contoh penggunaan:

- Mengetahui lokasi gangguan jaringan.
- Melihat jumlah hop menuju server.
- Menganalisis rute komunikasi data.

## 1. Pesan ICMP yang dihasilkan oleh program Ping!
**Langkah Praktikum:**

1. Membuka aplikasi Wireshark.
2. Memilih interface jaringan yang aktif kemudian memulai proses capture paket.
3. Membuka Command Prompt.
4. Menjalankan perintah berikut:
```bash
ping -n 10 www.ust.hk
```

![Tampilan Command Prompt ping](../assets/image/tampilan%20CMD%20ping%20-n10.png)

5. Menunggu hingga proses pengiriman paket selesai.
6. Menghentikan proses capture pada Wireshark.
7. Melakukan filter:
```bash
icmp
```
8. Mengamati paket ICMP yang dihasilkan.

**Hasil Pengamatan**

![Tampilan Hasil Filter Paket ICMP](../assets/image/Hasil%20Filter%20Paket%20ICMP.png)

Setelah proses capture selesai dan dilakukan filter menggunakan kata kunci icmp, Wireshark menampilkan paket yang berkaitan dengan protokol ICMP.

Pada hasil capture adanya pertukaran paket antara alamat sumber 192.168.1.14 dengan alamat tujuan 143.89.209.9. Paket yang muncul terdiri dari Echo (ping) request dan Echo (ping) reply yang menandakan proses komunikasi berhasil dilakukan.

Dari hasil pengamatan juga terlihat:

- Protocol yang digunakan adalah ICMP.
- Panjang paket sebesar 74 bytes.
- Terdapat informasi Source, Destination, TTL, dan Sequence Number.
- Paket ditampilkan berpasangan antara request dan reply.

Hasil filter ini digunakan untuk mempermudah proses analisis paket ICMP yang dihasilkan oleh program Ping.

![Tampilan Analisis Paket ICMP Echo Request](../assets/image/Analisis%20Paket%20ICMP%20Echo%20Request.png)

Pada gambar kedua paket Echo (ping) request yang dikirim dari komputer pengirim menuju server tujuan.

Informasi paket yang diperoleh:

**Parameter**	 | **Nilai**

Source	         | 192.168.1.14
Destination	     | 143.89.209.9
Type	         | 8
Code	         | 0
Identifier	     | 0x0001
Sequence Number	 | 3
TTL	             | 128
Data	         | 32 bytes

**Penjelasan:**

- Source 192.168.1.14 menunjukkan alamat perangkat pengirim.
- Destination 143.89.209.9 menunjukkan alamat server tujuan.
- Type = 8 menunjukkan paket ICMP Echo Request.
- Code = 0 berarti tidak terdapat informasi tambahan.
- Identifier = 0x0001 digunakan sebagai identitas paket.
- Sequence Number = 3 menunjukkan urutan pengiriman paket.
- TTL = 128 menunjukkan batas umur paket selama proses pengiriman.
- Data = 32 bytes merupakan ukuran data yang dikirim.

Paket Echo Request berfungsi untuk melakukan pengujian konektivitas dan meminta respons dari host tujuan.

![Tampilan Analisis Paket ICMP Echo Reply](../assets/image/Analisis%20Paket%20ICMP%20Echo%20Reply.png)

Pada gambar ketiga paket Echo (ping) reply yang dikirim oleh server tujuan sebagai balasan terhadap Echo Request.

Informasi paket yang diperoleh:

**Parameter**	 | **Nilai**

Source	         | 143.89.209.9
Destination	     | 192.168.1.14
Type	         | 0
Code             | 0
Identifier	     | 0x0001
Sequence Number	 | 3
TTL	             | 44
Response Time	 | 105.533 ms
Data	         | 32 bytes

**Penjelasan:**

- Source 143.89.209.9 menunjukkan paket berasal dari server tujuan.
- Destination 192.168.1.14 menunjukkan paket kembali ke perangkat pengirim.
- Type = 0 menunjukkan paket ICMP Echo Reply.
- Code = 0 berarti tidak ada informasi tambahan.
- Identifier tetap sama dengan paket request.
- Sequence Number = 3 menunjukkan balasan untuk paket urutan ke-3.
- TTL = 44 menunjukkan nilai TTL setelah melewati beberapa perangkat jaringan.
- Response Time = 105.533 ms menunjukkan waktu yang dibutuhkan paket untuk menerima balasan.

Paket Echo Reply menandakan bahwa host tujuan berhasil menerima permintaan dan mengirim respons kembali.

**Kesimpulan**

Berdasarkan hasil capture menggunakan Wireshark dan pengujian ping -n 10 www.ust.hk, diperoleh bahwa program Ping menghasilkan dua jenis pesan ICMP yaitu Echo Request (Type 8) dan Echo Reply (Type 0). Paket dikirim dari 192.168.1.14 menuju 143.89.209.9 dan memperoleh balasan dengan waktu respons sekitar 105.533 ms, sehingga dapat disimpulkan bahwa koneksi menuju host tujuan berjalan dengan baik.

## 2. Pesan ICMP yang dihasilkan oleh program Traceroute!
**Langkah Praktikum:**

1. Membuka aplikasi Wireshark.
2. Memilih interface jaringan yang aktif lalu memulai proses capture paket.
3. Membuka Command Prompt.
4. Menjalankan perintah berikut:
```bash
tracert www.ust.hk
```

![Tampilan Command Prompt tracert](../assets/image/Command%20Prompt%20tracert.png)

5. Menunggu hingga proses traceroute selesai.
6. Menghentikan proses capture pada Wireshark.
7. Melakukan filter:
```bash
icmp
```
8. Mengamati paket ICMP yang muncul.

**Hasil Pengamatan**

![Tampilan Hasil Filter Paket ICMP](../assets/image/Tampilan%20Hasil%20Filter%20Paket%20ICMP%20tracert.png)

Setelah proses capture selesai dan dilakukan filter menggunakan kata icmp, Wireshark menampilkan paket ICMP yang terbentuk selama proses Traceroute.

Dari hasil pengamatan terlihat adanya pertukaran paket antara perangkat pengirim 192.168.1.14 menuju 143.89.209.9 serta balasan dari beberapa perangkat jaringan yang dilewati.

Pada kolom informasi terlihat dua jenis pesan ICMP yang dominan yaitu:

- Echo (ping) request
- Time-to-live exceeded

Dan juga adanya perubahan nilai TTL secara bertahap mulai dari TTL = 1, TTL = 2, hingga TTL = 4. Hal tersebut menunjukkan bahwa paket sedang melakukan proses penelusuran jalur (route tracing) menuju tujuan.

Paket Time Exceeded muncul karena setiap router yang dilewati akan mengurangi nilai TTL. Ketika TTL mencapai nol maka router mengirim balasan ICMP ke pengirim.

![Tampilan Analisis Paket ICMP Echo Request](../assets/image/Analisis%20Paket%20ICMP%20Echo%20Request%20tracert.png)

Pada gambar kedua paket ICMP Echo Request yang dikirim oleh perangkat sumber menuju server tujuan.

Informasi paket yang diperoleh:

**Parameter**	 | **Nilai**

Source	         | 192.168.1.14
Destination  	 |143.89.209.9
Type	         | 8
Code	         | 0
Identifier	     | 0x0001
Sequence Number	 | 13
TTL	             | 1
Data	         | 64 bytes

**Penjelasan:**

- Source = 192.168.1.14 menunjukkan perangkat pengirim.
- Destination = 143.89.209.9 menunjukkan host tujuan.
- Type = 8 menandakan paket Echo Request.
- Code = 0 menunjukkan tidak ada informasi tambahan.
- Identifier = 0x0001 digunakan untuk identifikasi paket.
- Sequence Number = 13 menunjukkan urutan paket.
- TTL = 1 menunjukkan paket hanya diperbolehkan melewati satu hop.
- Data = 64 bytes merupakan data yang dibawa paket.

Pada proses traceroute, Echo Request dikirim berulang dengan nilai TTL yang terus bertambah untuk menemukan jalur menuju tujuan.

![Tampilan Analisis Paket ICMP Time Exceeded](../assets/image/Analisis%20Paket%20ICMP%20Time%20Exceeded.png)

Pada gambar ketiga paket balasan ICMP Time Exceeded yang dikirim oleh router.

Informasi paket yang diperoleh:

**Parameter**	| **Nilai**

Source	        | 192.168.1.1
Destination	    | 192.168.1.14
Type	        | 11
Code	        | 0
Keterangan	    | Time to Live Exceeded in Transit

**Penjelasan:**

- Source = 192.168.1.1 menunjukkan router yang mengirim balasan.
- Destination = 192.168.1.14 menunjukkan paket dikirim kembali ke perangkat asal.
- Type = 11 menunjukkan pesan Time Exceeded.
- Code = 0 menunjukkan TTL habis selama proses pengiriman.
- Router mengirim informasi bahwa paket tidak dapat diteruskan karena batas TTL telah tercapai.

Pada detail paket juga terlihat bahwa paket Echo Request (Type 8) sebelumnya disisipkan pada bagian payload sebagai informasi paket yang menyebabkan error.

Pesan Time Exceeded merupakan mekanisme utama yang digunakan oleh program Traceroute untuk mengetahui perangkat jaringan (router) yang dilewati paket.

**Pembahasan**

Berdasarkan hasil pengamatan menggunakan Traceroute dan Wireshark, terlihat bahwa proses traceroute bekerja dengan mengirim paket ICMP Echo Request menggunakan nilai TTL yang meningkat secara bertahap.

Ketika nilai TTL habis sebelum mencapai tujuan, router mengirimkan ICMP Time Exceeded (Type 11). Dengan cara tersebut, traceroute dapat menampilkan setiap hop atau perangkat jaringan yang dilewati hingga paket mencapai tujuan akhir.

**Kesimpulan**

Berdasarkan praktikum yang dilakukan, program Traceroute menghasilkan dua pesan ICMP utama yaitu Echo Request (Type 8) dan Time Exceeded (Type 11). Echo Request digunakan untuk mengirim paket percobaan, sedangkan Time Exceeded digunakan oleh router untuk memberi tahu bahwa nilai TTL telah habis. Dari hasil capture dapat diketahui jalur komunikasi yang dilewati paket menuju 
```bash
www.ust.hk.
```