##PROSES BOOTING PADA LINUX
 
####PENGERTIAN BOOTING
Pengertian booting adalah proses yang terjadi pada saat komputer dihidupkan, dimana masuknya arus listrik ke dalam peralatan komputer. Kemudian system memeriksa ada atau tidaknya perangkat keras atau hardware yang terhubung pada komputer agar user dapat berkomunikasi dengan komputer.

####TAHAP-TAHAP BOOTING SECARA UMUM
Tahap awal pada proses booting yang dilakukan oleh sistem operasi adalah bootstrap loader. Bootsrap loader adalah aplikasi pertama yang dijalankan BIOS sesaat setelah booting. Bootloader akan memproses kernel yang menjalankan sistem operasi, hal tersebut juga bertujuan untuk melacak semua alat input dan alat output yang terpasang atau terhubung pada komputer. Biasanya bootloader di tiap system berbeda-beda seperti Bootloader Windows, berbeda dengan Bootloader Linux, serta berbeda pula dengan bootloader BSD.
1. Saat komputer dihidupkan, kondisi memori pada komputer masih kosong yang berarti tidak ada perintah didalamnya untuk dapat di eksekusi oleh prosesor. Maka dari itu, prosesor dirancang untuk dapat mencari alamat yang terdapat dalam BIOS (Basic Input/Output System) ROM. Pada alamat tersebut terdapat perintah Jump yang dapat langsung menuju alamat eksekusi utama BIOS. Setelah itu prosesor akan menjalankan POST (Power On Self Test) untuk melihat atau memeriksa hardware yang terhubung ke komputer.
2. Pada tahap berikutnya, BIOS mencari video card. Video card disini merupakan VGA Card, yang sering disebut Graphic Card. Video card berfungsi untuk menerjemahkan/mengubah sinyal digital dari komputer menjadi tampilan grafis pada layar monitor. Kartu VGA (Video Graphic Adapter) berguna untuk menerjemahkan output (keluaran) komputer ke monitor. Kemudian sistem BIOS menjalankan Video Card BIOS. Barulah sesudah itu, Video Card di inisalisasi.
3. Kemudian BIOS memeriksa ROM pada hardware lain apakah hardware memiliki BIOS tersendiri. Jika ya maka akan dieksekusi juga.
4. Pada tahap akhir, BIOS melakukan pemeriksaan lagi seperti memeriksa besar memori, jenis memori, serta memeriksa hardware yang lain seperti disk. Kemudian BIOS mencari boot sector dimana booting bisa dijalankan. Boot sector dapat berada di harddisk maupun floppy disk.

####TAHAP-TAHAP BOOTING PADA LINUX
Secara ringkas, proses booting pada linux ada 6 tahap dengan uraian sebagai berikut:
<center><img src="img/booting1.png" height="300" width="300"></center>

1. BIOS
Ketika tombol power di tekan, proses pertama yang terjadi didalam Komputer adalah prosesor membaca sekumpulan instruksi yang berada di dalam ROM. Instruksi di dalam ROM adalah untuk menjalankan BIOS dimana BIOS adalah singkatan dari Basic Input / Output System. BIOS melakukan beberapa pemeriksaan integritas sistem, seperti memeriksa hardware, disk, VGA dan lain lain yang terdapat pada komputer. Setelah BIOS berjalan, selanjutnya BIOS akan memeriksa hardware yang ada salah satunya adalah memeriksa harddisk.
Pemeriksaan yang dilakukan adalah untuk mencari primary boot loader pada MBR (biasanya terletak pada sector 0 di harddisk dengan ukuran 512 byte). Ketika sudah ditemukan, maka proses booting akan berlanjut ke proses booting selanjutnya yaitu MBR.
2. MBR
Merupakan kepanjangan dari Master Boot Record. MBR hanya memiliki size 512 bytes dengan pembagian sebagai berikut:
434-446 bytes pertama digunakan sebagai primary boot loader
64 bytes selanjutnya digunakan sebagai table partisi
6 bytes selanjutnya digunakan untuk pengecekan validasi MBR
Pada tahap ini, MBR tidak dapat menjalankan kernel secara langsung karena size untuk kernel melebihi batas size yang dapat diproses oleh MBR, oleh karena itu akan dibutuhkan sebuah bootloader untuk dapat mengeksekusi kernel. Sehingga secara garis besar pada tahap ini, MBR akan memuat dan menjalankan bootloader.

3. GRUB
GRUB merupakan kepanjangan dari Grand Unified Bootloader dimana memiliki informasi tentang file system yang akan di jalankan. File konfigurasi GRUB pada linux terletak pada /boot/grub/grub.conf. Berikut adalah contohnya :
<center><img src="img/booting2.png" height="300" width="300"></center>

GRUB akan tampil setelah proses MBR dan akan menampilkan pilihan kernel yang akan di eksekusi. GRUB akan tampil selama beberapa detik, sehingga user dapat memilih kernel mana yang akan di muat dan di eksekusi. Proses memuat kernel oleh GRUB dibagi menjadi 3 tahap:
- Tahap 1
Primary boot loader memiliki size kurang dari 512 bytes yang mana itu terlalu kecil untuk memuat instruksi yang komplek, sehingga pada tahap ini primary boot loader akan memuat tahap 1.5 dan tahap 2.
- Tahap 1.5
Sebenarnya tahap 1 dapat mengakses tahap 2 secara langsung, tetapi pada umumnya, akan melewati tahap 1.5 terlebih dahulu. tahap 1.5 ini terletak pada 30KB harddisk tepat setelah MBR dan sebelum partisi yang pertama. Ruang ini digunakan untuk menyimpan file systems driver dan modules.
- Tahap 2
Tahap 2 ini bertanggung jawab untuk memuat kernel dari /boot/grub/grub.conf dan modul lain yang diperlukan. Kemudian memuat GUI antarmuka yaitu splash screen yang terletak di /grub/splash.xpm.gz dengan daftar kernel yang tersedia di mana user dapat secara manual memilih kernel atau setelah nilai default timeout kernel yang dipilih akan di eksekusi.

4. KERNEL
Kernel dapat dianggap sebagai jantung dari sistem operasi yang bertanggung jawab untuk menangani semua proses sistem. Kernel secara umum dimuat dalam tahapan sebagai berikut:
- Ketika kernel dimuat maka hardware dan memori akan dialokasikan ke system secepat mungkin.
- Selanjutnya kernel akan meng-uncompresses file image initrd. File initrd dikompresi menggunakan zlib ke zImage atau bzImage format. Setelah di uncompress selanjutnya akan di mount dan memuat semua driver yang diperlukan.
- Semua kegiatan diatas dilakukan dengan bantuan program seperti insmod, dan rmmod berada dalam file image initrd.
- Mencari tahu jenis hard disk apakah termasuk LVM atau RAID.
- Meng-unmounts image initrd dan membebaskan semua memori digunakan oleh disk image tersebut.
- Kemudian kernel akan me-mount partisi root seperti yang ditentukan dalam grub.conf sebagai read-only.
- Selanjutnya kernel akan menjalankan proses init.

5. PROSES INIT
Pada proses ini yang terjadi adalah eksekusi sistem untuk boot ke run level yang telah ditentukan di /etc/inittab. Berikut adalah contoh boot default runlevel pada file /etc/inittab:
<center><img src="img/booting3.png" height="300" width="300"></center>

Sesuai dengan gambar diatas, maka system akan di boot dengan run level 5. Untuk melakukan pengecekan run level yang berjalan, dapat menggunakan perintah dibawah ini:
<center><img src="img/booting4.png" height="300" width="300"></center>


Selanjutnya init proses akan memeriksa setiap baris entri pada fstab dan me-mount partisi root dengan mode read-write (yang sebelumnya dibaca dengan mode read-only).