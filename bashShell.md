# Bekerja dengan Bash Sell
___

<center><img src="bash.png" height="150" width="400"></center>

#### Pengertian Shell

Shell adalah program (penterjemah perintah) yang menjembatani user dengan sistem operasi dalam hal ini kernel (inti sistem operasi), umumnya shell menyediakan prompt sebagai user interface, tempat dimana user mengetikkan perintah-perintah yang diinginkan baik berupa perintah internal shell (internal command), ataupun perintah eksekusi suatu file progam (eksternal command), selain itu shell memungkinkan user menyusun sekumpulan perintah pada sebuah atau beberapa file untuk dieksekusi sebagai program.

#### Macam-Macam Shell

Tidak seperti sistem operasi lain yang hanya menyediakan satu atau 2 shell, sistem operasi dari keluarga unix misalnya linux sampai saat ini dilengkapi oleh banyak shell dengan kumpulan perintah yang sangat banyak, sehingga memungkinkan pemakai memilih shell mana yang paling baik untuk membantu menyelesaikan pekerjaannya, atau dapat pula berpindah-pindah dari shell yang satu ke shell yang lain dengan mudah, beberapa shell yang ada di linux antara lain:

<li>Bourne shell(sh),</li> 
<li>C shell(csh),</li> 
<li>Korn shell(ksh),</li> 
<li>Bourne again shell(bash).</li> 
<br>
Masing - masing shell mempunyai kelebihan dan kekurangan yang mungkin lebih didasarkan pada kebutuhan pemakai yang makin hari makin meningkat, untuk dokumentasi ini shell yang digunakan adalah bash shell dari GNU, yang merupakan pengembangan dari Bourne shell dan mengambil beberapa feature (keistimewaan) dari C shell serta Korn shell, Bash shell merupakan shell yang cukup banyak digunakan pemakai linux karena kemudahan serta banyaknya fasilitas perintah yang disediakan.Versi bash shell 2.04

<center><img src="img/sell.png" height="50" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

<h4>Pemrograman Shell</h4> 

Yaitu menyusun atau mengelompokkan beberapa perintah shell (internal atupun eksternal command) menjadi kumpulan perintah yang melakukan tugas tertentu sesuai tujuan penyusunnya. Kelebihan shell di linux dibanding sistem operasi lain adalah bahwa shell di linux memungkinkan kita untuk menyusun serangkaian perintah seperti halnya bahasa pemrograman (interpreter language), melakukan proses I/O, menyeleksi kondisi, looping, membuat fungsi, dsb. adalah proses - proses yang umumnya dilakukan oleh suatu bahasa pemrograman, jadi dengan shell di linux kita dapat membuat program seperti halnya bahasa pemrograman, untuk pemrograman shell pemakai unix atau linux menyebutnya sebagai script shell.

<h4>Kebutuhan Dasar</h4> 

Sebelum mempelajari pemrograman Bash shell di linux sebaiknya anda telah mengetahui dan menggunakan perintah - perintah dasar shell baik itu internal command yang telah disediakan shell maupun eksternal command atau utility, seperti
<br>
<li>cd, pwd, times, alias, umask, exit, logout, fg, bg, ls, mkdir, rmdir, mv, cp, rm, clear, ... </li> 
<li>utilitas seperti cat, cut, paste, chmod, lpr,... </li> 
<li>redirection (cara mengirim output ke file atau menerima input dari file), menggunakan operator redirect >, >>, <, <<, Contohnya: </li> 
ls > data<br>
hasil ls dikirim ke file data, jika file belum ada akan dibuat tetapi jika sudah ada isinya akan ditimpa.<br>

ls >> data<br>
hampir sama, bedanya jika file sudah ada maka isinya akan ditambah di akhir file.<br>

cat < data<br>
file data dijadikan input oleh perintah cat<br>

<li> pipa (output suatu perintah menjadi input perintah lain), operatornya : `|`, Contoh: </li> 
ls -l | sort -s<br>
ouput perintah ls -l (long) menjadi input perintah sort -s (urutkan secara descending), mending pake ls -l -r saja :-)<br>

ls -l | sort -s | more<br>

cat <data | sort > databaru

<li>Wildcard dengan karakter *, ?, [ ], Contohnya: </li> 
ls i*<br>
tampilkan semua file yang dimulai dengan i<br>

ls i?i<br>
tampilkan file yang dimulai dengan i, kemudian sembarang karakter tunggal, dan diakhiri dengan i<br>

ls [ab]`*`<br>
tampilkan file yang dimulai dengan salah satu karakter a atau b

<h4>Simple Bash Script</h4> 

Langkah awal sebaiknya periksa dulu shell aktif anda, gunakan perintah ps (report process status)

<center><img src="img/1.png" height="50" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

bash adalah shell aktif di system saya, jika disystem anda berbeda misalnya csh atau ksh ubahlah dengan perintah change shell

<center><img src="img/2.png" height="50" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

atau dengan mengetikkan bash

<center><img src="img/3.png" height="50" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

sekarang coba anda ketikkan perintah dibawah ini pada prompt shell
<br>
`echo "Script shell pertamaku di linux"`

<center><img src="img/4.png" height="50" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

string yang diapit tanda kutip ganda (double quoted) akan ditampilkan pada layar anda, echo adalah statement (perintah) built-in bash yang berfungsi menampilkan informasi ke standard output yang defaultnya adalah layar. jika diinginkan mengulangi proses tersebut, anda akan mengetikkan kembali perintah tadi, tapi dengan fasilitas history cukup menggunakan tombol panah kita sudah dapat mengulangi perintah tersebut, bagaimana jika berupa kumpulan perintah yang cukup banyak, tentunya dengan fasilitas hirtory kita akan kerepotan juga mengulangi perintah yang diinginkan apalagi jika selang beberapa waktu mungkin perintah-perintah tadi sudah tertimpa oleh perintah lain karena history mempunyai kapasitas penyimpanan yang ditentukan. untuk itulah sebaiknya perintah-perintah tsb disimpan ke sebuah file yang dapat kita panggil kapanpun diinginkan.

coba ikuti langkah - langkah berikut:
<br>
<li>Masuk ke editor anda, apakah memakai vi,pico,emacs,dsb...</li> 
<li>Ketikkan perintah berikut</li> 

`#!/bin/bash`
<br>
`echo "Hello, apa khabar"`

<li>simpan dengan nama file tes</li> 
<li>ubah permission file tes menggunakan chmod</li> 

`[fajar@linux$]chmod 755 tes`

<li>jalankan</li> 

`[fajar@linux$]./tes`

kapan saja anda mau mengeksekusinya tinggal memanggil file tes tersebut, jika diinginkan mengeset direktory kerja anda sehingga terdaftar pada search path ketikkan perintah berikut

`PATH=$PATH:.`
<br>
<br>
setelah itu script diatas dapat dijalankan dengan cara
<br>
<br>
`[fajar@linux$]tes
Hello, apa khabar`
<br>
<br>
tanda #! pada /bin/bash dalam script tes adalah perintah yang diterjemahkan ke kernel linux untuk mengeksekusi path yang disertakan dalam hal ini program bash pada direktory /bin, sebenarnya tanpa mengikutkan baris tersebut anda tetap dapat mengeksekusi script bash, dengan catatan bash adalah shell aktif. atau dengan mengetikkan bash pada prompt shell.

`[fajar@linux$]bash tes`
<br>
<br>
tentunya cara ini kurang efisien, menyertakan path program bash diawal script kemudian merubah permission file sehingga dapat anda execusi merupakan cara yang paling efisien.

Sekarang coba kita membuat script shell yang menampilkan informasi berikut:

<li>Waktu system</li> 
<li>Info tentang anda</li> 
<li>umlah pemakai yang sedang login di system</li> 
<br>

<b>Contoh scriptnya:</b> 

<center><img src="img/5.png" height="200" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

sebelum dijalankan jangan lupa untuk merubah permission file myinfo sehingga dapat dieksekusi oleh anda

<center><img src="img/6.png" height="130" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

tentunya layout diatas akan disesuaikan dengan system yang anda gunakan statement echo dengan opsi -n akan membuat posisi kursor untuk tidak berpindah ke baris baru karena secara default statement echo akan mengakhiri proses pencetakan ke standar output dengan karakter baris baru (newline), anda boleh mencoba tanpa menggunakan opsi -n, dan lihat perbedaannya. opsi lain yang dapat digunakan adalah -e (enable), memungkinkan penggunaan backslash karakter atau karakter sekuen seperti pada bahasa C atau perl, misalkan :

`echo -e "\abunyikan bell"`
<br>
jika dijalankan akan mengeluarkan bunyi bell, informasi opsi pada statement echo dan backslash karakter selengkapnya dapat dilihat via man di prompt shell.
<br>
`[fajar@linux$]man echo`

#### Pemakaian Variabel

Secara sederhana variabel adalah pengenal (identifier) berupa satuan dasar penyimpanan yang isi atau nilainya sewaktu-waktu dapat berubah baik oleh eksekusi program (runtime program) ataupun proses lain yang dilakukan sistem operasi. dalam dokumentasi ini saya membagi variabel menjadi 3 kategori:

1. Environment Variable
2. Positional Parameter
3. User Defined Variable

###### 1. Environment Variable
atau variabel lingkungan yang digunakan khusus oleh shell atau system linux kita untuk proses kerja system seperti variabel PS1, PS2, HOME, PATH, USER, SHELL,dsb...jika digunakan akan berdampak pada system, misalkan variabel PS1 yang digunakan untuk mengeset prompt shell pertama yaitu prompt tempat anda mengetikkan perintah - perintah shell (defaultnya "\s-\v\$"), PS2 untuk prompt pelengkap perintah, prompt ini akan ditampilkan jika perintah yang dimasukkan dianggap belum lengkap oleh shell (defaultnya ">"). anda dapat mengeset PS1 dan PS2 seperti berikut.

simpan dahulu isi PS1 asli system anda, sehingga nanti dapat dengan mudah dikembalikan
<br>
`[fajar@linux$]PS1LAMA=$PS1`
<br>
sekarang masukkan string yang diinginkan pada variabel PS1
<br>
`[fajar@linux$]PS1="Hi ini Promptku!"
Hi ini Promptku!PS2="Lengkapi dong ? "`
<br>
maka prompt pertama dan kedua akan berubah, untuk mengembalikan PS1 anda ke prompt semula ketikkan perintah
<br>
`[fajar@linux$]PS1=$PS1LAMA`
<br>
Jika anda ingin mengkonfigurasi prompt shell, bash telah menyediakan beberapa backslash karakter diantaranya adalah:

<center><img src="img/7.png" height="200" width="400" style="box-shadow: 0px 0px 15px -2px gray"></center>

###### 2. Positional Parameter
atau parameter posisi yaitu variabel yang digunakan shell untuk menampung argumen yang diberikan terhadap shell baik berupa argumen waktu sebuah file dijalankan atau argumen yang dikirim ke subrutin. variabel yang dimaksud adalah 1,2,3,dst..lebih jelasnya lihat contoh script berikut :
<br>
`#!/bin/bash
argumen1
echo $1 adalah salah satu $2 populer di $3`
<br>
Hasilnya:
<br>
`[fajar@linux$]./argumen1 bash shell linux
bash adalah salah satu shell populer di linux`
<br>
ada 3 argumen yang disertakan pada script argumen1 yaitu bash, shell, linux, masing2 argumen akan disimpan pada variabel 1,2,3 sesuai posisinya. variabel spesial lain yang dapat digunakan diperlihatkan pada script berikut:
<br>
`#!/bin/bash
argumen2
clear
echo "Nama script anda : $0";
echo "Banyak argumen   : $#";
echo "Argumennya adalah: $*";`
<br>
<Hasilnya:
<br>
`[fajar@linux$]./argumen 1 2 3 empat
Nama script anda  : ./argumen
Banyak argumen    : 4
Argumennya adalah : 1 2 3 empat`
<br>

###### 3. User Defined Variable
atau variabel yang didefinisikan sendiri oleh pembuat script sesuai dengan kebutuhannya, beberapa hal yang perlu diperhatikan dalam mendefenisikan variabel adalah:

dimulai dengan huruf atau underscore
hindari pemakaian spesial karakter seperti `*,$,#,dll...`
bash bersifat case sensitive, maksudnya membedakan huruf besar dan kecil, a berbeda dengan A, nama berbeda dengan Nama,NaMa,dsb..
untuk mengeset nilai variabel gunakan operator assignment (pemberi nilai)"=", contohnya :

`myos="linux"        #double-quoted
nama='pinguin'      #single-quoted 
hasil=ls -l;      #back-quoted
angka=12`

kalau anda perhatikan ada 3 tanda kutip yang kita gunakan untuk memberikan nilai string ke suatu variabel, adapun perbedaannya adalah dengan kutip ganda (double-quoted), bash mengizinkan kita untuk menyisipkan variabel di dalamnya. 
Dengan kutip terbalik (double-quoted), bash menerjemahkan sebagai perintah yang akan dieksekusi.

Untuk operasi matematika ada 3 cara yang dapat anda gunakan, dengan statement builtin let atau expr atau perintah subtitusi seperti contoh berikut:

<center><img src="img/8.png" height="300" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

<b>Hasilnya:</b> 

<center><img src="img/9.png" height="150" width="80%" style="box-shadow: 0px 0px 15px -2px gray"></center>

fungsi expr begitu berdaya guna baik untuk operasi matematika ataupun string.
Mungkin anda bertanya - tanya, apakah bisa variabel yang akan digunakan dideklarasikan secara eksplisit dengan tipe data tertentu?, mungkin seperti C atau pascal, untuk hal ini oleh Bash disediakan statement declare dengan opsi -i hanya untuk data integer (bilangan bulat). 

Apabila variabel yang dideklarasikan menggunakan declare -i ternyata anda beri nilai string (karakter), maka Bash akan mengubahnya ke nilai 0, tetapi jika anda tidak menggunakannya maka dianggap sebagai string.

#### 6. Simple I/O
I/O merupakan hal yang mendasar dari kerja komputer karena kapasitas inilah yang membuat komputer begitu berdayaguna. I/O yang dimaksud adalah device yang menangani masukan dan keluaran, baik itu berupa keyboard, floppy, layar monitor,dsb. sebenarnya kita telah menggunakan proses I/O ini pada contoh -contoh diatas seperti statement echo yang menampilkan teks atau informasi ke layar, atau operasi redirect ke ke file. selain echo, bash menyediakan perintah builtin printf untuk mengalihkan keluaran ke output standard, baik ke layar ataupun ke file dengan format tertentu, mirip statement printf kepunyaan bahasa C atau perl.

###### 1. Output dengan printf

untuk menggunakan format kontrol sertakan simbol %, bash akan mensubtitusikan format tsb dengan isi variabel yang berada di posisi kanan sesuai dengan urutannya jika lebih dari satu variabel, \n \t \a adalah karakter sekuen lepas newline,tab, dan bell.

<center><img src="img/11.png" height="150" width="300" style="box-shadow: 0px 0px 15px -2px gray"></center>

###### 2. Input dengan read

Setelah echo dan printf untuk proses output telah anda ketahui, sekarang kita menggunakan statement read yang cukup ampuh untuk membaca atau menerima masukan dari input standar. Jika nama_variabel tidak disertakan, maka data yang diinput akan disimpan di variabel REPLY contoh lain read menggunakan opsi
-t(TIMEOUT), -p (PROMPT), -s(SILENT), -n (NCHAR) dan -d(DELIM).

<center><img src="img/12.png" height="200" width="400" style="box-shadow: 0px 0px 15px -2px gray"></center>

###### 3. Output dengan konstanta ANSI
1. Pengaturan Warna
Untuk pewarnaan tampilan dilayar anda dapat menggunakan konstanta ANSI (salah satu badan nasional amerika yang mengurus standarisasi).syntaxnya:
<br>
`\033[warnam`
<br>
Dimana:
m menandakan setting color

Konstanta 31m adalah warna merah dan 0m untuk mengembalikan ke warna normal (none), tentunya konstanta warna ansi ini dapat dimasukkan ke variabel PS1 untuk mengatur tampilan prompt shell anda. berikut daftar warna yang dapat anda gunakan:
<br>
`foreground
       None    0m 
       Black       0;30     Dark Gray     1;30
       Red         0;31     Light Red     1;31
       Green       0;32     Light Green   1;32
       Brown       0;33     Yellow        1;33
       Blue        0;34     Light Blue    1;34
       Purple      0;35     Light Purple  1;35
       Cyan        0;36     Light Cyan    1;36
       Light Gray  0;37     White         1;37
background
       dimulai dengan 40 untuk BLACK,41 RED,dst
lain-lain
       4 underscore,5 blink, 7 inverse`
<br>
Tentunya untuk mendapatkan tampilan yang menarik anda dapat menggabungkannya antara foreground dan background

2. Menggunakan utulity tput untuk penempatan posisi kursor
Kita dapat pula mengatur penempatan posisi kursor di layar dengan memanfaatkan utility tput, syntaxnya:
<br>
`tput cup baris kolom`
<br>
<b>contohnya:</b> 
<br>
`#!/bin/bash
clear
tput cup 5 10
echo  "HELLO"
tput cup 6 10
echo  "PAKE TPUT"`
<br>
Jika dijalankan anda akan mendapatkan string HELLO di koordinat baris 5 kolom 10, dan string PAKE TPUT dibaris 6 kolom 10. informasi selengkapnya tentang tput gunakan man tput, atau info tput.

#### 7. Seleksi dan Perulangan
Bagian ini merupakan ciri yang paling khas dari suatu bahasa pemrograman dimana kita dapat mengeksekusi suatu pernyataan dengan kondisi terntentu dan mengulang beberapa pernyataan dengan kode script yang cukup singkat.

###### 1. test dan operator
Test adalah utility sh shell yang berguna untuk memeriksa informasi tentang suatu file dan berguna untuk melakukan perbandingan suatu nilai baik string ataupun numerik syntaxnya: test ekspresi.

Proses kerja test yaitu dengan mengembalikan sebuah informasi status yang dapat bernilai 0 (benar) atau 1 (salah) dimana nilai status ini dapat dibaca pada variabel spesial $?.

Simbol -gt dan -lt, itulah yang disebut sebagai operator, secara sederhana operator adalah karakter khusus (spesial) yang melakukan operasi terhadap sejumlah operand, misalkan 2+3, "+" adalah operator sedangkan 2 dan 3 adalah operandnya, pada contoh test tadi yang bertindak sebagai oparatornya adalah -lt dan -gt, sedangkan bilangan disebelah kiri dan kanannya adalah operand. cukup banyak operator yang disediakan bash antara lain:

1. Operator untuk integer

<center><img src="img/int.png" height="150" width="300" style="box-shadow: 0px 0px 15px -2px gray"></center>

Operasi string

<center><img src="img/string.png" height="75" width="430" style="box-shadow: 0px 0px 15px -2px gray"></center>

Operator file

<center><img src="img/file.png" height="75" width="400" style="box-shadow: 0px 0px 15px -2px gray"></center>

Operator logika

<center><img src="img/logika.png" height="75" width="400" style="box-shadow: 0px 0px 15px -2px gray"></center>

#### 8. Seleksi
###### 1. if
Statement builtin if berfungsi untuk melakukan seleksi berdasarkan suatu kondisi tertentu. Contoh:

<center><img src="img/13.png" height="400" width="800" style="box-shadow: 0px 0px 15px -2px gray"></center>

###### 2. While
Selama kondisi bernilai benar atau zero perintah dalam blok while akan diulang terus
<br>
<b>Syntaxnya:</b> 
<br>
`while KONDISI; do perintah; done;`

<b>Contohnya:</b> 
<br>
`#!/bin/bash`
<br>
`i=1;`<br>
`while [ $i -le 10 ];`<br>
`do`<br>
`echo “$i,”;`<br>
`let i=$i+2;`<br>
`done`<br>

<b>Hasilnya:</b> 
<br>
`[arif@linuxubuntu$]bash wh1`
<br>
`1,3,5,7,9`

#### 8. Until

Jika while akan mengulang selama kondisi benar, lain halnya dengan statement until yang akan mengulang selama kondisi salah. berikut contoh script ut menggunakan until

<b>Contohnya:</b>
<br> 
`#!/bin/bash`

`i=1;
until [ $i -gt 10 ];
do
echo $i;
let i=$i+1
done`

<b>Hasilnya:</b> 
`[arif@linuxubuntu$]bash ut
1,2,3,4,5,6,7,8,9,10,`

#### 9. Select

Select berguna untuk pembuatan layout berbentuk menu pilihan, anda lihat contoh script pembuatan menu diatas kita hanya melakukannya dengan echo secara satu persatu, dengan select akan terlihat lebih efisien.

<b>Syntaxnya:</b> 
`select varname in (&ltitem list>); do perintah; done`

<b>Contohnya:</b> 
`#!/bin/bash
menu1
clear
select menu
do
echo “Anda memilih $REPLY yaitu $menu”
done`

<b>Hasiilnya:</b> 
`[arif@linuxubuntu$]bash menu1 Slackware Redhat Mandrake
1) Slackware
2) Redhat
3) Mandrake
? 1
Anda memilih 1 yaitu Slackware`

#### 10. Array

Array adalah kumpulan variabel dengan tipe sejenis, dimana array ini merupakan feature Bash yang cukup indah dan salah satu hal yang cukup penting dalam bahasa pemrograman, anda bisa membayangkan array ini sebagai tumpukan buku – buku dimeja belajar. lebih jelasnya sebaiknya lihat dulu

<b>Contoh script berikut:</b> 

`#!/bin/bash
array1
buah=(Melon,Apel,Durian);
echo ${buah[*]};`

<b>Hasilnya :</b> 

`[arif@linuxubuntu$] bash array1
Melon,Apel,Durian`

Anda lihat bahwa membuat tipe array di Bash begitu mudah, secara otomatis array buah diciptakan dan string Melon menempati index pertama dari array buah, perlu diketahui bahwa array di Bash dimulai dari index 0, jadi array buah mempunyai struktur seperti berikut:

`buah[0] berisi Melon
buah[1] berisi Apel
buah[2] berisi Durian`

0,1,2 adalah index array, berarti ada 3 elemen pada array buah, untuk menampilkan isi semua elemen array gunakan perintah subtitusi seperti pada contoh diatas, dengan index berisi `"*"` atau "@". dengan adanya index array tentunya kita dapat mengisi array perindexnya dan menampilkan isi array sesuai dengan index yang diinginkan. anda lihat contoh berikut:

`#!/bin/bash
array2
bulan[0]=31
bulan[1]=28
bulan[2]=31
bulan[3]=30
bulan[4]=31
bulan[5]=30
bulan[6]=31
bulan[7]=31
bulan[8]=30
bulan[9]=31
bulan[10]=30
bulan[11]=31
echo "Banyak hari dalam bulan November adalah ${bulan[10]} hari"`

<b>Hasilnya:</b> 

`[arif@linuxubuntu$]bash array2
Banyak hari dalam bulan November adalah 30 hari`
























