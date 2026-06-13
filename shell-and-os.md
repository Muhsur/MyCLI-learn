# Shell & Sistem Operasi CLI

## Apa itu Shell?

Shell adalah program yang bertindak sebagai interpreter antara user dan operating system. Shell membaca perintah dari user, menginterpretasinya, dan menjalankan program sesuai perintah tersebut.

## Jenis-Jenis Shell

### 1. Windows Command Prompt (CMD)
Shell default Windows sebelum PowerShell.

```cmd
# Navigasi
cd C:\Users
dir /s

# File operations
copy file.txt backup.txt
del file.txt
mkdir newfolder

# System commands
ipconfig
tasklist
systeminfo
```

### 2. Windows PowerShell
Shell modern Windows dengan object-oriented approach.

```powershell
# Navigasi
Set-Location C:\Users
Get-ChildItem -Recurse

# File operations
Copy-Item file.txt backup.txt
Remove-Item file.txt
New-Item -ItemType Directory -Name newfolder

# Pipeline dengan objects
Get-Process | Where-Object {$_.Memory -gt 100MB}
```

### 3. Bash (Linux/Mac)
Shell paling populer di Unix-based systems.

```bash
# Navigasi
cd ~/Documents
ls -la

# File operations
cp file.txt backup.txt
rm file.txt
mkdir newfolder

# Advanced
find . -name "*.txt"
grep "pattern" file.txt
sed 's/old/new/g' file.txt
```

### 4. Zsh (Linux/Mac)
Shell modern dengan fitur interaktif lebih baik.

```bash
# Similar dengan Bash tapi dengan features tambahan
ls -la
cd ../
cat file.txt
```

## Perbedaan Shell

| Fitur | CMD | PowerShell | Bash | Zsh |
|-------|-----|-----------|------|-----|
| OS | Windows | Windows, Linux, Mac | Linux, Mac | Linux, Mac |
| Object-Oriented | ❌ | ✅ | ❌ | ❌ |
| Scripting | Sederhana | Advanced | Advanced | Advanced |
| Performance | Cepat | Lebih lambat | Cepat | Cepat |
| Cross-platform | ❌ | ✅ | ✅ | ✅ |

## Path Separator

Perbedaan penting antar OS:

```powershell
# Windows
C:\Users\madsu\Documents\file.txt
set PATH=%PATH%;C:\new\path

# Linux/Mac
/home/madsu/Documents/file.txt
export PATH=$PATH:/new/path
```

## Variabel Lingkungan Penting

### Windows
```cmd
%USERPROFILE%     # C:\Users\username
%APPDATA%         # Application data folder
%TEMP%            # Temporary folder
%PATH%            # Directories untuk executables
%JAVA_HOME%       # Java installation directory
```

### Linux/Mac
```bash
$HOME              # /home/username
$USER              # Current username
$PATH              # Directories untuk executables
$JAVA_HOME         # Java installation directory
$SHELL             # Current shell
```

## Permission & Access Control

### Linux/Mac (Unix Permissions)
```bash
# File permissions (rwx format)
-rw-r--r--         # Owner: read/write, Group: read, Others: read
-rwx--x--x         # Owner: all, Group: execute, Others: execute

# Change permissions
chmod 755 script.sh     # Owner: rwx, Others: rx
chmod +x script.sh      # Add execute permission

# Change owner
chown user:group file.txt
```

### Windows (NTFS Permissions)
```cmd
# View permissions
icacls file.txt

# Grant permissions
icacls file.txt /grant Users:F

# Remove permissions
icacls file.txt /remove Users
```

## Environment Configuration Files

### Windows PowerShell
```powershell
# Profile location
$PROFILE    # Usually: C:\Users\username\Documents\PowerShell\profile.ps1

# Edit profile
notepad $PROFILE

# Reload profile
. $PROFILE
```

### Linux/Mac (Bash)
```bash
# Profile files
~/.bashrc           # Interactive shell
~/.bash_profile     # Login shell
~/.profile          # Generic profile

# Edit bashrc
nano ~/.bashrc

# Reload bashrc
source ~/.bashrc
```

## PATH Environment Variable

PATH adalah list direktori di mana shell mencari executable programs.

```powershell
# Windows - View PATH
echo %PATH%

# Linux/Mac - View PATH
echo $PATH
```

Output:
```
C:\Program Files\nodejs;C:\Program Files\Python39;C:\Windows\System32
/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

### Menambah PATH

```powershell
# Windows PowerShell
$env:PATH += ";C:\new\path"

# Linux/Mac Bash
export PATH="$PATH:/new/path"
```

## Built-in Commands vs External Commands

### Built-in Commands
Perintah yang built-in ke shell (tidak perlu file eksternal).

```powershell
cd              # Built-in
echo            # Built-in
type            # Built-in (Windows) / cat (Linux)
```

### External Commands
Perintah yang membutuhkan executable file terpisah.

```powershell
node            # Requires node.exe
python          # Requires python.exe
git             # Requires git.exe
```

## Checking Shell Version

```bash
# Check current shell
echo $SHELL                 # Linux/Mac
$PSVersionTable             # PowerShell

# Check installed versions
which bash                  # Linux/Mac - find Bash
which python                # Find Python

# Windows
where python
where node
```
---
> [!NOTE]
> Memahami shell yang digunakan adalah kunci untuk efektif menggunakan CLI. Setiap shell memiliki karakteristik, keuntungan, dan use case tersendiri. Pilih yang sesuai dengan sistem operasi dan kebutuhan Anda.
