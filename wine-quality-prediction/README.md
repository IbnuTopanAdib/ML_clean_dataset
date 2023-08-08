# Predictive Analysis, Prediksi Kualitas White-wine

## Latar Belakang

Kualitas white-wine mengacu pada faktor-faktor yang digunakan untuk memproduksi white-wine, serta indikator atau karakteristik yang menunjukkan apakah white-wine tersebut berkualitas tinggi. Prediksi kualitas white-wine merupakan hal yang penting baik untuk pengoleksi white-wine dan juga para profesional pembuat white-wine. bagi para pengoleksi white-wine prediksi kualitas white-wine akan sangat berguna dikarenakan mereka bisa berada di posisi yang baik untuk melakukan pembelian white-wine. Selain itu dengan meningkatnya permintaan white-wine berkualitas tinggi, penilaian kualitas white-wine yang akurat sangat penting bagi para profesional pembuat white-wine untuk mempertahankan reputasi mereka dan memenuhi harapan konsumen.

## Business Understanding

### Problem Statements

Berdasarkan Latar belakang masalah tersebut, dikembangkan sebuah sistem prediksi kualitas white-wine untuk menjawab permasalahan berikut.

1. Fitur apa yang paling berpengaruh pada kualitas white-wine
2. Bagaimana kualitas white-wine berdasarkan fitur - fitur tertentu

### Goals

Adapun tujuan dibuatnya prediksi kualitas white-wine adalah sebagai berikut:

1. Membuat model machine learning yang dapat memprediksi kualitas white-wine seakurat mungkin berdasarkan fitur-fitur yang ada.
2. Mengetahui fitur yang paling mempengaruhi kualitas dari white-wine

### Solution Statements

- Prediksi kualitas white-wine dapat diselesaikan dengan model regresi, di mana tujuan dari model regresi adalah untuk memprediksi nilai numerik kontinu (skor kualitas) berdasarkan fitur input yang terkait dengan sifat white-wine. Regresi adalah pendekatan yang cocok untuk masalah ini diakarenakan berfokus pada pemodelan hubungan antara variabel input dan variabel target, sehingga kita dapat membuat prediksi yang berada dalam rentang yang kontinu.


- Metrik yang digunakan untuk mengevaluasi seberapa akurat prediksi yang dibuat adalah Mean Absolute Error(MSE). Mean Absolute Error (MAE) adalah salah satu metrik evaluasi untuk mengukur seberapa dekat prediksi model regresi yang kita buat(y predict) terhadap nilai sebenarnya (y). MAE mengukur rata-rata selisih absolut antara nilai prediksi dan nilai sebenarnya.

- Pengembangan model akan menggunakan beberapa algoritma regresi diantaranya adalah: K-Nearest Neighbor(KNN), Support Vector Regression(SVR), dan Boosting Algorithm. Dari ketiga model ini, akan dipilih satu model yang memiliki nilai mae paling kecil dan waktu pelatihan yang singkat selain itu juga dipertimbangkan masalah overfitting yaitu model yang terlalu yang terlalu akurat pada data training namun tidak bisa menggeneralisir pola sehingga model tidak bisa bekerja dengan baik pada data yang tidak pernah dilihat sebelumnya yaitu data test.


## Data Understanding

Berikut adalah informasi umum mengenai dataset yang digunakan:


<table border>
  <tr>
    <td>Sumber Dataset</td>
    <td>UCI Machine Learning Repository: <a href ="https://archive.ics.uci.edu/dataset/186/white-wine+quality">Link</a></td>
  </tr>
  <tr>
    <td>Nama Dataset</td>
    <td>wine quality</td>
  </tr>
  <tr>
      <td>Area subjek</td>
      <td>Bisnis</td>
  </tr>
  <tr>
      <td>Masalah Terkait</td>
      <td>Klasifikasi dan Regresi</td>
  </tr>

  <tr>
      <td>Jumlah Atribut/fitur</td>
      <td>12</td>
  </tr> 
  <tr>
      <td>Jumlah Instance</td>
      <td>4898</td>
  </tr> 
</table>

### Exploratory Data Analysis (EDA)

#### Deskripsi Variabel

Pada berkas yang diunduh terdapat dua dataset yaitu winequality-red.csv dan winequality-white.csv namun dikarenakan pada project ini kita hanaya menyelesaikan masalah prediksi kualitas white-wine bukan untuk mengklasifikasikan red-wine dan white-wine maka kedua kita hanya akan menggunakan winequality-red.csv. dataset tersebut memiliki 4898 baris dan 12 kolom berikut adalah informasi mengenai atribut/fitur pada dataset.

<table border>
    <tr>
        <th>Fitur</th>
        <th>Penjelasan</th>
    </tr>
    <tr>
        <td><strong>Fixed Acidity</strong> (Kekuatan Asam Tetap)</td>
        <td>Kekuatan asam non-volatil dalam white-wine. Berkontribusi pada keasaman keseluruhan dan profil rasa white-wine.</td>
    </tr>
    <tr>
        <td><strong>Volatile Acidity</strong> (Kekuatan Asam Volatil)</td>
        <td>Kekuatan asam yang mudah menguap dalam white-wine. Kadar kekuatan asam volatil yang tinggi dapat menghasilkan rasa cuka dan berdampak negatif pada kualitas white-wine.</td>
    </tr>
    <tr>
        <td><strong>Citric Acid</strong> (Asam Sitrat)</td>
        <td>Kandungan asam sitrat dalam white-wine yang mempengaruhi tingkat keasaman dan kesegarannya.</td>
    </tr>
    <tr>
        <td><strong>Residual Sugar</strong> (Sisa Gula)</td>
        <td>Jumlah gula yang tersisa dalam white-wine setelah fermentasi. Mempengaruhi tingkat manis dan keseimbangan white-wine.</td>
    </tr>
    <tr>
        <td><strong>Chlorides</strong> (Klorida)</td>
        <td>Konsentrasi garam, khususnya klorida, dalam white-wine yang mempengaruhi rasa dan persepsi keseluruhan.</td>
    </tr>
    <tr>
        <td><strong>Free Sulfur Dioxide</strong> (Sulfur Dioksida Bebas)</td>
        <td>Jumlah sulfur dioksida bebas dalam white-wine. Sulfur dioksida sering ditambahkan sebagai pengawet.</td>
    </tr>
    <tr>
        <td><strong>Total Sulfur Dioxide</strong> (Total Sulfur Dioksida)</td>
        <td>Jumlah total sulfur dioksida dalam white-wine, termasuk bentuk bebas dan terikat.</td>
    </tr>
    <tr>
        <td><strong>Density</strong> (Kepadatan)</td>
        <td>Massa white-wine per unit volume. Dipengaruhi oleh kandungan gula dan tingkat alkohol.</td>
    </tr>
    <tr>
        <td><strong>pH</strong></td>
        <td>Tingkat keasaman white-wine yang memengaruhi stabilitas, rasa, dan keseimbangan white-wine.</td>
    </tr>
    <tr>
        <td><strong>Sulphates</strong> (Sulfat)</td>
        <td>Konsentrasi senyawa sulfur yang ditambahkan sebagai zat pengawet.</td>
    </tr>
    <tr>
        <td><strong>Alcohol</strong> (Alkohol)</td>
        <td>Kandungan alkohol dalam white-wine yang memengaruhi keberanian, rasa, dan rasa panas white-wine.</td>
    </tr>
    <tr>
        <td><strong>Quality</strong> (Kualitas)</td>
        <td>Peringkat kualitas white-wine</td>
    </tr>
</table>

#### Menangani Missing Value dan Outliers

##### Menangani Missiing Value

berdasarkan informasi dari sumber dataset yaitu UCI Machine Learning Repository dataset tidak memiliki missing value. Oleh karena itu, tidak ada penanganan khusus terhadap missing value. 

##### Menangani Outliers 

Untuk mengetahui apakah terdapat outlier pada dataset dilakukan visualisasi menggunakan boxplot untuk demua fitur yang ada pada dataset.
![Box Plot 1](assets/boxplot1.png)

berdasarkan visualisasi diatas ditemukan beberapa outlier pada dataset untuk menangani outlier tersebut kita bisa menggunakan IQR method.

IQR sangat berguna dalam menemukan outlier, yang merupakan nilai yang secara signifikan berbeda dari data lainnya. Kita dapat menggunakan IQR untuk mengidentifikasi outlier dengan mempertimbangkan nilai yang berada di bawah kuartil pertama (Q1) atau di atas kuartit ketiga (Q3). Nilai apa pun di luar batas-batas ini dianggap sebagai outlier. 

![IQR](assets/iqr.png)

berikut adalah visualisasi boxplot setelah dilakukan pembersihan outlier

![Box Plot 2](assets/boxplot2.png)

visualisasi tersebut menunjukan bahwa sudah tidak terdapat lagi outlier pada dataset.


#### Univariate Analysis

Untuk menganalisis setiap fitur dalam dataset white-wine kita akan melihat histogram masing-masing fiturnya

![Histogram](assets/histogram.png)

Berdasarkan Histogram tersebut dapat disimpulkan banyak informasi diantaranya:

1. distribusi data tingkat kekuatan asam yang tidak volatile(fixed acidity) bersifat normal (bell curved ) dimana nilai median dan rata-ratanya hampir sama. sehingga dapat disimpulkan jika rata-rata white-wine memiliki tingkat kekuatan asam sekitar nilai median yang diperkirakan sekitar 6.8.

2. distribusi data tingkat kekuatan asam volatile(volatile acidity) bersifat normal (bell curved ) dimana nilai median dan rata-ratanya hampir sama. sehingga dapat disimpulkan jika rata-rata white-wine memiliki tingkat kekuatan asam sekitar nilai median yang diperkirakan sekitar 0.26.

3. Distribusi data tingkat asam sitrat juga bersifat normal (bell curved ) dimana nilai median dan rata-ratanya hampir sama. sehingga dapat disimpulkan jika rata-rata white-wine memiliki kadar asam sitrat sekitar nilai mediannya yang diperkirakan sekitar 0.31. namun terdapat peak yang akan mempengaruhi nilai rata ratanya. tapi peak tersebut hanya satu sehingga nilai rata-rata pun tidak terlalu berpengaruh.

4. Tingkat residual sugar atau gula tersisa dalam white-wine kebanyakan rendah hal ini dikarenakan frekuensi dari white-wine yang memiliki residual sugar rendah sangat tinggi sehingga bisa disimpulkan kebanyakan white-wine tidak begitu manis.

5. tingkat konsentrasi cloride atauu klorida dalam white-wine kebanyakan berada disekitar 0.03 sampai 0.05.

6. Distribusi data Jumlah sulfur dioksida bebas dalam white-wine tidak terdistribusi secara seragam hal ini dibuktikan dengan banyaknya peak dalam histogram.

7. Distribusi data total sulfur dioksida dalam white-wine juga bersifat normal (bell curved ) dimana nilai median dan rata-ratanya hampir sama. sehingga dapat disimpulkan jika rata-rata total sulfur dioksida dalam white-wine sekitar nilai mediannya yang diperkirakan sekitar 125.

8. Density atau massa jenis dari white-wine berada antara 0.998 dan 1.

9. pH dari white-wine kebanyakan berada sekitar 3.0 - 3.4.

10. kebanyakan white wine memiliki kadar senyawa sulfat sekitar 0.49 - 50.

11. Kebanyakan dari white-wine memiliki tingkat alkohol sekitar 9.5 dan sangat sedikit sekali white-wine yang memiliki tingkat alkohol dibawah 9 dan diatas 13.

12. Tingkat kualitas dari white-wine sebenarnya berada antara 4-9 namun dikarenakan white-wine yang memliki kualitas 8 dan 9 sangatlah sedikit maka tingkat kualitas tersebut dianggap outlier. sehingga kualitas white-wine pada data hanya dari 4 - 7
dimana kebanyakn white-wine memiliki kualitas 6.


#### Multivariate Analysis

Multivariate EDA menunjukkan hubungan antara dua atau lebih variabel pada data. Untuk mengamati hubungan antara fitur dalam dataset, kita akan menggunakan fungsi pairplot().

![Pairplot](assets/pairplot.png)

hasil visualisasi tersebut menunjukan jika tidak ada fitur yang berkorelasi tinggi dengan fitur target yaitu `quality` atau kualitas white-wine.

Untuk lebih mendalam memahami korelasi antar fitur digunakan Parameter correlation. Parameter ini digunakan untuk mengidentifikasi korelasi atau hubungan dari dua feature numerik dalam sebuah data. Korelasi ini digambarkan menggunakan nilai dengan rentang -1 hingga 1.

Pada parameter correlation, nilai negatif menggambarkan korelasi berlawanan (negative correlation), sedangkan nilai positif merepresentasikan korelasi bersesuaian (positive correlation). Jika correlation dari dua feature bernilai nol, keduanya dinyatakan tidak memiliki korelasi (no correlation).

Banyak fitur yang kurang berkorelasi dengan fitur target sehingga kita bisa menghapus fitur-fitur tersebut namun fitur yang dihapus hanya fitur yang korelasinya kurang dari 0.1 atau -0.1 hal ini dikarenakan jika kita menghapus banyak fitur tentunya kita akan kehilangan informasi yang mungkin berguna dari fitur tersebut. fitur tersebut diantaranya adalah 'residual sugar', 'pH', 'sulphates', 'free sulfur dioxide', 'total sulfur dioxide'.

## Data preparation

Pada tahap ini kita akan membuat data menjadi lebih mudah untuk diproses oleh model Machine Learning. Pada tahap ini kita akan melakukan 2 hal yaitu membagi data menjadi data training dan data test. selanjutnya kita akan melakukan feature scaling menggunakan standard scaler.

### Train Test Split

Sebelum dilakukan feature scaling seperti normalisasi ataupun standarisasi terlebih dahulu kita bagi terlebih dahulu dataset menjadi 2 bagian yaitu data train dan data test. proporsi yang digunakan dalam pembagian ini adalah  80:20 yang artinya 80% dari data akan dijadikan training set atau data yang digunakan untuk melatih model, dan 20 % dari data akan dijadikan test set atau data yang digunakan untuk menguji model.

### Standarisasi 

Fefeature scaling yang digunakan adalah standard scaler. StandardScaler melakukan proses standarisasi fitur dengan mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standar deviasi untuk menggeser distribusi.  StandardScaler menghasilkan distribusi dengan standar deviasi sama dengan 1 dan mean sama dengan 0. Sekitar 68% dari nilai akan berada di antara -1 dan 1.


## Modeling

Seperti yang dijelaskan pada tahap Business Understanding kita akan mengembangkan model machine learning dengan tiga algoritma yang berbeda. Kemudian, kita akan membandingkan mean absolute error dan waktu training masing-masing algoritma dan menentukan algoritma mana yang memberikan hasil prediksi terbaik. Ketiga algoritma tersebut antara lain:

1. K-Nearest Neighbor (KNN)
2. Support Vector Regression (SVR)
3. Boosting Algorithm


### K-Nearest Neighbor

Pertama kita akan membuat model machine learning dengan menggunakan algoritma KNN 

Kita menggunakan paremeter k = 10 tetangga dan metric default atau bawaan dari sklearn yaitu Euclidean selanjutnya kita melatih model tersebut dengan data train yang sudah kita siapkan sebelumnya. 

kemuadian waktu dari training model akan disimpan dalam dataframe yang sudah dibuat sebelumnya yang nantinya akan digunakan untuk membandingkan algoritma mana yang paling cepat.

Selanjutnya kita akan menyimpan hasil prediksi dari model untuk kemudian dilakukan evaluasi terhadap model pada tahap evaluasi 

### SVR

Kedua kita akan membuat model machine learning dengan menggunakan algoritma SVR

parameter yang digunakan antara lain adalah sebagai berikut:

- Kernel, Kernel adalah fungsi yang digunakan untuk mengukur seberapa mirip dua titik data dalam ruang fitur yang lebih tinggi: kernel yang digunakam adalah kernel rbf
- Parameter C Parameter C mengendalikan trade-off antara error pelatihan dan kompleksitas model: parameter c yang digunakan adalah 100
- Parameter gamma Parameter gamma mengontrol seberapa banyak pengaruh satu titik data tunggal: parameter gamma yang digunakan adalah 0.1

Selanjutnya kita akan menyimpan waktu training dari model untuk kemudian dilakukan evaluasi terhadap model pada tahap evaluasi.

### Boosting Algorithm

Terakhir kita akan membuat model Machine learning dengan Boosting Algorithm

Parameter yang digunakan antara lain adalah 

- learning_rate bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting : learning rate yang digunakan adalah 0.05
- random_state: digunakan untuk mengontrol random number generator yang digunakan:random_state yang digunakan adalah 123

sama seperti sebelumnya kita akan menyimpan waktu training dari model untuk kemudian dilakukan evaluasi terhadap model pada tahap evaluasi.

## Evaluasi

Setelah dilakukan pelatihan terhadap ketiga model machine learning kita akan mencari model yang memiliki performa terbaik yaitu waktu pelatihan yang relatif singkat dan error yang paling minim dari ketiga model.

### Mean Absolute Error (MAE) Model

Mean Absolute Error (MAE) adalah salah satu metrik evaluasi untuk mengukur seberapa dekat prediksi model regresi yang kita buat(y predict) terhadap nilai sebenarnya (y). MAE mengukur rata-rata selisih absolut antara nilai prediksi dan nilai sebenarnya. berikut adalah formula untuk menghitung MAE.

![Box Plot 1](assets/mae_formula.png)

Berikut adalah MAE ketiga model machine learning yang telah kita buat:

![Box Plot 1](assets/mae.png)

Berdasarkan nilai-nilai MAE di atas, kita dapat menyimpulkan beberapa hal:

- Model SVM memiliki performa yang lebih baik daripada model KNN dan Boosting pada kedua data training dan data test. Ini ditunjukkan oleh fakta bahwa nilai MAE untuk SVM lebih rendah daripada nilai MAE untuk model lainnya. namun model ini mengalami overfitting yang ditandai dengan error yang lebih tinggi pada data test

- Model Boosting memiliki MAE yang lebih rendah pada data training dan data testing daripada model KNN, namun model ini juga sedikit mengalami overfitting 

- Model KNN memiliki performa yang paling rendah dari ketiga model ini pada kedua data training dan data test. 

Kesimpulannya, berdasarkan nilai-nilai MAE ini, model SVM memiliki performa terbaik di antara ketiga model ini untuk memprediksi kualitas white-wine namun model ini mengalami overfitting.

### Waktu training Model
Berikut adalah waktu yang dibutuhkan untuk melatih ketiga model machine learning yang telah kita buat:

![Box Plot 1](assets/timex.png)

Model KNN memiliki waktu training yang sangat singkat dibandingkan dengan kedua model lainnya. Model Boosting memiliki waktu training kedua lebih cepat dibandingkan SVM sedangkan model SVM memiliki waktu yang jauh lebih lama dibandingkan 2 model lainnya.


### Kesimpulan
Setelah membandingkan akurasi dan juga waktu training model dapat disimpulkan jika model terbaik untuk memprediksi kualitas white-wine adalah model KNN dikarenakan model ini memiliki error yang tidak terlalu tinggi dan waktu training yang relatif singkat.
