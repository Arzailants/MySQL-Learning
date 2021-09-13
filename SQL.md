Pengertian Structured Query Language (SQL)
SQL (Structured Query Language) adalah bahasa pemrograman khusus yang digunakan untuk memanajemen data dalam RDBMS. SQL biasanya berupa perintah sederhana yang berisi instruksi-instruksi untuk manipulasi data. Perintah SQL ini sering juga disingkat dengan sebutan ‘query‘.

Sejarah SQL
Bersamaan dengan paper Dr. Edgar F. Codd pada tahun 1969 tentang Teori Database Relational, ia pun mengajukan sebuah bahasa yang disebut DSL/Alpha untuk memanajemen data dalam relational database. Berdasarkan ide Dr.Codd ini, beberapa saat setelah itu IBM mencoba merancang bahasa prototipe sederhana DSL/Alpha yang disebut SQUARE.

Pada tahun 1970, team yang beranggotakan peneliti IBM Donald D. Chamberlin dan Raymond F. Boyce, mengembangkan SQUARE lebih lanjut menjadi SEQUEL (Structured English Query Language). SEQUEL digunakan untuk mengoperasikan prototipe RDBMS pertama IBM, System R. Di kemudian hari, SEQUEL berubah nama menjadi SQL karena permasalahan merk dagang (trademark) dengan sebuah perusahaan pesawat di inggris yang terlebih dahulu telah memakai nama SEQUEL.

Pada akhir 1970an, perusahaan Relational Software, Inc. (sekarang Oracle Corporation) melihat potensi bahasa SQL dan mengembangkan sendiri versi SQL untuk RDBMS mereka. Oracle V2 (versi 2) yang dirilis Juni 1979 adalah RDBMS komersial pertama yang mengimplementasikan SQL.

Dengan kemudahan yang ditawarkan, SQL mulai diimplementasikan oleh berbagai RDBMS dengan versi SQL mereka masing-masing. Namun hal ini  menimbulkan permasalahan karena perbedaan penerapan SQL dari satu aplikasi dengan aplikasi database lainnya yang tidak seragam.Sehingga  pada tahun 1986, badan standar amerika, ANSI (American National Standards Institute) merancang sebuah standar untuk SQL. Satu tahun setelahnya, ISO (International Organization for Standardization) juga mengeluarkan standar untuk SQL. Versi terakhir standar SQL dirilis pada 2011, yang dinamakan SQL 2011. Dengan standar ini diharapkan ada keseragaman SQL antar aplikasi RDBMS.

Akan tetapi walaupun sudah ada standar tentang SQL, banyak perusahaan RDBMS yang menambahkan ‘fitur’ SQL selain standar yang ada. MySQL juga memiliki SQL yang tidak standar, yang tidak ada pada Oracle, begitu juga sebaliknya. Namun setidaknya bahasa SQL hampir sama untuk perintah-perintah dasar antar RDBMS. Perintah SQL untuk membuat tabel misalnya, dapat digunakan baik di Oracle maupun MySQL.

Jenis-jenis perintah SQL
Perintah atau instruksi SQL dapat dikelompokkan berdasarkan jenis dan fungsinya. Terdapat 3 jenis perintah dasar SQL : Data Definition Language, Data Manipulation Language dan Data Control Language.

Data Definition Language (DDL) adalah jenis instruksi SQL yang berkaitan dengan pembuatan struktur tabel maupun database. Termasuk diantaranya : CREATE, DROP, ALTER, dan RENAME.
Data Manipulation Language (DML) adalah jenis instruksi SQL yang berkaitan dengan data yang ada dalam tabel, tentang bagaiman menginput, menghapus, memperbaharui serta membaca data yang tersimpan di dalam database. Contoh perintah SQL untuk DML : SELECT, INSERT, DELETE, dan UPDATE.
Data Control Language (DCL) adalah jenis instruksi SQL yang berkaitan dengan manajemen hak akses dan pengguna (user) yang dapat mengakses database maupun tabel. Termasuk diantaranya : GRANT dan REVOKE.
Selain ketiga jenis perintah SQL, terdapat juga 2 jenis SQL tambahan : Transaction Control Language, dan Programmatic SQL.

Transaction Control Language (TCL) adalah perintah SQL untuk proses transaksi. Proses transaksi ini digunakan untuk perintah yang lebih dari 1, namun harus berjalan semua, atau tidak sama sekali. Misalnya untuk aplikasi critical seperti transfer uang dalam sistem database perbankan. Setidaknya akan ada 2 perintah, yaitu mengurangi uang nasabah A, dan menambah uang nasabah B. Namun jika terjadi kesalahan sistem, kedua transaksi ini harus dibatalkan. Tidak bisa hanya satu perintah saja. Termasuk ke dalam TCL adalah perintah : COMMIT, ROLLCABK, dan SET TRANSACTION.
Programmatic SQL berkaitan dengan sub program (stored procedure) maupun penjelasan mengenai struktur database. Contoh perintah seperti : DECLARE, EXPLAIN, PREPARE, dan DESCRIBE.
Setelah memahami sekilas tentang bahasa pemrograman database : SQL, dan teori-teori dasar database dari beberapa tutorial sebelumnya,  kita sudah siap untuk tutorial selanjutnya, download dan install aplikasi MySQL.

Sumber:

http://en.wikipedia.org/wiki/Sql
James R. Groff : SQL The Complete Reference, 3rd Edition,McGraw-Hill, 2010
