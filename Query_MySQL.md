## Menjalankan Perintah (query) MySQL

Setiap perintah, atau sering juga disebut “query” di dalam MySQL harus diakhiri dengan tanda titik koma “;” dan akan dieksekusi setelah tombol Enter ditekan. Selama query MySQL belum diakhiri dengan “;” maka itu dianggap masih dalam satu perintah.

Ketika kita menjalankan sebuah perintah MySQL (query), query tersebut akan dikirim dari MySQL Client ke MySQL Server untuk di proses, setelah proses selesai, hasilnya akan dikirim kembali ke MySQL Client.

Agar lebih mudah memahami query MySQL, kita akan langsung praktek beberapa query sederhana. Silahkan jalankan MySQL Server dan masuk sebagai user root dari MySQL Client (tutorialnya telah kita bahas pada Tutorial Belajar MySQL: Cara Menjalankan MySQL Server, dan Tutorial Belajar MySQL: Cara Menjalankan MySQL Client).

Setelah masuk ke dalam MySQL Client (ditandai dengan awalan mysql> pada jendela cmd), kita akan mencoba beberapa perintah MySQL sederhana. Ketikkan perintah berikut: SELECT NOW(); lalu akhiri dengan Enter pada keyboard.


mysql> SELECT NOW();
 
+---------------------+
| NOW()               |
+---------------------+
| 2014-11-13 09:21:08 |
+---------------------+
1 row in set (0.69 sec)

Contoh query diatas adalah untuk menampilkan tanggal dan waktu saat ini dengan fungsi NOW(). Query tersebut akan menghasilkan hasil yang berbeda-beda tergantung saat anda menjalankannya.

Perintah SELECT kebanyakan digunakan untuk proses pembacaan data dari database, tetapi juga dapat digunakan untuk menampilkan hasil dari fungsi tambahan, seperti fungsi NOW(), yang kita coba kali ini. Hasil query MySQL akan ditampilkan dalam bentuk tabel pada cmd windows, hasil ini dikirim dari MySQL Server.

Selain hasil dalam bentuk tabel, hampir setiap perintah query, MySQL juga akan menampilkan banyaknya baris yang dipengaruhi dan lamanya waktu eksekusi. Pada contoh kita diatas, ditampilkan keterangan: 1 row in set (0.00 sec). Keterangan ini berarti query kita diproses selama 0 detik (0 second), dan mempengaruhi 1 baris (1 row). o detik disini bukan berarti query tersebut akan tampil seketika, namun karena perintah yang sederhana, MySQL (mungkin) hanya membutuhkan waktu 0,001 sekian detik untuk memproses (dibulatkan menjadi 0,00).

Sebagai contoh query lainnya, kita akan mencoba untuk menampilkan nama user yang sedang aktif dan versi MySQL Server yang digunakan pada saat ini. Untuk menampilkan keterangan ini, MySQL menyediakan fungsi USER() dan VERSION()

mysql> SELECT NOW(),USER(),VERSION();
 
+---------------------+----------------+------------+
| NOW()               | USER()         | VERSION()  |
+---------------------+----------------+------------+
| 2014-11-13 09:21:37 | root@localhost | 5.6.21-log |
+---------------------+----------------+------------+
1 row in set (0.11 sec)

Dapat dilihat dari contoh query tersebut, untuk setiap fungsi dipisahkan dengan tanda koma “,”.

Penulisan perintah (query) MySQL juga tidak harus dalam satu baris. Misalnya, kita bisa menjalankan query berikut:


mysql> SELECT NOW(),
    -> USER(),
    -> VERSION();
 
+---------------------+----------------+------------+
| NOW()               | USER()         | VERSION()  |
+---------------------+----------------+------------+
| 2014-11-13 09:22:50 | root@localhost | 5.6.21-log |
+---------------------+----------------+------------+
1 row in set (0.00 sec)

Setelah fungsi NOW() pertama, tekan Enter untuk pindah baris, lalu ketikkan perintah sambungannya. Selama kita belum mengakhiri perintah tersebut dengan “;”, maka MySQL menganggap baris berikutnya adalah sambungan dari baris sebelumnya. Pemisahan perintah seperti diatas akan sangat berguna jika kita menuliskan query yang panjang, sehingga lebih mudah dibaca. Tanda mysql> akan berubah menjadi -> selama kita belum mengakhiri query tersebut dengan tanda titik koma “;”.

Jika kita telah membuat query MySQL, namun memutuskan untuk membatalkannya, dapat dilakukan dengan kode “\c”. Contoh querynya:

mysql> SELECT NOW(),
-> USER(),
-> \c
mysql>

Dapat anda perhatikan bahwa tanda -> akan kembali menjadi mysql> yang menandakan MySQL telah siap untuk perintah yang baru.

Selain menggunakan “;”, query MySQL juga akan mengeksekusi perintah juga diakhiri dengan tanda “\g”.

mysql> SELECT NOW(),USER(),VERSION()\g
 
+---------------------+----------------+------------+
| NOW()               | USER()         | VERSION()  |
+---------------------+----------------+------------+
| 2014-11-13 09:23:19 | root@localhost | 5.6.21-log |
+---------------------+----------------+------------+
1 row in set (0.00 sec)
Cara Merubah Tampilan output MySQL
Untuk perintah MySQL (query MySQL) yang menghasilkan output yang panjangnya melebihi layar cmd, akan sulit bagi kita dalam membacanya. MySQL menyediakan cara untuk merubah tampilan tabel menjadi baris.

Untuk merubah tampilan output MySQL menjadi baris, tambahkan tanda “\G” (huruf G besar, bukan g kecil) setelah perintah query. Berikut adalah contoh penggunaannya dalam MySQL:

mysql> SELECT NOW(),USER(),VERSION()\G
 
*************************** 1. row ***************************
    NOW(): 2014-11-13 09:23:41
   USER(): root@localhost
VERSION(): 5.6.21-log
1 row in set (0.00 sec)
Aturan Penulisan huruf BESAR dan kecil dalam MySQL
Konsep penggunaan huruf besar dan huruf kecil dalam MySQL akan berbeda tergantung saat penggunaannya.

MySQL tidak membedakan penulisan huruf besar maupun kecil (case insensitive) dalam penulisan fungsi dan identifier. Sebagai contoh, ketiga query ini akan menghasilkan output yang sama (kecuali header dari tabel):


mysql> SELECT Version();
 
+------------+
| Version()  |
+------------+
| 5.6.21-log |
+------------+
1 row in set (0.00 sec)
 
mysql> SELECT VERSION();
 
+------------+
| VERSION()  |
+------------+
| 5.6.21-log |
+------------+
1 row in set (0.00 sec)
 
mysql> select version();
 
+------------+
| version()  |
+------------+
| 5.6.21-log |
+------------+
1 row in set (0.00 sec)
Namun untuk penulisan nama database dan nama tabel, MySQL akan mengikuti sistem operasi dimana MySQL Server berjalan.

Untuk Sistem Operasi Windows, nama database mahasiswa dianggap sama dengan MaHaSIsWA, namun dalam MySQL Server yang berjalan pada Linux, kedua database tersebut dianggap berbeda (case sensitive).

Karena hal ini, ada baiknya kita membiasakan menggunakan kesepakatan dalam penamaan. Disarankan untuk menggunakan selalu huruf kecil dalam penulisan database, tabel dan variabel dalam MySQL, sehingga perbedaan huruf tidak akan menjadi masalah pada kemudian hari jika MySQL Server pindah sistem operasi.

Di dalam tutorial duniailkom, dan juga dalam beberapa buku MySQL, perintah-perintah dan fungsi baku MySQL akan menggunakan HURUF BESAR sedangkan untuk nama database, tabel, dan kolom akan menggunakan huruf kecil. Hal ini hanya semata-mata agar perintah SQL mudah dibaca dan dibedakan dengan nama database atau tabel. Kita bisa saja menggunakan huruf kecil untuk seluruh fungsi-fungsi dalam MySQL.


Perhatikan penggunaan tanda
Dalam beberapa kasus, sebuah query bisa saja menggunakan tanda baca selain angka dan huruf seperti : “,” (koma), “\” (forward slash/garis miring depan),”’” (tanda petik), dan “ “ (spasi). Misalnya untuk 123 dan ‘123’, 12e + 14 dan 12e+14 akan memiliki arti berbeda dalam MySQL. Jika anda menemui error, mungkin penggunaan “tanda” ini adalah masalahnya. Lebih jauh dalam penggunaan tanda ini akan kita pelajari dalam tutorial-tutorial MySQL selanjutnya.
