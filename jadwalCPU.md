# Penjadwalan CPU 

Penjadwalan CPU adalah pemilihan proses dari antrian ready untuk dapat dieksekusi. Penjadwalan CPU merupakan konsep dari multiprogramming, dimana CPU digunakan secara bergantian untuk proses yang berbeda. Suatu proses terdiri dari dua siklus yaitu Burst I/O dan Burst CPU yang dilakukan bergantian hingga proses selesai. Penjadwalan CPU mungkin dijalankan ketika proses: 

1. Running Ke Waiting
2. Running Ke Ready
3. Waiting Ke Ready
4. Stop Processing

Proses  1 Dan 4 adalah proses Non Preemptive, dimana proses tersebut tidak bisa di- interrupt, sedangkan 2 dan 3 adalah proses Preemptive, dimana proses boleh di interrupt.
Pada saat CPU menganggur, maka sistem operasi harus menyeleksi proses-proses yang ada di memori utama (ready queue) untuk dieksekusi dan mengalokasikan CPU untuk salah satu dari proses tersebut. Seleksi semacam ini disebut dengan shortterm scheduler (CPU scheduler). 
Komponen yang lain dalam penjadwalan CPU adalah dispatcher, Dispatcher adalah suatu modul yang akan memberikan kontrol pada CPU terhadap penyeleksian proses yang dilakukan selama short-term scheduling . Waktu yang diperlukan oleh dispatcher untuk menghentikan suatu proses dan memulai proses yang lain disebut dengan dispatch latency.
Jika dalam suatu proses Burst CPU jauh lebih besar daripada Burst I/O maka disebut CPU Bound. Demikian juga sebaliknya disebut dengan I/O Bound.

####PENJADWALAN PREEMPTIVE

Penjadwalan Preemptive mempunyai arti kemampuan sistem operasi untuk memberhentikan sementara proses yang sedang berjalan untuk memberi ruang kepada proses yang prioritasnya lebih tinggi. Penjadwalan ini bisa saja termasuk penjadwalan proses atau I/O. Penjadwalan Preemptive memungkinkan sistem untuk lebih bisa menjamin bahwa setiap proses mendapat sebuah slice waktu operasi. Dan juga membuat sistem lebih cepat merespon terhadap event dari luar (contohnya seperti ada data yang masuk) yang membutuhkan reaksi cepat dari satu atau beberapa proses. Membuat penjadwalan yang Preemptive mempunyai keuntungan yaitu sistem lebih responsif daripada sistem yang memakai penjadwalan Non Preemptive.
Dalam waktu-waktu tertentu, proses dapat dikelompokkan ke dalam dua kategori: proses yang memiliki Burst M/K yang sangat lama disebut I/O Bound, dan proses yang memiliki Burst CPU yang sangat lama disebut CPU Bound. Terkadang juga suatu sistem mengalami kondisi yang disebut busywait, yaitu saat dimana sistem menunggu request input(seperti disk, keyboard, atau jaringan). Saat busywait tersebut, proses tidak melakukan sesuatu yang produktif, tetapi tetap memakan resource dari CPU. Dengan penjadwalan Preemptive, hal tersebut dapat dihindari.
Dengan kata lain, penjadwalan Preemptive melibatkan mekanisme interupsi yang menyela proses yang sedang berjalan dan memaksa sistem untuk menentukan proses mana yang akan dieksekusi selanjutnya.
Lama waktu suatu proses diizinkan untuk dieksekusi dalam penjadwalan Preemptive disebut time slice/quantum. Penjadwalan berjalan setiap satu satuan time slice untuk memilih proses mana yang akan berjalan selanjutnya. Bila time slice terlalu pendek maka penjadwal akan memakan terlalu banyak waktu proses, tetapi bila time slice terlau lama maka memungkinkan proses untuk tidak dapat merespon terhadap event dari luar secepat yang diharapkan.

####PENJADWALAN NON PREEMPTIVE

Penjadwalan Non Preemptive ialah salah satu jenis penjadwalan dimana sistem operasi tidak pernah melakukan context switch dari proses yang sedang berjalan ke proses yang lain. Dengan kata lain, proses yang sedang berjalan tidak bisa di- interupt.
Penjadwalan Non Preemptive terjadi ketika proses hanya:
1. Berjalan dari running state sampai waiting state.
2. Dihentikan. 

Ini berarti CPU menjaga proses sampai proses itu pindah ke waiting state ataupun dihentikan (proses tidak diganggu). Metode ini digunakan oleh Microsoft Windows 3.1 dan Macintosh. Ini adalah metode yang dapat digunakan untuk platforms hardware tertentu, karena tidak memerlukan perangkat keras khusus (misalnya timer yang digunakan untuk meng interupt pada metode penjadwalan Preemptive).


####Kriteria Penjadwalan
Algoritma penjadwalan CPU yang berbeda akan memiliki perbedaan properti.
Sehingga untuk memilih algoritma ini harus dipertimbangkan dulu properti-properti
algoritma tersebut. Ada beberapa kriteria yang digunakan untuk melakukan
pembandingan algoritma penjadwalan CPU, antara lain:
1. CPU utilization. Diharapkan agar CPU selalu dalam keadaan sibuk. Utilitas CPU
dinyatakan dalam bentuk prosen yaitu 0-100%. Namun dalam kenyataannya hanya
berkisar antara 40-90%.
2. Throughput. Adalah banyaknya proses yang selesai dikerjakan dalam satu satuan
waktu.
3. Turnaround time. Banyaknya waktu yang diperlukan untuk mengeksekusi proses,
dari mulai menunggu untuk meminta tempat di memori utama, menunggu di ready
queue, eksekusi oleh CPU, dan mengerjakan I/O.
4. Waiting time. Waktu yang diperlukan oleh suatu proses untuk menunggu di ready
queue. Waiting time ini tidak mempengaruhi eksekusi proses dan penggunaan I/O.
5. Response time. Waktu yang dibutuhkan oleh suatu proses dari minta dilayani hingga
ada respon pertama yang menanggapi permintaan tersebut.
6. Fairness. Meyakinkan bahwa tiap-tiap proses akan mendapatkan pembagian waktu
penggunaan CPU secara terbuka (fair).

#####1.) First-Come First-Served Scheduling [ FCFS ]

Proses yang pertama kali meminta jatah waktu untuk menggunakan CPU akan
dilayani terlebih dahulu. Pada skema ini, proses yang meminta CPU pertama kali akan
dialokasikan ke CPU pertama kali.
Misalnya terdapat tiga proses yang dapat dengan urutan P1, P2, dan P3 dengan
waktu CPU-burst dalam milidetik yang diberikan sebagai berikut :

<center><img src="img/p1.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>

Gant Chart dengan penjadwalan FCFS adalah sebagai berikut :
                       
<center><img src="img/p2.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>

Waktu tunggu untuk P1 adalah 0, P2 adalah 24 dan P3 adalah 27 sehingga rata-rata
waktu tunggu adalah (0 + 24 + 27)/3 = 17 milidetik. Sedangkan apabila proses datang
dengan urutan P2, P3, dan P1, hasil penjadwalan CPU dapat dilihat pada gant chart
berikut :

<center><img src="img/p3.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>

Waktu tunggu sekarang untuk P1 adalah 6, P2 adalah 0 dan P3 adalah 3 sehingga ratarata
waktu tunggu adalah (6 + 0 + 3)/3 = 3 milidetik. Rata-rata waktu tunggu kasus ini
jauh lebih baik dibandingkan dengan kasus sebelumnya. Pada penjadwalan CPU
dimungkinkan terjadi Convoy effect apabila proses yang pendek berada pada proses
yang panjang.

Algoritma FCFS termasuk non-preemptive. karena, sekali CPU dialokasikan
pada suatu proses, maka proses tersebut tetap akan memakai CPU sampai proses
tersebut melepaskannya, yaitu jika proses tersebut berhenti atau meminta I/O.

#####2.) Shortest Job First Scheduler (SJF)

Pada Penjadwalan SJF, Proses Yang Memiliki CPU Burst Paling Kecil Dilayani Terlebih Dahulu. SJF Terbagi Menjadi Dua Skema :

1. SJF Non preemptive, bila CPU diberikan pada proses, maka tidak bisa ditunda
sampai CPU burst selesai.
2. SJF Preemptive, jika proses baru datang dengan panjang CPU burst lebih pendek
dari sisa waktu proses yang saat itu sedang dieksekusi, proses ini ditunda dan
diganti dengan proses baru. Skema ini disebut dengan Shortest-Remaining-
Time-First (SRTF).
     SJF adalah algoritma penjadwalan yang optimal dengan rata-rata waktu tunggu
yang minimal. Misalnya terdapat empat proses dengan panjang CPU burst dalam
milidetik.

<center><img src="img/p4.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>

`SJF   NON-PREEMPTIVE`

Dapat dilihat pada GantChart berikut :      
<center><img src="img/p5.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>
Cara Menganalisa :
* Pertama, Pada Urutan Pertama Masukkan Proses Yang Memiliki Arrival Time Terkecil. Dan Proses Selanjutnya Melihat Burst Time Terkecil
*  Menghitung Rata-Rata, Waktu Tunggu Dikurangi Arrival Time
Diperoleh Waktu tunggu untuk P1 adalah 0, P2 adalah 6, P3 adalah 3 dan P4 adalah 7 sehingga
rata-rata waktu tunggu adalah (0 + 6 + 3 + 7) /4 = 4 milidetik. 

`SJF   PREEMPTIVE`

Dapat dilihat pada GantChart berikut :
<center><img src="img/p6.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>         
Cara Menganalisa :
* Pertama, Urutkan Dari Arrival Time Terkecil 
* Masukkan Nilai Burst Time Ke Waktu Yang Telah Tersedia (Arrival Time). Misal P1 Memiliki Burst Time "7" Sedangkan P1 Yang Tersedia Harus Membutuhkan 2 Milidetik. Jadi 7 Dikurangi Waktu Yang Dibutuhkan (Bukan Waktu Proses) Jadi P1 Masih Tersisa "5"
* Karena P4 Tidak Memiliki Waktu Proses Jadi Langsung Diletakkan Di Bagian SISA
* Letakkan Waktu Yang Yang Tersisa Di Bagian Setelah Waktu Yang Ditentukan.
* Menghitung Rata-Rata, JIKA PROSES TERJADI LEBIH DARI 1 KALI misal P1 Ada Dua Seperti GantChart Diatas Di Awal Dan Diakhir. Cara Menghitung Adalah Waktu Tunggu Yang Terakhir Dikurangi Waktu Proses Yang Pertama. Jadi 11-2=9    P1=9 
* Jika Proses Hanya Terjadi 1 Kali Maka Cara Menghitungnya Adalah Waktu Tunggu Dikurangi Arrival Time.
SISA

P1 = 5
P2 = 2
P4 = 4
- Urutkan Dari SISA Yang Paling Kecil. Diperoleh P2, P4, P5
     Waktu tunggu untuk P1 adalah 9, P2 adalah 1, P3 adalah 0 dan P4 adalah 2 sehingga
rata-rata waktu tunggu adalah (9 + 1 + 0 + 2)/4 = 3 milidetik.

#####3.) Priority Scheduling

Algoritma SJF adalah suatu kasus khusus dari penjadwalan berprioritas. Tiap-tiap
proses dilengkapi dengan nomor prioritas (integer). CPU dialokasikan untuk proses
yang memiliki prioritas paling tinggi (nilai integer terkecil biasanya merupakan prioritas
terbesar). Jika beberapa proses memiliki prioritas yang sama, maka akan digunakan
algoritma FCFS. Penjadwalan berprioritas terdiri dari dua skema yaitu non preemptive
dan preemptive. Jika ada proses P1 yang datang pada saat P0 sedang berjalan, maka
akan dilihat prioritas P1. Seandainya prioritas P1 lebih besar dibanding dengan prioritas
P0, maka pada non-preemptive, algoritma tetap akan menyelesaikan P0 sampai habis
CPU burst-nya, dan meletakkan P1 pada posisi head queue. Sedangkan pada
preemptive, P0 akan dihentikan dulu, dan CPU ganti dialokasikan untuk P1.
Misalnya terdapat lima proses P1, P2, P3, P4 dan P5 yang datang secara berurutan dengan CPU burst dalam milidetik.

<center><img src="img/p7.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>         

Penjadwalan proses dengan algoritma priority dapat dilihat pada gant chart berikut :

<center><img src="img/p8.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>         

Waktu tunggu untuk P1 adalah 6, P2 adalah 0, P3 adalah 16, P4 adalah 18 dan P5 adalah 1 sehingga rata-rata waktu tunggu adalah (6 + 0 +16 + 18 + 1)/5 = 8.2 milidetik.

#####4.) Round-Robin Scheduling

Konsep dasar dari algoritma ini adalah dengan menggunakan time-sharing. Pada
dasarnya algoritma ini sama dengan FCFS, hanya saja bersifat preemptive. Setiap
proses mendapatkan waktu CPU yang disebut dengan waktu quantum (quantum time)
untuk membatasi waktu proses, biasanya 1-100 milidetik. Setelah waktu habis, proses
ditunda dan ditambahkan pada ready queue.

Jika suatu proses memiliki CPU burst lebih kecil dibandingkan dengan waktu
quantum, maka proses tersebut akan melepaskan CPU jika telah selesai bekerja,
sehingga CPU dapat segera digunakan oleh proses selanjutnya. Sebaliknya, jika suatu
proses memiliki CPU burst yang lebih besar dibandingkan dengan waktu quantum,
maka proses tersebut akan dihentikan sementara jika sudah mencapai waktu quantum,
dan selanjutnya mengantri kembali pada posisi ekor dari ready queue, CPU kemudian
menjalankan proses berikutnya.

Jika terdapat n proses pada ready queue dan waktu quantum q, maka setiap
proses mendapatkan 1/n dari waktu CPU paling banyak q unit waktu pada sekali
penjadwalan CPU. Tidak ada proses yang menunggu lebih dari (n-1)q unit waktu.
Performansi algoritma round robin dapat dijelaskan sebagai berikut, jika q besar, maka
yang digunakan adalah algoritma FIFO, tetapi jika q kecil maka sering terjadi context
switch.

Misalkan ada 3 proses: P1, P2, dan P3 yang meminta pelayanan CPU dengan
quantum-time sebesar 4 milidetik.
Catatan : Quantum Time "4" Berarti Hanya Maksimal 4 Milidetik (Ruang) Yang Akan Di Isi Burst Time nya. Misal Jika Burst Time P1 = 24 Berarti 24 Dikurangi 4 Dikurang 4 Lagi Dan Seterusnya, Sampai Burst Time Tidak Tersisa.

<center><img src="img/p9.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>         

Penjadwalan proses dengan algoritma round robin dapat dilihat pada gant chart berikut :

<center><img src="img/p10.jpg" style="box-shadow: 0px 0px 15px -2px gray"></center>         

Cara Menganalisa :
*  Menghitung Rata-Rata, Jika Proses Terjadi Lebih Dari 1 Kali Maka Berapa Jumlah Proses Tersebut, Itulah Nilai Waktu Tunggu Yang Akan Dihitung Rata-Rata. Misal P1 Terjadi 6 Kali. Jadi P1 = 6
Waktu tunggu untuk P1 adalah 6, P2 adalah 4, dan P3 adalah 7 sehingga rata-rata waktu
tunggu adalah (6 + 4 + 7)/3 = 5.66 milidetik.
