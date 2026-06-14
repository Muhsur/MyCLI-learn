# CLI Best Practices & Tips

## Navigasi </>
* **[readme](readme.md)** — Pengenalan CLI (Command Line Interface)
* **[basic-concept](basic-concept.md)** — Konsep Dasar CLI
* **[shell-and-os](shell-and-os.md)** — Shell & Sistem Operasi CLI
* **[You're here](best-practices.md)** — CLI Best Practices & Tips
* **[practical-examples.md](practical-examples.md)** — Contoh Praktis CLI
  
## 1. Command Organization

### Gunakan Perintah yang Jelas
```powershell
# ❌ Bad - tidak jelas apa yang dilakukan
cmd /c dir > temp.txt

# ✅ Good - jelas intent-nya
Get-ChildItem -Path ./src -Recurse | Out-File filelist.txt
```

### Group Related Commands
```powershell
# ❌ Bad - commands random
cd folder
ls
node app.js
npm install
echo "done"

# ✅ Good - logical order
npm install              # Setup
cd folder               # Navigate
node app.js             # Run
echo "done"             # Confirm
```

## 2. Efficiency Tips

### Tab Completion
```powershell
# Tekan TAB untuk auto-complete
cd Doc[TAB]  # Akan menjadi cd Documents

# Tekan TAB multiple times untuk cycle
git che[TAB]  # git cherry
git che[TAB]  # git cherry-pick
```

### Command History
```powershell
# Panah atas untuk previous command
[UP ARROW]   # Last command
[UP ARROW]   # Command sebelumnya

# Reverse search
Ctrl+R       # Search dalam history
# Ketik: find
# Tekan: Enter
```

### Reverse Search (Bash)
```bash
# Ctrl+R untuk reverse search
Ctrl+R
# Type pattern
find
# Result: find . -name "*.txt"
```

## 3. Output Management

### Redirect Output
```powershell
# Simpan output ke file
dir > filelist.txt

# Append output (tambah ke file)
dir >> filelist.txt

# Save both output dan error
command > output.txt 2>&1

# Linux/Mac
ls -la > files.txt
grep "error" log.txt >> errors.txt
```

### Piping untuk Filter
```powershell
# Cari file .txt
dir | findstr ".txt"

# Linux/Mac
ls | grep ".txt"

# Count hasil
ls *.txt | wc -l

# Sort hasil
ls -l | sort -k5 -n  # Sort by size
```

### Less/More Paging
```powershell
# Windows - pause output
dir /s | more

# Linux/Mac - use less
ls -la | less
# Tekan: Q untuk quit
# Tekan: Space untuk next page
```

## 4. Script & Automation

### Simple Script
```powershell
# backup.ps1 (PowerShell)
$backupDir = "C:\Backups"
$sourceDir = "C:\Important"
Copy-Item -Path $sourceDir -Destination $backupDir -Recurse
Write-Host "Backup completed at $(Get-Date)"
```

```bash
# backup.sh (Bash)
#!/bin/bash
BACKUP_DIR="/home/user/backups"
SOURCE_DIR="/home/user/important"
cp -r $SOURCE_DIR $BACKUP_DIR
echo "Backup completed at $(date)"
```

### Running Script
```powershell
# PowerShell
.\backup.ps1

# Bash
./backup.sh
chmod +x backup.sh  # Make executable first
```

## 5. Safe Operations

### Preview Sebelum Execute
```powershell
# Gunakan echo/Write-Host untuk preview
echo "Would delete: $file"

# Atau gunakan -WhatIf di PowerShell
Remove-Item -Path file.txt -WhatIf

# Atau gunakan -n di Linux
rm -i file.txt  # Interactive - ask for confirm
```

### Backup Sebelum Modifikasi
```powershell
# Copy original sebelum modifikasi
cp important.txt important.txt.backup

# Edit file
nano important.txt

# Jika error, restore
cp important.txt.backup important.txt
```

### Dry Run Commands
```powershell
# Test tanpa execute
rsync --dry-run -r source/ destination/

# Git dry-run untuk push
git push --dry-run origin main
```

## 6. Documentation & Help

### Built-in Help
```powershell
# Windows
help command
command /h
command /?

# PowerShell
Get-Help Get-ChildItem
Get-Help Get-ChildItem -Full

# Linux/Mac
man command
command --help
```

### Create Custom Help
```powershell
# Simpan tips di file
cat > cli-tips.txt << EOF
1. Always use absolute paths for critical operations
2. Test with --dry-run first
3. Keep backups of important files
EOF

# View help
cat cli-tips.txt
```

## 7. Common Mistakes to Avoid

### ❌ Dangerous Practices
```powershell
# NEVER - Delete everything
rm -rf /

# NEVER - Without confirmation
sudo rm -rf folder

# NEVER - Wrong path
mv file.txt ../../../file.txt  # Wrong destination!

# NEVER - Mixing paths
cd C:\Users && cd $HOME  # Inconsistent
```

### ✅ Safe Practices
```powershell
# GOOD - Verify path first
pwd  # Check current directory
dir  # Check contents
rm file.txt  # Then remove

# GOOD - Use -i flag
rm -i file.txt  # Ask for confirmation

# GOOD - Backup first
cp file.txt file.txt.backup
# Then modify safely
```

## 8. Performance Optimization

### Slow Command - Penyebab & Solusi
```powershell
# ❌ Lambat - Full recursive search
dir /s /p

# ✅ Cepat - Specific search
dir C:\specific\path

# ❌ Lambat - Wait for completion
npm install  # Takes time

# ✅ Cepat - Run in background
npm install &  # Linux/Mac
Start-Job -ScriptBlock {npm install}  # PowerShell
```

### Parallel Execution
```bash
# Run multiple commands in background
command1 &
command2 &
command3 &
wait  # Wait for all to complete
```

## 9. Useful Keyboard Shortcuts

| Shortcut | Function |
|----------|----------|
| Tab | Auto-complete |
| Ctrl+C | Cancel/Interrupt |
| Ctrl+L | Clear screen (Linux/Mac) |
| Ctrl+A | Beginning of line |
| Ctrl+E | End of line |
| Ctrl+R | Reverse search history |
| Ctrl+D | Logout/Exit |
| Up Arrow | Previous command |
| Down Arrow | Next command |

## 10. Cheat Sheet

```powershell
# Basic Navigation
pwd/cd              # Current/Change directory
ls/dir              # List files
mkdir               # Create folder
rmdir               # Delete folder

# File Operations
cat/type            # Display content
cp/copy             # Copy file
mv/move             # Move file
rm/del              # Delete file
find/where          # Search files

# Text Processing
grep/findstr        # Search text
sed                 # Stream editor
awk                 # Text processing
sort                # Sort lines
uniq                # Unique lines
wc                  # Word count

# System Info
whoami              # Current user
date                # Date & time
uname               # System info
df                  # Disk usage
ps                  # Running processes
```
---
> [!CAUTION]
> Efisiensi CLI datang dari practice dan pemahaman tools yang tersedia. Mulai dari command dasar, perlahan tingkatkan ke piping, scripting, dan automation. Safety adalah priority - selalu backup dan preview sebelum menjalankan commands destructive.
