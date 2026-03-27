# 🐦 Sentweet

<div align="center">

![Sentweet Banner](https://img.shields.io/badge/Sentweet-Sentiment%20Tweet%20Analyzer-1DA1F2?style=for-the-badge&logoColor=white)

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![BERT](https://img.shields.io/badge/BERT-NLP%20Model-FF6F00?style=flat-square&logo=google&logoColor=white)](https://huggingface.co/docs/transformers/model_doc/bert)
[![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)

</div>

---

## 📋 Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Fitur Utama](#-fitur-utama)
- [Tech Stack](#-tech-stack)
- [Struktur Proyek](#-struktur-proyek)
- [Cara Menjalankan](#-cara-menjalankan)
- [Alur Pemrosesan Data](#-alur-pemrosesan-data)
  
---

## 🔬 Tentang Proyek

**Sentweet** *(Sentiment Tweet)* adalah aplikasi berbasis web yang mengintegrasikan teknik **text mining** dan **analisis sentimen** untuk mengekstraksi wawasan dari tweet berbahasa Indonesia secara otomatis. Pengguna cukup memasukkan kata kunci dan rentang tanggal, lalu sistem akan merayapi tweet, mengklasifikasikan sentimen, dan menyajikan hasilnya dalam visualisasi yang interaktif.

### 🧠 Deskripsi Teknis

- Mengembangkan pipeline **text mining** end-to-end mulai dari crawling tweet, preprocessing teks, augmentasi data, hingga klasifikasi sentimen menggunakan model **BERT** berbasis Transformer
- Mengimplementasikan **data augmentation** dengan **Nlpaug** untuk menangani ketidakseimbangan kelas pada data tweet berbahasa Indonesia
- Membangun antarmuka analitik interaktif berbasis **Streamlit** yang memungkinkan eksplorasi hasil sentimen secara real-time

### 🎯 Tujuan Sistem

- Memungkinkan pengguna **merayapi tweet** berdasarkan kata kunci dan rentang tanggal tertentu secara otomatis
- Mengklasifikasikan sentimen tweet (positif, negatif, netral) menggunakan model **BERT** yang telah dilatih pada data bahasa Indonesia
- Menyajikan **wawasan dan visualisasi** hasil analisis sentimen secara interaktif dan mudah dipahami

---

## ✨ Fitur Utama

### 🔎 Crawling Tweet Berbahasa Indonesia
- Input kata kunci dan rentang tanggal secara fleksibel
- Pengambilan tweet secara otomatis dari Twitter/X
- Ekspor hasil crawling ke format CSV

### 🤖 Analisis Sentimen berbasis BERT
- Klasifikasi sentimen: **Positif**, **Negatif**, **Netral**
- Model berbasis **IndoBERT** yang dioptimalkan untuk teks bahasa Indonesia
- Augmentasi data menggunakan **Nlpaug** untuk meningkatkan akurasi model

### 📊 Visualisasi Interaktif
- Distribusi sentimen dalam bentuk **pie chart** dan **bar chart**
- **Word cloud** berdasarkan kata kunci per kategori sentimen
- Tren sentimen berdasarkan rentang waktu
- Tabel hasil analisis yang dapat difilter dan diurutkan

### 🖥️ Antarmuka Web (Streamlit)
- Input parameter crawling langsung dari browser
- Tampilan hasil analisis yang responsif dan intuitif
- Unduh hasil analisis dalam format CSV

---

## 🛠 Tech Stack

| Teknologi | Peran |
|-----------|-------|
| **Python** | Bahasa pemrograman utama |
| **Streamlit** | Framework web app & antarmuka pengguna |
| **BERT (IndoBERT)** | Model deep learning untuk klasifikasi sentimen |
| **PyTorch** | Framework training & inferensi model neural network |
| **Nlpaug** | Augmentasi data teks untuk penyeimbangan kelas |
| **Scikit-learn** | Evaluasi model (akurasi, precision, recall, F1) |

---

## 📁 Struktur Proyek

```
sentweet/
├── app.py                        # Entry point aplikasi Streamlit
├── modules/
│   ├── crawler.py                # Modul crawling tweet berdasarkan keyword
│   ├── preprocessor.py           # Preprocessing teks (cleaning, tokenisasi)
│   ├── augmentor.py              # Augmentasi data dengan Nlpaug
│   ├── sentiment_model.py        # Pemuatan & inferensi model BERT
│   └── visualizer.py             # Visualisasi hasil (chart, wordcloud)
├── model/
│   └── indobert-sentiment/       # Bobot model BERT yang telah dilatih
├── data/
│   ├── raw/                      # Data tweet hasil crawling
│   └── processed/                # Data setelah preprocessing & augmentasi
├── notebooks/
│   ├── training.ipynb            # Notebook pelatihan model BERT
│   └── evaluation.ipynb          # Notebook evaluasi performa model
├── utils/
│   ├── text_utils.py             # Helper preprocessing & normalisasi teks
│   └── export_utils.py           # Helper ekspor hasil ke CSV
├── requirements.txt              # Daftar dependensi Python
└── README.md
```

---

## 🚀 Cara Menjalankan

### Prasyarat

- **Python 3.8+** — https://www.python.org/downloads/
- **pip** (biasanya sudah terinstal bersama Python)
- Koneksi internet untuk crawling tweet dan mengunduh model BERT

### Langkah Instalasi

**1. Clone repositori**
```bash
git clone https://github.com/username/sentweet.git
cd sentweet
```

**2. Buat virtual environment** (opsional tapi direkomendasikan)
```bash
python -m venv venv

# Aktivasi (Windows)
venv\Scripts\activate

# Aktivasi (Mac/Linux)
source venv/bin/activate
```

**3. Install dependensi**
```bash
pip install -r requirements.txt
```

**4. Jalankan aplikasi**
```bash
streamlit run app.py
```

Aplikasi akan otomatis terbuka di browser pada http://localhost:8501

### Isi `requirements.txt`

```
streamlit
transformers
torch
nlpaug
scikit-learn
pandas
matplotlib
wordcloud
snscrape
```

---

## 🔄 Alur Pemrosesan Data

```
Input: Kata Kunci + Rentang Tanggal
              │
              ▼
      Crawling Tweet
  (snscrape / Twitter API)
              │
              ▼
    Preprocessing Teks
  (cleaning, normalisasi,
   tokenisasi bahasa Indonesia)
              │
              ▼
    Augmentasi Data (Nlpaug)
  (synonym replacement, back-
   translation untuk data minoritas)
              │
              ▼
   Klasifikasi Sentimen (BERT)
  (IndoBERT fine-tuned untuk
   teks bahasa Indonesia)
              │
        ┌─────┴──────────┐
        ▼       ▼        ▼
    POSITIF  NEGATIF   NETRAL
        │       │        │
        └───────┴────────┘
                │
                ▼
     Visualisasi Interaktif
  (Pie Chart, Bar Chart, Word Cloud,
   Tren Waktu, Tabel Hasil)
                │
                ▼
     Output: Wawasan Sentimen
     + Ekspor CSV hasil analisis
```

---

<div align="center">

🐦 *Dari ribuan tweet, Sentweet membaca apa yang dunia rasakan.*

</div>
