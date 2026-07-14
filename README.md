# Scrapping Berita mengenai Hubungan Kejaksaan - Polri

Scrapping ini untuk melihat trend berita yang muncul melalui 
Google Trend dengan memanfaatkan daftar kunci 
dan memunculkan berita terbaru

# Kajian Kejaksaan: Analisis Sentimen & Tren Pemberitaan Kasus Korupsi MBG dan Hubungan Antar Lembaga (Kejaksaan & Polri)

Repositori ini berisi notebook analisis data (`Kajian_kejaksaan.ipynb`) yang digunakan untuk memproses, membersihkan, dan memvisualisasikan tren pemberitaan media digital terkait Kejaksaan Agung, Kepolisian Republik Indonesia (Polri), serta kasus korupsi proyek Makan Bergizi Gratis (MBG) yang melibatkan tersangka Brigjen Pol Lalu Muhammad Iwan Mahardan.

## 📌 Latar Belakang & Deskripsi Proyek
Proyek ini bertujuan untuk menganalisis dinamika opini publik dan intensitas pemberitaan media massa mengenai:
1. **Kasus Korupsi MBG (Makan Bergizi Gratis):** Penelusuran profil, kekayaan, dan keterlibatan Brigjen Pol Lalu Muhammad Iwan Mahardan sebagai salah satu tersangka utama.
2. **Hubungan Kelembagaan:** Mengamati interaksi, sinergi, maupun ketegangan isu di media antara institusi **Kejaksaan Agung** dan **Polri**.
3. **Analisis Tren Waktu:** Memetakan volume publikasi berita dari waktu ke waktu untuk melihat puncak-puncak isu (*hype*) tertentu.

---

## 🛠️ Alur Analisis (Workflow)
Proses analisis dalam notebook ini dibagi menjadi beberapa tahap utama:

### 1. Memuat Data (Data Loading)
Data bersumber dari hasil scraping berita digital yang disimpan dalam format:
* `hasil_scraping (1).csv`: Berisi dataset berita mentah (judul, tanggal, kategori, dll).
* `berita_dengan_isi.xlsx`: Dataset yang lebih lengkap yang mencakup konten/isi berita secara utuh.

### 2. Pembersihan Data (Data Cleaning)
Aktivitas pre-processing yang dilakukan meliputi:
* **Pengecekan Duplikasi:** Mendeteksi baris data yang berulang menggunakan `.duplicated().sum()`.
* **Penanganan Missing Values:** Mengidentifikasi data kosong menggunakan `.isna().sum()`.
* **Reduksi Dimensi:** Menghapus kolom yang tidak relevan seperti `Kategori` dan `Isi` (pada tahap analisis tren tertentu) untuk mengoptimalkan kinerja komputasi menggunakan `.drop()`.
* **Konversi Tipe Data:** Mengubah kolom tanggal (`Date`) menjadi format `datetime` standar Pandas agar dapat diolah berdasarkan kronologi waktu.

### 3. Agregasi & Visualisasi Tren Berita
* Mengelompokkan berita berdasarkan tanggal rilis (`df.groupby(df['Date'].dt.date).size()`).
* Mengurutkan data secara kronologis untuk melihat perkembangan isu.
* Membuat visualisasi menggunakan **Matplotlib**:
  * **Bar Chart (Steel Blue):** Menampilkan jumlah artikel konkret per tanggal dengan label angka (*data label*) di atas setiap batang.
  * **Line Chart (Red):** Sebagai garis tren (*trendline*) untuk mempermudah identifikasi fluktuasi pergerakan isu di media.

---

## 📊 Hasil Analisis Visual
Notebook ini menghasilkan grafik interaktif yang memetakan **"Jumlah Artikel Berita tentang Hubungan antara Kejaksaan, MBG, dan Polri"**. Visualisasi ini sangat berguna bagi akademisi, peneliti hukum, maupun jurnalis untuk melihat kapan sebuah isu mengalami eskalasi atau de-eskalasi.

---

## 💻 Prasyarat & Instalasi

Untuk menjalankan notebook ini secara lokal, Anda memerlukan Python 3.x beserta beberapa pustaka pendukung.

### Pustaka yang Diperlukan:
```bash
pip install pandas matplotlib openpyxl

# Struktur Scrapping

nama-project/
├── data/
│   └── berita_scraped.csv
├── notebook/
│   └── analisis.ipynb
├── output/
│   └── barplot_frekuensi.png
└── README.md
