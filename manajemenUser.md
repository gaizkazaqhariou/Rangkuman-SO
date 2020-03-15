####Manajemen User
Hampir semua sistem operasi baru saat ini sudah dikembangkan dengan konsep multiuser dan multitasking, sehingga merupakan hal yang umum apabila dalam setiap komputer akan ada mekanisme identifikasi setiap orang yang akan menggunakannya. Sistem Debian juga mendukung sistem multiuser ini, dimana dalam satu waktu dapat lebih dari satu user yang mengakses sistem ini.

Terkait dengan lingkungan multiuser tersebut, pada materi kali ini akan dibahas berbagai teknik pengelolaan yang berkaitan dengan user. Pengelolaan disini meliputi:

####Pembuatan user baru
Perubahan data user
Penghapusan user
Pada sistem Linux user didefinisikan dengan menggunakan nama user (username) ataupun ID user (UID). UID dinyatakan dalam bentuk numerik dan nilainya dapat ditentukan otomatis oleh sistem saat user pertama kali didaftarkan atau dapat juga oleh user sendiri.

Berbeda dengan username, merupakan data dalam format alfanumerik, yang namanya ditentukan sendiri oleh user. Pada sistem Linux, setiap aplikasi diperbolehkan memilih salah satu dari dua data ini untuk mengenali user yang menggunakan aplikasinya. Namun, dari sisi user cenderung lebih mudah mengingat username dibandingkan UID, karena dapat dibuat mewakili nama sebenarnya dari user.

Pembuatan User Baru
Perintah berikut dapat digunakan untuk membuat user baru. Agar dapat berjalan perintah ini harus dijalankan dengan menggunakan user root di terminal.

`adduser  username`

Selain perintah adduser ada juga perintah useradd yang memiliki fungsi yang sama. Perintah diatas selain dapat dijalankan di Debian juga dapat berlaku untuk sistem Linux lainnya. Parameter-parameter pendukung lainnya untuk perintah ini dapat dilihat dengan perintah man adduser atau adduser –help.

Selain penentuan username ada juga beberapa data lainnya yang perlu diberikan, sebagai berikut.

* Password (wajib)
* Nama lengkap (tidak wajib)
* Nomor ruang (tidak wajib)
* Telepon kantor (tidak wajib)
* Telepon rumah (tidak wajib)
* Lainnya (tidak wajib)

Setiap user di sistem Linux diwajibkan untuk memiliki password sebagai pengamanan awal. Pengamanan awal ini diperlukan apabila ada data pribadi atau sensitif yang akan disimpan pada komputer karena masih ada hal lain yang perlu dilakukan untuk mengamankan data. Berikut ini merupakan contoh pembuatannya.

<center><img src="img/manaUser1.png" width="500" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>

Perintah berikut dapat digunakan untuk menguji apakah user tersebut telah berhasil dibuat atau tidak.

`su  –  username
whoami
pwd`

Perintah pertama berguna untuk login menggunakan user lain, sedangkan yang kedua untuk mengetahui siapa user yang login saat ini dan yang terakhir untuk mengetahui lokasi user saat ini. Apabila sesuai maka perintah pwd akan menampilkan lokasi home untuk user terpilih. Contohnya diberikan pada gambar berikut.

<center><img src="img/manaUser2.png" width="500" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>

####Perubahan Data User
Terkait dengan perubahan data user ini ada sejumlah perintah terkait yang dapat digunakan

chfn  username

Penggantian data pribadi user seperti nama lengkap, ruangan, telp. kantor, telp. rumah, dan lainnya. Apabila tidak ada perubahan yang dilakukan cukup tekan enter pada setiap entri.

`passwd  username`

Penggantian password user.

####Penghapusan User
Ini merupakan operasi yang dapat berefek cukup besar baik pada user ataupun sistem, karena dapat menyebabkan kehilangan data ataupun menyebabkan sistem tidak dapat berjalan sebagaimana mestinya. Oleh karena itu, perlu perhatian khusus saat akan melakukan operasi ini. Apabila akan menghapus suatu user dari sistem pastikan bahwa file-file penting milik user tersebut sudah dibackup dan pastikan juga tidak ada proses di sistem yang memerlukan user tersebut. Perintah penghapusan user diberikan sebagai berikut.

`deluser  username`
atau
`deluser  –remove-home  username`
atau
`deluser  –remove-home  –backup  username`

Pada perintah pertama, penghapusan akan menyebabkan hanya data user tersebut yang akan dihapus dari sistem. Apabila menggunakan perintah yang kedua, penghapusan akan menyebabkan semua file yang tersimpan pada direktori home dari user tersebut akan terhapus. Perintah terakhir ini mungkin lebih aman karena sebelum menghapus semua isi dari direktori home user tersebut, ada backup yang dibuat. Backup-nya dinyatakan dalam file terkompresi (`*.tar.bz2`). Contoh penerapannya ditunjukkan sebagai berikut.

<center><img src="img/manaUser3.png" width="500" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>

Selain menggunakan deluser untuk menghapus user juga dapat menggunakan perintah userdel. Perintah userdel memiliki fungsi yang sama hanya memiliki parameter yang berbeda dari deluser.

Semua data user yang dioleh dalam perintah-perintah diatas oleh sistem Linux tersimpan pada file /etc/passwd dan /etc/shadow. Pengubahan dapat juga dilakukan langsung melalui file-file ini. Namun, harap berhati-hari karena semua user yang ada di sistem juga disimpan pada file yang sama. Apabila tidak, akan dapat berdampak pada sistem.

Selain melalui CLI ada juga aplikasi GUI untuk melakukan manajemen ini, yakni melalui aplikasi User Accounts. Aplikasi ini dapat diakses di Debian melalui menu Applications > System Tools > Preferences > System Settings > System: User Accounts.

<center><img src="img/manaUser4.png" width="500" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>

Pada aplikasi User Accounts tombol Unlock perlu diklik dahulu agar dapat menambahkan, memodifikasi ataupun menghapus user. Setelah itu akan muncul window baru untuk memasukkan password root.

####Manajemen Group
Ada banyak file yang dihasilkan di sistem, baik yang dibawa oleh sistem Linux sendiri ataupun file dari user. Akses ke setiap file tersebut perlu adanya pembatasan (pengelompokkan), sehingga dapat menjamin kinerja sistem tetap baik dan data-data sistem/user tetap aman. Pengelompokan hak akses ini oleh Linux diterapkan dengan membuat grup akses. Bukan hanya user, setiap aplikasi server dapat memiliki grupnya sendiri-sendiri. Selain untuk pembatasan akses, grup juga dapat digunakan untuk melakukan klasifikasi user-user yang ada di sistem.

Manajemen grup di Linux dapat meliputi kegiatan, seperti penambahan grup baru dan penghapusan grup.

####Penambahan Group Baru
Perintah berikut dapat digunakan untuk menambahkan grup baru di Linux:

`groupadd  namagroup`

Perintah diatas hanya dapat dijalankan oleh user root. Sebagai contoh pembuatan grup ditunjukkan pada gambar berikut.

Apabila berhasil dijalankan seperti contoh diatas, maka pada file /etc/group akan ada tambahan baris yang menyatakan grup baru yang telah dibuat. Hal yang sama juga berlaku untuk grup di Linux seperti layaknya user, dimana setiap grup akan memiliki nama dan juga ID grup (GID).

####Penghapusan Group
Operasi ini dapat dilakukan dengan menggunakan perintah berikut.

`groupdel  namagrup`

Grup yang telah dihasillkan akan dihapus dari sistem, termasuk juga dari file `/etc/group`.