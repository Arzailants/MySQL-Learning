## Pengertian Database dalam Relational Database

Dalam relational database model, sebuah database adalah kumpulan relasi yang saling terhubung satu sama lainnya. Relasi adalah istilah dalam relational database, tapi kita lebih familiar jika menyebutnya sebagai tabel. Selayaknya tabel yang memiliki kolom dan baris, dalam relational database, kolom (column) disebut attribute, sedangkan baris (row) disebut tuple. Hal ini hanya sekedar penamaan, dan agar lebih gampang, kita hanya akan menggunakan istilah tabel, kolom dan baris dalam tutorial ini, namun jika anda menemui istilah relation, attribut dan tuple, itu hanya penamaan lain dari tabel, kolom, dan baris.

ReRelasi (tabel), Tuple (baris) dan Attribute (kolom) | wikipedia

### Candidate Key (Kunci Kandidat)
Database dalam relational database dapat di sederhanakan sebagai sekumpulan tabel yang saling terhubung. Setiap baris dari dalam tabel setidaknya harus memiliki sebuah kolom yang unik. Unik disini maksudnya tidak boleh sama. Contohnya, dalam tabel 4.1 : tabel data_mahasiswa, kolom NIM (Nomor Induk Mahasiswa) akan menjadi kandidat yang bagus, karena tidak mungkin ada 2 mahasiswa yang memiliki NIM yang sama. NIM disini disebut juga dengan Candidate Key (Kunci Kandidat). Candidate Key adalah satu atau beberapa kolom dalam tabel yang bisa mengidentifikasi tiap baris dari tabel tersebut.


Nomor KTP juga merupakan candidate key yang bagus, setidaknya setiap orang akan memiliki Nomor KTP yang berbeda-beda. Namun dalam beberapa kasus, nomor KTP tidak selalu ada, karena bisa saja seseorang belum memiliki KTP karena sesuatu dan lain hal. Beberapa karakteristik Candidate key : unik (tidak boleh berulang), tidak boleh memiliki nilai null (kosong), nilai dari candidate key akan sangat jarang berubah.


### Primary Key (Kunci Utama)
Dalam sebuah tabel, akan terdapat beberapa candidate key, namun hanya ada 1 Primary key (kunci utama). Primary key adalah salah satu candidate key yang kita nobatkan sebagai kolom unik untuk identifikasi baris dalam tabel. Kolom ini tidak boleh berulang, dan tidak boleh kosong (null). Dari tabel data_mahasiswa, NIM dapat kita tetapkan sebagai primary key.


### Foreign Key (Kunci Tamu)
Dalam sebuah database, biasanya akan terdapat beberapa tabel. Tabel-tabel ini dapat dihubungkan satu dengan yang lainnya dengan kolom yang merupakan bagian dari tabel lain. Foreign Key (Kunci Tamu) adalah Primary key dari tabel lainnya yang terdapat di tabel saat ini. Di dalam contoh tabel 4.2 : Tabel data_mahasiswa dapat terlihat bahwa NIM adalah primary key dari tabel data_mahasiswa, dan kode_jurusan adalah primary key pada tabel_jurusan. Kedua tabel tersebut dihubungkan oleh kolom kode jurusan.


### Referential Integrity
Referential Integrity berkaitan erat dengan foreign key. Pada dasarnya Referential Integrity adalah penerapan aturan bahwa untuk setiap foreign key yang terdapat pada suatu tabel, harus ada nilainya di tabel asal kolom tersebut. Dalam contoh kita, pada tabel 4.2 dan 4.3 setiap kode_jurusan dalam tabel data_mahasiswa harus ada nilainya dalam tabel kode_jurusan. Di dalam tabel data_mahasiswa kita tidak bisa memasukkan nilai 20, karena di tabel kode_jurusan, kode jurusan 20 belum diinput. Dan jika kita ingin menghapus suatu jurusan dari tabel_jurusan, semua mahasiswa harus terlebih dahulu sudah tidak ada yang memiliki kode jurusan tersebut.


### Index
Index dalam database adalah sebuah struktur data yang diimplementasikan oleh RDBMS untuk mempercepat proses pembacaan data. Index lebih kepada penerapan algoritma dari masing-masing aplikasi database, dan diterapkan ke dalam kolom dari tabel yang kita inginkan. Mirip Index yang ada di belakang buku, index seolah-olah daftar cepat untuk mencari sesuatu oleh RDBMS. Kita dapat mendeklarasikan kolom mana saja yang akan di index.

Untuk MySQL, kolom yang ditetapkan sebagai primary key akan otomatis di-index. Tetapi dalam satu tabel, bisa saja terdapat beberapa kolom yang di index. Pertanyaannya, jika index digunakan untuk mempercepat proses pembacaan, kenapa tidak semua kolom saja kita index? Jawabannya, karena index sendiri juga memiliki kelemahan.

Ketika data baru ditambahkan atau terdapat data yang akan dirubah, index yang tersimpan untuk tabel tersebut harus dibuat ulang, sehingga memperlama proses penambahan data. Namun untuk tabel yang jarang bertambah, index menawarkan perfoma yang cepat untuk pembacaan data.

### Normalisasi Database
Normalisasi database (Database normalization) adalah proses penyusunan kolom dan tabel untuk meminimalkan redundansi data (data yang berulang). Normalisasi biasanya akan membagi tabel besar menjadi beberapa tabel kecil yang saling terhubung. Hal ini dilakukan agar mudah dalam mengatur, dan mengorganisasi data yang ada.

Contohnya, untuk tabel data_mahasiswa, jika terjadi perubahan nama jurusan, misalnya dari Ilmu Komputer menjadi Teknik Informatika, maka kita harus merubah satu-satu  tiap mahasiswa. Namun jika di bagi menjadi 2 tabel, kita hanya tinggal merubah baris no urut 14 dari tabel  kode_jurusan menjadi Teknik Informatika. Dan otomatis setiap mahasiswa yang memiliki kode_jurusan 14, adalah mahasiswa Teknik Informatika.

Normalisasi database memiliki beberapa tahapan. Dari wikipedia, normalisasi database setidaknya memiliki 9 tahapan. Pada setiap tahapan, ada syarat yang harus dipenuhi, sampai sebuah tabel tidak lagi memiliki kolom yang redundant. Kita tidak harus mengikuti semua tahap, biasanya hanya dibutuhkan 3 tahapan normalisasi untuk membuat sebuah desain database sederhana. Proses normalisasi database tidak akan kita bahas disini, namun setidaknya kita mengetahui bahwa normalisasi database adalah proses untuk mendesain database agar terorganisir.


### Entity Relationship Diagram (ERD)
Entity Relationship Diagram adalah diagram untuk menggambarkan desain database yang akan dibuat. Di dalam ERD akan terlihat semua tabel yang akan dirancang, primary key masing-masing tabel, serta foreign key, dan kolom-kolom apa saja yang nantinya tersedia. ERD memiliki berbagai versi, baik yang berbentuk balon, maupun tabel. ERD inilah sebagai blueprint dari database yang akan dirancang.



Itulah beberapa istilah yang sering di temui untuk pembahasan mengenai relational database, yang dapat digunakan sebagai dasar untuk mempelajari MySQL dan memaksimalkan penggunaannya. Selanjutnya kita akan membahas tentang SQL (Structured Query Language), bahasa wajib yang diketahui untuk mempelajari MySQL.

Sumber:

http://en.wikipedia.org/wiki/Relational_database
http://en.wikipedia.org/wiki/Database_normalization
Michael J. Hernandez : Database Design for Mere Mortals, Addison Wesley, 2003
Clare Churcher: Beginning Database Design From Novice to Professional, Apress,  2007
