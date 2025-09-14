# 🛳️ Pendahuluan: Analisis Dataset Titanic

Kapal RMS Titanic adalah kapal penumpang terbesar dan termewah pada masanya, yang tenggelam pada pelayaran perdananya tahun 1912 setelah menabrak gunung es. Dari lebih dari 2.200 orang yang berada di kapal, sekitar 1.500 orang tidak selamat. Tragedi ini menjadi salah satu peristiwa paling terkenal dalam sejarah dunia.

Dataset Titanic kemudian banyak digunakan di dunia data science karena datanya cukup lengkap dan relevan untuk dipelajari. Dataset ini berisi informasi tentang penumpang, seperti usia, jenis kelamin, kelas penumpang, tarif tiket, hingga status keselamatan (selamat atau tidak).

# 🎯 Tujuan Analisis

Melalui analisis ini, kita akan mencoba:

Melihat perbandingan jumlah penumpang yang selamat dan tidak selamat.

Mengeksplorasi bagaimana faktor-faktor seperti jenis kelamin, kelas, usia, dan tarif tiket berpengaruh pada peluang keselamatan.

Membuat visualisasi untuk memahami pola data secara lebih mudah dan menarik.

# Data Awal TITANIC 
[Open In Google Colab](https://colab.research.google.com/drive/1BBnmCH8oSt7lcCzMBUD7Fbb4kOQmeCsJ?usp=sharing#scrollTo=btn0BuO-Fcus)

# Data Explorasi TITANIC 
[Open In Google Colab](https://colab.research.google.com/drive/15wAfiTE-5ZLW30irz7CfzG6m59UqWXmg#scrollTo=CYQ5s96reDes)

# Analisis Data Titanic
# 1. Import Library

Langkah ini memanggil library pandas, seaborn, dan matplotlib yang dipakai untuk membaca data Titanic dan membuat visualisasi.

# 2. Load Dataset Titanic

Dataset Titanic bawaan seaborn dimuat. Dataset berisi 891 baris (penumpang) dan 15 kolom (variabel), misalnya age, sex, pclass, fare, embark_town, dan lain-lain.

# 3. Cek Data Awal

info() menunjukkan ada beberapa kolom dengan data hilang: age (177 missing), deck (688 missing), embark_town (2 missing).

head() menampilkan 5 baris pertama dataset. Ini membantu melihat struktur data: siapa saja penumpangnya, umur, gender, kelas tiket, dll.

# 4. Visualisasi Missing Value

Heatmap menunjukkan lokasi data kosong. Kolom deck paling banyak bolong, lalu age, lalu embark_town.

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

Dari hasil eksplorasi dataset Titanic, terdapat beberapa pola penting yang bisa dipelajari:

Jenis kelamin sangat berpengaruh terhadap peluang selamat. Penumpang perempuan memiliki kemungkinan selamat lebih tinggi dibanding laki-laki.

Kelas penumpang juga berhubungan erat dengan survival. Penumpang kelas 1 memiliki peluang selamat lebih besar dibanding kelas 2 dan terutama kelas 3.

Usia memberikan indikasi bahwa anak-anak relatif lebih banyak yang selamat dibanding penumpang dewasa.

Tarif tiket (fare) cenderung lebih tinggi pada penumpang yang selamat, yang sejalan dengan fakta bahwa penumpang kelas atas memiliki akses lebih besar untuk evakuasi.

Kombinasi antara gender dan kelas menunjukkan bahwa perempuan di kelas 1 memiliki peluang terbesar untuk selamat, sedangkan laki-laki di kelas 3 merupakan kelompok dengan risiko paling tinggi.
