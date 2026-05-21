[<-Back](../03-user-management/01-user-management.md) | [Index](../../README.md) | [Next->](../05-vi-shortcut/01-vi-shortcut.md) 


# 📁 File Management in Linux

## 📌 What is File Management?
In Linux everything is a file!
File management means
creating, viewing, editing, copying,
moving and deleting files and folders!

---

## 📂 Folder Operations

### Create Folder
```bash
# Create single folder
mkdir foldername

# Create multiple folders at once
mkdir folder1 folder2 folder3

# Create nested folders
mkdir -p parent/child/grandchild
```

### Delete Folder
```bash
# Delete empty folder
rmdir foldername

# Delete folder with files inside
rm -r foldername

# Force delete without confirmation
rm -rf foldername
```

> ⚠️ Be careful with `rm -rf`
> It deletes everything permanently
> No recycle bin in Linux!

---

## 📄 File Operations

### Create File
```bash
# Create single file
touch filename.txt

# Create multiple files at once
touch file1.txt file2.txt file3.txt
```

### Delete File
```bash
# Delete a file
rm filename.txt
```

### Copy File or Folder
```bash
# Copy file
cp sourcefile.txt destinationfile.txt

# Copy file to another directory
cp file.txt /home/manoj/documents/

# Copy folder
cp -r sourcefolder/ destinationfolder/
```

### Move or Rename File or Folder
```bash
# Rename file
mv oldname.txt newname.txt

# Move file to another directory
mv file.txt /home/manoj/documents/

# Move folder
mv sourcefolder/ destinationfolder/
```

> 💡 `mv` does two jobs!
> Rename and Move!

---

## 👀 Viewing Files

### cat — View Full File
```bash
# View file content
cat filename.txt

# View with line numbers
cat -n filename.txt
```

### head — View Top Lines
```bash
# View top 10 lines (default)
head filename.txt

# View top 20 lines
head -n 20 filename.txt
```

### tail — View Bottom Lines
```bash
# View bottom 10 lines (default)
tail filename.txt

# View bottom 100 lines
tail -n 100 filename.txt

# Monitor live log file ← Very Important in DevOps!
tail -f filename.txt
```

> 💡 `tail -f` is very important in DevOps!
> Used to monitor log files in real time!
```bash
# Monitor system logs live
tail -f /var/log/syslog

# Monitor nginx logs live
tail -f /var/log/nginx/access.log
```

### less — View Large Files
```bash
# View large file page by page
less filename.txt

# Controls
# space     → next page
# b         → previous page
# q         → quit
# /keyword  → search in file
```

---

## 📋 Listing Files

```bash
# Simple list
ls

# Detailed list
ls -l

# Hidden files list
ls -a

# Hidden files with details
ls -la

# List with file sizes
ls -lh
```

---

## 🧭 Navigation

```bash
# Go into a folder
cd foldername

# Go back one level
cd ..

# Go to home directory
cd ~

# Go to root directory
cd /

# Go to previous directory
cd -

# Check current directory
pwd
```

---

## ✍️ Writing to Files

```bash
# Overwrite file content
echo "Hello DevOps" > filename.txt

# Append to file
echo "New Line" >> filename.txt

# Write multiple lines
cat > filename.txt << EOF
Line 1
Line 2
Line 3
EOF
```

| Operator | Meaning |
|---|---|
| `>` | overwrite — replaces existing content |
| `>>` | append — adds to existing content |

---

## 🔍 Finding Files

```bash
# Find file by name
find / -name filename.txt

# Find in current directory
find . -name filename.txt

# Find files only
find . -type f

# Find folders only
find . -type d

# Find files bigger than 100MB
find . -size +100M

# Find files modified in last 7 days
find . -mtime -7
```

---

## 🔍 Finding Commands

```bash
# Find where a command is stored
which ls
which docker
which nginx
```

---

## 💾 Disk Usage

```bash
# Check folder size
du -sh foldername

# Check all folders size
du -sh *

# Check disk space
df -h
```

---

## 🖨️ Print and Echo

```bash
# Print text
echo "Hello DevOps"

# Print with new line
echo -e "Line1\nLine2"

# Print without new line
echo -n "Hello"
```

---

## 🎯 Real World DevOps Examples

```bash
# 1. Create project structure
mkdir -p myproject/src
mkdir -p myproject/logs
mkdir -p myproject/config
touch myproject/config/app.conf
touch myproject/logs/app.log

# 2. Write config to file
echo "PORT=3000" > myproject/config/app.conf
echo "DB_HOST=localhost" >> myproject/config/app.conf

# 3. View config
cat myproject/config/app.conf

# 4. Monitor logs live
tail -f myproject/logs/app.log

# 5. Find large log files
find /var/log -size +100M

# 6. Check disk space
df -h
```

---

## 📊 Commands Summary

| Category | Command | Purpose |
|---|---|---|
| **Folder** | `mkdir foldername` | create folder |
| **Folder** | `rm -r foldername` | delete folder |
| **File** | `touch filename` | create file |
| **File** | `rm filename` | delete file |
| **File** | `cp source dest` | copy file |
| **File** | `mv old new` | move or rename |
| **View** | `cat filename` | view full file |
| **View** | `head -n 10 filename` | view top lines |
| **View** | `tail -n 10 filename` | view bottom lines |
| **View** | `tail -f filename` | monitor live |
| **View** | `less filename` | view page by page |
| **List** | `ls -la` | list all with details |
| **Navigate** | `cd foldername` | go into folder |
| **Navigate** | `cd ..` | go back one level |
| **Navigate** | `cd ~` | go to home |
| **Navigate** | `pwd` | current directory |
| **Write** | `echo "text" > file` | overwrite file |
| **Write** | `echo "text" >> file` | append to file |
| **Find** | `find . -name file` | find a file |
| **Find** | `which command` | find command location |
| **Disk** | `df -h` | check disk space |
| **Disk** | `du -sh folder` | check folder size |

