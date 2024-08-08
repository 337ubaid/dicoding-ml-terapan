# Laporan Proyek Machine Learning - Muhammad Ubaidillah


## Domain Proyek
Sepakbola merupakan salah satu olahraga yang sangat populer dengan berbagai penggemar di seluruh dunia ([Artnzen, 2021](https://himolde.brage.unit.no/himolde-xmlui/bitstream/handle/11250/3036758/smj_team_vs_players_R2.pdf?sequence=2)). Evaluasi pemain perlu dilakukan untuk memperbaiki kelemahan dan meningkatkan potensi dari tim. Evaluasi tidak dapat dilakukan secara subjektif pelatih, tetapi harus dilakukan secara objektif dan ilmiah berdasarkan statistik yang ada di lapangan. Penilaian ini dapat dilakukan dengan analisis statistik dengan memprediksi rating musim sehingga membantu dalam memahami kontribusi pemain terhadap kinerja tim. 

<!-- 
**Rubrik/Kriteria Tambahan (Opsional)**:
- Jelaskan mengapa dan bagaimana masalah tersebut harus diselesaikan
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.  
-->

## Business Understanding

menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

<!-- **Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Statement” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution statement. Misalnya, menggunakan dua atau lebih algoritma untuk mencapai solusi yang diinginkan atau melakukan improvement pada baseline model dengan hyperparameter tuning.
    - Solusi yang diberikan harus dapat terukur dengan metrik evaluasi. -->

## Data Understanding
Data yang digunakan merupakan data [Football Players Datasets 2015 - 2024](https://www.kaggle.com/datasets/abdulmalik1518/football-players-datasets-2015-2024/) yang bersumber dari [Kaggle](https://www.kaggle.com/). Dataset ini merupakan data yang dipublikasikan pada 29 Juli 2024 oleh [Abdul Malik](https://www.kaggle.com/abdulmalik1518). Berikut penjelasan seluruh fitur dalam dataset :

### Fitur pada Football Players Datasets 2015 - 2024 
- Teams           : Nama klub sepak bola di mana pemain tersebut bernaung selama musim tersebut.
- Seasons         : Musim sepak bola tertentu ketika statistik pemain dicatat, misal 2023/2024
- Players         : Nama pemain yang statistiknya dicatat
- Matches         : Jumlah pertandingan yang dimainkan oleh pemain dalam 1 musim sepak bola
- Goals           : Jumlah goal yang dicetak oleh pemain dalam 1 musim sepak bola
- Assists         : Jumlah assists yang diberikan oleh pemain dalam 1 musim sepak bola
- Seasons Ratings : Penilaian kualitas kinerja pemain selama 1 musim sepak bola

### Exploratory Data Analysis (EDA)
Library yang digunakan pada tahap EDA
```py
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```
#### Data Load
```py
df = pd.read_csv('football.csv')
```
#### Bentuk dari dataset
```py
df.shape
```
> Dataset memiliki 1,216 baris dan 7 kolom fitur.
#### Informasi dataset
```py
df.info()
```
> Tidak ada data yang bernilai `null`. Terdapat 3 fitur bertipe string (Teams, Seasons, Players) dan 4 fitur bertipe numerik (Mathes, Goals, Assists, Seasons Ratings).
#### Korelasi antar fitur numerik 
```py
numerical_features = df.select_dtypes(include=['number']).columns.to_list() # ['Matches', 'Goals', 'Assists', 'Seasons Ratings']
correlation_matrix = df[numerical_features].corr().round(2)
 
plt.figure(figsize=(10, 8))
sns.heatmap(data=correlation_matrix, annot=True, cmap='coolwarm', linewidths=0.5, vmin=-1, vmax=1)
```
> Semua kolom numerik saling berkolerasi selaras satu sama lain

<!-- 
**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis. -->

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

