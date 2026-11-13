## Tentang Dataset

Repositori ini dibangun sebagai bagian dari pemenuhan tugas Ujian Tengah Semester (UTS) mata kuliah **Temu Kembali Informasi (Information Retrieval)**. Dataset berfokus pada ranah hukum pidana khusus, secara spesifik kasus penyalahgunaan Narkotika dan Psikotropika.

Dokumen dalam dataset ini bersifat terbuka (Open Data) dan tidak terikat Hak Atas Kekayaan Intelektual (HaKI), menjadikannya sumber pengetahuan dan korpus teks yang ideal untuk riset Pemrosesan Bahasa Alami (NLP), Ekstraksi Informasi, dan Sistem Temu Kembali Informasi (TKI).

## Struktur Direktori

Repositori ini disusun dengan struktur berikut untuk memudahkan navigasi dan penggunaan data:

```
Dataset-Narkotika_321_307
 ┣ Dataset
 ┃ ┗ Narkotika.zip          # Berisi 50 dokumen putusan asli dalam format PDF
 ┣ Overview
 ┃ ┗ Overview.xlsx          # Tabel rekapitulasi ekstraksi informasi (metadata)
 ┗ README.md                # Dokumentasi repositori

```

## Struktur Data (`Overview.xlsx`)

File `Overview.xlsx` merangkum metadata esensial dari ke-50 putusan PDF. Informasi diekstrak secara *verbatim* (tanpa parafrase) ke dalam struktur tabel berikut:

| Nama Kolom            | Deskripsi                                                                     |
| --------------------- | ----------------------------------------------------------------------------- |
| **No**                | Nomor urut data (1-50).                                                       |
| **No Putusan**        | Nomor registrasi resmi putusan pengadilan. |
| **Lembaga Peradilan** | Nama Pengadilan Negeri yang memeriksa dan mengadili perkara.                  |
| **Barang Bukti**      | Rincian komprehensif barang bukti yang disita sesuai dokumen putusan.         |
| **Amar Putusan**      | Putusan akhir (vonis) hakim terhadap terdakwa.                                |

## Metode Akuisisi Data

Data dikumpulkan secara manual melalui tahapan berikut:

1. Mengunjungi website [**Direktori Putusan Mahkamah Agung RI**](https://putusan3.mahkamahagung.go.id/direktori.html).

2. Memfilter pencarian pada direktori **PIDANA KHUSUS** dan klasifikasi **NARKOTIKA DAN PSIKOTROPIKA**.

3. Menyeleksi putusan dari satu Pengadilan Negeri spesifik yaitu **\[Makassar\]**.

4. Memilih rentang tahun putusan antara **2023 hingga 2025**.

5. Memastikan seluruh putusan yang didownload **TIDAK** berstatus Berkekuatan Hukum Tetap (BHT).

## Tim Pengembang

Proyek dataset ini disusun oleh:

* **Nisrina Nurhafizhah** - NIM: `202310370311321` 

* **Nur Indah Amelia Agustin** - NIM: `202310370311307` 

Mata Kuliah: Temu Kembali Informasi
Fakultas Teknik, Universitas Muhammadiyah Malang (UMM)
Tahun Akademik: Ganjil 2026/2027

*Dibuat untuk tujuan akademis dan riset.*
