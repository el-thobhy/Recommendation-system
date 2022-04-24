#  Laporan Proyek Machine Learning - Auriwan Yasper

##  Project Overview

Pada Proyek kali ini domain proyek yang penulis pilih adalah mengenai hiburan yaitu "Anime Recommendation system".

**Latar Belakang**
Saat ini kartun jepang atau *anime* mengalami perkembangan yang sangat cepat dan penggemarnya tersebar diseluruh dunia. Terutama dengan merebaknya pandemi yang serba terbatas, membuat kebutuhan manusia akan hiburan semakin bertambah, salah satunya kartun jepang ini. Sudah banyak sekali platform yang menyediakan media hiburan seperti kartun jepang. Tentunya sebagai salah satu strategi marketing dalam dunia bisnis, UX atau user experience merupakan hal yang sangat penting bagi perkembangan platform tersebut. Maka salah satu strategi yang disiapkan perusahaan agar user betah dengan platform tersebut adalah adalah sistem rekomendasi mengenai sesuatu atau apa saja yang mungkin disukai oleh user. Disinilah Machine learning akan bekerja, dengan mengumpulkan data dari user, perusahaan harus mampu membuat suatu sitem rekomendasi yang mungkin akan disukai oleh pengguna.

Terdapat cukup banyak pendekatan yang bisa digunakan dalam sistem rekomendasi diantaranya Content-Based-Filtering, Collaborative-Filtering, Multi-criteria, risk aware, dan hybrid-filtering. Badal Soni et al [[1]](https://arxiv.org/abs/2106.12970) dengan RikoNet-nya menggabungkan pendekatan content-based dan collaborative filtering dalam sistem rekomendasi yang dibuatnya. Begitu juga Sistem rekomendasi yang dirancang oleh Ramashini et al[[2]](http://ir.kdu.ac.lk/handle/345/4173) yang juga menggunakan kombinasi antara content-base dan collaborative filtering. Kumar et al[[3]](https://www.ijcaonline.org/archives/volume124/number3/22082-2015904111) dengan MOV REC-nya mengajukan sistem rekomendasi dengan pendekatan collaborative filtering yang menggunakan informasi yang disediakan oleh penguna, lalu menganalisanya dan mebuat list rekomendasi yang cocok untuk para pengguna.

##  Business Understanding

Dalam dunia bisnis, user experience sangat berperan penting dalam perkembangan produk milik perusahaan. Sehingga dibutuhkan strategi yang tepat untuk membuat pengguna nyaman dengan plaform tersebut. Jadi sistem rekomendasi akan membuat user experience menjadi lebih baik karena pengguna bisa menemukan rekomendasi tontonan yang tepat, dalam hal ini adalah kartun jepang atau anime.

###  Problem Statements

Berdasarkan latarbelakang yang disebutkan diatas, permasalahan yang dapat diselesaikan pada proyek ini adalah

- Bagaimana cara pengolahan data yang tepat untuk digunakan dalam merancang suatu model machine learning

- Bagaimana cara merancang model machine learning untuk sistem rekomendasi kartun jepang.

###  Goals

Tujuan dari dibuatnya proyek ini adalah:

- Melakukan data pre-processing yang baik yang akan digunakan dalam merancang model machine learning

- Merancang model machine learning untuk membuat sistem rekomendasi kartun jepang.

### Solution statements
Untuk mencapai tujuan dari proyek ini maka penulis menggunakan 2 algoritma yaitu content base filtering dan collaborative filtering. 
	- Content-base filtering merupakan cara untuk memberikan rekomendasi berdasarkan genre atau item pada fitur yang diminati pengguna. Ide dari sistem rekomendasi berbasis konten (_content-based filtering_) adalah merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu
	- _Collaborative Filtering_ merupakan cara untuk memberi rekomendasi bedasarkan penilaian komunitas pengguna atau biasa disebut dengan _rating_

##  Data Understanding

Terdapat dua sumber dataset yang penulis gunakan yaitu dataset anime dan dataset rating 
| jenis | Keterangan |
|--|--|
| Sumber | Dataset: [Kaggle](https://www.kaggle.com/datasets/hernan4444/anime-recommendation-database-2020) |
| Dataset Owner | Hernan Valdivieso |
| lisensi | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)|
| Usability | 10.00 |
| Jenis dan ukuran berkas | ZIP(693Mb) |
| Jumlah file dataset | 6 file(5 csv, 1 folder) |

Berikut ini file yang terdapat pada dataset:
- html folder
- anime.csv
- anime_with_synopsis.csv
- animelist.csv
- rating_complete.csv
- watching_status.csv

 Dataset yang akan digunakan hanya dataset anime.csv
 lalu selanjutnya dataset rating yang diambil dari sumber berbeda, dengan sumber sebelumnya karena dataset dari hernan terlalu besar, berikut dataset yang akan digunakan:
 
| Jenis | Keterangan |
|--|--|
| Sumber  | Dataset: [Kaggle](https://www.kaggle.com/datasets/marlesson/myanimelist-dataset-animes-profiles-reviews) |
| Dataset Owner | Marlesson |
| lisensi | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) |
| Usability | 10.00 |
| Jenis dan ukuran berkas | ZIP(227Mb) |
| Jumlah file dataset | 3 file csv |

 Berikut file yang ada pada dataset
 - animes.csv
 - profiles.csv
 - reviews.csv

Dataset yang akan digunakan hanya reviews.csv untuk mendapatkan user_id untuk Collaborative learning. 

`anime.csv`
jumlah data 17.562 
1.  MAL_ID: Id anime
2.  Name: Judul Anime
3.  Score: Rata rating user
4.  Genres: Genre-genre dari anime
5.  English name: Judul dalam bahasa ingris
6.  Japanese name: Judul dalam bahasa jepang
7.  Type: Tipe data TV ataukah Movie
8.  Episodes': Jumlah episode
9.  Aired: tanggal tanyangnya
10.  Premiered: season premiere
11.  Producers: list produser
12.  Licensors: list Lisensi
13.  Studios: Studio yang menggarap
14.  Source: Sumber anime
15.  Duration: Durasi dari anime
16.  Rating: age rate (e.g. R - 17+ (violence & profanity))
17.  Ranked: Rangking berdasarkan score
18.  Popularity: rangking berdasarkan user yang menambahkan ke list tonton
19.  Members: Jumlah pemain dalam anime
20.  Favorites: Jumlah User yang menambahkan sebagai favorite
21.  Watching: Jumlah user yang menonton anime
22.  Completed: Jumlah user yang selesai menonton
23.  On-Hold: Jumlah user yang hold anime
24.  Dropped: Jumlah user yabg drop anime
25.  Plan to Watch': Jumlah user yang berencana menonton
26.  Score-10': jumlah user yang memberi rating 10
27.  Score-9': jumlah user yang memberi rating 9
28.  Score-8': jumlah user yang memberi rating 8
29.  Score-7': jumlah user yang memberi rating 7
30.  Score-6': jumlah user yang memberi rating 6
31.  Score-5': jumlah user yang memberi rating 5
32.  Score-4': jumlah user yang memberi rating 4
33.  Score-3': jumlah user yang memberi rating 3
34.  Score-2': jumlah user yang memberi rating 2
35.  Score-1': jumlah user yang memberi rating 1

`reviews.csv`
Jumlah data 192112
1. uid : ID User
2.  profile  : User profile
3.  anime_uid :  ID Anime
4.  text : Text review
5.  score : Rating
6.  scores : Semua rating
7. link : Link review

- **Sebaran data**
Sebaran data genre anime
![Sebaran data genre anime](https://github.com/auriwan/Recommendation-system/blob/image/image/Distribusi%20sebaran%20genre%20anime.png?raw=true)
terdapat 47 data genre dan dari data diatas genre paling banyak adalah Comedy

10 Anime dengan rating tertinggi
![Sebaran Rating 10 anime  tertinggi](https://github.com/auriwan/Recommendation-system/blob/image/image/Distribusi%20sebaran%20rating%20dari%2010%20anime%20tertinggi.png?raw=true)

Terlihat pada gambar diatas anime dengan rating tertinggi dipegang oleh Sword Art Online


**Rubrik/Kriteria Tambahan (Opsional)**:

- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

##  Data Preparation

1. Check missing value
Pada tahapan ini Penulis memeriksa apakah ada data kosong atau missing value, karena missing value ini akan mempengaruhi keakuratan rekomendasi karena terdapat banyak data yang kosong dan setelah diperiksa tidak ada missing value pada kedua dataset. Jadi penulis tidak perlu melakukan drop  data.
2.  Check Duplikasi data
Selanjutnya memeriksa data duplikat. Duplikat juga akan memperlama pemrosesan data karena itu data duplikat harus kita hapus. Setelah dilakukan pengecekan tidak terdapat data duplikat pada dataset anime, sedangkan pada dataset rating terdapat 61593 data duplikat jadi data ini harus dihapus.
3. Menggabungkan data

**Rubrik/Kriteria Tambahan (Opsional)**:

- Menjelaskan proses data preparation yang dilakukan

- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

##  Modeling

Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**:

- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.

- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

##  Evaluation

Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:

- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_

- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_

- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
