#  Laporan Proyek Machine Learning - Auriwan Yasper

##  Project Overview

Pada Proyek kali ini domain proyek yang penulis pilih adalah mengenai hiburan yaitu "Anime Recommendation system".

**Latar Belakang**
Saat ini kartun jepang atau *anime* mengalami perkembangan yang sangat cepat dan penggemarnya tersebar diseluruh dunia. Terutama dengan merebaknya pandemi yang serba terbatas, membuat kebutuhan manusia akan hiburan semakin bertambah, salah satunya kartun jepang ini. Sudah banyak sekali platform yang menyediakan media hiburan seperti kartun jepang. Tentunya sebagai salah satu strategi marketing dalam dunia bisnis, UX atau user experience merupakan hal yang sangat penting bagi perkembangan platform tersebut. Maka salah satu strategi yang disiapkan perusahaan agar user betah dengan platform tersebut adalah adalah sistem rekomendasi mengenai sesuatu atau apa saja yang mungkin disukai oleh user. Disinilah Machine learning akan bekerja, dengan mengumpulkan data dari user, perusahaan harus mampu membuat suatu sitem rekomendasi yang mungkin akan disukai oleh pengguna.

Terdapat cukup banyak pendekatan yang bisa digunakan dalam sistem rekomendasi diantaranya Content-Based-Filtering, Collaborative-Filtering, Multi-criteria, risk aware, hybrid-filtering dan lainnya. Badal Soni et al [[1]](https://arxiv.org/abs/2106.12970) dengan RikoNet-nya menggabungkan pendekatan content-based dan collaborative filtering dalam sistem rekomendasi yang dibuatnya. Begitu juga Sistem rekomendasi yang dirancang oleh Ramashini et al[[2]](http://ir.kdu.ac.lk/handle/345/4173) yang juga menggunakan kombinasi antara content-base dan collaborative filtering. Kumar et al[[3]](https://www.ijcaonline.org/archives/volume124/number3/22082-2015904111) dengan MOV REC-nya mengajukan sistem rekomendasi dengan pendekatan collaborative filtering yang menggunakan informasi yang disediakan oleh penguna, lalu menganalisanya dan mebuat list rekomendasi yang cocok untuk para pengguna.

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

sebaran 10 Anime dengan rating tertinggi
![Sebaran Rating 10 anime  tertinggi](https://github.com/auriwan/Recommendation-system/blob/image/image/Distribusi%20sebaran%20rating%20dari%2010%20anime.png?raw=true)

Terlihat pada gambar diatas anime dengan rating tertinggi dipegang oleh Death Note

##  Data Preparation

- Content-Based-filtering
	1. Check missing value
Pada tahapan ini Penulis memeriksa apakah ada data kosong atau missing value, karena missing value ini akan mempengaruhi keakuratan rekomendasi karena terdapat banyak data yang kosong dan setelah diperiksa tidak ada missing value pada kedua dataset. Jadi penulis tidak perlu melakukan drop  data.
	2.  Check Duplikasi data
Selanjutnya memeriksa data duplikat. Duplikat juga akan memperlama pemrosesan data karena itu data duplikat harus kita hapus. Setelah dilakukan pengecekan tidak terdapat data duplikat pada dataset anime, sedangkan pada dataset rating terdapat 61584 data duplikat jadi data ini harus dihapus.
- Collaborative filtering
Pada algoritma ini tahapan persiapan datanya sama dengan content base filtering, yaitu check missing value dan check duplikasi data pada data rating, yang berbeda hanya pada tahapan menggabungkan data anime dan rating. Karena pada algoritma collaborative filtering kita membutuhkan data rating atau score, user id, serta anime_id, jadi kita harus menggabungkan data anime dan rating. Setelah data digabungkan, penulis melakukan encoder pada user id dan anime id agar data dapat dilatih dengan maksimal oleh model. Kemudian data yang sudah diencode anak di mapping kedalam data yang digunakan dan juga mengubah nilai rating menjadi float. Selanjutnya barulah data dibagi menjadi training dan data test.

##  Modeling

Model yang penulis gunakan adalah deep learning dan cosine similarity. Deep learning untuk sistem rekomendasi dengan algoritma Collaborative learning dan cosine similarity untuk Conten-based-learning.

1. Content Based Filtering
Pada model ini langkah pertama yang dilakukan ialah melakukan ekstraksi fitur pada genre. Fungsi digunakan adalah tfidfvectorizer() dari library sklearn. Setelah data diekstraksi tahapan selanjutnya adalah melakukan fit dan transformasi ke dalam bentuk matriks, outputnya adalah berupa matriks 17562 x 47 yang merupakan representasi jumlah data anime dan jumlah genre anime.

	Untuk menghitung derajat kesamaan (_similarity degree_) antar anime, penulis menggunakan teknik  _cosine similarity_  dengan fungsi  _cosine_similarity_  dari  _library_  sklearn. Data yang digunakan adalah data matriks yang sudah penulis dapatkan sebelumnya.
	Langkah selanjutnya yaitu menggunakan  _argpartition_  untuk mengambil sejumlah nilai k tertinggi dari  _similarity_  data kemudian mengambil data dari bobot (tingkat kesamaan) tertinggi ke terendah. Kemudian menguji akurasi dari sistem rekomendasi ini untuk menemukan rekomendasi anime yang mirip dari anime yang ingin dicari.

-   Kelebihan
    
    -   Akurasi akan cukup bagus dengan banyaknya informasi yang diberikan pengguna.
-   Kekurangan
    
    -   Hanya dapat digunakan untuk fitur yang sesuai, seperti film, anime, buku, dan lain-lain.
    -   Tidak mampu menentukan profil dari user baru.

Berikut ini adalah konten yang dijadikan referensi untuk menentukan 10 rekomendasi anime tertinggi yang memiliki kesamaan genre yang sama:
![Reference of Recommendation](https://github.com/auriwan/Recommendation-system/blob/image/image/referensi%20rekomendasi.PNG?raw=true)

Terlihat pada tabel diatas bahwasannya penulis akan menguji coba model berdasarkan judul anime "Cowboy Bebop" dengan genre Action, Adventure, comedy, Drama, Sci-fi, dan Space.

Berikut ini adalah hasil rekomendasi tertinggi dari model  _Content Based Filtering_  berdasarkan referensi anime diatas:
![Rekomendasi](https://github.com/auriwan/Recommendation-system/blob/image/image/rekomendasi.PNG?raw=true)

3. Collaborative Filtering
Pada Model ini data yang akan digunakan adalah data gabungan antara data anime dan data rating. User id dan anime_id akan diencode dan dimapping kedalam data dan data rating akan diubah menjadi float. Selanjutnya data akan displit menjadi data train dan data test sebesat 80% untuk data training dan 20% untuk data validasi.

	Lalu penulis melakukan proses _embedding_ terhadap data anime dan pengguna. Lalu lakukan operasi perkalian _dot product_ antara _embedding_ pengguna dan anime. Selain itu, penulis juga menambahkan bias untuk setiap pengguna dan anime. Skor kecocokan ditetapkan dalam skala [0,1] dengan fungsi aktivasi _sigmoid_. Untuk mendapatkan rekomendasi anime, data gabungan akan diacak terlebih dahulu dan mendefinisikan variabel _movie_not_watched_ yang merupakan daftar anime yang belum pernah ditonton oleh pengguna.
	Berikut adalah kelebihan dan kekurangan dari algoritma collaborative filtering
-   Kelebihan
    -   Tidak memerlukan atribut untuk setiap itemnya.
    -   Dapat membuat rekomendasi tanpa harus selalu menggunakan dataset yang lengkap.
    -   Unggul dari segi kecepatan dan skalabilitas.
    -   Rekomendasi akan tetap berjalan meski data sulit dianalisis
-   Kekurangan
    -   Membutuhkan parameter rating, sehingga jika ada item baru sistem tidak akan merekomendasikan item tersebut.
    
    Berikut ini adalah hasil rekomendasi anime tertinggi untuk user 35511:
    ![Rekomendasi](https://github.com/auriwan/Recommendation-system/blob/image/image/rekomendasi%20collaborative.PNG?raw=true)
    

##  Evaluation


Evaluasi yang akan penulis lakukan disini yaitu evaluasi dengan Mean Absolute Error (MAE) dan Root Mean Squared Error (RMSE) pada Collaborative Filtering dan Precision Content Based Filtering

## Content Based Filtering

Pada evaluasi model ini penulis menggunakan metrik precision content based filtering untuk menghitung precision model sistem telah dibuat sebelumnya.
Precision ini menghitung jumlah data relevan dibagi dengan jumlah item yang kita rekomendasikan.
rumus untuk precision adalah sebagai berikut 
![formula presisi](https://github.com/auriwan/Recommendation-system/blob/image/image/precision_formula.png?raw=true)

hasil dari tesnya adalah sebagai berikut:
![Hasil tes presisi](https://github.com/auriwan/Recommendation-system/blob/image/image/hasil%20tes%20presisi.PNG?raw=true)
Data referensi kita yaitu Cowboy Bebop memiliki 6 genre yaitu Action, adventure, Comedy, Drama, Sci-fi, dan Space. 
Lalu hasil rekomendasi yang relevan hanya 1 yang sama persis memiliki 6 genre yaitu anime dengan judul yang sama juga yaitu Cowboy Bebop: Yose Atsuma Blues. Akan tetapi terdapat 7 anime dengan genre yang sama sebanyak 5 genre, sehingga data ini juga relevan dengan anime referensi yang kita gunakan. Jadi Presisi sistem kita sebesar 8/10 atau 80%.

##  Collaborative Filtering
1. Mean Absolute Error (MAE)
	MAE mengukur berapa besar rata-rata kesalahan yang dilakukan oleh model yang sudah dilatih kepada data tes, tampa mempertimbangkan arahnya. Semakin rendah nilai MAE makan akan semakin baik model yang sudah dirancang.
	Formula MAE:
	![formula mae](https://camo.githubusercontent.com/c77f373a758989aaf94b5c9adbafb11c41f25b6baeb47c93a328ed4a94f16cd4/68747470733a2f2f67697367656f6772617068792e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031342f30382f6d61652d666f726d756c612e706e67)
	Berikut hasil grafik MAE
	![Grafik mae](https://github.com/auriwan/Recommendation-system/blob/image/image/grafik%20MAE.png?raw=true)
	Berdasarkan fitting diatas nilai error model adalah dibawah 0.025, sedangkan nilai error untu validasi diatas 0.200
	
3. Root Mean Squared Error (RMSE)
RMSE merupakan aturan penilaian kuadrat yang juga mengukur besarnya rata-rata error, semakin kecil errornya maka model semakin baik
Rumus RMSE adalah sebagai berikut:
![Rumus RMSE](https://github.com/auriwan/Recommendation-system/blob/image/image/rumus%20RMSE.jpg?raw=true)
Berikut Grafik RMSE
![Grafik RMSE](https://github.com/auriwan/Recommendation-system/blob/image/image/Grafik%20MSE.png?raw=true)

Dari Grafik diatas dapat kita lihat bahwa niliai error RMSE adalah dibawah 0.05 pada data training, dan diatas 0.20 pada data tes. Nilai error ini cukup bagus unutk sistem rekomendasi anime, bisa kita lihat pada gambar berikut

![Rekomendasi](https://github.com/auriwan/Recommendation-system/blob/image/image/rekomendasi%20collaborative.PNG?raw=true)
cukup banyak anime dengan genre yang sesuai dengan yang sudah diberi rating oleh user, jadi bisa dibilang rekomendasinya cukup bagus.
