####File perangkat keras

/dev berisi file device (perangkat) yang merupakan aspek penting pada sistem file Linux. /dev/cdrom dan /dev/fd0 merupakan drive CD-ROM dan floppy pada komputer anda. Kita dapat melakukan akses read dan write pada perangkat. Sebagai contoh /dev/dsp merupakan perangkat speaker. Sembarang data yang ditulis ke file ini akan dialihkan ke speaker. `cat /boot/vmlinuz > /dev/dsp` menyebabkan kita dapat mendengarkan suara dari speaker. Untuk mencetak file dapat dikirim ke perangkat `/dev/lp0`. Mengirim data dan membaca data dari `/dev/ttyS0` akan menyebabkan komunikasi dengan perangkat modem.

Mayoritas device berupa block device atau character device. Block deviceadalah device yang menyimpan atau membawa data, character device adalah device yang mengirim atau transfer data. Sebagai contoh, disket drive, hard drive dan CDROM drive adalah block device, sedangkan serial port, mouse dan parallel printer adalah character device.

Beberapa file perangkat yang umum digunakan yang perlu diingat adalah :
`/dev/ttyS0` (first communication port, COM1) : first serial port (mouse, modem),
`/dev/psaux` (PS/2) : PS/2 mouse connection (mouse, keyboard), 
`/dev/lp0` (first printer port, LPT 1) : first parallel port (printer, scanner, dsb), 
`/dev/dsp` (first audio device) : sound card, digitized voice dan PCM, /dev/usb/ (USB device) : node USB device, 
`/dev/sda` (C:/SCSI device) : first SCSI device (HDD, Memory stick, external mass storage device seperti CD-ROM pada laptop), 
`/dev/scd/` (D:\SCSI CD-ROM device) : first SCSI CD-ROM device, /dev/js0 (standard gameport joystick) : first joystick device.

Device didefinisikan sebagai tipe seperti block atau character dan nomor mayor dan minor. Nomor mayor digunakan untuk melakukan katagori device dan nomor minor untuk mengidentifikasi tipe device khusus. Sebagai contoh, semua IDE device dihubungkan dengan primary controller mempunyai nomor mayor 3. Perangkat master dan slave, didefinisikan lebih jauh dengan nomor minor. Terdapat dua nomor sebelum tanggal yang tercetak. Jika kita lakukan perintahls `–l /hd*` maka akan terlihat nomor mayor untuk perangkat hda dan hdb adalah 3. Nomor minor berubah untuk setiap partisi tertentu. Kita dapat selalu membuat perangkat menggunakan skrip MAKEDEV dimana akan diletakkan pada direktori /dev.
`# MAKEDEV *`

####Perintah Mount dan Umount

Sebelum menggunakan sistem file, harus di-mount terlebih dahulu. Kemudian sistem operasi dapat mengerjakan penyimpaanan file. Karena semua file UNIX berada pada satu pohon direktori, operasi mount akan terlihat seperti isi dari sub direktori yang ada pada sistem file yang sudah dilakukan mounting. Contoh perintah mount :

`$ mount /dev/hda2
/home $ mount
/dev/hda3 /usr`

Perintah mount mempunyai 2 argumen, argument pertama adalah file device yang berhubungan dengan disk atau partisi dengan sistem file. Argument kedua adalah direktori yang dimounting. Perintah diatas berarti bahwa `/dev/hda2` dilakukan mounting ke `/home` begitu juga dengan `/usr`. Perbedaan antara file device `/dev/hda2` dan direktori mount `/home` adalah file device memberikan akses ke isi disk mentah, direktori mount memberikan akses ke file dari disk. Direktori mount disebut mount point.
Linux mendukung beberapa tipe sistem file. Mount akan menebak tipe dari sistem file. Opsi –t fstype akan memberikan spesifikasi tipe sistem file. Sebagai contoh, untuk mount floppy MS-DOS, dapat menggunakan perintah berikut :

`$ mount –t msdos /dev/fd0 /floppy`

Sistem file root dilakukan mounting pada waktu booting. Jika sistem file root tidak dapat dimounting, sistem tidak dapat melakukan booting. Nama sistem file dimounting sebagai root. Sistem file root mula-mula bersifat read-only. Skip startup kemudian menjalankan fsck untuk melakukan verifikasi validitas dan jika tidak ada permasalahan, dilakukan mounting lagi sehingga write diperbolehkan.fsck tidak boleh dijalankan pada saat sistem file dimounting, karena setiap perubahan ke sistem file saat fsck berjalan mengakibatkan kesalahan. Bila sistem file root dimounting read-only saat dilakukan pengecekan, fsck dapat memperbaiki permasalahan.
Jika sistem file tidak diperlukan untuk dimounting, dapat dilakukan unmounting dengan perintah umount. Perintah umount mempunyai satu argument berupa file device atau mount point. Sebagai contoh untuk unmount direktori pada contoh diatas dapat digunakan perintah :

`$ umount /dev/hda2
$ umount /usr
Kita dapat melihat perangkat floppy dan mount point yang diijinkan pada/etc/fstab.
$ cat /etc/fstab
/dev/fd0     /mnt/floppy                 auto       rw, user, noauto    0 0
/dev/hdc    /mnt/cdrom                  iso9660 ro, user, noauto      0 0
/dev/hdc      /mnt/cdrom                iso9660  0  0  0`

Kolom terdiri dari file device, directory mounting, tipe sistem file, opsi, frequency backup, fsck pass number (0 berarti tanpa cek). Opsi noauto menghentikan mounting yang dilakukan secara otomatis jika sistem dimulai (misalnya menghentikan mount –a). Opsi user mengijinkan sembarang user melakukan mounting sistem file dan karena alasan keamanan, eksekusi program tidak diijinkan (normal atau setuid).
Jika ingin menyediakan akses ke beberapa tipe floppy, perlu diberikan beberapa mount point. Setting berbeda untuk setiap mount point. Sebagai contoh untuk memberikan akses ke floppy MS-DOS dan ext2, dilakukan perubahan baris pada /etc/fstab :

`/dev/fd0 /dosfloppy msdos user, noauto 0 0 /dev/fd0
/ext2floppy ext user, noauto 0 0`
