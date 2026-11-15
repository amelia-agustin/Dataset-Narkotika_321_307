<p align="center">
  <img src="https://img.shields.io/badge/Dokumen-54%20putusan-1f6feb" alt="dokumen">
  <img src="https://img.shields.io/badge/Pengadilan-PN%20Makassar-8957e5" alt="pengadilan">
  <img src="https://img.shields.io/badge/Tahun-2024--2026-2da44e" alt="tahun">
  <img src="https://img.shields.io/badge/Format-PDF%20%2B%20XLSX-orange" alt="format">
  <img src="https://img.shields.io/badge/Sumber-Direktori%20Putusan%20MA%20RI-lightgrey" alt="sumber">
</p>

<h1 align="center">⚖️ Dataset-Narkotika_321_307</h1>

<p align="center"><b>Dataset putusan pengadilan perkara Narkotika dan Psikotropika dari PN Makassar</b><br>
untuk riset Temu Kembali Informasi (<i>Information Retrieval</i>) pada dokumen hukum berbahasa Indonesia.</p>

---

## 📌 Tentang Dataset

Repositori ini berisi **54 dokumen putusan** tingkat pertama perkara **Pidana Khusus – Narkotika dan Psikotropika** yang diputus oleh **PN Makassar** pada rentang tahun **2024–2026**. Seluruh dokumen diakuisisi secara manual dari [Direktori Putusan Mahkamah Agung RI](https://putusan3.mahkamahagung.go.id/direktori.html) dan dilengkapi berkas ringkasan terstruktur (`Overview.xlsx`) yang memuat nomor putusan, lembaga peradilan, barang bukti, dan amar putusan.

Dataset ini disusun sebagai bahan untuk tahapan TKI berikutnya: *crawling*, ekstraksi informasi, *preprocessing*, pengindeksan, dan pencarian dokumen putusan.

## 🗂️ Struktur Repositori

```
Dataset-Narkotika_321_307/
├── Dataset/
│   └── Narkotika.zip      # 54 dokumen putusan (*.pdf)
├── Overview/
│   └── Overview.xlsx      # ringkasan 54 putusan
└── README.md
```

## 📊 Ringkasan Statistik

**Distribusi putusan per tahun**

| Tahun | Jumlah putusan |
|:-----:|:--------------:|
| 2024 | 11 |
| 2025 | 23 |
| 2026 | 19 |

**Jenis barang bukti narkotika/psikotropika** (satu putusan dapat memuat lebih dari satu jenis)

| Jenis | Jumlah putusan |
|-------|:--------------:|
| Sabu (metamfetamina) | 23 |
| Tembakau sintetis | 6 |

**Lama pidana penjara** (diambil dari amar putusan)

| Minimum | Rata-rata | Maksimum |
|:-------:|:---------:|:--------:|
| 1 tahun 6 bulan | 4 tahun 8 bulan | 15 tahun |

## 🧾 Skema `Overview.xlsx`

| Kolom | Tipe | Deskripsi |
|-------|------|-----------|
| `No` | integer | Nomor urut data |
| `No Putusan` | string | Nomor register perkara, format `nomor/Pid.Sus/tahun/PN kode` |
| `Lembaga Peradilan` | string | Pengadilan Negeri yang memutus perkara |
| `Barang Bukti` | string | Daftar barang bukti yang ditetapkan dalam amar putusan |
| `Amar Putusan` | string | Isi amar putusan (bagian setelah *MENGADILI*) |

**Contoh satu baris data**

| No Putusan | Lembaga Peradilan | Barang Bukti | Amar Putusan (dipotong) |
|---|---|---|---|
| 615/Pid.Sus/2024/PN Mks | PN Makassar |  | 1. Menyatakan terdakwa Akbar Alimuddin Bin Alimuddin, telah terbukti secara sah dan meyakinkan bersalah melakukan tindak pidana “Percobaan atau permufakatan jahat untuk melakukan tindak pidana Narkotika dan Prekursor Narkotika Dengan tanpa hak atau melawan hukum Memiliki, menyimpan, menguasai, atau menyediakan Narkotika Golongan I bukan tanaman; 2. Menjatuhkan pidana terhadap Terdakwa Akbar Alimud... |

## 🔎 Metodologi Akuisisi

1. **Sumber**: Direktori Putusan Mahkamah Agung RI (`putusan3.mahkamahagung.go.id`).
2. **Filter direktori**: Pidana Khusus → klasifikasi **Narkotika dan Psikotropika** → **PN Makassar** → tahun putusan 2024–2026.
3. **Kriteria inklusi**: putusan tingkat pertama, dokumen PDF lengkap dan dapat dibaca, status putusan **bukan** *Berkekuatan Hukum Tetap* sesuai ketentuan tugas.
4. **Pengunduhan**: dilakukan manual satu per satu melalui tombol unduh PDF pada halaman detail putusan.
5. **Pembuatan ringkasan**: teks PDF diekstraksi dengan PyMuPDF, watermark/header/disclaimer MA dibersihkan, lalu kolom `No Putusan`, `Lembaga Peradilan`, `Barang Bukti`, dan `Amar Putusan` diekstraksi berbasis pola kalimat (regex) dan **diverifikasi manual** terhadap dokumen asli.

## 🚀 Cara Menggunakan

```python
import zipfile, pandas as pd

# ekstrak dokumen putusan
zipfile.ZipFile("Dataset/Narkotika.zip").extractall("putusan_pdf")

# baca ringkasan
df = pd.read_excel("Overview/Overview.xlsx")
print(df.shape)
print(df[["No Putusan", "Lembaga Peradilan"]].head())
```

Ide pemanfaatan: pencarian putusan berbasis kata kunci (TF-IDF/BM25), pencarian perkara serupa (*similar case retrieval*), ekstraksi entitas hukum (terdakwa, pasal, barang bukti), serta analisis pola pemidanaan perkara narkotika.

## ⚠️ Etika dan Lisensi

- Dokumen putusan pengadilan bersifat **terbuka untuk publik** dan tidak terikat HaKI. Seluruh hak atas isi dokumen tetap mengacu pada Mahkamah Agung RI.
- Dokumen memuat **nama dan identitas terdakwa** sebagaimana dipublikasikan oleh MA. Gunakan dataset ini hanya untuk keperluan pendidikan dan penelitian, dan hindari penggunaan yang merugikan pihak yang disebut dalam putusan.
- Ringkasan pada `Overview.xlsx` merupakan hasil ekstraksi dan dapat memuat kekeliruan; rujuk dokumen PDF asli untuk keperluan yang memerlukan ketepatan hukum.

## 👥 Tim Penyusun

| Nama | NIM |
|------|-----|
| Nisrina Nurhafizhah | 202310370311321 |
| Nur Indah Amelia Agustin | 202310370311307 |

**Mata kuliah**: Temu Kembali Informasi (Kelas A/D), Semester Ganjil 2026/2027<br>
**Dosen pengampu**: Galih Wasis Wicaksono<br>
**Program studi**: Informatika, Universitas Muhammadiyah Malang

## 📚 Sitasi

```
Nisrina Nurhafizhah & Nur Indah Amelia Agustin (2026). Dataset-Narkotika_321_307: Dataset Putusan Perkara Narkotika dan
Psikotropika PN Makassar. GitHub repository.
```
