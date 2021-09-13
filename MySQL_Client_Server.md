## MySQL Server dan MySQL Client

Dalam penerapan sistem sebenarnya, MySQL Server dan MySQL Client biasanya dijalankan pada komputer yang berbeda. Komputer Server berada pada sebuah ruangan tersendiri dan terhubung melalui jaringan dengan beberapa komputer Client. Namun kali ini kita akan menjalankan keduanya di dalam sebuah komputer saja.

Untuk MySQL Server, kita telah menjalankannya baik sebagai service, atau manual dengan mysqld.exe pada Tutorial Belajar MySQL: Cara Menjalankan MySQL Server.

Dengan MySQL server yang telah berjalan, kita akan mengaksesnya menggunakan MySQL Client dari Command Prompt Windows (selanjutnya akan kita singkat dengan cmd), menggunakan aplikasi mysql.exe dari folder bin MySQL.

Perhatikan bahwa untuk MySQL Server, kita menggunakan mysqld.exe, sedangkan untuk MySQL Client,kita menggunakan mysql.exe.

### Menjalankan MySQL Client dengan MySQL Client Console
Cara paling cepat untuk memulai MySQL Client adalah dengan menggunakan Command Line Client. Aplikasi ini bisa diakses dari menu Start –> MySQL –> MySQL 8.0 Command Line Client.


**Perhatikan bahwa pada MySQL 8.0, terdapat 2 buah aplikasi Command Line Client, yakni MySQL 8.0 Command Line Client, dan MySQL 8.0 Command Line Client – Unicode. Versi Unicode ditujukan jika anda menggunakan karakter non latin di dalam database, seperti menggunakan huruf jepang, cina, atau korea. Dalam tutorial ini saya menggunakan versi normal, bukan Unicode.**

Pada jendela DOS yang terbuka, masukkan password untuk user root, misalnya “qwerty”, lalu tekan Enter. Jika tampilan “Welcome to the MySQL monitor” telah muncul, berarti kita telah berhasil login sebagai root, dan bisa mulai menggunakan MySQL.

Walaupun menggunakan MySQL Client Console lebih praktis, tetapi kita terikat dengan user root. Bagaimana jika kita ingin menggunakan user lain? untuk hal ini kita akan mempelajari cara mengakses MySQL Client secara manual dari command prompt Windows.

### Menjalankan MySQL Client dari cmd Windows (mysql.exe)

Untuk menjalankan MySQL Client secara manual, sama seperti menjalankan MySQL Server secara manual, kita akan mengakses folder instalasi MySQL dari cmd (command prompt) Windows. Dalam contoh ini, file instalasi MySQL saya berada di C:\MySQL 8.0\bin. Jika folder instalasi MySQL di komputer anda berbeda, silahkan lakukan penyesuaian.

Caranya sama seperti menjalankan MySQL Server secara manual, yakni buka cmd Windows, kemudian pindah ke folder C:\MySQL 8.0\bin dengan perintah cd C:\MySQL 8.0\bin:

Karena kita akan sering mengakses file “C:\MySQL 8.0\bin” dari cmd, maka akan lebih mudah jika membuat shortcut untuk langsung masuk ke dalam folder ini dari cmd.

Caranya, cari aplikasi cmd dari menu Search. Kemudian klik kanan, pilih Open file location.

Pilih open file location cmd WindowsAkan terbuka jendela Windows Explorer yang berisi icon cmd Windows, kemudian klik kanan, pilih menu Send To -> Desktop (create shortcut):

Buat shortcut cmd Windows 10

Hasilnya, akan tampil shortcut cmd di Desktop. Klik kanan shortcut cmd ini, lalu pilih properties:Dari tab Shortcut, cari input box “Start in”. Ubah isian kotak input ini menjadi “C:\MySQL 8.0\bin”, atau dengan lokasi lain folder bin dari MySQL jika anda menginstallnya bukan di “C:\MySQL 8.0”. Lalu klik OK.

Mengubah shortcut cmd menjadi start in MySQL 8.0-min

Sekarang, ketika shortcut ini di klik, akan langsung terbuka di folder C:\MySQL 8.0

Cmd Windows langsung berjalan di folder MySQL 8

Silahkan me-rename shortcut ini menjadi lebih spesifik, Misalnya: “MySQL Folder”, atau “MySQL cmd”.

### Memulai Koneksi dengan MySQL Server

Jika MySQL Server telah berjalan, baik sebagai service maupun langsung dengan mysqld.exe (Lihat Tutorial MySQL: Cara Menjalankan MySQL Server), kita bisa login ke dalam Server dengan format perintah:

1
**mysql -h host -u user –p_password**
mysql adalah program MySQL Client yang kita gunakan untuk mengakses server (file aslinya bernama: mysql.exe).
–h adalah kode untuk mysql bahwa perintah setelahnya adalah host. Host disini merupakan alamat IP dari komputer server. Karena kita menjalankan MySQL Server pada komputer yang sama dengan MySQL Client, alamat IP dari komputer kita adalah 127.0.0.1, atau sering juga disebut dengan localhost.

–u adalah kode untuk mysql bahwa perintah setelahnya adalah inputan nama user. User adalah username pengguna yang akan login ke MySQL server. User ini bisa kita buat sendiri nantinya dengan hak akses masing-masing, namun karena pertama kali digunakan, user yang tersedia adalah root.
-p adalah kode untuk mysql bahwa perintah setelahnya adalah password dari user. Inputan password harus langsung digabungkan dengan –p. contohnya, dalam tutorial ini, saya menggunakan password “qwerty” untuk user root. Maka penulisannya menjadi –pqwerty.
Untuk masuk pada localhost sebagai user root dengan password qwerty, perintah nya adalah:

1
mysql -h localhost -u root –pqwerty
Jika tulisan “Welcome to the MySQL monitor” seperti pada gambar sudah keluar, maka kita sukses login sebagai root. Setiap perintah di dalam Client MySQL akan di awali dengan tanda mysql>.

Login sebagai MySQL Client


Jika anda copy-paste perintah diatas, kadang terjadi error. Silahkan coba lagi dengan mengetik ulang secara manual.
Untuk keluar dari Client, ketik perintah:

1
exit
Atau tutup cmd dengan klik tombol close windows pada sudut kanan atas. Koneksi MySQL Client otomatis akan terputus.

Logout sebagai MySQL Client

Perintah -h localhost merupakan lokasi dari MySQL Server yang ingin diakses. Apabila MySQL Server berada di komputer lain, kita bisa menggunakan alamat IP server tersebut. Sebagai contoh, seandainya MySQL Server berada di alamat: 10.12.254.14, maka perintahnya menjadi:

1
**mysql -h 10.12.254.14 -u root –pqwerty**
Localhost adalah penyebutan untuk alamat komputer itu sendiri (bisa juga diganti dengan alamat IP: 127.0.0.1), dan oleh karena itu, perintah –h localhost juga dapat ditiadakan. Sehingga kita dapat masuk dengan perintah:

1
mysql -u root –pqwerty
Jika anda perhatikan, pada pesan “Welcome to the MySQL Monitor” diatas, terdapat baris peringatan: “Warning: Using a password on the command line interface can be insecure.” Hal ini terjadi karena kita menulis password root secara langsung, sehingga dianggap tidak aman. Sebagai solusinya, kita bisa menginput password user root dengan lebih aman menggunakan perintah:

1
mysql -u root –p
Tampilan cmd akan berhenti sesaat untuk menunggu kita menginputkan password:

1
Enter password:*****
Login sebagai MySQL Client dengan password


Sedikit tips untuk penggunaan melalui cmd (command prompt), kita dapat mengulang perintah-perintah yang pernah digunakan dengan menekan tombol panah atas pada keyboard.
Setelah menjalankan MySQL Server pada Tutorial Belajar MySQL: Cara Menjalankan MySQL Server, dan masuk sebagai MySQL Client pada Tutorial Belajar MySQL: Cara Menjalankan MySQL Client, saatnya kita mempelajari cara penulisan perintah (query) MySQL pada Tutorial Belajar MySQL: Dasar Penulisan Query MySQL.
