# UTS-AVD-HARITS-2509116048

## UTS-AVD: Explanatory Data Analysis (EDA) Faktor Peringkat Anime Menggunakan Dataset MyAnimeList

### **Informasi Penulis**
Nama: Harits
NIM: 2509116048
Dataset: anime (1).csv

### **Latar Belakang**
Industri anime global mengalami pertumbuhan pesat, didukung oleh platform streaming dan komunitas daring seperti MyAnimeList. Peringkat anime di platform ini ditentukan oleh berbagai indikator seperti skor (rating pengguna), jumlah anggota (`members`), popularitas, tipe anime (TV/Movie), dan jumlah episode.

Namun, seringkali ditemukan fenomena di mana anime dengan skor tinggi tidak selalu memiliki popularitas tertinggi, dan sebaliknya. Ini menimbulkan pertanyaan penting seperti apakah skor tinggi selalu berbanding lurus dengan jumlah `members`, apakah tipe anime berpengaruh pada popularitas, dan apakah tahun rilis mempengaruhi jumlah penonton serta peringkat.

Memahami faktor-faktor ini sangat krusial bagi platform streaming, distributor, dan rumah produksi hiburan untuk menentukan strategi promosi, lisensi, dan rekomendasi konten yang efektif. Oleh karena itu, diperlukan analisis mendalam terhadap variabel-variabel dalam dataset ini untuk mengidentifikasi faktor-faktor yang memengaruhi peringkat dan popularitas anime secara keseluruhan.

### **Tujuan Analisis**
*   Mengidentifikasi pola distribusi skor anime
*   Menganalisis hubungan antara `score` dan jumlah `members`
*   Membandingkan popularitas berdasarkan tipe anime (TV/Movie)
*   Menganalisis pengaruh jumlah episode terhadap jumlah `members`
*   Mengidentifikasi pengaruh tahun rilis terhadap `popularity` ranking
*   Mengetahui apakah anime dengan `score` yang tinggi selalu memiliki popularitas yang sama tinggi

### **Ringkasan Hasil EDA**
**1. Ringkasan Dataset**
| Aspek         | Nilai       |
| :------------ | :---------- |
| Total Baris   | 10,000      |
| Total Kolom   | 12          |
| Tipe Data     | Numerik dan Kategorikal |
| Rentang Score | 6.05 - 9.29 |

**2. Struktur Data**
Dataset terdiri dari 12 kolom dengan deskripsi sebagai berikut:

| Kolom        | Tipe    | Deskripsi                                                |
| :----------- | :------ | :------------------------------------------------------- |
| `anime_id`   | `int64` | ID unik untuk setiap anime.                              |
| `title`      | `object`| Judul anime.                                             |
| `score`      | `float64`| Skor atau rating rata-rata anime dari pengguna.        |
| `rank`       | `int64` | Peringkat anime berdasarkan skornya.                     |
| `popularity` | `int64` | Peringkat popularitas anime.                             |
| `members`    | `int64` | Jumlah anggota MyAnimeList yang telah menambahkan anime ini ke daftar mereka. |
| `synopsis`   | `object`| Ringkasan atau sinopsis cerita anime. (Ada 2 missing)    |
| `start_date` | `object`| Tanggal mulai tayang atau rilis anime. (Ada 2 missing)   |
| `end_date`   | `object`| Tanggal selesai tayang atau rilis anime. (Ada 84 missing)|
| `type`       | `object`| Tipe anime (misalnya: TV, Movie, OVA, ONA, dll).         |
| `episodes`   | `float64`| Jumlah episode dari anime. (Ada 48 missing)              |
| `image_url`  | `object`| URL gambar sampul atau poster anime.                     |

**3. Statistik Deskriptif**
**Variabel Numerik:**

| Statistik | `score` | `rank`   | `popularity` | `members`    | `episodes` |
| :-------- | :------ | :------- | :----------- | :----------- | :--------- |
| Mean      | 6.98    | 5000.49  | 6490.90      | 107530       | 15.70      |
| Std Dev   | 0.62    | 2886.89  | 4646.30      | 273351       | 41.86      |
| Min       | 6.05    | 1        | 1            | 226          | 1          |
| 25%       | 6.47    | 2500.75  | 2591.75      | 4270.25      | 1          |
| Median    | 6.90    | 5000.50  | 5564.50      | 18179        | 11         |
| 75%       | 7.39    | 7500.25  | 9824.25      | 84692.75     | 13         |
| Max       | 9.29    | 10000    | 22184        | 4262220      | 1787       |

**Variabel Kategorikal (Frekuensi):**
*   **`type`**: Terdapat 6 tipe unik, dengan 'TV' sebagai tipe paling dominan (43.3% dari total data).
*   **`title`**: 9999 judul unik dari 10000 data, dengan 1 duplikasi (`Ling Jian Zun 4th Season`).
*   **`start_date`**: Terdapat 68 tanggal mulai unik, dengan `2023-01-01` sebagai tanggal yang paling sering muncul (kemungkinan placeholder).

### **Key Findings (Temuan Utama)**
**1. Kualitas dan Kelengkapan Data**
*   **Missing Values**: Dataset sangat lengkap, dengan `synopsis` (0.02%), `start_date` (0.02%), `end_date` (0.84%), dan `episodes` (0.48%) memiliki missing values yang sangat kecil. Missing pada `end_date` kemungkinan karena status anime yang masih tayang (`ongoing`).
*   **Duplikasi**: Ditemukan 1 baris duplikat pada kolom `title` (`Ling Jian Zun 4th Season`).
*   **Outliers**: Kolom `members`, `popularity`, dan `episodes` menunjukkan keberadaan outlier yang signifikan, mengindikasikan distribusi yang tidak merata.

**2. Distribusi Score Anime**
*   Skor anime (`score`) terkonsentrasi antara 6 hingga 9, dengan distribusi yang relatif simetris dan sedikit kecenderungan ke kanan (mean sedikit lebih tinggi dari median). Ini menunjukkan dataset cenderung berisi anime dengan rating yang cukup tinggi.

**3. Popularitas dan Members**
*   Kolom `popularity` dan `members` menunjukkan distribusi `right-skewed` yang kuat. Ini berarti sejumlah kecil anime memiliki `fanbase` yang sangat besar (jutaan `members` dan popularitas tinggi), sementara mayoritas memiliki jumlah `members` dan tingkat popularitas yang relatif rendah.
*   Perbedaan ekstrem antara nilai min dan max pada `members` (226 vs 4.26 juta) mendukung adanya outlier signifikan.

**4. Dominasi Tipe Anime**
*   Tipe anime 'TV' adalah yang paling dominan dan memiliki proporsi popularitas tertinggi dibandingkan tipe lain seperti 'Movie' dan 'ONA', menunjukkan bahwa serial TV memiliki jangkauan dan pengaruh terbesar dalam dataset ini.

**5. Jumlah Episode Anime**
*   Jumlah episode (`episodes`) sangat bervariasi, dari 1 hingga 1787 episode. Adanya nilai maksimum yang sangat tinggi mengindikasikan keberadaan serial anime yang sangat panjang, seperti `One Piece` atau seri dengan banyak musim yang digabung.

**6. Korelasi Antara Popularitas dan Score**
*   Analisis korelasi antara `popularity` (sebagai peringkat, di mana nilai lebih kecil berarti lebih populer) dan `score` (rating) diharapkan menunjukkan korelasi negatif. Artinya, anime dengan peringkat popularitas lebih tinggi (`popularity` lebih kecil) cenderung memiliki `score` yang lebih tinggi, mengonfirmasi hubungan antara kualitas dan daya tarik bagi penonton.

**7. Anime dengan Episode Terbanyak**
*   Beberapa judul anime, seperti seri 'Gintama' dan 'Ling Jian Zun 4th Season', menonjol sebagai anime dengan jumlah episode terbanyak, mengindikasikan seri panjang atau banyak musim yang populer.

### **Kesimpulan**
Dataset anime ini, meskipun sangat bersih dengan sedikit *missing values* dan satu duplikasi, memiliki distribusi popularitas dan jumlah `members` yang sangat tidak merata (right-skewed), dipengaruhi oleh segelintir judul anime raksasa yang memiliki `fanbase` sangat besar. Tipe anime TV adalah yang paling dominan dan populer, dan terdapat hubungan antara kualitas (`score`) dengan popularitas (`rank`), di mana anime dengan `score` tinggi cenderung memiliki `rank` popularitas yang lebih baik. Jumlah episode juga sangat bervariasi, dengan keberadaan seri yang sangat panjang. Insights ini memberikan pemahaman awal tentang faktor-faktor yang membentuk popularitas dan peringkat anime di MyAnimeList, menyoroti pentingnya kualitas (`score`) dan durasi (`episodes`) dalam menarik perhatian `members` dan popularitas secara keseluruhan.

---

### **File dan Referensi**
Dataset: `anime (1).csv`

Notebook: `UTS_AVD_Harits.ipynb`

Platform: Google Colab dengan Python 3

Library: pandas, matplotlib, seaborn, numpy
