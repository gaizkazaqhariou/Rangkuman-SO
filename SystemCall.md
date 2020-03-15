##System Call

#####Pengertian dan jenis-jenis system call
System Call adalah penyedia antarmuka dari pelayanan-palayanan yang tersedia dengan Sistem Operasi. Umumnya System Call menggunakan bahasa C dan C++, meskipun tugas-tugas seperti hardware yang harus diakses langsung, maka menggunakan bahasa assembly.

#####Bagaimana cara kerja system calls?
<center><img src="img/systemcall1.png" width="300" height="300" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Dari gambar diatas, file sumber mempunyai beberapa proses sampai akhirnya sampai di file tujuan.

Pertama, kita dapat menulis suatu program sederhana untuk membaca satu file ke file lainnya. Program akan membutuhkan nama dari 2 file input dan output.
Memasukkan nama file input dan menampilkannya pada layar, menerima masukan seperti inputan data dari keyboard yang diketik, dan nama file output hasil dari ketikkan kita. Setelah dua nama file telah diperoleh program harus membuka file input dan membuat file output. Masing-masing membutuhkan system call. Mungkin ada juga kondisi kesalahan yang dilakukkan operator.

Ketika program mencoba untuk membuka file input dan ternyata tidak ada nama file itu atau bahwa file tersebut dilindungi pengaksesannya. Maka, kita harus membuat perintah di command interpreter (baca mengenai command interpreter) yang terdapat di OS kita dan membukakan file tersebut. Jika file input ada, maka kita harus membuat file output baru. Kita mungkin akan menemukan file output dengan nama yang sama. Situasi tersebut dapat membuat program dibatalkan (system call), atau kita dapat menghapus file yang ada dan membuat yang baru.

Setelah dua file input dan output telah ditetapkan, maka program akan melooping membaca file input dan menulis ke file output sampai akhir file. Jika proses sudah selesai, program akan menutup kedua file dan akan terdapat pesan di layar bahwa proses telah selesai dan mengakhiri program dengan normal.

####Jenis-jenis System Call:
1. Process control: mengontrol proses yang berjalan
2. File management: memanage file-file yang berjalan pada program
3. Device management: memanage device apa saja yang digunakan pada program
4. Information Maintenance: sebagai penghubung antara user dengan sistem operasi dari berbagai informasi.
5. Communication: pertukaran informasi dari proses yang berjalan dengan sistem operasi.

####Jenis sistem calls

System call menyediakan interface antara program (program pengguna yang berjalan) dan bagian OS. System call menjadi jembatan antara proses dan sistem operasi. System call ditulis dalam bahasa assembly
Contoh: UNIX menyediakan system call: read, write => operasi I/O untuk berkas. Sering pengguna program harus memberikan data (parameter) ke OS yang akan dipanggil. Contoh pada UNIX: read(buffer, max_size, file_id); Mengenai shell, shell itu sendiri secara umum adalah layer yang berfungsi sebagai interface antara user dan inti dalam sistem operasi (kernel). Melalui shell, user dapat memberi perintah-perintah yang akan dikirim ke sistem operasi, sehingga shell ini merupakan layer yang menerima interaksi dari user secara langsung. Shell dalam SO secara umum dibagi menjadi 2, Comman d Line(CLI) dan Graphical(GUI). Jadi dengan kata lain, system calls berperan sebagai interface dalam layanan-layanan yang disediakan oleh sistem operasi.


####System call dikelompokkan dalam 5 kategori:

Kontrol Proses • Mengakhiri (end) dan membatalkan (abort);
Mengambil (load) dan eksekusi (execute);
Membuat dan mengakhiri proses;
Menentukan dan mengeset atribut proses; • Wait for time; • Wait event, signal event; • Mengalokasikan dan membebaskan memori.
Contoh: Sistem operasi pada MS-DOS menggunakan sistem singletasking yang memiliki command interpreter yang akan bekerja pada saat start. Karena singletasking, maka akan menggunakan metode yang sederhana untuk menjalankan program dan tidak akan membuat proses baru.

Manipulasi File
Membuat dan menghapus file;
Membuka dan menutup file;
Membaca, menulis, dan mereposisi file;
Menentukan dan mengeset atribut file;
Manipulasi Device
Meminta dan mebebaskan device;
Membaca, menulis, dan mereposisi device;
Menentukan dan mengeset atribut device;
Informasi Lingkungan
Mengambil atau mengeset waktu atau tanggal;
Mengambil atau mengeset sistem data;
Mengambil atau mengeset proses, file atau atribut atribut device;
Komunikasi
Membuat dan menghapus sambungan
Mengirima dan menerima pesan;
Mentransfer satus informasi


####Jenis-jenis Sistem Call : 
Berikut ini adalah jenis system call:

- Manajemen Proses. System call untuk manajemen proses diperlukan untuk mengatur proses-proses yang sedang berjalan. Kita dapat melihat penggunaan system calls untuk manajemen proses pada Sistem Operasi Unix.
Contoh yang paling baik untuk melihat bagaimana system call bekerja untuk manajemen proses adalah Fork. Fork adalah satu satunya cara untuk membuat sebuah proses baru pada sistem Unix.

- Manajemen Berkas. System calls yang berhubungan dengan berkas sangat diperlukan. Seperti ketika kita ingin membuat atau menghapus suatu berkas, atau ketika ingin membuka atau menutup suatu berkas yang telah ada, membaca berkas tersebut, dan menulis berkas itu. System calls juga diperlukan ketika kita ingin mengetahui atribut dari suatu berkas atau ketika kita juga ingin merubah atribut tersebut. Yang termasuk atribut berkas adalah nama berkas, jenis berkas, dan lain-lain. Ada juga system calls yang menyediakan mekanisme lain yang berhubungan dengan direktori atau sistem berkas secara keseluruhan. Jadi bukan hanya berhubungan dengan satu spesifik berkas. Contohnya membuat atau menghapus suatu direktori, dan lain-lain.
Manajemen Piranti. Program yang sedang dijalankan kadang kala memerlukan tambahan sumber daya. Jika banyak pengguna yang menggunakan sistem dan memerlukan tambahan sumber daya maka harus meminta peranti terlebih dahulu. Lalu setelah selesai, penggunaannnya harus dilepaskan kembali dan ketika sebuah peranti telah diminta dan dialokasikan maka peranti tersebut bisa dibaca, ditulis, atau direposisi.

- System Call Informasi/Pemeliharaan. Beberapa system calls disediakan untuk membantu pertukaran informasi antara pengguna dan sistem operasi, contohnya adalah system calls untuk meminta dan mengatur waktu dan tanggal atau meminta informasi tentang sistem itu sendiri, seperti jumlah pengguna, jumlah memori dan disk yang masih bisa digunakan, dan lain-lain. Ada juga system calls untuk meminta informasi tentang proses yang disimpan oleh sistem dan system calls untuk merubah informasi tersebut. Dua model komunikasi:

- Message-passing. Pertukaran informasi dilakukan melalui fasilitas komunikasi antar proses yang disediakan oleh sistem operasi. • Shared-memory. Proses menggunakan memori yang bisa digunakan oleh berbagai proses untuk pertukaran informasi dengan membaca dan menulis data pada memori tersebut. Dalam message-passing, sebelum komunikasi dapat dilakukan harus dibangun dulu sebuah koneksi. Untuk itu diperlukan suatu system calls dalam pengaturan koneksi tersebut, baik dalam menghubungkan koneksi .

- System Calls For Signaling,

Pemanggilan sinyal interupsi yang digunakan untuk menghentikan suatu proses jika terdapat kesalahan atau jika ada proses lainnya yang perlu didahulukan.

- System Calls for File Management,

Sistem untuk manajemen file baik untuk membuat, membaca, membatasi pemakai memanipulasi file, dsb.

- System Calls for Directory Manajemen,

Sistem untuk mengatur suatu direktori yang berisikan file-file yang biasanya sudah dispesifikasikan tujuannya, seperti untuk user tertentu, dan untuk pemakaian secara bersama, sehingga tidak perlu banyak mengatur file-file tersebut tetapi cukup dengan mengatur direktorinya saja.

- System Call for Protection,

Sistem untuk menjaga keamanan pada suatu file/direktori sehingga hanya user tertentu yang dapat menggunakannya, untuk mencegah hal-hal yang tidak diinginkan.

- Sistem Program/OS
Perangkat lunak yang bertindak sebagai perantara antara pengguna dan perangkat keras. membekali kemampuan diri sehingga yang bersangkutan dapat melakukan evaluasi performasi (unjuk kerja) dan mendaya gunakan sistem komputer secara efisien. Sistem Operasi Juga adalah Suatu modul program pada sistem komputer yang mangatur sumber daya pada komputer.


####Alasan untuk mengetahui Sistem Operasi.
Setiap pemakai harus berhubungan dengan Sistem Operasi untuk dapat memanfaatkan komputer
Untuk dapat memilih Sistem Operasi yang sesuai untuk suatu instalasi.
Banyak konsep & teknik yang terdapat pada Sistem Operasi yang berlaku umum yang dapat digunakan pada program aplikasi-aplikasi
Untuk dapat merancang Sistem Operasi baru, atau memodifikasi Sistem Operasi yang telah ada