# Analisis-Data-Real-Time-Drilling-Operation-Manajemen-Risiko-Termomekanis-Well-58-32
Repositori ini berisi proyek analisis data log pemboran dari sumur **Well 58-32**. Fokus utama dari penelitian dan pengolahan data ini adalah melakukan Exploratory Data Analysis (EDA) terhadap data sensor *Pason log*, membersihkan data kotor (*data wrangling*), serta membangun fungsi otomasi untuk klasifikasi risiko termal guna menjaga integritas struktural alat pemboran (*drill string*).

## 📊 Ikhtisar Dataset
Dataset yang digunakan mencakup rekaman parameter teknik dari sistem sensor rig pemboran (Pason Log).
* **Total Elemen Data**: 197.397 elemen
* **Total Baris**: 7.311 baris data log
* **Total Fitur/Kolom**: 27 variabel teknis

## 💻 Fitur Utama & Struktur Kode
Notebook ini dirancang dengan alur *Data Science Lifecycle* terstruktur yang mencakup:

1. **Data Ingestion:** Pemuatan data berskala besar berbasis file `.csv` hasil perekaman log real-time sensor pason pemboran dengan total **197.397 elemen data** (7.311 baris dan 27 parameter operasional).
2. **Data Wrangling & Cleaning:**
   * Otomasi pembersihan nama kolom (`clean_column_string`) dari spasi kosong (*whitespace*) maupun karakter khusus (`%`, `(`, `)`).
   * Konversi matriks satuan operasional pemboran (Imperial ke Metrik) secara serentak.
3. **Advanced Control Flow Logic:**
   * Fungsi kondisional mendalam `klasifikasi_zona_termal` untuk memetakan level bahaya operasional berdasarkan temperatur fluida lumpur pemboran yang keluar sumur (`Temp Out`).
4. **Interactive Exploratory Data Analysis (EDA):**
   * Visualisasi sebaran parameter fisis pemboran (seperti *Rate of Penetration* / ROP, *Weight on Bit* / WOB, *Surface Torque*, dan *Flow In*) menggunakan kombinasi pustaka static matplot/seaborn dan grafik interaktif plotly.


## 📊 Hasil Analisis & Insight Utama

Berdasarkan visualisasi dan statistik deskriptif data log pemboran sumur Well 58-32, diperoleh kesimpulan penting berupa:
* **Korelasi Kedalaman vs Gesekan:** Terdapat korelasi kuat yang linear antara peningkatan kedalaman sumur dengan lonjakan nilai *Surface Torque* serta suhu fluida pemboran. Semakin dalam sumur ditembus, efek gesekan mekanis berpadu dengan gradien geotermal bumi secara signifikan meningkatkan beban termomekanis pada rangkaian pipa bor (*drill string*).
* **Indikasi Formasi Keras (Hard Formation):** Distribusi laju penembusan (*ROP*) menunjukkan pola sebaran yang melandai dan tidak beraturan pada kedalaman tertentu, mengindikasikan kerja pahat bor (*drill bit*) yang kurang efisien akibat perubahan karakteristik batuan formasi.


## 🛠️ Rekomendasi Operasional (Mitigasi Risiko)

Untuk mencegah kegagalan mekanis dini (*catastrophic failure*) di lapangan, rekomendasi teknis berikut dapat diimplementasikan:
1. **Zonasi Formasi Keras (Torque > 150 psi):** Pada interval kedalaman yang teridentifikasi sebagai lapisan batuan keras, disarankan untuk membatasi *Weight on Bit* (WOB) di bawah **30 k-lbs** guna mencegah patahnya mata bor akibat getaran berlebih (*vibration damping*).
2. **Manajemen Termal (Suhu > 138°F):** Saat beralih ke zona klasifikasi *High Risk / Elevated Thermal*, laju aliran lumpur masuk (*Flow In*) harus ditingkatkan secara bertahap hingga stabil di atas kisaran **1.000 gal/min** (atau setara 227 Sm³/jam) demi mengoptimalkan pendinginan pahat bor dan mengangkat serpihan batuan (*cuttings*) secara maksimal.
3. **Pengendalian Kumulatif Volume:** Monitoring ketat pada grafik kumulatif injeksi fluida lumpur harus dipertahankan. Jika garis kumulatif melandai secara drastis sementara tekanan pompa (*Pump Pressure*) naik, segera lakukan sirkulasi penuh untuk menghindari risiko pipa terjepit (*pipe sticking*).


## 📦 Library yang Digunakan
Pastikan Anda menginstal pustaka-pustaka Python berikut sebelum menjalankan notebook:
```bash
pip install pandas numpy matplotlib seaborn plotly
