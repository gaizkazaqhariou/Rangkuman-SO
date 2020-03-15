# Operasi File dan Struktur Direktori

###1. ORGANISASI FILE
Sistem file pada Linux menyerupai pepohonan (tree), yaitu dimulai dari root, kemudian direktory dan sub direktory. Sistem file pada Linux diatur secara hierarkikal, yaitu dimulai dari root dengan symbol “/” seperti Gambar 3.1
Kita dapat menciptakan File dan Direktori mulai dari root ke bawah. Direktori adalah file khusus, yang berisi nama file dan INODE (Pointer yang menunjuk ke data / isi file tersebut). Secara logika, direktori dapat berisi File dan Direktori lagi (disebut juga Subdirektori).
<center><img src="2.jpg" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>

###2. DIREKTORI STANDAR

Setelah proses instalasi, Linux menciptakan system file yang baku, terdiri atas direktory sebagai berikut : 
<center><img src="1.jpg" height="600" width="450" style="box-shadow: 0px 0px 15px -2px gray"></center>

#####Direktori /etc
Berisi file yang berhubungan dengan administrasi system, maintanance script, konfigurasi, security dll. Hanya superuser yang boleh memodifikasi file yang berada di direktori ini. Subdirektori yang sering diakses pada direktori /etc antaran lain :
* Httpd, apache web server.
* Ppp, point to point protocol untuk koneksi ke internet.
* rc.d atau init.d , inisialisasi (startup) dan terminasi (shutdown) proses di Linux dengan konsep runlevel.
* cron.d rincian proses yang dieksekusi dengan menggunakan jadwal ( time dependent process)
* FILES, file security dan konfigurasi meliputi : passwd, hosts, shadow, ftpaccess, inetd.conf, lilo.conf, motd, printcap, profile, resolv.conf, sendmail.cf, syslog.conf, dhcp.conf, smb.conf, fstab.

#####Direktori /dev
Konsep Unix dan Linux adalah memperlakukan peralatan hardware sama seperti penanganan file. Setiap alat mempunyai nama file yang disimpan pada direktori /dev.
<center><img src="3.jpg" height="250" width="450" style="box-shadow: 0px 0px 15px -2px gray"></center>

#####Direktori /proc
Direktori /proc adalah direktori yang dibuat diatas RAM (Random Access Memory) dengan system file yang diatur oleh kernel. /proc berisi nomor proses dari system dan nama driver yang aktif di system. Semua direktori berukuran 0 (kosong) kecuali file kcore dan self. Setiap nomor yang ada pada direktori tsb merepresentasikan PID (proses ID).

###3. TIPE FILE

Pada Linux terdapat 6 buah tipe file yaitu :
* Ordinary file
* Direktori
* Block Device ( Peralatan I/O )
Merupakan representasi dari peralatan hardware yang menggunakan transmisi data per block (misalnya 1 KB block), seperti disk, floppy, tape.
* Character Device (Peralatan I/O)
Merupakan representasi dari peralatan hardware yang menggunakan transmisi data karakter per karakter, seperti terminal, modem, plotter dll.
* Named Pipe (FIFO)
File yang digunakan secara intern oleh system operasi untuk komunikasi antar proses.
* Link File

###4. PROPERTI FILE
File mempunyai beberapa atribut, antara lain :
* Tipe file : menentukan tipe dari file, yaitu :
<br>
<img src="4.jpg" height="150" width="250" style="box-shadow: 0px 0px 15px -2px gray">
<br>
* Ijin akses : menentukan hak user terhadap file ini.
* Jumlah link : jumlah link untuk file ini.
* Pemilik (owner) : menentukan siapa pemilik file ini
* Group : menentukan grup yang memiliki file ini
* Jumlah karakter : menentukan ukuran file dalam byte
* Waktu Pembuatan : menentukan kapan file terakhir dimodifikasi
* Nama File : menentukan nama file yang dimaksud

Contoh :
`-rw-rw-r-- 1 bin auth 1639 oct 16 13:00 /etc/passwd`
Penjelasan :
	* `-` : merupakan tipe
	* `rw-rw-r--` : merupakan ijin akses
	* `1` : jumlah link
	* `bin` : pemilik
	* `auth` : group
	* `1639` : jumlah karakter
	* `Oct 16 13:00` : waktu
	* `/etc/passwd` : Nama file


###5. NAMA FILE
Nama file maksimal terdiri dari 255 karakter berupa alfanumerik dan beberapa karakter spesial yaitu garis bawah, titik, koma dan lainnya kecuali spasi dan karakter-karakter berikut :
`&` , `,`, `|` , `?` , `’` , `(` , `)` , `[` , `]` , `$` , `<` , `>` , `{` , `}` , `^` , `#` , `\` , `/`.
Linux membedakan huruf kecil dengan huruf besar (case sensitif), 
Contoh nama file yang benar :
* Abcde5434
* 3
* Prog.txt
* PROG.txt
* Prog.txt, old
* report_1-1, v2.0.1
* 5-01.web.html

###6. SIMBOLIC LINK
Link adalah teknik untuk memberikan lebih dari satu nama file dengan data yang sama. Bila file asli dihapus, maka data yang baru juga terhapus. Format dari Link : ln fileAsli fileDuplikat
File duplikat disebut hard link dimana kedua file akan muncul identik (link count=2) Bila fileAsli atau fileDuplikat diubah, maka perubahan akan terjadi pada file lainnya.
Simbolic link diperlukan bila file tersebut di `Link` dengan direktori /file yang berada pada partisi yang berbeda. Tipe file menjadi 1 (link) dan file tersebut menunjuk ke tempat asal. Format :
`ln –s /fullpath/fileAsli /FullPath/FileDuplikat`
Pilihan `–s` (shortcut) merupakan bentuk soft link, simbolic link dapat dilakukan pada file yang tidak ada, sedangkan pada hard link tidak dimungkinkan. Perbedaan lain, simbolic link dapat dibentuk melalui media disk atau partisi yang berbeda dengan soft link, tetapi pada hard link terbatas pada partisi disk yang sama.

###7. MELIHAT ISI FILE
Untuk melihat jenis file menggunakan format :
file filename(s)
isi file akan dilaporkan dengan deskripsi level tinggi seperti contoh berikut :
`# file myprog.c letter.txt webpage.html`
`myproc.c : C program text`
`letter.txt : ASCII text`
`webpage.html : HTML document text`

perintah ini dapat digunakan secara luas untuk file yang kadang membingungkan, misalnya antara kode C++ dan java.

###8. MENCARI FILE
Jika ingin melihat bagaimana pohon direktori dapat digunakan perintah
* Find
Format : find directory_name targetfile –print
Akan melihat file yang bernama targetfile (bisa berupa karakter wildcard)
* Which
Format : which command
Untuk mengetahui letak system utility
* Locate
Format : locate string
Akan mencari file pada semua direktori dengan lebih cepat dan ditampilkan dengan path yang penuh.

###9. MENCARI TEXT PADA FILE
Untuk mencari text pada file digunakan perintah grep (General Regular Expression Print) dengan format perintah : 
grep option pattern files
Grep akan mencari file yang bernama sesuai pattern yang diberikan dan akan menampilkan baris yang sesuai.

