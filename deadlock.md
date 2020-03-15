##Pengertian Deadlock
Pengertian Deadlock ialah keadaan dimana 2 atau lebih proses saling menunggu meminta resources untuk waktu yang tidak terbatas lamanya.
Analoginya seperti pada kondisi jalan raya dimana terjadi kemacetan parah.
<center><img src="img/deadlock1.png" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Contoh Deadlock di Persimpangan Jalan
<center><img src="img/deadlock2.png" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Deadlock pada jembatan

- Deadlock adalah efek samping dari sinkronisasi, dimana satu variabel digunakan oleh 2 proses.
- Kejadian Deadlock selalu tidak lepas dari sumber daya, bahwa hampir seluruhnya merupakan masalah sumber daya yang digunakan bersama-sama. Oleh karena itu, kita juga perlu tahu tentang jenis sumber daya, yaitu: sumber daya dapat digunakan lagi berulang-ulang dan sumber daya yang dapat digunakan dan habis dipakai atau dapat dikatakan sumber daya sekali pakai. Sumber daya ini tidak habis dipakai oleh proses mana pun.Tetapi setelah proses berakhir, sumber daya ini dikembalikan untuk dipakai oleh proses lain yang sebelumnya tidak kebagian sumber daya ini.

#####Contoh
Contohnya prosesor, Channel I/O, disk. Contoh peran sumber daya jenis ini pada terjadinya Deadlock ialah misalnya sebuah proses memakai disk A dan B, maka akan terjadi Deadlock jika setiap proses sudah memiliki salah satu disk dan meminta disk yang lain. Masalah ini tidak hanya dirasakan oleh pemrogram tetapi oleh seorang yang merancang sebuah sistem operasi.
Cara yang digunakan pada umumnya dengan cara memperhitungkan dahulu sumber daya yang digunakan oleh proses-proses yang akan menggunakan sumber daya tersebut
 

####Pengoperasian I/O
* meminta (request) : meminta pelayanan perangkat masukan / keluaran
* memakai (use) : memakai perangkat masukan / keluaran
* melepaskan (release) : melepaskan pemakaian perangkat masukan / keluaran
 

####RESOURCE
Resource dapat berupa hardware device (seperti tape drive, memori) atau berupa informasi (record dalam suatu basis data, variable global, dll).
Resource ada 2 jenis, yaitu:
- Preemptable
- Nonpreemtable.

####Dua Jenis Resource :
<b>Resource preemtable</b> adalah resource yang dapat diambil (dilepas) dari proses yang sedang memakainya tanpa memberi efek apapun pada proses tersebut.

<b>Resource nonpreemtable</b> adalah resource yang tidak dapat diambil dari proses yang sedang membawanya karena akan menimbulkan kegagalan komputasi. Resource jenis ini yang sering Menyebabkan deadlock.


####DIAGRAM GRAF
Sebuah sistem komputer terdiri dari berbagai macam sumber daya (resources), seperti:
1. Fisik (Perangkat, Memori)
2. Logika (Lock, Database record)
3. Sistem Operasi (PCB Slots)
4. plikasi (Berkas)

Mekanisme hubungan dari proses-proses dan sumber-daya yang dibutuhkan/digunakan dapat di diwakilkan dengan graf.

<center><img src="img/deadlock3.png" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Proses Pi meminta sumber daya Rj
<center><img src="img/deadlock4.png" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Proses Pi meminta sumber daya Rj
<center><img src="img/deadlock5.png" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Sumber daya Rj yang mengalokasikan salah satu
<center><img src="img/deadlock6.png" height="250" width="400" style="border-radius: 10px; box-shadow: 0px 0px 15px -2px gray"></center>
Graf Alokasi Sumber daya
 

Untuk mengetahui ada atau tidaknya deadlock (Pendeteksian) dalam suatu graf dapat dilihat dari perputaran dan resource yang dimilikinya, yaitu:
- Jika tidak ada perputaran berarti tidak deadlock.
- Jika ada perputaran, ada potensi terjadi deadlock.
- Resource dengan instan tunggal dan perputaran mengakibatkan deadlock.