# Airbnb Listing Analysis for Large Family Holiday Stay

## Deskripsi Project
Project ini bertujuan untuk menganalisis data Airbnb dan memberikan rekomendasi penginapan yang paling sesuai untuk **keluarga besar (> 5 orang)** selama **liburan Natal**. Analisis difokuskan pada kesesuaian penginapan untuk :
- keluarga
- efisiensi harga
- tingkat popularitas penginapan
Karena dataset tidak menyediakan informasi ketersediaan dan booking, analisis menggunakan **proxy variables** seperti jumlah review dan harga per orang untuk merepresentasikan permintaan (demand) dan efisiensi harga (value for money).

---

## Tujuan
- Menentukan wilayah terbaik untuk penginapan keluarga besar  
- Mengidentifikasi karakteristik penginapan Airbnb yang ideal untuk keluarga besar  
- Mengembangkan sistem penilaian (scoring) untuk meranking penginapan di Airbnb  

---

## Pertanyaan Bisnis
1. Wilayah mana yang paling optimal untuk keluarga besar berdasarkan kesesuaian keluarga, harga, dan popularitas?  
2. Apakah harga penginapan yang lebih tinggi selalu mencerminkan kualitas yang lebih baik untuk keluarga besar?  
3. Karakteristik apa yang dimiliki penginapan ideal untuk keluarga besar dari sisi kapasitas, kamar, fasilitas, dan efisiensi harga?

---

## Dataset
Dataset yang digunakan merupakan data publik Airbnb dengan variabel utama:
- `accommodates`
- `bedrooms`
- `price`
- `room_type`
- `amenities`
- `total_reviews`
- `reviews_per_month`
- `district`

---

## Metodologi
### Data Understanding
- Lihat 5 baris pertama
- Mengetahui info, dtypes, total baris dan kolom
- Descriptive statistics awal untuk cek nilai 0
- Melihat duplikasi data
- Mengetahui persentase / proporsi nilai hilang (missing values)
  
### Data Preparation
- Pembersihan data dan penanganan missing value  
- Normalisasi harga  

### Feature Engineering & Scoring
- **Family Suitability Score** berdasarkan : kapasitas, jumlah kamar, tipe kamar, dan fasilitas  
- **Value for Money Score** berdasarkan harga per orang  
- **Popularity Score** berdasarkan jumlah dan frekuensi review  
- **Final Score** sebagai agregasi seluruh skor untuk menentukan ranking penginapan
- Filter data untuk keluarga besar (`accommodates > 5` dan `bedrooms ≥ 3`)

---

## Analisis
Analisis dilakukan untuk:
- Penginapan
  - Distribusi skor kesesuaian keluarga
  - Total penginapan tiap kategori ukuran keluarga -> dari akomodasi penginapan
  - Total penginapan tiap wilayah untuk keluarga besar
  - Total penginapan berdasarkan tipe kamar untuk keluarga besar
- Harga
  - Tren harga per tamu/orang dan total akomodasi (kapasitas tamu)
  - Harga tiap orang di setiap wilayah
  - Distribusi harga per orang dan skor popularitas
- Wilayah
  - Wilayah terbaik berdasarkan final score
  - Wilayah terbaik berdasarkan final score untuk keluarga besar
- Penginapan terbaik untuk keluarga besar, khususnya seluruh tempat (Entire Place), di setiap wilayah
- Distribusi harga pada penginapan dengan tipe Entire Place

---

## Insight Utama
- Penginapan dengan kesesuaian tinggi untuk keluarga besar jumlahnya relatif terbatas
  - <img width="510" height="300" alt="image" src="https://github.com/user-attachments/assets/17ad312c-6f81-421d-b8f7-1669c71acf3e" />
- Wilayah dengan harga tinggi tidak selalu memberikan kualitas terbaik untuk keluarga besar
  - <img width="510" height="300" alt="image" src="https://github.com/user-attachments/assets/bb8d5276-e9d1-4d8e-948a-a9b4f41d3100" />
  - <img width="510" height="300" alt="image" src="https://github.com/user-attachments/assets/aa3034ba-31df-47d7-8eb9-acf14efd261d" />
- Beberapa wilayah menawarkan kombinasi keseuaian keluarga dan harga yang lebih efisien
  - <img width="1489" height="985" alt="image" src="https://github.com/user-attachments/assets/a95635e5-01cc-4367-b90a-8927e1c62b24" />

---

## Kesimpulan
Berdasarkan hasil analisis, wilayah Queens, Staten Island, dan Brooklyn lebih optimal untuk keluarga besar karena menawarkan kecocokan penginapan yang lebih baik dengan harga yang lebih efisien. Hasil ini dapat digunakan sebagai dasar rekomendasi bagi keluarga besar maupun sebagai insight bagi pemilik penginapan.

---
## Assumptions (Asumsi Analisis)
Analisis dibuat dengan beberapa asumsi utama sebagai berikut:
- Jumlah dan frekuensi review digunakan sebagai **proxy untuk tingkat permintaan (demand)** karena tidak tersedia data booking dan ketersediaan penginapan
- Harga per orang digunakan sebagai **proxy efisiensi harga**, dengan asumsi bahwa biaya per individu lebih relevan untuk keluarga besar dibandingkan harga total penginapan
- Penginapan dengan kapasitas lebih besar, jumlah kamar lebih banyak, dan fasilitas utama (seperti dapur) dianggap lebih cocok untuk keluarga besar

---

## Limitations (Keterbatasan Analisis)
Beberapa keterbatasan dalam project ini antara lain:
- Dataset tidak menyediakan data aktual mengenai **booking, occupancy rate, dan availability**, sehingga analisis tidak dapat memastikan penginapan benar-benar tersedia saat special occasion tertentu, misal : Liburan Natal
- Review digunakan sebagai proxy demand, namun jumlah review tidak selalu merepresentasikan kondisi permintaan terkini
- Bobot dalam sistem scoring ditentukan berdasarkan pertimbangan logis dan konteks bisnis, bukan hasil optimasi statistik atau validasi eksternal
- Analisis tidak mempertimbangkan faktor musiman lain seperti event khusus, promosi, atau perubahan harga dinamis
- Preferensi keluarga besar dapat bervariasi dan tidak sepenuhnya terwakili hanya melalui variabel kuantitatif

---

## Recommendations (Rekomendasi)
Berdasarkan hasil analisis, rekomendasi yang dapat diberikan adalah:
- Keluarga besar yang merencanakan liburan disarankan untuk mempertimbangkan wilayah dengan **efisiensi harga tinggi dan kesesuaian keluarga yang baik**, seperti wilayah dengan final score tinggi : Brooklyn, Queens, Staten Island
- Pemilik penginapan dapat meningkatkan daya tarik dengan menambahkan fasilitas yang relevan untuk keluarga besar, seperti dapur, mesin cuci, dan jumlah kamar yang memadai
- Untuk analisis lanjutan, disarankan menggunakan data tambahan seperti availability kalender, data harga musiman, atau booking rate agar hasil rekomendasi lebih akurat
- Sistem scoring dapat dikembangkan lebih lanjut dengan penyesuaian bobot berdasarkan survei pengguna atau validasi terhadap data aktual pemesanan

---

## Tools
- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- Jupyter Notebook  

---

## Catatan
Project ini merupakan **self project** untuk menunjukkan kemampuan analisis data dan pengambilan insight berbasis data.
