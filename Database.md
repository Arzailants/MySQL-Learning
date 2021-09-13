## Pengertian Database
Banyak pendapat jika menyangkut tentang pengertian database, berbagai textbook dan pendapat para expert di dunia database. Namun agar tidak terlalu pusing, marilah kita ambil saja pendapat Wikipedia: “A database is an organized collection of data”. Dengan terjemahan bebasnya, Database adalah kumpulan data yang terorganisir.
Tidak peduli apakah data ini tersimpan dalam bentuk kertas atau file komputer, selama data ini tersusun dalam aturan dan untuk keperluan tertentu, dapat disebut sebagai database. Namun biasanya jika kita menyebut database, hal ini merujuk kepada kumpulan data yang disimpan secara elektronik dalam komputer.

### Pengertian Database Model

Sekali lagi, mari kita kutip  Wikipedia : A database model is the theoretical foundation of a database and fundamentally determines in which manner data can be stored, organized, and manipulated in a database system. Artian bebasnya, database model adalah teori seputar bagaimana data itu akan disimpan, disusun, dan dimanipulasi dalam sebuah sistem database.

Dari awal konsep database mulai banyak digunakan (sekitar tahun 1960an – di amerika sana), berbagai teori dikemukakan tentang bagaimana cara menyajikan data agar mudah digunakan. Mudah digunakan disini mencakup: membuat, membaca, memperbaharui, dan menghapus data, atau istilah kerennya : CRUD (Create, Read, Update and Delete).

Mulailah berkembang berbagai database model, dari Flat model, Hierarchical model, Network model, hingga Relational model. Flat model adalah istilah lain dari tabel sederhana seperti di microsoft excel, tanpa aturan dan cara penulisan tertentu. Dalam Hierarchical model, data disusun seperti pohon terbalik, sehingga data terorganisasi dari atas ke bawah. Model database ini digunakan pada sistem database awal, seperti Information Management System (IMS) oleh IBM (1966). Network database model merupakan pengembangan dari Hierarchical model. Pembahasan lebih lanjut tentang Database Model, dapat dibaca di wikipedia-database model.

## 5 Tipe Database Model

### 1. Database Model : Relation
Konsep Relational Database Model diajukan pertama kali oleh peneliti IBM, Dr. Edgar F. Codd pada tahun 1969, dan merupakan database model yang paling banyak digunakan saat ini.

Dr. Codd pada awalnya mencari cara baru untuk menangani data dalam jumlah besar. Namun karena keterbatasan pada Hierarchical dan Network model yang umum digunakan saat itu, ia menerapkan prinsip matematis dalam menyusun data-data tersebut. Dan karena memang memiliki keahlian di bidang matematika, Dr.Codd berusaha mencari cara untuk menyelesaikan permasalahan yang sering timbul dalam database model saat itu, seperti redundansi data, hubungan antar data, dan ketergantungan kepada urutan di media penyimpanan.

Dr.Codd mengajukan ide tentang relational model ini dalam sebuah paper berjudul “A Relational Model of Data for Large Shared Databanks” pada Juni 1970. Relational Database model berasal dari 2 cabang ilmu matematika : set theory dan first-order predicate logic.

Edgar Frank "Ted" Codd (August 23, 1923 – April 18, 2003) | wikipedia

Sebuah relational database menyimpan data dalam ‘relasi’, atau yang disebut juga tabel. Setiap tabel terdiri dari tuple atau record dan atribut atau field. Urutan penyusunan dalam media penyimpanan fisik tidak berpengaruh dalam model ini, dan setiap record di dalam tabel diidentifikasi dengan sebuah field unik.

Relational Database Model inilah yang paling populer dan banyak diimplementasi dalam berbagai aplikasi database saat ini, termasuk Oracle dan MySQL. Aplikasi database untuk relational model, dikenal juga dengan Relational Database Management Systems (RDBMS).

### 2. RDBMS : Relational Database Management Systems
Relational Database Management Systems (RDBMS) adalah software/aplikasi yang menggunakan relational database model sebagai dasarnya. Sejak 1970an, RDBMS sudah banyak digunakan oleh berbagai vendor, dan dalam berbagai sistem hardware. Dua RDBMS pertama adalah System R, yang dikembangkan oleh IBM, dan INGRES (Interactive Graphics Retrieval System) yang dikembangkan oleh University of California di Berkeley. Keduanya pada awal 1970an.

Setelah keunggulan Relational Database banyak dikenal, berbagai perusahaan mulai berlalih dari hierarchical dan network database model ke relational database model. Pada tahun 1980an, Oracle RDBMS lahir, dan diikuti oleh pesaingnya saat itu, IBM DB2 RDBMS.

Jika pada tahun 1980an RDBMS hanya dapat digunakan dalam sistem mainframe perusahaan besar, namun saat ini dengan semakin majunya perkembangan teknologi di sisi hardware, PC-based RDBMS sudah banyak tersedia. MySQL RDBMS dapat diinstall di komputer/laptop biasa.

### 3. Client-Server RDBMS Arsitektur
Kebutuhan akan database yang dapat diakses bersama-sama oleh banyak pengguna mulai muncul di sekitar awal 1990an. Sebuah database terpusat, namun dapat diakses dari tiap komputer yang berjauhan, membuat banyak RDBMS dikembangkan dengan arsitektur Client-Server.

Dalam arsitektur Client-Server, sebuah komputer bertindak sebagai Database Server pusat. Server inilah yang akan melayani segala permintaan dari komputer (Client) yang membutuhkan akses ke database. Namun fisik database itu sendiri juga tidak harus di dalam Server, bisa saja berada di tempat lain, namun terhubung ke Database Server untuk memprosesnya.

MySQL juga menggunakan arsitektur Client-Server. Namun nantinya dalam tutorial ini, kita akan menjalankan aplikasi server dan client di komputer yang sama. Namun pada dasarnya, jika kita menjalankan MySQL Server di komputer, setiap komputer yang terhubung kedalam jaringan dapat mengaksesnya dengan menggunakan MySQL Client. Lebih lanjut tentang hal ini akan kita pelajari dalam tutorial selanjutnya.

### 4. Setelah Relational Database Model : Object-Oriented Database Model
Walaupun RDBMS sudah populer, dan digunakan pada hampir semua keperluan seperti bisnis, inventory, bank, dll, namun untuk kasus-kasus tertentu, Relational Database Model dianggap masih kurang mendukung, khususnya untuk aplikasi baru seperti sistem informasi geografis, dan multimedia. Sehingga mulailah dikembangkan berbagai model database lainnya, seperti Object-Oriented Database dan Object-Relational Database.

Konsep Database Objek Model ini berasal dari dunia programming: OOP (Object Oriented Programming), dimana setiap data dikaitkan dengan objek dari data tersebut. ODBMS (Object Database Management System) juga sudah banyak beredar, seperti Versant ODBMS oleh Versant Corporation, UniData dari IBM, dan VelocityDB.

Namun konsep Object Oriented Database ini belum terlalu populer digunakan, dan mungkin saja nantinya hanya sebagai pelengkap dari relational database, yang untuk kasus per kasus memerlukan sistem database khusus.

Demikian pembahasan singkat kita tentang pengertian database, database model dan perkembangan RDBMS. Dalam tutorial selanjutnya, kita akan bahas lebih mendalam konsep Teori Relational Database, sebelum mempraktekkannya dengan MySQL.

Sumber :

http://en.wikipedia.org/wiki/Database
http://en.wikipedia.org/wiki/Database_model
Michael J. Hernandez : Database Design for Mere Mortals, Addison Wesley, 2003
