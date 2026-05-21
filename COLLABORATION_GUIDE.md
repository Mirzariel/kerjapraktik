# Panduan Kolaborasi Git & GitHub

Dokumen ini menjelaskan alur kerja (workflow) kolaborasi menggunakan Git bersama rekan tim Anda untuk mengerjakan dokumen laporan ini.

---

## 1. Alur Kerja untuk Anda (Mirzariel)

Karena folder proyek saat ini di komputer Anda sudah terhubung ke GitHub, **Anda tidak perlu melakukan `git clone` di komputer ini.** Anda bisa langsung bekerja. 

Namun, jika Anda pindah ke komputer baru, lakukan langkah ini terlebih dahulu:
```cmd
git clone https://github.com/Mirzariel/kerjapraktik
```

### Langkah Kerja Harian:
1. **Tarik perubahan terbaru** sebelum mulai mengedit (selalu lakukan ini agar tidak bentrok dengan perubahan teman):
   ```cmd
   git pull origin main
   ```
2. **Edit berkas laporan** (misalnya menambahkan paragraf di `bab3.tex` atau memperbarui gambar).
3. **Simpan dan lakukan kompilasi** untuk memastikan tidak ada error.
4. **Unggah perubahan ke GitHub**:
   ```cmd
   git add .
   git commit -m "Menambahkan analisis kelayakan modul pada Bab 3"
   git push origin main
   ```

---

## 2. Alur Kerja untuk Teman Anda (Bagus)

Agar teman Anda bisa mengedit dan mengunggah perubahan ke repositori yang sama, lakukan langkah persiapan berikut:

### Langkah 1: Undang Teman sebagai Kolaborator di GitHub
Karena repositori Anda bersifat *private* (atau untuk mengizinkan akses *push* langsung):
1. Buka repositori Anda di web GitHub: **https://github.com/Mirzariel/kerjapraktik**.
2. Klik tab **Settings** > **Collaborators**.
3. Klik **Add people**, lalu masukkan username GitHub atau email rekan Anda.
4. Rekan Anda akan menerima email undangan. Rekan Anda **harus menerima undangan tersebut** sebelum bisa melakukan push.

### Langkah 2: Teman Melakukan Clone Proyek
Rekan Anda membuka CMD di komputernya dan mengunduh repositori tersebut:
```cmd
git clone https://github.com/Mirzariel/kerjapraktik
```

### Langkah 3: Teman Melakukan Kerja & Push
Setiap kali rekan Anda ingin mengedit berkas:
1. Masuk ke direktori hasil clone:
   ```cmd
   cd kerjapraktik
   ```
2. Tarik update terbaru (penting agar selalu sinkron):
   ```cmd
   git pull origin main
   ```
3. Lakukan pengeditan berkas.
4. Upload perubahan ke GitHub:
   ```cmd
   git add .
   git commit -m "Mengedit bagian landasan teori Bab 2"
   git push origin main
   ```

---

## 3. Aturan Emas Kolaborasi Git (PENTING)

1. **Selalu lakukan `git pull` sebelum mulai menulis.** Jika Anda atau teman Anda mengedit tanpa melakukan `git pull` terlebih dahulu, Git akan mendeteksi perbedaan versi (*conflict*) ketika melakukan `git push`.
2. **Jangan commit berkas PDF hasil kompilasi jika sering bentrok.** Berkas PDF biner seringkali sulit digabungkan secara otomatis oleh Git jika diedit bersamaan. Berkas `.gitignore` sudah otomatis mengecualikan berkas auxiliary LaTeX sementara, namun berkas `main.pdf` tetap disertakan. Jika PDF sering bentrok, Anda bisa menambahkannya ke `.gitignore`.
3. **Gunakan pesan commit yang jelas.** Pesan seperti `"Update bab 2"` lebih baik daripada hanya `"edit"` atau `"test"`.
