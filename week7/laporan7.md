# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 7

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 7 (SOCKET PROGRAMMING: MEMBUAT APLIKASI JARINGAN)

## Tujuan Praktikum
- Memahami konsep dasar socket programming dalam jaringan komputer
- Mengetahui cara kerja komunikasi antara client dan server
- Mengimplementasikan program client-server menggunakan bahasa Python
- Memahami penggunaan library socket pada Python
- Mengetahui perbedaan antara protokol TCP dan UDP
- Melatih kemampuan dalam membuat aplikasi jaringan sederhana
- Menguji proses pengiriman dan penerimaan data antar perangkat dalam jaringan

## Langkah Percobaan

# 1. Membuat Folder Project

     - Buka File Explorer
     - Masuk ke folder Documents
     - Buat folder baru dengan nama:
     ![tampilan folder](../assets/image/folder%20praktikum-jarkom.png)
     - Buka folder tersebut di Vs Code

# 2. Membuat File Program

     Di dalam folder, saya menambahkan 4 file
     ![tampilan 4 file](../assets/image/4%20file.png)

# 3. Memasukkan Kode Program

     - a. TCP Server
          ![tampilan kode program TCP Server](../assets/image/Kode%20Program%20TCP%20Server.png)
          - Menerima koneksi dari client
          - Mengubah pesan menjadi huruf besar (UPPERCASE)
          - Mengirim kembali ke client

     - b. TCP Client
          ![tampilan kode program TCP Client](../assets/image/kode%20program%20tcp_client.png)
          - Mengirim pesan ke server
          - Menerima balasan dari server

     - c. UDP Server
          ![tampilan kode program UDP Server](../assets/image/Kode%20program%20UDP%20Server.png)
          - Menerima pesan tanpa koneksi
          - Mengubah pesan menjadi huruf besar
          - Mengirim kembali ke client

     - d. UDP Client
          ![tampilan kode program UDP Client](../assets/image/Kode%20program%20UDP%20Client.png)
          - Mengirim pesan ke server menggunakan IP
          - Menerima balasan dari server

# 4. Mengecek IP Address

     Buka aplikasi Command Prompt (CMD)
     IP saya = "192.168.1.14"
     ![tampilan Command Prompt (CMD)](../assets/image/tampilan%20cmd%20ipconfig.png)

# 5. Hasil Percobaan TCP

     - Server
       Menerima dan memproses pesan
       ![tampilan tcp_server](../assets/image/Kode%20Program%20TCP%20Server.png)

       - Output pada Server
         ![tampilan output pada Server TCP](../assets/image/Output%20pada%20Server.png)

     - Client
       Mengirim dan menerima pesan
       ![tampilan tcp_client](../assets/image/kode%20program%20tcp_client.png)

       - Input dari Client
         ![tampilan Input dari Client](../assets/image/Input%20dari%20Client.png)

       - Output pada Client
         ![tampilan Output dari Client](../assets/image/Output%20dari%20Client.png)

# 6. Hasil Percobaan UDP

     - Server
       Menampilkan pesan dari Client
       ![tampilan udp_server](../assets/image/Kode%20program%20UDP%20Server.png)

       - Output pada Server
         ![tampilan output pada Server UDP](../assets/image/tampilan%20output%20pada%20udp_server.png)

     - Client
       Menampilkan balasan dari Server
       ![tampilan udp_client](../assets/image/Kode%20program%20UDP%20Client.png)

       - Input dari Client
         ![tampilan input dari Client](../assets/image/tampilan%20input%20udp_client.png)

       - Output pada Client
         ![tampilan output dari Client](../assets/image/tampilan%20output%20udp_client.png)

# 7. Hasil Analisis

     - TCP:
       - Menggunakan koneksi (connection-oriented)
       - Lebih stabil dan terjamin

     - UDP:
       - Tidak menggunakan koneksi (connectionless)
       - Lebih cepat namun bisa terjadi timeout

     - Kedua program berhasil:
       - Mengirim data
       - Memproses data
       - Mengembalikan hasil

# 8. Kesimpulan

     - TCP cocok untuk komunikasi yang membutuhkan keandalan
     - UDP cocok untuk komunikasi cepat
     - Program client-server berhasil berjalan dengan baik
     - Data berhasil dikirim dan diproses menjadi huruf kapital