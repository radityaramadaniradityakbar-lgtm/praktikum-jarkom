# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 3

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 3 (HTTP)

## Tujuan Praktikum
1. Memahami konsep dasar protokol HTTP dalam komunikasi jaringan.
2. Menganalisis proses HTTP GET dan response antara client dan server.
3. Memahami mekanisme Conditional GET dan caching pada HTTP.
4. Menganalisis pengiriman data berukuran besar menggunakan segmentasi pada TCP.
5. Mengidentifikasi proses pengambilan objek tambahan (embedded objects) dalam halaman web.
6. Memahami mekanisme autentikasi pada HTTP (HTTP Authentication).
7. Menggunakan Wireshark untuk menangkap dan menganalisis paket jaringan.

3.1 Basic HTTP GET / Response
1. Membuka aplikasi Wireshark dan memilih interface jaringan (Wi-Fi).
2. Mengisi display filter dengan http.
3. Memulai proses capture.
4. Membuka browser dan mengakses: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file1.html
5. Menghentikan capture setelah halaman termuat.

# Lampiran:
Tampilan awal capture di tools WiFi (Wireshark) ![Tampilan awal capture di tools WiFi](../assets/image/Tampilan%20awal%20capture%20di%20tools%20WiFi%20(Wireshark).png)
Tampilan berhasil mengakses UMass Edu di Chrome ![Tampilan berhasil Umass Edu di Chrome](../assets/image/Tampilan%20berhasil%20mengakses%20UMass%20Edu%20di%20Chrome.png)
Tampilan hasil capture HTTP di tools WiFi (Wireshark) ![Tampilan hasil browser di tools WiFi](../assets/image/Tampilan%20hasil%20capture%20HTTP%20di%20tools%20WiFi%20(Wireshark).png)

3.2 HTTP Conditional GET
1. Membersihkan cache browser.
2. Menjalankan Wireshark kembali.
3. MengakTampilan berhasil mengakses UMass Edu di Chromeses: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file2.html
4. Melakukan refresh halaman.
5. Menghentikan capture dan tetap menggunakan filter http.

# Lampiran:
Tampilan berhasil membuka file kedua di Chrome ![Tampilan berhasil membuka file kedua di Chrome](../assets/image/Tampilan%20berhasil%20membuka%20file%20kedua%20di%20Chrome.png)
Tampilan hasil capture HTTP di Wireshark (file kedua) ![Tampilan hasil capture HTTP di Wireshark (file kedua)](../assets/image/Tampilan%20hasil%20capture%20HTTP%20di%20Wireshark%20(file%20kedua).png)

3.3 Retrieving Long Documents
1. Membersihkan cache browser.
2. Menjalankan Wireshark.
3. Mengakses: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file3.html
4. Melakukan Refresh Halaman Ulang.
5. Menghentikan capture.

# Lampiran:
Tampilan berhasil membuka file ketiga di Chrome ![Tampilan berhasil membuka file ketiga di Chrome](../assets/image/Tampilan%20berhasil%20membuka%20file%20ketiga%20di%20Chrome.png)
Tampilan hasil capture HTTP di Wireshark (file ketiga) ![Tampilan hasil capture HTTP di Wireshark (file ketiga)](../assets/image/Tampilan%20hasil%20capture%20HTTP%20di%20Wireshark%20(file%20ketiga).png)

3.4 HTML dengan Embedded Objects
1. Menjalankan aplikasi Wireshark.
2. Memulai proses capture pada interface Wi-Fi.
3. Menggunakan filter http.
4. Membuka browser dan mengakses: http://gaia.cs.umass.edu/wireshark-labs/HTTP-wireshark-file4.html
5. Menghentikan capture setelah halaman termuat.

# Lampiran:
Tampilan berhasil membuka halaman file4 di Chrome ![Tampilan berhasil membuka halaman file4 di Chrome](../assets/image/Tampilan%20berhasil%20membuka%20halaman%20file4%20di%20Chrome.png)
Tampilan hasil capture HTTP pada Wireshark (file4) ![Tampilan hasil capture HTTP pada Wireshark (file4)](../assets/image/Tampilan%20hasil%20capture%20HTTP%20pada%20Wireshark%20(file4).png)

3.5  HTTP Authentication
1. Membersihkan cache browser.
2. Menjalankan Wireshark.
3. Mengakses: http://gaia.cs.umass.edu/wireshark-labs/protected_pages/HTTP-wireshark-file5.html
4. Memasukkan:
Username: wireshark-students
Password: network
5. Menghentikan capture.

# Lampiran:
Tampilan berhasil membuka halaman file5 (protected page) di Chrome ![Tampilan berhasil membuka halaman file5 di Chrome](../assets/image/Tampilan%20berhasil%20membuka%20halaman%20file5%20(protected%20page)%20di%20Chrome.png)
Tampilan hasil capture HTTP pada Wireshark (file5) ![Tampilan hasil capture HTTP pada Wireshark (file5)](../assets/image/Tampilan%20hasil%20capture%20HTTP%20pada%20Wireshark%20(file5).png)