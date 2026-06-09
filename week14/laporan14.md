# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 14

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 14 (802.11 WiFi)

---

## Tujuan Praktikum
1. Memahami konsep dasar jaringan nirkabel (WiFi) berdasarkan standar IEEE 802.11.
2. Menggunakan Wireshark untuk menganalisis paket komunikasi pada jaringan WiFi.
3. Mengamati proses Beacon Frame yang dikirim oleh Access Point untuk mengumumkan keberadaan jaringan nirkabel.
4. Menganalisis proses transfer data pada jaringan WiFi menggunakan protokol TCP dan HTTP.
5. Memahami proses Association Request dan Association Response antara klien dan Access Point.
6. Mengetahui mekanisme koneksi perangkat ke jaringan WiFi melalui proses asosiasi.
7. Mengidentifikasi parameter penting jaringan WiFi seperti SSID, channel, data rate, dan kekuatan sinyal.
8. Mengamati proses Disassociation pada jaringan WiFi menggunakan Wireshark.
9. Memahami peran frame manajemen (Management Frame) dalam komunikasi jaringan IEEE 802.11.
10. Menganalisis komunikasi jaringan nirkabel berdasarkan hasil capture paket pada file Wireshark_802_11.pcap.

---

## Dasar Teori
1. IEEE 802.11 (WiFi)

IEEE 802.11 merupakan standar jaringan nirkabel (Wireless Local Area Network/WLAN) yang dikembangkan oleh Institute of Electrical and Electronics Engineers (IEEE). Standar ini mengatur komunikasi data pada jaringan WiFi, baik pada lapisan fisik (Physical Layer) maupun lapisan MAC (Media Access Control).

Teknologi WiFi memungkinkan perangkat untuk saling bertukar data tanpa menggunakan kabel dengan memanfaatkan gelombang radio sebagai media transmisinya. Saat ini standar IEEE 802.11 telah berkembang menjadi beberapa versi seperti 802.11a, 802.11b, 802.11g, 802.11n, 802.11ac, dan 802.11ax yang menawarkan kecepatan dan jangkauan berbeda.

---

2. Access Point (AP)

Access Point merupakan perangkat jaringan yang berfungsi sebagai pusat komunikasi pada jaringan WiFi. Access Point bertugas menghubungkan perangkat nirkabel dengan jaringan lokal maupun internet.

Selain menyediakan akses jaringan, Access Point juga bertanggung jawab mengirimkan informasi jaringan kepada perangkat di sekitarnya melalui Beacon Frame sehingga perangkat dapat menemukan dan terhubung ke jaringan WiFi yang tersedia.

---

3. Beacon Frame

Beacon Frame adalah salah satu jenis Management Frame pada jaringan IEEE 802.11 yang dikirim secara berkala oleh Access Point.

Beacon Frame berfungsi untuk mengumumkan keberadaan jaringan WiFi kepada perangkat klien. Informasi yang dibawa oleh Beacon Frame antara lain:

- SSID (Service Set Identifier)
- Channel WiFi
- Data Rate yang didukung
- Informasi keamanan jaringan
- Interval Beacon

Dengan adanya Beacon Frame, perangkat klien dapat mengetahui jaringan WiFi yang tersedia dan memilih jaringan yang ingin digunakan.

---

4. Data Transfer pada Jaringan WiFi

Setelah perangkat berhasil terhubung ke Access Point, proses pertukaran data dapat dilakukan melalui berbagai protokol jaringan seperti TCP/IP dan HTTP.

Sebelum data dikirim, umumnya terjadi proses TCP Three-Way Handshake yang terdiri dari:

1. SYN
2. SYN-ACK
3. ACK

Setelah koneksi TCP berhasil dibentuk, perangkat dapat melakukan pertukaran data, misalnya mengirim permintaan HTTP GET untuk mengambil halaman web atau file dari server.

---

5. Association Request dan Association Response

Association merupakan proses ketika perangkat klien meminta izin untuk bergabung ke sebuah jaringan WiFi.

Proses asosiasi terdiri dari dua frame utama:

a. Association Request

Association Request dikirim oleh klien kepada Access Point sebagai permintaan untuk bergabung ke jaringan.

Frame ini berisi informasi seperti:

- SSID tujuan
- Supported Rates
- Capability Information

b. Association Response

Association Response dikirim oleh Access Point sebagai balasan terhadap permintaan asosiasi.

Frame ini berisi:

- Status koneksi (berhasil atau gagal)
- Association ID (AID)
- Informasi kemampuan jaringan

Jika status yang diterima adalah Successful, maka perangkat klien berhasil terhubung ke jaringan WiFi.

---

6. Disassociation

Disassociation merupakan proses pemutusan hubungan antara perangkat klien dan Access Point.

Proses ini dapat terjadi karena:

- Klien berpindah ke Access Point lain (roaming)
- Sinyal melemah atau hilang
- Access Point memutus koneksi
- Pengguna memutuskan sambungan jaringan

Setelah proses Disassociation terjadi, perangkat harus melakukan proses Association kembali apabila ingin terhubung ke jaringan tersebut.

---

7. Wireshark

Wireshark adalah perangkat lunak network protocol analyzer yang digunakan untuk menangkap (capture), memfilter, dan menganalisis paket jaringan secara detail.

Pada praktikum ini Wireshark digunakan untuk:

- Mengamati Beacon Frame
- Menganalisis proses transfer data
-Mengamati Association Request dan Association Response
- Mengidentifikasi Disassociation
- Mempelajari komunikasi jaringan WiFi berdasarkan standar IEEE 802.11

Dengan Wireshark, setiap paket yang dikirim dan diterima pada jaringan dapat diamati secara rinci sehingga memudahkan proses analisis jaringan.

## Langkah Praktikum

1. Menyiapkan File Capture

- Mengunduh file praktikum dari alamat:

http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip

- Mengekstrak file ZIP yang telah diunduh.

- Membuka file Wireshark_802_11.pcap menggunakan aplikasi Wireshark.

Gambar 1. File Wireshark_802_11 yang digunakan

![tampilan File Wireshark_802_11 yang digunakan](../assets/image/tampilan%20File%20Wireshark_802_11%20yang%20digunakan.png)

---

2. Membuka File Capture di Wireshark

Setelah file berhasil diekstrak, file Wireshark_802_11.pcap dibuka menggunakan Wireshark untuk dianalisis.

Gambar 2. File Wireshark_802_11.pcap berhasil dibuka di Wireshark

![Tampilan Membuka File Capture di Wireshark](../assets/image/Tampilan%20Membuka%20File%20Capture%20di%20Wireshark.png)

---

3. Menganalisis Beacon Frame

Untuk menampilkan Beacon Frame digunakan filter:

wlan.fc.subtype == 8 && wlan.fc.type == 0

Filter tersebut digunakan untuk menampilkan frame manajemen (Management Frame) dengan subtype Beacon yang dikirim secara berkala oleh Access Point.

Gambar 3. Hasil Filter Beacon Frame

![Hasil Filter Beacon Frame](../assets/image/Hasil%20Filter%20Beacon%20Frame.png)

Filter tersebut digunakan untuk menampilkan paket Beacon Frame yang dikirim secara periodik oleh Access Point. Beacon Frame merupakan salah satu Management Frame pada standar IEEE 802.11 yang berfungsi untuk mengumumkan keberadaan jaringan WiFi kepada perangkat di sekitarnya.

Berdasarkan hasil capture, terlihat sejumlah paket Beacon Frame yang dikirim secara berulang oleh Access Point. Paket-paket tersebut digunakan untuk menyebarkan informasi jaringan sehingga perangkat klien dapat mendeteksi dan mengetahui parameter jaringan yang tersedia.

---

4. Melihat Detail Beacon Frame

Salah satu Beacon Frame dipilih untuk melihat informasi yang terdapat di dalamnya seperti SSID, Channel, Data Rate, dan parameter jaringan lainnya.

Gambar 4. Detail Beacon Frame

![Detail Beacon Frame](../assets/image/Detail%20Beacon%20Frame.png)

Berdasarkan hasil analisis salah satu Beacon Frame diperoleh informasi sebagai berikut:

|Parameter     | Nilai        |
|--------------|--------------|
|SSID          | 30 Munroe St |
|Channel       | 6            |
|Frequency     | 2437 MHz     |
|Data Rate     | 1.0 Mb/s     |
|Antenna Signal| -32 dBm      |
|Antenna Noise | -100 dBm     |

Selain itu, pada bagian Tagged Parameters diperoleh informasi:

Supported Rates

- 1 Mbps
- 2 Mbps
- 5.5 Mbps
- 11 Mbps

Extended Supported Rates

- 6 Mbps
- 9 Mbps
- 12 Mbps
- 18 Mbps
- 24 Mbps
- 36 Mbps
- 48 Mbps
- 54 Mbps

Analisis

SSID yang terdeteksi adalah "30 Munroe St", yang merupakan identitas jaringan WiFi yang dipancarkan oleh Access Point.

Jaringan beroperasi pada Channel 6 dengan frekuensi 2437 MHz yang berada pada pita frekuensi 2.4 GHz. Nilai Antenna Signal sebesar -32 dBm menunjukkan bahwa kualitas sinyal yang diterima sangat baik, sedangkan nilai Antenna Noise sebesar -100 dBm menunjukkan tingkat gangguan yang sangat rendah.

Supported Rates dan Extended Supported Rates menunjukkan berbagai kecepatan transfer data yang didukung oleh Access Point, mulai dari 1 Mbps hingga 54 Mbps.

Berdasarkan informasi tersebut dapat disimpulkan bahwa Beacon Frame berfungsi sebagai media penyebaran informasi jaringan WiFi kepada perangkat klien sehingga perangkat dapat menemukan dan melakukan koneksi ke jaringan yang tersedia.

---

5. Menganalisis Data Transfer

Untuk mengamati proses transfer data antara host dan server digunakan filter:

ip.addr == 128.119.245.12

Filter tersebut menampilkan seluruh komunikasi yang melibatkan server dengan alamat IP 128.119.245.12.

Gambar 5. Hasil Filter Data Transfer

![Tampilan Hasil Filter Data Transfer](../assets/image/Tampilan%20Hasil%20Filter%20Data%20Transfer.png)

Filter tersebut digunakan untuk menampilkan seluruh paket komunikasi yang melibatkan server dengan alamat IP 128.119.245.12.

Berdasarkan hasil capture, terlihat proses komunikasi antara host dengan alamat IP 192.168.1.109 dan server dengan alamat IP 128.119.245.12.

Sebelum proses transfer data berlangsung, terjadi proses TCP Three-Way Handshake yang terdiri dari:

Frame 474 – SYN

Host 192.168.1.109 mengirimkan paket SYN kepada server 128.119.245.12 sebagai permintaan untuk membangun koneksi TCP.

Frame 476 – SYN, ACK

Server 128.119.245.12 membalas dengan paket SYN-ACK sebagai tanda bahwa permintaan koneksi telah diterima.

Frame 478 – ACK

Host mengirimkan paket ACK sebagai konfirmasi sehingga koneksi TCP berhasil terbentuk.

Setelah proses Three-Way Handshake selesai, host mengirimkan permintaan HTTP berupa:

GET /wireshark-labs/alice.txt HTTP/1.1

Permintaan tersebut bertujuan untuk mengambil file alice.txt dari server.

Analisis

Hasil pengamatan menunjukkan bahwa komunikasi data pada jaringan WiFi tetap menggunakan protokol TCP/IP sebagaimana jaringan kabel. Sebelum data ditransmisikan, koneksi TCP harus dibentuk terlebih dahulu melalui proses Three-Way Handshake.

Setelah koneksi berhasil dibentuk, komunikasi HTTP dapat berlangsung dan host dapat mengakses sumber daya yang tersedia pada server tujuan.

---

6. Mengamati Informasi Beacon Frame

Pada tahap ini dilakukan pengamatan lebih lanjut terhadap Beacon Frame yang berisi informasi mengenai jaringan WiFi yang dipancarkan oleh Access Point.

Gambar 6. Analisis Beacon Frame

![Tampilan Analisis Beacon Frame](../assets/image/Tampilan%20Analisis%20Beacon%20Frame.png)

Hasil pengamatan menunjukkan bahwa Access Point secara berkala mengirimkan Beacon Frame untuk mengumumkan keberadaan jaringan nirkabel.

Beacon Frame membawa berbagai informasi penting seperti SSID, channel, frekuensi operasi, kecepatan transfer data yang didukung, serta parameter jaringan lainnya. Informasi tersebut digunakan oleh perangkat klien untuk melakukan proses pemindaian jaringan sebelum melakukan koneksi.

Dengan adanya Beacon Frame, perangkat dapat mengetahui karakteristik jaringan WiFi yang tersedia dan memilih Access Point yang sesuai untuk digunakan.

---

7. Menganalisis Association Request

Untuk melihat paket Association Request digunakan filter:

wlan.fc.type_subtype == 0

Filter tersebut menampilkan paket permintaan asosiasi yang dikirim oleh klien kepada Access Point saat ingin bergabung ke jaringan WiFi.

Gambar 7. Association Request

![Tampilan Association Request](../assets/image/Tampilan%20Association%20Request.png)

Filter tersebut digunakan untuk menampilkan paket Association Request yang dikirim oleh perangkat klien kepada Access Point.

Berdasarkan hasil pengamatan pada Frame 1750, terlihat bahwa klien mengirimkan Association Request menuju Access Point dengan SSID:

linksys_SES_24086

Association Request merupakan tahap awal ketika perangkat klien meminta izin untuk bergabung ke jaringan WiFi.

---

8. Membandingkan Association Request

Masih menggunakan filter:

wlan.fc.type_subtype == 0

Dilakukan pengamatan terhadap beberapa Association Request untuk melihat perubahan SSID yang digunakan klien saat berpindah Access Point.

Gambar 8. Analisis Association Request

![Tampilan Analisis Association Request](../assets/image/Tampilan%20Analisis%20Association%20Request.png)

Masih menggunakan filter:

wlan.fc.type_subtype == 0

Pada Frame 2162 terlihat bahwa klien mengirimkan Association Request menuju Access Point dengan SSID:

30 Munroe St

Jika dibandingkan dengan Frame 1750, terlihat adanya perubahan SSID tujuan.

Analisis

Perubahan SSID dari "linksys_SES_24086" menjadi "30 Munroe St" menunjukkan bahwa perangkat klien berpindah koneksi dari satu Access Point ke Access Point lainnya.

Peristiwa ini dikenal sebagai roaming, yaitu proses perpindahan koneksi antar Access Point tanpa harus memutus komunikasi jaringan secara keseluruhan.

Klien akan mengirimkan Association Request baru kepada Access Point yang dipilih sebelum dapat menggunakan jaringan tersebut.

---

9. Menganalisis Association Response

Untuk melihat balasan dari Access Point digunakan filter:

wlan.fc.type_subtype == 1

Filter ini menampilkan paket Association Response yang berisi status penerimaan atau penolakan permintaan koneksi dari klien.

Gambar 9. Association Response

![Tampilan Association Response](../assets/image/Tampilan%20Association%20Response.png)

Filter tersebut digunakan untuk menampilkan paket Association Response yang dikirim oleh Access Point sebagai balasan terhadap Association Request.

Berdasarkan hasil pengamatan pada Frame 2166 diperoleh informasi:

|Parameter   | Nilai      |        |
|------------|------------|--------|
|tatus Code  | Successful |(0x0000)|
|Association | ID         | 0x0005 |

Analisis

Status Code bernilai Successful menunjukkan bahwa Access Point menerima dan menyetujui permintaan asosiasi yang dikirim oleh klien.

Association Response merupakan tahap penting dalam proses koneksi WiFi karena menandakan bahwa perangkat telah memperoleh izin untuk bergabung ke jaringan yang dipilih.

Dengan diterimanya Association Response, perangkat klien dapat melanjutkan komunikasi data melalui jaringan WiFi tersebut.

---

10. Menganalisis Disassociation

Untuk mengamati proses pemutusan hubungan antara klien dan Access Point digunakan filter:

wlan.fc.subtype == 10 && wlan.fc.type == 0

Filter tersebut menampilkan frame Disassociation yang menunjukkan berakhirnya hubungan komunikasi antara perangkat klien dan Access Point.

Gambar 10. Disassociation

![Tampilan Disassociation](../assets/image/Tampilan%20Disassociation.png)

Filter tersebut digunakan untuk menampilkan paket Disassociation yang berfungsi untuk mengakhiri hubungan antara perangkat klien dan Access Point.

Berdasarkan hasil filter yang dilakukan, tidak ditemukan paket Disassociation pada file capture yang digunakan.

Analisis

Tidak ditemukannya paket Disassociation menunjukkan bahwa selama proses capture berlangsung tidak terjadi pemutusan hubungan antara perangkat klien dan Access Point.

Dengan demikian, komunikasi jaringan tetap berlangsung tanpa adanya proses penghentian koneksi yang tercatat pada file capture.

---

## Kesimpulan
Berdasarkan hasil praktikum dan analisis paket jaringan WiFi menggunakan Wireshark, dapat disimpulkan bahwa:

1. IEEE 802.11 merupakan standar jaringan nirkabel (WiFi) yang mengatur komunikasi data antara perangkat klien dan Access Point melalui media gelombang radio.

2. Beacon Frame berfungsi untuk mengumumkan keberadaan jaringan WiFi kepada perangkat di sekitarnya dengan menyebarkan informasi seperti SSID, channel, frekuensi, dan data rate yang didukung.

3. Hasil analisis Beacon Frame menunjukkan bahwa Access Point dengan SSID "30 Munroe St" beroperasi pada Channel 6 dengan frekuensi 2437 MHz pada pita frekuensi 2.4 GHz.

4. Proses transfer data pada jaringan WiFi tetap menggunakan protokol TCP/IP. Sebelum data dikirim, terjadi proses TCP Three-Way Handshake yang terdiri dari SYN, SYN-ACK, dan ACK untuk membentuk koneksi yang andal.

5. Association Request merupakan proses ketika perangkat klien meminta izin untuk bergabung dengan Access Point, sedangkan Association Response merupakan balasan dari Access Point yang menunjukkan apakah permintaan tersebut diterima atau ditolak.

6. Hasil pengamatan menunjukkan adanya perpindahan asosiasi dari SSID "linksys_SES_24086" menuju SSID "30 Munroe St", yang menunjukkan proses roaming antar Access Point.

7. Association Response yang diperoleh memiliki status Successful (0x0000), yang menandakan bahwa permintaan koneksi dari klien berhasil diterima oleh Access Point.

8. Berdasarkan hasil filter Disassociation, tidak ditemukan paket Disassociation pada file capture yang digunakan, sehingga tidak terdapat proses pemutusan koneksi selama periode pengamatan.

9. Wireshark dapat digunakan sebagai alat analisis jaringan yang efektif untuk mengamati berbagai jenis frame pada jaringan WiFi, seperti Beacon Frame, Association Request, Association Response, dan proses transfer data secara detail.