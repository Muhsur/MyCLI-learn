# Konsep Dasar CLI

## 1. Command (Perintah)

Command adalah instruksi dasar yang memberitahu sistem operasi untuk melakukan sesuatu.

### Struktur Command
```
command [options] [arguments]
```

### Contoh Command Umum
```powershell
# File & Folder
ls              # List files (Linux/Mac)
dir             # List files (Windows)
mkdir           # Create folder
rm              # Remove file
cp              # Copy file
mv              # Move file
cat             # Display file content

# Navigation
cd              # Change directory
pwd             # Print working directory
pushd           # Push directory
popd            # Pop directory

# System
echo            # Print text
clear           # Clear screen
date            # Show date & time
whoami          # Show current user
```

## 2. Arguments (Argumen)

Argumen adalah nilai yang dikirim ke command untuk diproses. Biasanya merupakan file, path, atau data yang akan dioperasikan command.

### Contoh Argumen
```powershell
# Command: copy, Arguments: file1.txt (source), file2.txt (destination)
copy file1.txt file2.txt

# Command: dir, Argument: C:\Users
dir C:\Users

# Command: echo, Argument: "Hello World"
echo "Hello World"
```

## 3. Options/Flags (Pilihan)

Options adalah pengubah yang mengatur bagaimana command akan berjalan. Biasanya diawali dengan dash (`-`) atau double dash (`--`).

### Format Options
```powershell
# Single dash dengan single letter
ls -l
dir /s

# Double dash dengan nama lengkap
ls --all
npm --version

# Kombinasi
ls -la
git log --oneline --graph
```

### Contoh Options Umum
```powershell
# Verbose mode (menampilkan detail)
dir /s
ls -v

# All files (termasuk hidden)
ls -a
dir /ah

# Recursive (mencari di subfolder)
rm -r folder
del /s /q folder

# Force (tanpa konfirmasi)
rm -f file.txt
del /f file.txt
```

## 4. Standard Input/Output (I/O)

### Input (Masukan)
```powershell
# Input dari keyboard
command < input.txt

# Input dari command lain (piping)
cat file.txt | grep "pattern"
```

### Output (Keluaran)
```powershell
# Output ke layar (default)
echo "Hello"

# Output ke file (overwrite)
echo "Hello" > output.txt

# Output ke file (append)
echo "World" >> output.txt

# Redirect error
command 2> error.txt

# Redirect semua output
command > output.txt 2>&1
```

## 5. Piping (Pipa)

Piping menghubungkan output dari satu command sebagai input untuk command lain.

```powershell
# Contoh dasar
cat file.txt | grep "search" | sort

# Pipeline dengan multiple commands
ls | grep ".txt" | wc -l

# Combine dengan redirection
ps aux | grep "node" > processes.txt
```

## 6. Environment Variables (Variabel Lingkungan)

Variabel yang menyimpan informasi tentang environment sistem.

```powershell
# Display variable
echo $HOME          # Linux/Mac
echo %USERPROFILE%  # Windows

# Set variable
export VAR="value"  # Linux/Mac
set VAR=value       # Windows (session)

# Use variable
echo $VAR
```

## 7. Working Directory (Direktori Kerja)

Directory saat ini tempat commands dijalankan.

```powershell
# Lihat current directory
pwd                 # Linux/Mac
cd                  # Windows

# Change directory
cd /path/to/dir

# Relative paths
cd ..               # Parent directory
cd ./folder         # Subfolder
cd ~/Documents      # Home directory
```

## 8. Path (Jalur)

### Absolute Path
Path lengkap dari root directory.
```powershell
C:\Users\madsu\Documents\file.txt     # Windows
/home/user/documents/file.txt         # Linux
```

### Relative Path
Path relatif dari current directory.
```powershell
Documents\file.txt
../Documents/file.txt
./subfolder/file.txt
```

## Ringkasan

| Konsep | Penjelasan | Contoh |
|--------|-----------|--------|
| Command | Instruksi dasar | `ls`, `cd`, `echo` |
| Argument | Nilai untuk command | `dir C:\Users` |
| Option | Pengubah perilaku | `ls -la`, `dir /s` |
| I/O | Input/Output | `>`, `<`, `\|` |
| Path | Lokasi file/folder | `/home/user/file.txt` |
| Variable | Penyimpan nilai | `$HOME`, `%USERPROFILE%` |
