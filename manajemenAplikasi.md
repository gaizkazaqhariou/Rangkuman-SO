##Manajemen Aplikasi Linux

Pada pembahasan kali ini anda akan mempelajari dan dapat mengerti konsep RPM, TAR dan GZIP. menggunakan RPM, menggunakan TAR dan GZIP untuk  instalasi software .

1.    MANAJEMEN PAKET SOFTWARE

Setiap system Linux mempunyai manajemen paket software, yang paling popular adalah RPM (RedHat Package Management). 

RPM mengatur instalasi paket software, maintenance/upgrade dan menghapus paketsoftware dari system, atau lebih dikenal dengan install dan uninstall (install / remove).

RPM menyimpan informasi tentang paket yang diinstalasi dalam sebuah database. Penghapusan paket berarti juga menghapus semua files dan direktori yang terdaftar pada database tersebut, lengkap dengan nama PATH (lokasi dimana file dan direktori tersebut berada). 

RPM menyimpan paket dalam bentuk file yang telah dikompres dan ditulis sebagai file degan ekstensi .rpm. 

2.    FUNGSI MANAJER PAKET SOFTWARE

Menghitung besar paketyang disesuaikan dengan kapasitas penyimpanan disk yang masih tersedia, apakah cukup atau tidak.
Memeriksa apakah ada library atau file- file lain yang dibutuhkan untuk software tersebut.
Menghindari konflik dengan software yang telah terpasang di system.
Proses instalasi tidak mengacaukan system (membuat system file menjadi terganggu / korup). 
Upgrade ke versi yang baru tanpa mengganggu konfigurasi yang sudah ada.
Verifikasi files dalam paket tersebut.
3.    PAKET SOFTWARE

Terdiri dari 2 jenis :
Paket binary (biner), terdiri atas kumpulan program executable. Paket ini berekstensi *.rpm.
Paket source, Berisi teks dari program yang kemudian dapat dikompilasi menjadi executable. Paket ini mempunyai ekstensi *.src.rpm.
4.    NAMA PAKET

Penamaan paket diatur dengan konven si sebagai berikut :
Nama
Versi
Release
Platform arsitektur (Intel, Alpha, Risc, …)
Linux

5.    RPM QUERY

RPM dengan opsi  –qmemberikan informasi tentang paket sebagai berikut :

`# rpm –q samba
samba –2.0.5 -1S
#`

Informasi tentang versi paket samba adalah versi 2.0.5. 
Beberapa sub - opsi dapat diberikan, antara lain :

i	menampilkan informasi yang lebih rinci
l	list (daftar) se mua file(s)
d	tampilkan hanya file dokumentasi saja
c	tampilkan hanya konfigurasi file
f	info tentang paket memiliki file apa saja
p	berfungsi pada paket yang belum diinstalasi
--scripts	menampilkan script untuk instalasi

6.    TAR

Tar singkatan dari Tape A Rchive. Tar mula- mula didesain untuk backup tape, tetapi digunakan untuk membuat file tar pada semua sistem file. tar membuat satu "tar nama  versi   release   platform file" (yang disebut dengan "tarball") pada beberapa file dan direktori. File tar tidak dikompresi, hanya sebuah file heap yang dibentuk bersama dalam satu kontainer.Sehingga file tar akan mempunyai jumlah byte yang sama dengan semua file individu yang dikombinasikan ditambah sedikit file ekstra. File tar dapat dikompresi dengan menggunakan gzip atau bzip2.
Contoh :

tar  –xvf example.tar  mengekstraksi isi dari  example.tar dan menunjukkan file yang akan diekstraksi
tar  –cf backup.tar /home/ftp/pub  membuat file tar bernama backup.tar  dari isi direktori home/ftp/pub
tar –tvf example.tar  menampilkan isi dari example.tar pada screen. 

7.    GZIP

Gzip merupakan format ZIP UNIX yang asli. Biasanya membentuk file tar terlebih dahulu dan kemudian mengkompresi dengan menggunakan gzip. File -file ini mempunyai ekstensi .tar.gz yang menunjukkan file tar yang di - zip dengan gzip. Selain itu juga terdapat file berekstensi .tgz. File ini merupakan file kompresi dengan gzip yang kompatibel dengan WinZip dan PkZip. Sehingga file zip pada UNIX dapat di unzip pada Windows.
Contoh :

Untuk kompresi file menggunakan gzip, eksekusi perintah berikut  : gzip filename.tar (dimana filename.tar adalah nama file yang dikompres).  Hasil dari operasi ini adalah file yang bernama filename.tar.gz.  Defaultnya, gzip akan menghapus file filename.tar
Untuk dekompresi file menggunakan gzip, eksekusi perintah beriku t : gzip   – d filename.tar.gz. Hasil dari operasi ini adalah file bernama filename.tar. Defaultnya, gzip akan menghapus file filename.tar.gz