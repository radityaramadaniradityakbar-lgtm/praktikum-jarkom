# Laporan Praktikum JarKom IF
# Laporan Praktikum Jaringan Komputer Week 9

## Keterangan
- Nama : Mochammad Raditya Ramadani Akbar
- NIM : 103072400039
- Kelas : IF 04-05
- Mata Kuliah : Praktikum Jaringan Komputer (JarKom)
- Modul : 9 (WEB SERVER)

## Tujuan Praktikum
- Memahami konsep dasar jaringan komputer khususnya komunikasi client-server.
- Memahami prinsip kerja protokol TCP dalam pertukaran data.
- Memahami konsep dasar protokol HTTP sebagai protokol komunikasi web.
- Mempelajari penggunaan socket programming dalam Python.
- Mampu membuat dan mengkonfigurasi server socket.
- Mampu menerima koneksi dari client menggunakan metode accept().
- Mampu membaca dan memahami HTTP request dari browser.
- Mampu memproses permintaan file dari client.
- Mampu membaca file dari sistem (file HTML).
- Mampu mengirimkan HTTP response yang sesuai ke client.
- Mampu menampilkan halaman web sederhana di browser.
- Mampu menangani kesalahan seperti 404 Not Found.
- Memahami alur kerja server dari menerima request hingga mengirim response.
- Mampu menguji server menggunakan browser.
- Meningkatkan pemahaman praktis dalam implementasi web server sederhana.

## Langkah Percobaan Praktikum

## Web Server Awal
**Langkah-langkah**

1. Pertama Membuat file **server.py**
2. Masukkan Skeleton Kode
```python
from socket import *
import threading

def handle_client(connectionSocket):
    try:
        # menerima pesan user
        message = connectionSocket.recv(1024).decode() # decode = 10101010 = "message"

        # index.html, hello.html
        # message isinya = /GET /index.html HTTP/1.1
        message = message[4:15]
        print(message)
        # filename = message.split()[1]

        # membuka index.html serta menghilangkan "/"
        f = open(message[1:])

        # membaca file html
        outputData = f.read()

        # kirim respon
        connectionSocket.send(
            "HTTP/1.1 200 OK\r\n\r\n".encode()
        )

        # kirim data
        connectionSocket.sendall(outputData.encode())

        # tutup koneksi
        connectionSocket.close()
    
    except IOError:
        # kirim respon bila tidak ditemukan
        connectionSocket.send(
            "HTTP/1.1 404 Not Found\r\n\r\n".encode()
        )

        # kirim data
        connectionSocket.send(
            "<h1>404 Not Found</h1>".encode()
        )

        # tutup koneksinya
        connectionSocket.close()


serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', 6789))
serverSocket.listen(5) # dapat menerima sebanyak 5 client
print("[SYSTEM] server is running...")

while True:
    connectionSocket, addr =  serverSocket.accept()

    # membuat thread dan target threadnya, beseerta parameter
    thread = threading.Thread(
        target = handle_client,
        args = (connectionSocket,)
        )
    # menjalankan
    thread.start()
```
3. Membuat file index.html
4. Masukkan Skeleton Kode
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Server</title>
    <style>
        body {
            display: flex;
            justify-content: center;  /* tengah kiri-kanan */
            align-items: center;      /* tengah atas-bawah */
            height: 100vh;
            margin: 0;
        }

        h1 {
            font-size: 80px;  /* bikin gede */
        }
    </style>
</head>

<body>
    <h1>P P Apaa?</h1>
</body>
</html>
```
5. Lalu buka terminal di Vscode dan jalankan (Run Code) File server.py
6. Buka Chrome/Browser Ketik URL: http://localhost:6789/index.html

**Hasil Percobaan**

- Server Berhasil
![Tampilan Server Diterima/Berhasil](../assets/image/Server%20Berhasil%20Menampilkan%20isi%20dari%20html%20nya.png)

Ketika server berhasil memproses permintaan dari klien, server akan mengirimkan respons dengan status 200 OK. Selain itu, isi file yang diminta juga dikirimkan ke browser sehingga halaman web dapat ditampilkan dengan baik sesuai dengan permintaan pengguna.

- Server Ditolak/Gagal
![Tampilan Server Gagal](../assets/image/Chrome-Web%20error%20404.png)

Apabila file yang diminta tidak tersedia atau terjadi kesalahan dalam proses pembacaan file, server akan mengirimkan respons 404 Not Found. Hal ini menunjukkan bahwa permintaan dari klien tidak dapat dipenuhi oleh server.

## Latihan Tambahan
1. Masukkan/Ketik Kode
```python
from socket import *
import threading

def handle_client(connectionSocket):
    try:
        # menerima pesan user
        message = connectionSocket.recv(1024).decode() # decode = 10101010 = "message"

        # index.html, hello.html
        # message isinya = /GET /index.html HTTP/1.1
        message = message[4:15]
        print(message)
        # filename = message.split()[1]

        # membuka index.html serta menghilangkan "/"
        f = open(message[1:])

        # membaca file html
        outputData = f.read()

        # kirim respon
        connectionSocket.send(
            "HTTP/1.1 200 OK\r\n\r\n".encode()
        )

        # kirim data
        connectionSocket.sendall(outputData.encode())

        # tutup koneksi
        connectionSocket.close()
    
    except IOError:
        # kirim respon bila tidak ditemukan
        connectionSocket.send(
            "HTTP/1.1 404 Not Found\r\n\r\n".encode()
        )

        # kirim data
        connectionSocket.send(
            "<h1>404 Not Found</h1>".encode()
        )

        # tutup koneksinya
        connectionSocket.close()


serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', 6789))
serverSocket.listen(5) # dapat menerima sebanyak 5 client
print("[SYSTEM] server is running...")

while True:
    connectionSocket, addr =  serverSocket.accept()

    # membuat thread dan target threadnya, beseerta parameter
    thread = threading.Thread(
        target = handle_client,
        args = (connectionSocket,)
        )
    # menjalankan
    thread.start()
```
2. Masukkan Isi dari file index.html
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Server</title>
    <style>
        body {
            display: flex;
            justify-content: center;  /* tengah kiri-kanan */
            align-items: center;      /* tengah atas-bawah */
            height: 100vh;
            margin: 0;
        }

        h1 {
            font-size: 80px;  /* bikin gede */
        }
    </style>
</head>

<body>
    <h1>Pagi Kicau Mania Malamnya Kacau Mania -_-</h1>
</body>
</html>
```
3. Buka Terminal di VsCode dan jalankan (Run Code) file **server.py**
4. Buka Chrome/Browser Ketik URL: http://localhost:6789/index.html

Pada tahap ini dilakukan pengujian terhadap server multithreaded yang telah dibuat. Server mampu menangani beberapa permintaan klien secara bersamaan dengan memanfaatkan thread terpisah untuk setiap koneksi yang masuk. Dengan demikian, proses pelayanan terhadap klien menjadi lebih cepat dan efisien dibandingkan dengan server single-threaded.

**Hasil Percobaan**
![Tampilan Percobaan Web server](../assets/image/tampilan%20web%20server%20tambahan.png)

Pada kondisi berhasil, server mampu menerima dan memproses setiap permintaan klien secara bersamaan, kemudian mengirimkan respons 200 OK beserta isi file yang diminta. Hal ini dibuktikan dengan tampilnya halaman web secara normal pada beberapa browser atau tab yang dibuka secara bersamaan.

## Kesimpulan Hasil Percobaan
Berdasarkan hasil percobaan yang telah saya lakukan, dapat disimpulkan bahwa implementasi multithreading pada web server berhasil meningkatkan kemampuan server dalam menangani banyak permintaan klien secara bersamaan. Setiap koneksi yang masuk diproses dalam thread yang berbeda sehingga server tidak mengalami bottleneck seperti pada server single-threaded.
Selain itu, server tetap mampu memberikan respons yang sesuai terhadap setiap permintaan, baik dalam kondisi berhasil dengan mengirimkan status 200 OK maupun dalam kondisi gagal dengan memberikan status 404 Not Found. Hal ini menunjukkan bahwa server tidak hanya lebih efisien, tetapi juga tetap andal dalam menangani berbagai kondisi permintaan dari klien.
Dengan demikian, penggunaan multithreading terbukti efektif dalam meningkatkan performa dan efisiensi web server dalam lingkungan jaringan yang melibatkan banyak pengguna secara simultan.