# Panduan Eksekusi LuaLaTeX & Struktur Proyek

Dokumen ini berisi panduan untuk melakukan kompilasi berkas LaTeX menggunakan **LuaLaTeX** pada Windows Command Prompt (CMD), serta penjelasan mengenai hierarki folder dan berkas proyek.

---

## 1. File dengan Hierarki Tertinggi (Entrypoint)

Berkas utama yang memiliki hierarki tertinggi dalam proyek ini adalah:
* **[main.tex](file:///c:/Users/Mirzariel/Downloads/Kerja%20Praktik/latex/latex_laporan_v1/main.tex)**

Semua berkas bab, konfigurasi preamble, daftar isi, daftar gambar/tabel, lampiran, dan daftar pustaka di-input atau di-include ke dalam berkas [main.tex](file:///c:/Users/Mirzariel/Downloads/Kerja%20Praktik/latex/latex_laporan_v1/main.tex). Oleh karena itu, proses kompilasi selalu dijalankan pada berkas ini.

---

## 2. Panduan Eksekusi LuaLaTeX di Windows CMD

Untuk melakukan kompilasi berkas LaTeX menjadi PDF di Windows menggunakan Command Prompt (CMD), ikuti langkah-langkah berikut:

### Prasyarat
Pastikan distribusi LaTeX Anda (seperti **MiKTeX** atau **TeX Live**) sudah terpasang dan `lualatex` terdaftar dalam variabel lingkungan sistem (`PATH`). Anda dapat memverifikasinya dengan menjalankan perintah berikut di CMD:
```cmd
lualatex --version
```

### Langkah-Langkah Kompilasi
1. Buka **Command Prompt (CMD)**.
2. Arahkan direktori aktif ke folder proyek kerja praktik Anda:
   ```cmd
   cd "C:\Users\Mirzariel\Downloads\Kerja Praktik\latex\latex_laporan_v1"
   ```
3. Jalankan perintah kompilasi menggunakan `lualatex`. Karena dokumen ini berisi referensi silang (cross-references), daftar isi, daftar gambar, dan daftar tabel, kompilasi harus dijalankan sebanyak **dua kali** agar seluruh halaman dan nomor referensi ter-update dengan benar:
   ```cmd
   lualatex --interaction=nonstopmode main.tex
   lualatex --interaction=nonstopmode main.tex
   ```
   *Catatan: Parameter `--interaction=nonstopmode` digunakan agar proses kompilasi tetap berjalan jika ada warning kecil dan tidak berhenti meminta input manual di tengah proses.*
4. Setelah kompilasi selesai tanpa pesan error kritis, berkas PDF hasil kompilasi akan diperbarui pada berkas **[main.pdf](file:///c:/Users/Mirzariel/Downloads/Kerja%20Praktik/latex/latex_laporan_v1/main.pdf)**.

---

## 3. Hierarki Folder dan Berkas Proyek

Berikut adalah struktur lengkap folder dan berkas penyusun laporan ini:

```text
latex_laporan_v1/
│
├── main.tex                    # Berkas utama (entrypoint) laporan
├── main.pdf                    # Berkas PDF hasil kompilasi laporan
├── README.md                   # Catatan awal template
├── GUIDE.md                    # Berkas panduan ini
│
├── bibliography/               # Folder bibliografi tambahan (saat ini kosong)
│
├── gambar/                     # Folder aset gambar & diagram laporan
│   ├── logo-ugm.png            # Logo UGM untuk halaman sampul
│   ├── logo-ugm-emas.jpeg      # Logo UGM emas untuk halaman pengesahan
│   ├── pltscirata.jpg          # Foto dokumentasi utama PLTS Cirata
│   ├── JKM560N-72HL4-BDV.jpg   # Gambar brosur modul Jinko Solar
│   ├── foto-modul-onshore.jpg  # Dokumentasi modul surya darat
│   ├── foto-iv-curve-tracer.jpg# Alat ukur I-V curve tracer
│   ├── diagram.png             # Diagram sistem pendukung
│   ├── sistem-umum-plts-terapung.png
│   ├── fig_2_1_visualisasi_plts_cirata.png
│   ├── fig_2_2_struktur_kepemilikan.png
│   ├── fig_2_3_struktur_proyek.png
│   ├── fig_2_4_teknologi_plts_terapung.png
│   ├── fig_2_5_load_calculation.png
│   ├── fig_2_5_pengenalan_k3_hdec.jpeg
│   ├── fig_2_6_basic_sea_survival.png
│   └── fig_2_6_proses_pemeliharaan.png
│
└── chapters/                   # Folder komponen isi dokumen laporan
    ├── preambles.tex           # Konfigurasi paket LaTeX, layout, dan margin
    ├── identitas.tex           # Berkas identitas laporan (penulis, NIM, judul)
    ├── database.hyphenate.tex  # Kamus pemenggalan kata (hyphenation)
    │
    # Front Matter (Halaman Depan)
    ├── sampul.tex              # Format sampul depan laporan
    ├── sampuldalam.tex         # Format halaman sampul dalam
    ├── pengesahan.tex          # Halaman pengesahan institusi/dosen pembimbing
    ├── pengesahanPerusahaan.tex# Halaman pengesahan instansi magang/perusahaan
    ├── pernyataan.tex          # Pernyataan keaslian laporan
    ├── katapengantar.tex       # Kata pengantar laporan
    ├── daftarisi.tex           # Konfigurasi halaman daftar isi
    ├── daftargambar.tex        # Konfigurasi halaman daftar gambar
    ├── daftartabel.tex         # Konfigurasi halaman daftar tabel
    ├── daftarsingkatan.tex     # Daftar singkatan dan notasi ilmiah
    ├── abstrak.tex             # Halaman abstrak Bahasa Indonesia
    ├── abstract.tex            # Halaman abstract Bahasa Inggris
    ├── daftarlampiran.tex      # Konfigurasi halaman daftar lampiran
    ├── logbook.tex             # Catatan aktivitas mingguan (logbook)
    ├── lembarPerbaikan.tex     # Halaman catatan perbaikan sidang
    ├── motto.tex               # Halaman kutipan/motto hidup
    ├── rekognisi.tex           # Informasi pengakuan mata kuliah/sks
    │
    # Main Matter (Isi Laporan Utama)
    ├── bab1.tex                # Bab I: Pendahuluan
    ├── bab2.tex                # Bab II: Profil Perusahaan
    ├── bab3.tex                # Bab III: Pembahasan Utama Kerja Praktik
    ├── bab4.tex                # Bab IV: Analisis dan Hasil Pengujian
    ├── bab5.tex                # Bab V: Penutup (Kesimpulan dan Saran)
    │
    # Back Matter (Lampiran & Referensi)
    ├── daftarpustaka.tex       # Daftar Pustaka (menggunakan thebibliography)
    ├── pustaka.bib             # Database cadangan pustaka BibTeX
    ├── lampiran1.tex           # Berkas lampiran laporan ke-1
    └── lampiran2.tex           # Berkas lampiran laporan ke-2
```
