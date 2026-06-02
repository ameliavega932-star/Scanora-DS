# Scanora - Data Science Documentation

Scanora adalah proyek capstone bertema sustainable living yang berfokus pada deteksi dan pengelolaan kesegaran buah. Repository ini berisi pekerjaan dari learning path **Data Scientist**, meliputi pengumpulan dataset, data assessing, data cleaning, feature engineering, exploratory data analysis, visualisasi, preprocessing, serta pengembangan dashboard analisis data.

## Project Scope

Pada bagian Data Science, analisis difokuskan pada dua dataset utama:

1. **Fruits Image Dataset**
   Digunakan untuk menganalisis data gambar buah berdasarkan jenis buah dan kondisi kesegaran.

2. **Fruits Consumption Dataset**
   Digunakan sebagai data pendukung untuk melihat pola konsumsi buah masyarakat, khususnya buah target Scanora.

Buah target awal Scanora terdiri dari:

* Apel
* Pisang
* Jeruk

Kondisi kesegaran yang dianalisis:

* Unripe
* Ripe
* Rotten

## Dataset

Dataset tidak disertakan langsung dalam repository karena ukuran file cukup besar. Pengguna perlu mengunduh dataset secara manual melalui sumber berikut:

### 1. Fruits Image Dataset

Source: Kaggle - Fruits Fresh and Rotten for Classification
Link: https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification

Dataset ini digunakan sebagai data utama untuk analisis gambar buah. Dataset berisi gambar buah apel, pisang, dan jeruk dalam beberapa kondisi kesegaran.

Setelah diunduh, letakkan dataset pada folder:

```bash
data/
```

Struktur folder yang digunakan:

```bash
data/
├── unripe/
│   ├── apple/
│   ├── banana/
│   └── orange/
├── ripe/
│   ├── apple/
│   ├── banana/
│   └── orange/
└── rotten/
    ├── apple/
    ├── banana/
    └── orange/
```

### 2. Fruits Consumption Dataset

Source: BPS - Rata-rata Konsumsi Perkapita Seminggu Menurut Kelompok Buah-buahan per Kabupaten/Kota Komoditas 2025
Link: https://www.bps.go.id/id/statistics-table/2/MjU1OCMy/rata-rata-konsumsi-perkapita-seminggu-menurut-kelompok-buah-buahan-per-kabupaten-kota-komoditas-2025.html

Dataset ini digunakan untuk melihat posisi konsumsi buah target Scanora dibandingkan komoditas buah lainnya.

## Data Science Workflow

Tahapan yang dilakukan dalam notebook Data Science:

### 1. Data Gathering

* Mengatur path dataset gambar.
* Membaca struktur folder dataset.
* Membuat metadata gambar berdasarkan folder, nama file, jenis buah, kondisi buah, dan label kombinasi kelas.
* Membaca fruits consumption dataset dari BPS.

### 2. Data Assessing

Pada fruits image dataset, dilakukan pengecekan:

* Struktur metadata.
* Distribusi jenis buah, kondisi buah, dan kombinasi kelas.
* File corrupt.
* Sampel gambar per kelas.
* Ukuran gambar.
* Mode warna gambar.
* Duplikasi gambar.
* Outlier kualitas gambar.

Pada fruits consumption dataset, dilakukan pengecekan:

* Struktur dataset.
* Statistik deskriptif.
* Missing value.
* Duplikasi data.
* Outlier konsumsi.

### 3. Data Cleaning

Pada fruits image dataset:

* Menghapus duplicate image.
* Meninjau dan menghapus gambar yang tidak layak secara manual.
* Menstandarkan seluruh gambar ke mode warna RGB.
* Menyalin hasil cleaning ke folder `data_processed`.

Pada fruits consumption dataset:

* Menghapus kolom dengan missing value tinggi.
* Melakukan imputasi missing value menggunakan median.
* Menangani outlier menggunakan metode capping.
* Menyimpan hasil cleaning sebagai `fruit_consumption_summary.csv`.

### 4. Feature Engineering

Pada fruits image dataset:

* Membentuk label kombinasi kelas, seperti `apple_ripe`, `banana_rotten`, dan `orange_unripe`.
* Mengekstraksi metrik kualitas gambar, seperti blur score, brightness score, contrast score, dan entropy score.
* Melakukan encoding label kelas.
* Menyiapkan augmentasi gambar untuk training set.

Pada fruits consumption dataset:

* Menstandarkan komoditas buah target Scanora.
* Membentuk ringkasan konsumsi buah.
* Membuat ranking konsumsi buah.
* Menandai buah target Scanora.
* Membandingkan konsumsi buah target terhadap rata-rata seluruh buah.
* Melabeli prioritas pengembangan komoditas buah.

### 5. Exploratory Data Analysis

EDA dilakukan untuk menjawab beberapa pertanyaan utama:

* Bagaimana distribusi gambar berdasarkan jenis buah?
* Bagaimana distribusi gambar berdasarkan kondisi kesegaran?
* Bagaimana distribusi kombinasi kelas fruit-condition?
* Bagaimana posisi konsumsi buah target Scanora dibandingkan buah lain?
* Buah apa saja yang berpotensi menjadi kandidat pengembangan berikutnya?

### 6. Visualization & Explanatory Analysis

Visualisasi dibuat untuk menjelaskan:

* Distribusi jenis buah.
* Distribusi kondisi buah.
* Kombinasi kelas.
* Tingkat konsumsi buah target.
* Kandidat buah untuk pengembangan Scanora.

### 7. Data Preprocessing

Tahap preprocessing meliputi:

* Pembagian dataset menjadi training, validation, dan testing dengan rasio 70:15:15.
* Konfigurasi input model dengan ukuran gambar 224 x 224 piksel.
* Batch size sebesar 32.
* Augmentasi data gambar pada training set.

## Key Results

Hasil utama dari proses Data Science:

* Dataset akhir fruits image dataset terdiri dari 19.766 gambar.
* Dataset mencakup 3 jenis buah, 3 kondisi kesegaran, dan 9 kombinasi kelas.
* Sebanyak 153 duplicate image dihapus dari dataset.
* Sebanyak 37 gambar tidak layak dihapus setelah manual review.
* Seluruh gambar hasil cleaning telah distandardisasi ke mode warna RGB.
* Dataset dibagi menjadi 13.836 data training, 2.965 data validation, dan 2.965 data testing.
* Fruits consumption dataset digunakan untuk melihat relevansi buah target Scanora berdasarkan pola konsumsi masyarakat.
* Dashboard Streamlit dikembangkan untuk menampilkan overview dataset, distribusi data, image preview, konsumsi buah, dan key insights.

## Dashboard

Dashboard analisis data dibuat menggunakan Streamlit untuk membantu eksplorasi dan penyampaian insight secara interaktif.

Dashboard menampilkan:

* Overview dataset.
* Distribusi jenis buah.
* Distribusi kondisi buah.
* Distribusi kombinasi kelas.
* Image preview.
* Rata-rata konsumsi buah target Scanora.
* Top komoditas buah berdasarkan konsumsi.
* Key insights.

Streamlit Dashboard Repository: https://github.com/emilianaaelgaa/scanora-dashboard.git
Live Dashboard: https://scanora-dashboard-capstone-project.streamlit.app

## Project Structure

Contoh struktur awal folder untuk bagian Data Science:

```bash
CAPSTONE/
├── .venv/
├── dashboard/
│   ├── image/
│   └── streamlit_app.py
├── data/
│   ├── ripe/
│       ├── apple/
│       ├── banana/
│       └── orange/
│   ├── rotten/
│       ├── apple/
│       ├── banana/
│       └── orange/
│   └── unripe/
│       ├── apple/
│       ├── banana/
│       └── orange/
├── DS_DICODING.ipynb
├── Fruits Consumption Dataset.csv
└── requirements.txt
```
Catatan:

* `.venv/` berisi virtual environment lokal dan tidak disertakan dalam repository.
* `dashboard/` berisi file dashboard Streamlit yang digunakan untuk visualisasi dan eksplorasi data. Dashboard tersedia pada repository dan deployment terpisah.
* `data/` berisi fruits image dataset mentah.
* `DS_DICODING.ipynb` merupakan notebook utama untuk proses Data Science.
* `Fruits Consumption Dataset.csv` merupakan dataset konsumsi buah dari BPS.
* `requirements.txt` berisi daftar dependencies yang diperlukan untuk menjalankan notebook.

## How to Reproduce

Ikuti langkah berikut untuk menjalankan ulang proses Data Science:

### 1. Clone Repository

```bash
git clone https://github.com/ameliavega932-star/Scanora-DS.git
cd Scanora-DS
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Download Dataset

Unduh dataset dari sumber berikut:

* Fruits Image Dataset: https://www.kaggle.com/datasets/sriramr/fruits-fresh-and-rotten-for-classification
* Fruits Consumption Dataset: https://www.bps.go.id/id/statistics-table/2/MjU1OCMy/rata-rata-konsumsi-perkapita-seminggu-menurut-kelompok-buah-buahan-per-kabupaten-kota-komoditas-2025.html

Sesuaikan struktur folder dan letakkan fruits image dataset pada folder:

```bash
data/
```

### 4. Run Notebook

Jalankan notebook DS_DICODING.ipynb:

```bash
jupyter notebook notebook/
```

Notebook akan menjalankan proses:

* Membuat metadata dataset gambar.
* Assessing dataset.
* Cleaning dataset.
* Feature engineering.
* EDA.
* Visualisasi.
* Preprocessing.
* Menyimpan output hasil cleaning.

### 5. Run Dashboard

Jika ingin menjalankan dashboard Streamlit secara lokal:

```bash
streamlit run dashboard/app.py
```

## Output Files

Beberapa file output yang dihasilkan:

```bash
data_processed
fruit_consumption_summary.csv
metadata_dataset.csv
review_candidates.csv
metadata_cleaned.csv
metadata_processed.csv
test_metadata.csv
train_metadata.csv
val_metadata.csv
```

Keterangan:

* `data_processed/` berisi hasil cleaning dan standardisasi gambar.
* `fruit_consumption_summary.csv` merupakan hasil cleaning dan ringkasan data konsumsi buah.
* `metadata_dataset.csv` berisi metadata awal fruits image dataset.
* `review_candidates.csv` berisi daftar kandidat gambar yang ditinjau pada proses quality review.
* `metadata_cleaned.csv` berisi metadata setelah proses data cleaning.
* `metadata_processed.csv` berisi metadata final setelah proses preprocessing.
* `train_metadata.csv`, `val_metadata.csv`, dan `test_metadata.csv` berisi hasil pembagian dataset untuk training, validation, dan testing.

## Notes

Dataset gambar tidak diunggah langsung ke GitHub karena ukuran file besar. Untuk mereplikasi hasil, pengguna perlu mengunduh dataset dari sumber asli, meletakkannya pada struktur folder yang sesuai, lalu menjalankan notebook dari awal.
