##Pengertian Sistem File (File System)

Sistem file (file system) atau sistem berkas merupakan struktur logika yang digunakan untuk mengendalikan akses terhadap data yang ada pada disk. Dengan kata lain, sistem file merupakan database khusus untuk penyimpanan, pengelolaan, manipulasi dan pengambilan data, agar mudah ditemukan dan diakses.
Hubungan antara sistem operasi dengan sistem file adalah sistem file (file system) merupakan interface yang menghubungkan sistem operasi dengan disk. Ketika program menginginkan pembacaan dari hard disk atau media penyimpanan lainnya, sistem operasi akan meminta sistem file untuk mencari lokasi dari file yang diinginkan. Setelah file ditemukan, sistem file (file system) akan membuka dan membaca file tersebut, kemudian mengirimkan informasinya kepada sistem operasi dan akhirnya bisa dibaca oleh pengguna.

####Sistem File Linux

Sistem operasi Linux mendukung banyak File System yang berbeda, tapi pilihan yang umum digunakan adalah keluarga Ext* (Ext2, Ext3 dan Ext4) dan ReiserFS. Berikut sistem file yang umumnya digunakan pada sistem operasi Linux:
<center><img src="img/systemfile1.png" width="500" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
- `Ext2 (2nd Extended)`
Ext2 merupakan jenis sistem file Linux paling tua yang masih ada. Sistem file ini pertama kali dikenalkan pada Januari 1993. File system ini ditulis oleh Rémy Card, Theodore T. dan Stephen Tweedie. File system ini merupakan penulisan ulang besar-besaran dari Extended file system. Ext2 adalah sistem file yang paling ampuh di Linux dan menjadi dasar dari segala distribusi linux.
Pada sistem file Ext2, file data disimpan sebagai data blok. Data blok ini mempunyai panjang yang sama dan meskipun panjangnya bervariasi di antara sistem file Ext2, besar blok tersebut ditentukan pada saat sistem file dibuat dengan mk2fs. Jika besar blok adalah 1024 bytes, maka file dengan besar 1025 bytes akan memakai 2 blok. Ini berarti kita membuang setengah blok per file.
Sistem file Ext2 menyimpan data secara hirarki standar yang banyak digunakan oleh sistem operasi. Data tersimpan di dalam file, file tersimpan di dalam direktori. Sebuah direktori bisa mencakup file dan direktori lagi di dalamnya yang disebut sub direktori.
Ext2 mendefinisikan topologi sistem file dengan memberikan arti bahwa setiap file pada sistem diasosiasiakan dengan struktur data inode. Sebuah inode menunjukkan blok mana dalam suatu file tentang hak akses setiap file, waktu modifikasi file, dan tipe file. Setiap file dalam sistem file Ext2 terdiri dari inode tunggal dan setiap inode mempunyai nomor identifikasi yang unik. Inode-inode file sistem disimpan dalam tabel inode. Direktori dalam sistem file Ext2 adalah file khusus yang mengandung pointer ke inode masing-masing isi direktori tersebut.
Gufron Rajo Kaciak


####Struktur Sistem File Ext2

1. Inode dalam Ext2
Inode adalah kerangka dasar yang membangun Ext2. Inode dari setiap kumpulan blok disimpan dalam tabel inode bersama dengan peta bit yang menyebabkan sistem dapat mengetahui inode mana yang telah teralokasi dana inode mana yang belum. Inode juga dapat menunjuk pada device khusus dan dapat menangani program sehingga program dapat mengakses ke device. Semua file device di dalam drektori /dev dapat membantu program mengakses device.

2. Superblok dalam Ext2
Superblok mengandung informasi tentang ukuran dasar dan bentuk file sistem. Informasi di dalamnya memungkinkan file system manager untuk menggunakan dan merawat sistem file. Biasanya, hanya superblok di blok group 0 saat file sistem di-mount tetapi setiap blok grup mengandung duplikatnya untuk menjaga jika file sistem menjadi rusak. Informasi yang dikandung adalah:
Magic Number, meyakinkan software bahwa ini adalah superblok dari sistem file Ext2.
Revision Level, menunjukkan revisi mayor dan minor dari sistem file.
Mount Count dan Maximum Mount Count, menunjukkan pada sistem jika harus dilakukan pengecekan dan maksimum mount yang diijikan sebelum e2fsck dijalankan.
Blocks per Size, besar blok dalam file sistem, contohnya 1024 bytes.
Blocks per Group, banyaknya blok per grup.
Block Group Number, nomor blok grup yang mengadung copy dari superblok.
Free Blocks, banyaknya blok yang kosong dalam file sistem.
Free Inode, banyak inode kosong dalam file sistem.
First Inode, nomor inode dalam inode pertama dalam file sistem, inode pertama dalam Ext2 root file sistem adalah direktori "/".

- `Ext3 (3rd Extended)`

Ext3 adalah peningkatan dari sistem file Ext2. Peningkatan ini memiliki beberapa keuntungan, diantaranya:
Journaling,
dengan menggunakan journaling, maka waktu recovery pada shutdown mendadak tidak akan selama pada Ext2. Namun ini menjadi kekurangan dari Ext3, karena dengan adanya fitur journaling, maka membutuhkan memori yang lebih dan memperlambat operasi I/O (Input/Output).
Integritas data,
Ext3 menjamin adanya integritas data setelah terjadi kerusakan atau unclean shut down. Ext3 memungkinkan kita memilih jenis dan tipe proteksi dari data.
Kecepatan,
daripada menulis data lebih dari sekali, Ext3 mempunyai throughput yang lebih besar daripada Ext2 karena Ext3 memaksimalkan pergerakan head hard disk. Kita bisa memilih tiga jurnal mode untuk memaksimalkan kecepatan, tetapi integritas data tidak terjamin.
Mudah dilakukan migrasi,
kita dapat berpindah dari sistem file Ext2 ke sistem file Ext3 tanpa melakukan format ulang.

- `Ext4 (4th Extended)`

Ext4 merupakan peningkatan dari sistem file Ext3. Ext4 dirilis secara lengkap dan stabil mulai dari kernel 2.6.28. Keuntungan menggunakan Ext4 adalah mempunyai pengalamatan 48-bit blok yang artinya dia akan mempunyai 1 EiB = 1.048.576 TB. Ukuran maksimum sistem file 16 TB.

- `JFS (Journalis File System)`

JFS atau dikenal juga dengan nama IBM Journal File System merupakan sistem file pertama yang menawarkan journaling. JFS sudah bertahun-tahun digunakan dalam IBM AIX® OS sebelum digunakan ke GNU/Linux. JFS saat ini menggunakan sumber daya CPU paling sedikit dibandingkan sistem file GNU/Linux lainnya. JFS sangat cepat diformat, mounting dan fsck, serta memiliki kinerja sangat baik, terutama berkaitan dengan deadline I/O scheduler. Walaupun begitu, dukungan terhadap JFS tidak seluas sistem file Ext atau Reiser FS.

- `Reiser FS`

Sistem file Reiser dibuat berdasarkan balance tree yang cepat dan unggul dalam hal kinerja, dengan algoritma yang lebih rumit. Sistem file Reiser juga memiliki jurnal yang cepat dan ciri-cirinya mirip sistem file Ext3. Sistem file Reiser lebih efisien dalam pemanfaatan ruang disk, dimana dapat menghemat disk sampai dengan 6 persen. Contohnya jika kita menulis file 100 bytes, hanya ditempatkan dalam satu blok sementara sistem file lain menempatkannya dalam 100 blok. Reiser file system tidak memiliki pengalokasian yang tetap untuk inode.