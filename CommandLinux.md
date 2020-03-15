# Perintah Dasar Dalam Linux

Tidak Semua Perintah Dasar Linux Sama. Linux sendiri ada beberapa turunan atau varian yang mempunyai perintah dasar yang berbeda – beda. Sebagai contoh, untuk menangani masalah package manager Ubuntu menggunakan perintah “<b>apt</b>”, Fedora menggunakan “<b>yum</b>”, sedangkan Arch menggunakan “<b>pacman</b>”.

Secara umum semua perintah tersebut kegunaannya hampir sama, yaitu untuk mengelola paket yang ada di Linux.

Jadi sebagai catatan, pada kesempatan ini saya akan mencoba menjelaskan secara umum mengenai perintah dasar linux yang bisa berjalan di hampir semua varian Linux.

<h3>List Perintah Dasar Linux Yang Wajib Diketahui</h3>
<br>
1. <b>man (perintah)</b><br>
	Melihat kegunaan dari perintah (melihat buku manual dari sebuah program). Contohnya seperti `$ man apt` akan menampilkan manual penggunaan dari program `apt`.
2. <b>(perintah) -help</b><br>
	Hampir sama kegunaannya dengan `man`, akan tetapi hasil yang dimunculkan lebih ringkas daripada menggunakan perintah `man`.
3. <b>sudo</b><br>
	Menjalankan program sebagai user <i>root</i> atau <i>super user</i>.
4. <b>ls</b><br>
	Melihat daftar file & folder yang ada direktori pada saat itu, contohnya `$ ls /var/lib` digunakan untuk melihat apa saja yang ada pada folder `lib`.
5. <b>cd</b><br>
	Masuk ke direktori yang diinginkan, contohnya seperti `$ cd /home/` untuk menjadikan folder home sebagai direktori pada saat itu.
6. <b>mkdir (nama folder)</b><br>
	Membuat folder pada direktori kerja pada saat itu.
7. <b>pwd</b><br>
	Melihat direktori kerja yang pada saat itu aktif. Contoh hasilnya `/home/niagahoster`
8. <b>vim</b><br>
	Membuka text editor Vim untuk mengedit teks.
9. <b>cp (asal) (tujuan)</b><br>
	Menyalin file dan folder, bisa ke folder itu juga atau ke folder yang lain. Seperti `$ cp /home/test.php /var/www/html` akan memindahkan file `test.php` ke folder `html`. Sedangkan jika menyalin folder harus menggunakan opsi `-r`.
10. <b>mv (asal) (tujuan)</b><br>
	Memindahkan file dan folder, bisa ke folder itu juga atau ke folder yang lain. Seperti `$ cp /home/test.php /var/www/html` digunakan untuk memindahkan file `test.php` ke folder `html`.
11. <b>rm (file)</b><br>
	Menghapus file, bisa juga untuk menghapus folder pada direktori tertentu.
12. <b>find (nama file)</b><br>
	Mencari file dalam direktori hirarki. Contoh penggunaannya `$ find -name niagahoster.txt`
13. <b>history</b><br>
	Perintah dasar linux ini digunakan untuk melihat riwayat perintah yang sudah pernah digunakan sebelumnya. Jika ingin mencari perintah tertentu bisa menggunakan `$ history | grep` apt untuk mencari nama perintah yang sudah pernah diketikan dan mengandung potongan kata `apt`.
14. <b>cat</b><br>
	Melihat isi dari sebuah file, bisa juga untuk menggabungkan isi dari dua buah file. Contohnya `$ cat niagahoster1.txt niagahoster2.txt`.
15. <b>echo</b><br>
	Perintah ini digunakan untuk menampilkan satu baris teks. Bisa juga untuk menuliskan sebuah teks kedalam file, contohnya seperti berikut `$ echo “Teks” >> niagahoster.txt`. Perintah tersebut akan menuliskan `Teks` ke dalam file `niagahoster.txt`, jika file tersebut belum ada maka otomatis akan dibuat.
16. <b>grep</b><br>
	Menampilkan baris yang mengandung kata yang sama sesuai dengan pattern, contohnya seperti `$ grep -i source niagahoster.txt` maka akan memunculkan baris yang mengandung kata `source` pada `niagahoster.txt`.
17. <b>wc</b><br>
	Menampilkan baris baru, kata, dan bite pada sebuah file.
18.	<b>sort</b><br>
	Mengurutkan hasil dari pembacaan isi file.
19.	<b>chmod</b><br>
	Mengganti hak akses pada sebuah file. Contohnya jika ingin menggani hak akses `niagahoster.txt` menjadi 644 menggunakan baris perintah `$ chmod 644 niagahoster.txt`.
20.	<b>chown</b><br>
	Mengganti pemilik dan group dari sebuah file. Contohnya jika ingin mengubah kepemilikan `niagahoster.txt` menjadi `niaga` bisa menggunakan perintah `$ chown niaga:niaga niagahoster.txt`. Kata `niaga` di depan merujuk pada user sedangkan `niaga` di belakang merujuk pada nama group.
21.	<b>su</b><br>
	Mengganti user ID, contohnya `$ su <nama user>` atau menjadikan user pada saat itu menjadi super user.
22.	<b>passwd</b><br>
	Perintah ini digunakan untuk mengganti password dari user. Mengetikan `$ sudo passwd` mengganti password user pada saat itu, sedangkan `$ sudo passwd niagahoster` digunakan untuk mengganti password user `niagahoster`.
23.	<b>who</b><br>
	Perintah dasar linux ini digunakan untuk menampilkan user pada saat ini dipakai.
24.	<b>ps</b><br>
	Menampilkan snapshot  process yang sedang berjalan.
25.	<b>kill</b><br>
	Menghentikan program yang berjalan dengan menggunakan signal. Biasanya perintah ini ditambahkan opsi “-9” pada saat mengeksekusi. Contohnya seperti `$ sudo kill -9 373`, 373 adalah PID dari proses yang sedang berjalan.
26.	<b>tar</b><br>
	Ini merupakan program pengarsipan atau untuk mengumpulkan beberapa file menjadi satu file, dengan ekstensi `namafile.tar`. Perintah ini juga menggunakan beberapa opsi, sebagai contoh, opsi `c` untuk membuat arsip, opsi `v` untuk operasi verbose, sedangkan `f` untuk menentukan nama file.
27.	<b>zip</b><br>
	Alat kompresi file menjadi ,zip”, hampir sama penggunaannya dengan tar.
28.	<b>unzip</b><br>
	Mengekstrak/membongkar file `.zip`.
29.	<b>ssh</b><br>
	Mengakses komputer/server dari jarak jauh. Contoh perintah yang bisa digunakan seperti `$ ssh <namauser>@<ip>`.
30.	<b>scp</b><br>
	Menyalin file dari host lain yang terhubung dalam satu jaringan. Contohnya `$ scp <file> <user>@<ip>:<folder tujuan>`
31.	<b>fdisk</b><br>
	Menampilkan list partisi pada perangkat, biasanya menggunakan opsi `-l`, contohnya `$ sudo fdisk -l`
32.	<b>mount</b><br>
	Melampirkan sebuah filesystem kedalam satu folder besar. Sehingga tidak perlu melakukan akses langsung ke filesystem. Sebagai contoh menggunakan `$ sudo mount /dev/sda2 /mnt`. Perintah ini akan membuat isi partisi `/dev/sda2` bisa diakses melalui `/mnt`.
33.	<b>umount</b><br>
	Mengunlock perintah mount, contohnya `$ umount /mnt` digunakan untuk memutuskan perintah mount pada folder `/mnt`.
34.	<b>du</b><br>
	Menampilkan ukuran file secara rekursif.
35.	<b>df</b><br>
	Menampilkan penggunaan ruang disk pada filesystem.
36.	<b>quota</b><br>
	Menampilkan ruang disk dan batasannya.
37.	<b>reboot</b><br>
	Menjalankan perintah `restart`.
38.	<b>poweroff</b><br>
	Menjalankan perintah `shutdown`.
39.	<b>gedit</b><br>
	Membuka Text Editor untuk mengedit teks file.
40.	<b>kate</b><br>
	Program yang digunakan sebagai file editor pada KDE, beberapa sistem operasi harus melakukan instalasi terlebih dahulu. Fungsinya hampir sama seperti Gedit.
41.	<b>bg</b><br>
	Membuat proses foreground untuk berjalan di background.
42.	<b>fg (id program)</b><br>
	Membuat background proses menjadi foreground proses.
43.	<b>jobs (id program)</b><br>
	Menampilkan nama dan ID dari background jobs.
44.	<b>sed</b><br>
	Memfilter teks pada sebuah file dan menggantinya dengan teks yang baru. Contoh penggunaannya sed `‘s/niaga/hoster/g’ niagahoster.txt`
45.	<b>awk</b><br>
	Perintah ini digunakan untuk memindah teks dan memproses bahasa.
46.	<b>locate</b><br>
	Digunakan untuk menemukan atau mencari file.
47.	<b>ifconfig</b><br>
	Melihat IP yang sedang terkoneksi dan network device apa saja yang tersedia.
48.	<b>date</b><br>
	Menampilkan tanggal hari ini.
49.	<b>nano</b><br>
	Perintah digunakan sebagai text editor yang tidak perlu membuka jendela baru. Hampir sama dengan Vi namun lebih manusiawi.
50.	<b>top</b><br>
	Melihat semua proses yang sedang berjalan, diurutkan dari proses yang paling besar. Fungsinya hampir sama seperti system monitor.
51.	<b>clear</b><br>
	Membersihkan jendela terminal. Jadi isi jendela terminal akan kosong, namun jika di scroll keatas maka perintah yang sebelumnya dijalankan masih bisa terlihat.
52.	<b>dpkg -i (namapackage).deb</b><br>
	Berguna untuk melakukan instalasi paket dengan ekstensi `.deb`. Terkadang bisa juga menggunakan program `gdebi`, tetapi harus install.
53.	<b>uname</b><br>
	Menampilkan versi kernel yang dipakai, tanggal instalasi, dan jenis arsitektur sistem operasi.
54.	<b>* </b><br>
	Ini adalah sebuah tanda yang digunakan untuk mendeskripsikan satu string yang digunakan untuk memberikan deskripsi singkat dari satu elemen.