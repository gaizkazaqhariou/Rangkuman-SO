##Manajemen Memori di Linux

####Manajemen Memori Fisik

Bagian ini menjelaskan bagaimana linux menangani memori dalam sistem. Memori manajemen merupakan salah satu bagian terpenting dalam sistem operasi. Karena adanya keterbatasan memori, diperlukan suatu strategi dalam menangani masalah ini. Jalan keluarnya adalah dengan menggunakan memori virtual. Dengan memori virtual, memori tampak lebih besar daripada ukuran yang sebenarnya.
Dengan memori virtual kita dapat:
1. Ruang alamat yang besar
Sistem operasi membuat memori terlihat lebih besar daripada ukuran memori sebenarnya. Memori virtual bisa beberapa kali lebih besar daripada memori fisiknya.
2. Pembagian memori fisik yang dil
Manajemen memori membuat pembagian yang adil dalam pengalokasian memori antara proses-proses.
3. Perlindungan
Memori manajemen menjamin setiap proses dalam sistem terlindung dari proses-proses lainnya. Dengan demikian, program yang crash tidak akan mempengaruhi proses lain dalam sistem tersebut.
4. Penggunaan memori virtual bersama
Memori virtual mengizinkan dua buah proses berbagi memori diantara keduanya, contohnya dalam shared	library. Kode library dapat berada di satu tempat, dan tidak dikopi pada dua program yang berbeda.

####Memori Virtual
<center><img src="img/memori1.png" width="500" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
gambar model mapping virtual to physical address

Memori fisik dan memori virtual dibagi menjadi bagian-bagian yang disebut page. Page ini memiliki ukuran yang sama besar. Tiap page ini punya nomor yang unik, yaitu Page Frame Number (PFN). Untuk setiap instruksi dalam program, CPU melakukan mapping dari alamat virtual ke memori fisik yang sebenarnya.

Penerjemahan alamat di antara virtual dan memori fisik dilakukan oleh CPU menggunakan tabel page untuk proses x dan proses y. Ini menunjukkan virtial PFN 0 dari proses x dimap ke memori fisik PFN 1. Setiap anggota tabel page mengandung informasi berikut ini:
1. Virtual PFN
2. PFN fisik
3. informasi akses page dari page tersebut

Untuk menerjemahkan alamat virtual ke alamat fisik, pertama-tama CPU harus menangani alamat virtual PFN dan offsetnya di virtual page. CPU mencari tabel page proses dan mancari anggota yang sesuai degan virtual PFN. Ini memberikan PFN fisik yang dicari. CPU kemudian mengambil PFN fisik dan mengalikannya dengan besar page untuk mendapat alamat basis page tersebut di dalam memori fisik. Terakhir, CPU menambahkan offset ke instruksi atau data yang dibutuhkan. Dengan cara ini, memori virtual dapat dimap ke page fisik dengan urutan yang teracak.

####Demand Paging

Cara untuk menghemat memori fisik adalah dengan hanya meload page virtual yang sedang digunakan oleh program yang sedang dieksekusi. Tehnik dimana hanya meload page virtual ke memori hanya ketika program dijalankan disebut demand paging.

Ketika proses mencoba mengakses alamat virtual yang tidak ada di dalam memori, CPU tidak dapat menemukan anggota tabel page. Contohnya, dalam gambar, tidak ada anggota tabel page untuk proses x untuk virtual PFN 2 dan jika proses x ingin membaca alamat dari virtual PFN 2, CPU tidak dapat menterjemahkan alamat ke alamat fisik. Saat ini CPU bergantung pada sistem operasi untuk menangani masalah ini. CPU menginformasikan kepada sistem operasi bahwa page fault telah terjadi, dan sistem operasi membuat proses menunggu selama sistem operasi menagani masalah ini.

CPU harus membawa page yang benar ke memori dari image di disk. Akses disk membutuhkan waktu yang sangat lama dan proses harus menunggu sampai page selesai diambil. Jika ada proses lain yang dapat dijalankan, maka sistem operai akan memilihnya untuk kemudian dijalankan. Page yang diambil kemudian dituliskan di dalam page fisik yang masih kosong dan anggota dari virtual PFN ditambahkan dalam tabel page proses. Proses kemudian dimulai lagi pada tempat dimana page fault terjadi. Saat ini terjadi pengaksesan memori virtual, CPU membuat penerjemahan dan kemudian proses dijalankan kembali.

Demand paging terjadi saat sistem sedang sibuk atau saat image pertama kali diload ke memori. Mekanisme ini berarti sebuah proses dapat mengeksekusi image dimana hanya sebagian dari image tersebut terdapat dalam memori fisik.

####Swaping

Jika memori fisik tiba-tiba habis dan proses ingin memindahkan sebuah page ke memori, sistem operasi harus memutuskan apa yang harus dilakukan. Sistem operasi harus adil dalam mambagi page fisik dalam sistem diantara proses yang ada, bisa juga sistem operasi menghapus satu atau lebih page dari memori untuk membuat ruang untuk page baru yang dibawa ke memori. Cara page virtual dipilih dari memori fisik berpengaruh pada efisiensi sistem.

Linux menggunakan tehnik page aging agar adil dalam memilih page yang akan dihapus dari sistem. Ini berarti setiap page memiliki usia sesuai dengan berapa sering page itu diakses. Semakin sering sebuah page diakses, semakin muda page tersebut. Page yang tua adalah kandidat untuk diswap.

####Pengaksesan memori virtual bersama

Memori virtual mempermudah proses untuk berbagi memori saat semua akses ke memori menggunakan tabel page. Proses yang akan berbagi memori virtual yang sama, page fisik yang sama direference oleh banyak proses. Tabel page untuk setiap proses mengandung anggota page table yang mempunyai PFN fisik yang sama.

####Efisiensi

Desainer dari CPU dan sistem operasi berusaha meningkatkan kinerja dari sistem. Disamping membuat prosesor, memori semakin cepat, jalan terbaik adalah manggunakan cache. Berikut ini adalah beberapa cache dalam manajemen memori di linux:
1. Page Cache
Digunakan untuk meningkatkan akses ke image dan data dalam disk. Saat dibaca dari disk, page dicache di page cache. Jika page ini tidak dibutuhkan lagi pada suatu saat, tetapi dibutuhkan lagi pada saat yang lain, page ini dapat segera diambil dari page cache.
2. Buffer Cache
Page mungkin mengandung buffer data yang sedang digunakan oleh kernel, device driver dan lain-lain. Buffer cache tampak seperti daftar buffer. Contohnya, device driver membutuhkan buffer 256 bytes, adalah lebih cepat untuk mengambil buffer dari buffer cache daripada mengalokasikan page fisik lalu kemudian memecahnya menjadi 256 bytes buffer-buffer.
3. Swap Cache
Hanya page yang telah ditulis ditempatkan dalam swap file. Selama page ini tidak mengalami perubahan setelah ditulis ke dalam swap file, maka saat berikutnya page di swap out tidak perlu menuliskan kembali jika page telah ada di swap file. Di sistem yang sering mengalami swap, ini dapat menghemat akses disk yang tidak perlu.


Salah satu implementasi yang umum dari hardware cache adalah di CPU, cache dari anggota tabel page. Dalam hal ini, CPU tidak secara langsung membaca tabel page, tetap mencache terjemahan page yang dibutuhkan.

####Load dan Eksekusi Program

1. Penempatan program dalam memori

Linux membuat tabel-tabel fungsi untuk loading program, memberikan kesempatan kepada setiap fungsi untuk meload file yang diberikan saat sistem call exec dijalankan. Pertama-tama file binari dari page ditempatkan pada memori virtual. Hanya pada saat program mencoba mengakses page yang telah diberikan terjadi page fault, maka page akan diload ke memori fisik.

2. Linking statis dan linking dinamis

* Linking statis:
librari-librari yang digunakan oleh program ditaruh secara langsung dalam file binari yang dapat dieksekusi. Kerugian dari linking statis adalah setiap program harus mengandung kopi library sistem yang umum.
* Linking dinamis:
hanya sekali meload librari sistem menuju memori. Linking dinamis lebih efisien dalam hal memori fisik dan ruang disk.