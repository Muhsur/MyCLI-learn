# Contoh Praktis CLI
## 🗺️ Navigasi <>
* **[readme](readme.md)** — Pengenalan CLI (Command Line Interface)
* **[basic-concept](basic-concept.md)** — Konsep Dasar CLI
* **[shell-and-os](shell-and-os.md)** — Shell & Sistem Operasi CLI
* **[best-practices](best-practices.md)** — CLI Best Practices & Tips
* **[You're here](practical-examples.md)** — Contoh Praktis CLI

## 1. File & Folder Management

### Create Directory Structure
```powershell
# Windows PowerShell
New-Item -ItemType Directory -Path "project\src\components\buttons"

# Linux/Mac Bash
mkdir -p project/src/components/buttons
```

### Copy Multiple Files
```powershell
# Copy semua .txt files
Get-ChildItem *.txt | Copy-Item -Destination .\backup\

# Linux/Mac
cp *.txt ./backup/
```

### Find & Replace dalam Multiple Files
```bash
# Linux/Mac - Find dan replace di semua .js files
sed -i 's/oldText/newText/g' *.js

# Windows PowerShell
Get-ChildItem *.js | ForEach-Object {
    (Get-Content $_) -replace 'oldText', 'newText' | Set-Content $_
}
```

### Delete Files Older than X Days
```bash
# Delete files older than 30 days
find . -type f -mtime +30 -delete

# Or just list them first (safer)
find . -type f -mtime +30
```

## 2. Text Processing

### Search & Count
```bash
# Count occurrences
grep -c "pattern" file.txt

# Count files with pattern
grep -r "pattern" . | wc -l

# Show line numbers
grep -n "pattern" file.txt
```

### Extract Specific Columns
```bash
# Show column 1 and 3 (space-separated)
awk '{print $1, $3}' file.txt

# Show column 2 (comma-separated CSV)
awk -F',' '{print $2}' data.csv
```

### Sort Data
```bash
# Sort files by size (largest first)
ls -lS

# Sort alphabetically with reverse
sort -r names.txt

# Sort by column
sort -k3 -n data.txt  # Sort by column 3 numerically
```

## 3. Git Operations

### Common Git Commands
```bash
# Initialize & clone
git init
git clone <url>

# Check status & diff
git status
git diff
git log --oneline

# Stage & commit
git add .
git commit -m "Message"

# Push & pull
git push origin main
git pull origin main

# Create & switch branch
git branch feature
git checkout -b feature

# Merge & rebase
git merge feature
git rebase main
```

### Useful Git Aliases
```bash
# Create aliases for faster commands
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch

# Usage
git st          # Instead of git status
git co main     # Instead of git checkout main
```

## 4. Node.js & NPM

### Project Setup
```bash
# Initialize project
npm init -y

# Install dependencies
npm install express dotenv

# Install dev dependencies
npm install -D nodemon

# Install specific version
npm install express@4.17.1
```

### Running Scripts
```bash
# From package.json scripts
npm start
npm test
npm run dev

# Global packages
npm install -g nodemon
npm uninstall -g nodemon
```

### Check Versions & Updates
```bash
# Check versions
npm -v
node -v
npm list
npm list -g

# Check for outdated packages
npm outdated

# Update packages
npm update
npm update express
```

## 5. Docker Operations

### Container Management
```bash
# List images & containers
docker images
docker ps
docker ps -a

# Build image
docker build -t myapp:1.0 .

# Run container
docker run -p 3000:3000 myapp:1.0

# Stop & remove
docker stop <container-id>
docker rm <container-id>
```

### Useful Docker Commands
```bash
# View logs
docker logs <container-id>
docker logs -f <container-id>  # Follow logs

# Execute command in container
docker exec -it <container-id> /bin/bash

# Push to registry
docker tag myapp:1.0 username/myapp:1.0
docker push username/myapp:1.0
```

## 6. Database Operations

### MySQL/PostgreSQL
```bash
# Connect to database
mysql -u root -p

# Common queries
SELECT * FROM users;
INSERT INTO users (name) VALUES ('John');
UPDATE users SET name='Jane' WHERE id=1;
DELETE FROM users WHERE id=1;

# Export database
mysqldump -u root -p database > backup.sql

# Import database
mysql -u root -p database < backup.sql
```

### MongoDB
```bash
# Connect
mongo mongodb://localhost:27017/dbname

# Common operations
db.collection.find()
db.collection.insertOne({name: 'John'})
db.collection.updateOne({_id: ObjectId('...')}, {$set: {name: 'Jane'}})
db.collection.deleteOne({_id: ObjectId('...')})
```

## 7. System Monitoring

### Check System Resources
```bash
# CPU & Memory usage
top                    # Linux/Mac
tasklist /v            # Windows

# Disk space
df -h                  # Linux/Mac
diskutil list          # Mac
Get-Volume             # PowerShell

# Network status
netstat -an
ss -tuln               # Linux
```

### Monitor Processes
```bash
# List all processes
ps aux

# Find process by name
ps aux | grep node

# Kill process
kill -9 <PID>

# Monitor in real-time
top -p <PID>
```

## 8. Network Operations

### Check Connectivity
```bash
# Ping server
ping google.com

# DNS lookup
nslookup google.com
dig google.com

# Check port
telnet localhost 3000
nc -zv localhost 3000
```

### Download Files
```bash
# Using curl
curl -O https://example.com/file.zip

# Using wget (Linux)
wget https://example.com/file.zip

# With authentication
curl -u username:password https://example.com/file.zip
```

## 9. Backup & Archive

### Create Archives
```bash
# Create tar.gz
tar -czf backup.tar.gz folder/

# Create zip
zip -r backup.zip folder/

# Extract
tar -xzf backup.tar.gz
unzip backup.zip
```

### Automated Backup Script
```bash
#!/bin/bash
BACKUP_DIR="/mnt/backups"
SOURCE_DIR="/home/user/important"
DATE=$(date +%Y-%m-%d)

tar -czf "$BACKUP_DIR/backup-$DATE.tar.gz" $SOURCE_DIR
echo "Backup completed: backup-$DATE.tar.gz"

# Remove old backups (older than 30 days)
find $BACKUP_DIR -name "backup-*.tar.gz" -mtime +30 -delete
```

## 10. Useful One-Liners

```bash
# Find large files
find . -type f -size +10M

# List files with their sizes
ls -lh | sort -k5 -h

# Download entire website
wget -r --no-parent https://example.com

# Create numbered backup
for i in {1..5}; do cp file.txt file.txt.$i; done

# Show duplicate files
find . -type f -exec md5sum {} + | sort | uniq -d

# Count lines in all .js files
find . -name "*.js" -exec wc -l {} + | tail -1

# Replace text in all files
find . -name "*.js" -type f -exec sed -i 's/old/new/g' {} +

# Create index.html for each directory
find . -type d -exec touch {}/.index.html \;

# List top 10 largest directories
du -sh */ | sort -rh | head -10

# Monitor file changes
watch -n 1 'ls -la'
```
---
> [!TIP]
> Praktik langsung adalah cara terbaik untuk menguasai CLI. Mulai dengan perintah dasar, kemudian eksplorasi kombinasi commands yang lebih kompleks.
