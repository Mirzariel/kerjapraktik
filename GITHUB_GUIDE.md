# Panduan Menghubungkan Proyek ke GitHub & Melakukan Push

Dokumen ini berisi panduan langkah-demi-langkah tentang bagaimana proyek ini dihubungkan ke repositori GitHub **https://github.com/Mirzariel/kerjapraktik** dan cara mengunggah (push) perubahan selanjutnya.

---

## 1. Langkah-Langkah Awal (Sudah Dieksekusi)
Repositori lokal saat ini sudah diinisialisasi dan diunggah pertama kali ke GitHub menggunakan perintah berikut:

1. **Inisialisasi Repositori Git Lokal**:
   ```cmd
   git init
   ```

2. **Membuat Berkas `.gitignore`**:
   Berkas `.gitignore` telah dibuat untuk mengecualikan berkas-berkas sementara/auxiliary hasil kompilasi LaTeX agar tidak mengotori repositori GitHub.

3. **Mengonfigurasi Identitas Pengguna Git Lokal**:
   ```cmd
   git config user.name "Mirzariel Akmal Norman"
   git config user.email "mirzariel@gmail.com"
   ```

4. **Menambahkan dan Melakukan Commit Semua Berkas**:
   ```cmd
   git add .
   git commit -m "Initial commit: Laporan Kerja Praktik dengan format terstandardisasi dan penambahan penulis baru"
   ```

5. **Mengubah Nama Branch Utama**:
   ```cmd
   git branch -M main
   ```

6. **Menghubungkan ke GitHub Remote & Push**:
   ```cmd
   git remote add origin https://github.com/Mirzariel/kerjapraktik
   git push -u origin main
   ```

---

## 2. Cara Melakukan Push untuk Perubahan Selanjutnya

Jika Anda melakukan perubahan pada dokumen LaTeX di masa mendatang, ikuti langkah-langkah berikut untuk memperbarui repositori GitHub Anda:

1. **Buka Windows Command Prompt (CMD)** dan masuk ke direktori proyek:
   ```cmd
   cd "C:\Users\Mirzariel\Downloads\Kerja Praktik\latex\latex_laporan_v1"
   ```

2. **Cek status berkas** yang berubah:
   ```cmd
   git status
   ```

3. **Tambahkan berkas** yang diubah ke area staging:
   * Untuk menambahkan semua perubahan:
     ```cmd
     git add .
     ```
   * Atau tambahkan berkas tertentu saja (misalnya bab 2):
     ```cmd
     git add chapters/bab2.tex
     ```

4. **Lakukan Commit** dengan menuliskan pesan deskripsi perubahan Anda:
   ```cmd
   git commit -m "Deskripsi perubahan yang Anda lakukan"
   ```

5. **Push perubahan** ke GitHub:
   ```cmd
   git push
   ```

---

## 3. Penanganan Autentikasi GitHub (Bila Diminta)

Apabila di kemudian hari Git meminta kredensial autentikasi saat melakukan `git push`, Anda dapat menggunakan salah satu metode berikut:

### Metode A: Personal Access Token (PAT) - Sangat Direkomendasikan
GitHub tidak lagi mendukung penggunaan kata sandi (password) akun langsung melalui HTTPS. Sebagai gantinya, Anda harus menggunakan Personal Access Token:
1. Buka GitHub Anda, pergi ke **Settings** > **Developer Settings** > **Personal Access Tokens** > **Tokens (classic)**.
2. Klik **Generate new token (classic)**.
3. Beri nama token, centang cakupan (scope) `repo`, lalu klik **Generate token**.
4. Salin token tersebut dan simpan dengan aman.
5. Saat CMD meminta kata sandi (password) ketika melakukan push, masukkan token tersebut sebagai pengganti password akun Anda.

### Metode B: Menggunakan SSH (Opsional)
Jika Anda lebih menyukai SSH, Anda dapat mengubah URL remote Anda menjadi SSH:
1. Ubah URL remote:
   ```cmd
   git remote set-url origin git@github.com:Mirzariel/kerjapraktik.git
   ```
2. Pastikan Anda telah membuat SSH Key pada komputer Anda dan menambahkannya ke akun GitHub Anda (**Settings** > **SSH and GPG keys**).
