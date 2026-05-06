# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 5

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 5 (UDP)

## Tujuan Praktikum
1. Mahasiswa dapat memahami konsep dasar protokol User Datagram Protocol (UDP) sebagai salah satu protokol pada lapisan transport.
2. Mahasiswa dapat menganalisis struktur header UDP yang terdiri dari source port, destination port, length, dan checksum.
3. Mahasiswa dapat menggunakan aplikasi Wireshark untuk menangkap dan mengamati paket UDP secara langsung.
4. Mahasiswa dapat mengidentifikasi hubungan antara paket request dan response pada komunikasi UDP.
5. Mahasiswa dapat menghitung ukuran header dan payload pada paket UDP berdasarkan hasil capture.
6. Mahasiswa dapat mengetahui karakteristik UDP yang bersifat connectionless, tidak reliabel, dan tanpa mekanisme kontrol aliran.
7. Mahasiswa dapat memahami penggunaan nomor port dalam komunikasi UDP.

# Langkah Percobaan
1. Download file http://gaia.cs.umass.edu/wireshark-labs/wireshark-traces.zip di .pdf

2. Extract di file dan cari file http-ethereal-trace-5

3. Lalu klik kanan file tersebut dan buka dengan menggunakan wireshark
   ![tampilan http-ethereal-trace-5](../assets/image/tampilan%20http-ethereal-5.png)

4. Lakukan filter UDP dan pilih 1 paket UDP

# Jawaban Pertanyaan
1. Pilih satu paket UDP yang terdapat pada trace Anda. Dari paket tersebut, berapa banyak 
   “field” yang terdapat pada header UDP? Sebutkan nama-nama field yang Anda temukan!
   ![tampilan field UDP](../assets/image/tampilan%20field%20UDP.png)

   Terdapat 4 field utama pada header UDP:
   - Source Port → port pengirim
   - Destination Port → port tujuan
   - Length → panjang total UDP (header + data)
   - Checksum → pengecekan error

2. Perhatikan informasi “content field” pada paket yang Anda pilih di pertanyaan 1. Berapa 
   panjang (dalam satuan byte) masing-masing “field” yang terdapat pada header UDP?
   
   - Source Port = 2 byte
   - Destination Port = 2 byte
   - Length = 2 byte
   - Checksum = 2 byte
   - Total header UDP = 8 byte

3. Nilai yang tertera pada ”Length” menyatakan nilai apa? Verfikasi jawaban Anda melalui 
   paket UDP pada trace.
   ![tampilan total panjang udp](../assets/image/nilai%20length.png)

   - Length = 58 byte
   - Header = 8 byte
   - Data = 50 byte
   - 58 – 8 = 50 byte (payload)

4. Berapa jumlah maksimum byte yang dapat disertakan dalam payload UDP? (Petunjuk: 
   jawaban untuk pertanyaan ini dapat ditentukan dari jawaban Anda untuk pertanyaan 2)
   Maksimum ukuran UDP:
   - Total maksimal IP = 65535 byte
   - Dikurangi header IP (20 byte) + UDP (8 byte)
   - 65535 – 20 – 8 = 65507 byte
   - Jadi: Maksimum payload UDP = 65507 byte

5. Berapa nomor port terbesar yang dapat menjadi port sumber? (Petunjuk: lihat petunjuk 
   pada pertanyaan 4)
   Karena port = 16 bit:
   - Maksimum = 65535

6. Berapa nomor protokol untuk UDP? Berikan jawaban Anda dalam notasi heksadesimal dan 
   desimal. Untuk menjawab pertanyaan ini, Anda harus melihat ke bagian ”Protocol” pada 
   datagram IP yang mengandung segmen UDP.
   ![tampilan nomor protokol UDP](../assets/image/nomor%20protokol%20udp.png)

   - Desimal: 17
   - Heksadesimal: 0x11

7. Periksa pasangan paket UDP di mana host Anda mengirimkan paket UDP pertama dan paket 
   UDP kedua merupakan balasan dari paket UDP yang pertama. (Petunjuk: agar paket kedua merupakan balasan dari paket pertama, pengirim paket pertama harus menjadi tujuan dari paket kedua). Jelaskan hubungan antara nomor port pada kedua paket tersebut!
   ![tampilan hubungan port request](../assets/image/hubungan%20port%20request.png)
   ![tampilan hubungan port response](../assets/image/hubungan%20port%20response.png)

   - Paket 1:
      - Source Port = 1334
      - Destination Port = 161
   - Paket 2 (balasan):
      - Source Port = 161
      - Destination Port = 1334

   Port saling bertukar
   Artinya:
   - Pengirim awal jadi penerima
   - Penerima jadi pengirim
