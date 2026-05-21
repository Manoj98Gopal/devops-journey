[<-Back](../02-folder-structure/01-folder-structure.md) | [Index](../../README.md) | [Next->](../04-file-management/01-file-management.md) 


# 👤 Users and Groups in Linux

## 📌 What is a User in Linux?
Linux is a **multi-user operating system**
We can create accounts for different people
and different purposes!

```
Example:
manoj     → developer account
testuser  → testing account
www-data  → web server account
root      → admin account
```

---

## 👤 Creating a User

### Two Commands to Create User

| Command | What it does |
|---|---|
| `useradd` | creates user — manual setup needed |
| `adduser` | creates user — automatic setup |

---

### 1️⃣ useradd — Manual Way

```bash
# Basic create — no home, no shell
sudo useradd username

# Create with home directory
sudo useradd -m username

# Create with home + shell
sudo useradd -m -s /bin/bash username

# Create with home + shell + group
sudo useradd -m -s /bin/bash -G groupname username

# Set password
sudo passwd username
```

---

### 2️⃣ adduser — Automatic Way

```bash
# Creates everything automatically
# home directory, shell, password
sudo adduser username
```

> It will ask:
```
Enter password:
Full Name:
Room Number:
Phone:
```

---

### useradd vs adduser

| Feature | useradd | adduser |
|---|---|---|
| Home Directory | manual `-m` needed | automatic ✅ |
| Shell | manual `-s` needed | automatic ✅ |
| Password | manual `passwd` needed | asks during creation ✅ |
| Interactive | No | Yes |
| Scripting | ✅ better for scripts | not good for scripts |

> 💡 For **scripts** use `useradd`
> For **manual creation** use `adduser`

---

## 📂 Important User Files

### /etc/passwd — User Information
```bash
# See all users
cat /etc/passwd

# See only human users
awk -F: '$3 >= 1000' /etc/passwd

# See only usernames
cut -d: -f1 /etc/passwd
```

Format:
```
manoj : x : 1000 : 1000 : : /home/manoj : /bin/bash
  |    |    |      |     |       |              |
User  Pwd  UID   GID  Info   Home Dir        Shell

x = password stored in /etc/shadow
```

---

### /etc/shadow — Password Information
```bash
# See encrypted passwords
sudo cat /etc/shadow
```

Format:
```
manoj : $6$xyz$abc : 19000 : 0 : 99999
  |         |          |            |
User    Hashed       Last          Max
       Password    Changed        Days
```

> 💡 Passwords are **hashed** not encrypted!
> Hashing is **one way only**
> Cannot be reversed — even admin cannot see it!

```
Hashing     →  one way — cannot reverse ✅
Encryption  →  two way — can decrypt ❌
```

---

## 🔄 Modifying a User

```bash
# Change username
sudo usermod -l newname oldname

# Change home directory
sudo usermod -d /new/home/directory -m username

# Change shell
sudo usermod -s /bin/zsh username

# Add user to group
sudo usermod -aG groupname username

# Lock user account
sudo usermod -L username

# Unlock user account
sudo usermod -U username
```

---

## ❌ Deleting a User

```bash
# Delete account only
# home directory still exists
sudo userdel username

# Delete account + home directory + files
sudo userdel -r username
```

| Command | What gets deleted |
|---|---|
| `userdel username` | account only |
| `userdel -r username` | account + home + all files |

---

## 👥 Creating a Group

```bash
# Create a group
sudo groupadd groupname

# Example
sudo groupadd devops
```

> All groups stored in `/etc/group`

```bash
# See all groups
cat /etc/group

# Format
devops : x : 1001 : manoj,testuser
   |    |    |           |
 Name  Pwd  GID       Members
```

---

## 👥 Managing Groups

```bash
# Add user to group
sudo usermod -aG groupname username

# Remove user from group
sudo gpasswd -d username groupname

# See groups of a user
groups username

# See all members of a group
getent group groupname

# Rename a group
sudo groupmod -n newname oldname

# Delete a group
sudo groupdel groupname
```

---

## 🔍 Checking User Information

```bash
# Check current logged in user
whoami

# Check user details
id username

# Check user groups
groups username

# Switch to another user
su - username

# Switch to root
sudo su -

# Check if user is locked
sudo passwd -S username

# See password expiry info
sudo chage -l username
```

---

## 🎯 Real World DevOps Example

```bash
# Create a devops team

# 1. Create group
sudo groupadd devops

# 2. Create user
sudo useradd -m -s /bin/bash manoj

# 3. Set password
sudo passwd manoj

# 4. Add user to devops group
sudo usermod -aG devops manoj

# 5. Verify
id manoj
groups manoj

# 6. Give devops group access to a folder
sudo chgrp devops /project
sudo chmod 770 /project
```

---

## 📊 Important Files Summary

| File | Purpose |
|---|---|
| `/etc/passwd` | stores all user information |
| `/etc/shadow` | stores encrypted passwords |
| `/etc/group` | stores all group information |
| `/etc/sudoers` | stores sudo permissions |

