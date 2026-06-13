# Pengenalan CLI (Command Line Interface)

## Apa itu CLI?

CLI (Command Line Interface) adalah antarmuka berbasis teks yang memungkinkan pengguna untuk berinteraksi dengan komputer melalui perintah-perintah tekstual. Berbeda dengan GUI (Graphical User Interface) yang menggunakan mouse dan icon, CLI menggunakan keyboard untuk mengetikkan perintah.

## Keuntungan Menggunakan CLI

- **Efisiensi**: Lebih cepat untuk tugas-tugas repetitif
- **Otomasi**: Mudah untuk membuat script dan automasi
- **Resource ringan**: Tidak memerlukan resources grafis yang besar
- **Remote access**: Dapat diakses dari mesin lain melalui SSH
- **Precision**: Kontrol penuh atas operasi yang dilakukan
- **Batch processing**: Dapat memproses banyak file sekaligus

## Bagian-Bagian Dasar CLI

### Prompt
```
C:\Users\madsu>
```
Tempat di mana user mengetikkan perintah.

### Command (Perintah)
Instruksi yang ingin dijalankan, contoh: `dir`, `cd`, `echo`

### Arguments (Argumen)
Parameter tambahan untuk command, contoh: `dir C:\Users`

### Options/Flags (Pilihan)
Pengubah perilaku command, biasanya diawali dengan `-` atau `--`
Contoh: `dir /s` atau `ls --color`

## Struktur Perintah Umum

```
command [options] [arguments]
```

### Contoh:
```powershell
# Menampilkan isi direktori dengan detail
dir /s /p

# Copy file dengan verifikasi
copy file1.txt file2.txt

# Menampilkan isi file
type filename.txt
```

## Jenis-Jenis CLI

### 1. Shell (Bash, PowerShell, CMD)
Shell yang paling umum digunakan untuk menjalankan perintah sistem.

### 2. Git CLI
Mengelola version control dan repository.

### 3. NPM CLI
Mengelola JavaScript packages dan dependencies.

### 4. Docker CLI
Mengelola container dan image Docker.

### 5. Cloud CLIs
AWS CLI, Azure CLI, Google Cloud CLI untuk mengelola cloud resources.

## Navigasi Dasar

```powershell
# Melihat direktori saat ini
pwd  # Linux/Mac
cd   # Windows

# Pindah ke direktori lain
cd path\to\directory

# Kembali ke direktori sebelumnya
cd ..

# Ke direktori home
cd ~

# Melihat isi direktori
ls      # Linux/Mac
dir     # Windows
```

## Tips & Trik

1. **Tab Completion**: Tekan Tab untuk auto-complete perintah atau file
2. **History**: Gunakan panah atas/bawah untuk mengulang perintah sebelumnya
3. **Clear Screen**: Gunakan `clear` (Linux/Mac) atau `cls` (Windows)
4. **Help Command**: Gunakan `--help` atau `/h` untuk melihat dokumentasi
5. **Piping**: Gunakan `|` untuk menggabungkan beberapa perintah
----
> [!NOTE]
> CLI adalah alat yang powerful untuk developer dan system administrator. Menguasai CLI akan meningkatkan produktivitas dan membuka banyak kemungkinan otomasi dalam pekerjaan sehari-hari.
