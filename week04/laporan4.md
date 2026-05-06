# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 4

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 4 (DNS)

## Tujuan Praktikum
1. Memahami konsep dasar Domain Name System (DNS) dalam jaringan komputer.
2. Mengetahui fungsi DNS dalam menerjemahkan nama domain menjadi alamat IP.
3. Menggunakan perintah nslookup untuk melakukan query DNS terhadap suatu domain.
4. Menganalisis proses DNS request dan DNS response menggunakan aplikasi Wireshark.
5. Mengidentifikasi jenis-jenis query DNS seperti A (Address Record) dan NS (Name Server).
6. Mengetahui penggunaan protokol UDP pada port 53 dalam komunikasi DNS.
7. Menganalisis informasi yang terdapat dalam paket DNS seperti:
   - Source dan destination IP
   - Port
   - Query type
   - Answer record
   - Time To Live (TTL)
8. Memahami proses komunikasi antara client dan server DNS, termasuk penggunaan DNS server lokal dan server eksternal.
9. Menganalisis hubungan antara proses DNS dengan komunikasi selanjutnya seperti TCP SYN dan akses HTTP.
10. Memahami konsep DNS caching serta pengaruhnya terhadap efisiensi akses jaringan.
11. Menggunakan Wireshark sebagai tools untuk capture dan analisis paket jaringan secara real-time.

# Modul 4.2 Nslookup
  Pada modul ini digunakan perintah nslookup (Name Server Lookup) yang tersedia pada sistem operasi Linux/Unix dan Windows. Perintah ini dijalankan melalui terminal atau Command Prompt (CMD).

  Nslookup berfungsi untuk melakukan query ke server DNS (Domain Name System) guna memperoleh informasi suatu domain, seperti alamat IP, name server, dan mail server.

  Dalam prosesnya, nslookup mengirimkan permintaan DNS ke server yang ditentukan, kemudian menerima balasan berupa informasi yang diminta dan menampilkannya kepada pengguna.

## Langkah Percobaan
1. Menjalankan nslookup untuk mengetahui IP domain
   Perintah nslookup digunakan untuk mengetahui alamat IP dari suatu domain. Pada langkah ini dilakukan query terhadap domain www.mit.edu⁠ dengan menggunakan DNS publik agar proses berjalan dengan baik.
   ![tampilan Menjalankan nslookup untuk mengetahui IP domain](../assets/image/Menjalankan%20nslookup%20untuk%20mengetahui%20IP%20domain.png)

2. Menampilkan Name Server (NS)
   Perintah ini digunakan untuk mengetahui server DNS yang bertanggung jawab (otoritatif) terhadap domain mit.edu. Informasi ini penting untuk mengetahui server mana yang menyimpan data DNS domain tersebut.
   ![tampilan Menampilkan Name Server (NS)](../assets/image/Menampilkan%20Name%20Server%20(NS).png)

3. Query domain menggunakan DNS tertentu
   Perintah ini digunakan untuk mencari alamat IP domain www.aiit.or.kr⁠. Pada percobaan ini digunakan DNS publik karena server DNS tertentu (seperti bitsy.mit.edu) tidak dapat diakses dari jaringan yang digunakan.
   ![tampilan Query domain menggunakan DNS tertentu](../assets/image/Query%20domain%20menggunakan%20DNS%20tertentu.png)

## Jawaban Pertanyaan
1. Mencari IP server web di Asia
   Perintah ini digunakan untuk mengetahui alamat IP dari server web yang berada di wilayah Asia, yaitu domain www.u-tokyo.ac.jp⁠
   ![Tampilan Mencari IP server web di Asia](../assets/image/Mencari%20IP%20server%20web%20di%20Asia.png)

2. Mencari DNS otoritatif universitas di Eropa
   Perintah ini digunakan untuk mengetahui server DNS otoritatif dari domain cam.ac.uk yang merupakan universitas di Eropa.
   ![Tampilan Mencari DNS otoritatif universitas di Eropa](../assets/image/Mencari%20DNS%20otoritatif%20universitas%20di%20Eropa.png)

3. Mencari mail server Yahoo
   Perintah ini digunakan untuk mengetahui mail server dari domain yahoo.com menggunakan query tipe MX, kemudian dilanjutkan untuk mengetahui alamat IP dari mail server tersebut.
   ![Tampilan Mencari mail server Yahoo](../assets/image/Mencari%20mail%20server%20Yahoo.png)

# Modul 4.3 Ipconfig
  Perintah ipconfig digunakan untuk menampilkan informasi konfigurasi jaringan pada komputer. Dengan ipconfig, kita dapat mengetahui alamat IP, subnet mask, gateway, serta DNS server yang digunakan oleh perangkat.
  Selain itu, ipconfig juga dapat digunakan untuk melihat cache DNS yang tersimpan dan menghapusnya jika diperlukan.

## Langkah Percobaan
1. Menampilkan Informasi IP
   Perintah ini digunakan untuk menampilkan seluruh informasi jaringan pada komputer, termasuk alamat IP dan DNS server yang digunakan.
   ![Tampilan Menampilkan Informasi IP](../assets/image/Menampilkan%20Informasi%20IP.png)

2. Menyimpan Informasi ke File
   Perintah ini digunakan untuk menyimpan hasil konfigurasi jaringan ke dalam file agar dapat dibuka dan dianalisis kembali.
   ![Tampilan Menyimpan Informasi ke File](../assets/image/Menyimpan%20Informasi%20ke%20File.png)

3. Menampilkan Cache DNS
   Perintah ini digunakan untuk menampilkan daftar cache DNS yang tersimpan pada komputer, yaitu domain yang pernah diakses beserta alamat IP-nya.
   ![Tampilan Menampilkan Cache DNS](../assets/image/Menampilkan%20Cache%20DNS.png)

4. Menghapus Cache DNS
   Perintah ini digunakan untuk menghapus seluruh cache DNS sehingga sistem akan melakukan pencarian DNS ulang ke server.
   ![Tampilan Menghapus Cache DNS](../assets/image/Menghapus%20Cache%20DNS.png)

# Modul 4.4 Tracing DNS dengan Wireshark
  Pada percobaan ini, dilakukan analisis paket DNS menggunakan Wireshark. Tujuannya adalah untuk melihat bagaimana proses permintaan (request) dan balasan (response) DNS terjadi ketika mengakses suatu website.
  Wireshark digunakan untuk menangkap paket jaringan secara langsung, sehingga kita dapat mengetahui protokol yang digunakan, alamat IP, port, serta isi dari pesan DNS.

# A

## Langkah Percobaan
1. Persiapan Awal
   Perintah ini digunakan untuk menghapus cache DNS agar proses request benar-benar dilakukan ke server DNS.
   ![Tampilan Persiapan Awal](../assets/image/cek%20ip%20address%20dan%20membersihkan%20cache.png)

2. Menjalankan Wireshark
   Filter ini digunakan agar hanya paket dari dan ke host Anda yang ditampilkan.
   ![Tampilan Menjalankan Wireshark](../assets/image/Menjalankan%20Wireshark.png)

3. Membuka Browser http://www.ietf.org/
   ![Tampilan Browser ietf](../assets/image/tampilan%20browser%20ietf.png)

4. Capture Paket DNS
   - Klik Start Capture
   - Buka browser dan akses
   - Tunggu sampai halaman terbuka
   - Stop capture di Wireshark
   ![Tampilan Capture Paket DNS/IETF](../assets/image/Capture%20Paket%20DNS.png)

## Jawaban Pertanyaan
1. Cari pesan permintaan DNS dan balasannya. Apakah pesan tersebut dikirimkan melalui UDP atau TCP?
   ![Tampilan Pertanyaan 1](../assets/image/tampilan%20pertanyaan%201.png)

   - DNS menggunakan protokol UDP.
   - Pada Wireshark terlihat bahwa DNS menggunakan UDP karena lebih cepat (connectionless).

2. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasannya?
   ![Tampilan Pertanyaan 2](../assets/image/tampilan%20pertanyaan%202.png)

   - Port 53 adalah port standar yang digunakan oleh DNS.

# B

## Langkah Percobaan
1. Membuka Command Prompt (cmd), kemudian menjalankan perintah: nslookup www.mit.edu 8.8.8.8
   ![tampilan cmd www.mit.edu](../assets/image/tampilan%20Command%20Prompt%20(cmd)%20mit.edu.png)

   Perintah ini digunakan untuk mencari alamat IP dari domain www.mit.edu⁠ dengan menggunakan server DNS eksternal yaitu Google DNS (8.8.8.8).

2. Lalu Buka Wireshark dan filter dns
   ![tampilan filter dns](../assets/image/tampilan%20dns.png)

   untuk menampilkan paket DNS yang tertangkap.

## Jawaban Pertanyaan
1. Apa port tujuan pada pesan permintaan DNS? Apa port sumber pada pesan balasan DNS?
   ![tampilan request](../assets/image/tampilan%20request.png)

   ![tampilan response](../assets/image/tampilan%20response.png)
   
   - Port tujuan pada pesan permintaan DNS adalah 53, sedangkan port sumber pada pesan balasan DNS juga menggunakan port 53.
   - Port 53 merupakan port standar yang digunakan oleh protokol DNS untuk komunikasi antara client dan server.

2. Ke alamat IP manakah pesan permintaan DNS dikirimkan? Apakah alamat IP tersebut merupakan default alamat IP server DNS lokal Anda?
   ![tampilan mit.edu wireshark](../assets/image/tampilan%20mit.edu.png)

   Pesan permintaan DNS dikirimkan ke alamat IP 8.8.8.8.
   Alamat IP tersebut bukan merupakan DNS lokal, melainkan DNS publik (Google DNS) yang digunakan untuk menggantikan DNS lokal karena sebelumnya terjadi error pada DNS lokal.

3. Periksa pesan permintaan DNS. Apa ”jenis” atau ”type” dari pesan tersebut? Apakah pesan tersebut mengandung ”jawaban” atau ”answers”?
   ![tampilan type dan answer](../assets/image/tampilan%20type%20and%20answer.png)

   Jenis (type) dari pesan permintaan DNS adalah A (Address Record), yaitu untuk mencari alamat IP dari suatu domain.
   Pesan permintaan DNS tidak mengandung jawaban (answers), karena hanya berisi permintaan informasi kepada server DNS.

# C

## Langkah Percobaan
1. Menjalankan perintah nslookup NS
   Perintah ini digunakan untuk mengetahui Name Server (NS) atau server DNS yang bertanggung jawab terhadap domain mit.edu.
   ![tampilan perintah nslookup](../assets/image/cmd%20-type=NS%20mit.edu.png)

2. Melakukan capture menggunakan Wireshark
   Buka aplikasi Wireshark, kemudian:
   Pilih interface jaringan (Wi-Fi)
   Klik Start Capture
   Gunakan filter
   ![tampilan menggunakan wireshark](../assets/image/tampilan%20mit.edu.%20dns.png)

3. Ambil data dari Standard Query
   Standard Query digunakan untuk melihat proses permintaan DNS dari client ke server, serta mengetahui informasi dasar seperti domain yang diminta, jenis query, dan alamat tujuan.

   ![tampilan data dari Standard Query](../assets/image/tampilan%20data%20dari%20Standard%20Query.png)

## Jawaban Pertanyaan
1. Alamat IP Request
   ![tampilan alamat IP Request](../assets/image/alamat%20ip.png)

   Alamat tersebut merupakan server DNS yang digunakan untuk melakukan query, dalam hal ini adalah DNS publik (Google DNS).

2. Type dan Answer Request
   ![tampilan type dan answer request](../assets/image/type%20dan%20answer%20request.png)

   Pesan request tidak mengandung answers (jawaban) karena hanya berisi permintaan informasi mengenai name server dari domain mit.edu.

3. Answer Response
   ![tampilan answer response](../assets/image/answer%20response.png)

   Response ini menunjukkan server DNS otoritatif untuk domain tersebut. Pada umumnya, response hanya menampilkan nama server tanpa langsung menyertakan alamat IP-nya.

# D

## Langkah Percobaan
1. Menjalankan perintah nslookup
   Perintah ini digunakan untuk mencari alamat IP dari domain www.aiit.or.kr⁠
   ![tampilan nslookup](../assets/image/tampilann%20alamat%20ip.png)

2. Melakukan capture menggunakan Wireshark
   Buka aplikasi Wireshark, kemudian:
   Pilih interface jaringan (Wi-Fi)
   Klik Start Capture
   Gunakan filter
   ![tampilan filter dns](../assets/image/tampilan%20filter%20dns%20aiit.png)

3. Ambil data dari Standard Query
   Standard Query digunakan untuk melihat proses permintaan DNS dari client ke server, serta mengetahui informasi dasar seperti domain yang diminta, jenis query, dan alamat tujuan.
   ![tampilan ambil data Standard Query](../assets/image/tampilan%20data%20aiit.png)

## Jawaban Pertanyaan
1. Alamat IP Request
   ![tampilan Alamat IP Request](../assets/image/Alamat%20IP%20Request.png)
   
   - Pesan dikirim ke 8.8.8.8.
   - Alamat tersebut bukan DNS lokal, melainkan DNS publik.

2. Type dan Answer Request
   ![tampilan type dan answer request](../assets/image/Tampilan%20Type%20dan%20answer%20request.png)
   
   - Type: A (Address Record)
   - Request tidak memiliki answers.

3. Answer Response
   ![tampilan answer response](../assets/image/tampilan%20answer%20response%20dns.png)

   Pada percobaan ini, tidak diperoleh jawaban (answers) dari server DNS karena terjadi DNS request timed out.