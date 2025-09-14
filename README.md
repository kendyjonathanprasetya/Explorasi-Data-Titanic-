# 🛳️ Pendahuluan: Analisis Dataset Titanic

Tragedi tenggelamnya kapal Titanic merupakan salah satu peristiwa bersejarah yang banyak diteliti menggunakan data. Dataset Titanic yang tersedia di seaborn berisi informasi penumpang seperti jenis kelamin, umur, kelas tiket, harga tiket, dan kota embarkasi. Dengan data ini, kita dapat mengeksplorasi faktor-faktor apa saja yang memengaruhi peluang seorang penumpang untuk selamat. Analisis ini menggunakan pendekatan eksplorasi data (EDA) dengan bantuan visualisasi, sehingga pola dan hubungan antarvariabel dapat terlihat lebih jelas.

# 🎯 Tujuan Analisis

Mengidentifikasi kondisi awal dataset, termasuk data hilang (missing value).

Mengeksplorasi distribusi data berdasarkan kategori seperti gender, kelas, dan kota embarkasi.

Melihat hubungan antarvariabel numerik seperti kelas tiket dan harga tiket.

Membuat variabel baru gabungan gender dan kota embarkasi untuk memperjelas pola survival.

Menjelaskan faktor utama yang berhubungan dengan peluang keselamatan penumpang Titanic.

# Data Awal TITANIC 
[Open In Google Colab](https://colab.research.google.com/drive/1BBnmCH8oSt7lcCzMBUD7Fbb4kOQmeCsJ?usp=sharing#scrollTo=btn0BuO-Fcus)

# Data Explorasi TITANIC 
[Open In Google Colab](https://colab.research.google.com/drive/15wAfiTE-5ZLW30irz7CfzG6m59UqWXmg#scrollTo=CYQ5s96reDes)

# Analisis Data Titanic
# 1. Import Library

Langkah ini memanggil library pandas, seaborn, dan matplotlib yang dipakai untuk membaca data Titanic dan membuat visualisasi.

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# 2. Load Dataset Titanic

Dataset Titanic bawaan seaborn dimuat. Dataset berisi 891 baris (penumpang) dan 15 kolom (variabel), misalnya age, sex, pclass, fare, embark_town, dan lain-lain.

titanic = sns.load_dataset("titanic")

# 3. Cek Data Awal

info() menunjukkan ada beberapa kolom dengan data hilang: age (177 missing), deck (688 missing), embark_town (2 missing).

print(titanic.info())

head() menampilkan 5 baris pertama dataset. Ini membantu melihat struktur data: siapa saja penumpangnya, umur, gender, kelas tiket, dll.

print(titanic.head())

# 4. Visualisasi Missing Value

Heatmap menunjukkan lokasi data kosong. Kolom deck paling banyak bolong, lalu age, lalu embark_town.

![Heatmap](https://raw.githubusercontent.com/username/repo/main/images/heatmap.png)


Bar chart jumlah missing memperjelas kolom mana yang perlu dibersihkan.

# 5. Distribusi Variabel Kategorik

Plot gender (sex) → laki-laki jumlahnya lebih banyak dibanding perempuan.

Plot kelas (class) → penumpang terbanyak ada di kelas 3, paling sedikit di kelas 1.

# 6. Distribusi Variabel Numerik

Umur (age) → mayoritas penumpang berusia 20–30 tahun. Anak-anak ada, tapi sedikit. Penumpang lansia hampir tidak ada.

Harga tiket (fare) → mayoritas tiket murah (<100), hanya sedikit tiket mahal (outlier di atas 400).

# 7. Korelasi Numerik

Korelasi pclass dengan fare bernilai negatif sedang (~ -0.55). Artinya, makin tinggi kelas (kelas 1), harga tiket makin mahal.

Korelasi sibsp dengan parch positif kecil. Penumpang yang bawa pasangan/saudara kadang juga bawa anak/ortu.

age tidak berkorelasi kuat dengan variabel lain.

# 8. Variabel Baru: sex_embark

Dibuat variabel baru sex_embark dari gabungan sex + embark_town. Contoh kategori:

female_Cherbourg

male_Southampton

female_Queenstown
Visualisasi countplot menunjukkan jumlah penumpang berbeda per kota dan gender:

Cherbourg → lebih banyak perempuan.

Southampton → lebih banyak laki-laki.

Queenstown → jumlah penumpang jauh lebih sedikit.

# 9. Survival Rate berdasarkan Gender + Kota

Perempuan Cherbourg memiliki survival rate paling tinggi (sekitar 76%).

Perempuan Southampton juga cukup tinggi, meski sedikit lebih rendah.

Laki-laki Southampton survival rate paling rendah (~18%).

Pola konsisten: gender berpengaruh kuat, perempuan lebih tinggi daripada laki-laki di semua kota.

# 10. Korelasi sex_embark dengan Fare

Boxplot menunjukkan median fare tertinggi ada di female Cherbourg (banyak penumpang kelas 1).

Laki-laki Southampton memiliki median fare paling rendah (dominan kelas 3).

Jadi perbedaan survival bukan hanya gender, tapi juga dipengaruhi harga tiket dan kelas.

# 11. Korelasi sex_embark dengan Pclass

Grafik catplot membagi survival rate per gender dan kelas di tiap kota.

Terlihat jelas:

Perempuan kelas 1 Cherbourg hampir semua selamat.

Laki-laki kelas 3 Southampton paling sedikit selamat.

Faktor kota embarkasi memengaruhi survival karena terkait distribusi kelas.

# 📝 Kesimpulan

Perempuan punya peluang selamat lebih besar dibanding laki-laki.

Penumpang dari Cherbourg cenderung lebih banyak selamat, sedangkan dari Southampton lebih sedikit.

Kelas 1 dengan tiket mahal punya survival rate lebih tinggi dibanding kelas 3 dengan tiket murah.

Variabel baru gabungan gender + kota embarkasi membantu memperjelas pola survival.
