[<-Back](../05-vi-shortcut/01-vi-shortcut.md) | [Index](../../README.md) | [Next->]() 


# 🔐 File Permissions in Linux

## 📌 What is File Permission?
In Linux every file and folder has permissions
It controls **who can do what** with a file!

---

## 🔍 Check Permissions

```bash
# List files with permissions
ls -l
```

Output:
```
-rw-rw-r-- 1 manoj manoj 14 May 16 myfile.txt
drwxr-xr-x 2 manoj manoj 4096 May 16 myfolder
```

---

## 📌 Permission Structure

```
-  rw-  rw-  r--
|   |    |    |
|  Own  Grp  Others
|
- = file
d = directory
l = link
```

| Symbol | Meaning |
|---|---|
| `-` | file |
| `d` | directory |
| `l` | link |

---

## 📌 Permission Types

| Symbol | Name | Value | Meaning |
|---|---|---|---|
| `r` | read | 4 | can view file |
| `w` | write | 2 | can edit file |
| `x` | execute | 1 | can run file |
| `-` | none | 0 | no permission |

---

## 📌 Permission Groups

```
rw-     rw-     r--
 |       |       |
Owner   Group  Others

Owner  →  user who created file
Group  →  team members
Others →  everyone else
```

---

## 📌 Permission Numbers

```
r = 4
w = 2
x = 1
- = 0
```

| Number | Calculation | Permission |
|---|---|---|
| `7` | 4+2+1 | read + write + execute |
| `6` | 4+2+0 | read + write |
| `5` | 4+0+1 | read + execute |
| `4` | 4+0+0 | read only |
| `0` | 0+0+0 | no permission |

---

## 🔄 chmod — Change Permission

### Method 1 — Numeric

```bash
# Syntax
chmod [number] filename

# Examples
chmod 777 filename    # everyone full access
chmod 755 filename    # owner full, others read+execute
chmod 644 filename    # owner read+write, others read
chmod 600 filename    # owner only
chmod 666 filename    # everyone read+write
```

---

### Method 2 — Symbolic

```bash
# Add permission
chmod +x filename     # add execute to all
chmod +w filename     # add write to all
chmod +r filename     # add read to all

# Remove permission
chmod -x filename     # remove execute
chmod -w filename     # remove write
chmod -r filename     # remove read

# Specific user permission
chmod u+x filename    # add execute to owner only
chmod g+x filename    # add execute to group only
chmod o-r filename    # remove read from others
```

> 💡 `u` = owner, `g` = group, `o` = others

---

### Recursive Permission

```bash
# Change permission of folder + all files inside
chmod -R 755 foldername
```

---

## 🎯 Execute Permission — Important in DevOps!

```bash
# Create a shell script
touch deploy.sh
echo "echo Hello DevOps" > deploy.sh

# Try to run without execute permission
./deploy.sh
# Permission denied! ❌

# Give execute permission
chmod +x deploy.sh

# Now run
./deploy.sh
# Hello DevOps ✅
```

> 💡 In DevOps you will use
> `chmod +x` very often
> for shell scripts and deployment scripts!

---

## 🔄 chown — Change Ownership

```bash
# Change owner only
sudo chown owner filename

# Change group only
sudo chown :group filename

# Change both owner and group
sudo chown owner:group filename

# Recursive ownership change
sudo chown -R owner:group foldername
```

### Example

```bash
# Change owner to qa
sudo chown qa filename

# Change group to qa
sudo chown :qa filename

# Change both to qa
sudo chown qa:qa filename

# Recursive
sudo chown -R qa:qa foldername
```

---

## 📌 Most Used Permissions in DevOps

| Permission | Use Case |
|---|---|
| `chmod 777` | ⚠️ never use on production |
| `chmod 755` | directories and scripts |
| `chmod 644` | normal config files |
| `chmod 600` | private SSH keys |
| `chmod +x` | shell scripts |
| `chmod -R 755` | entire folder recursively |

---

## 🔒 Sticky Bit — Special Permission

> Sticky bit is used on **directories**
> Even if others have write permission
> They can only delete **their own files**
> Cannot delete other users files!

```bash
# Check sticky bit
ls -la /
# you will see
drwxrwxrwt /tmp
         ↑
         t = sticky bit active
```

```bash
# Enable sticky bit
chmod +t foldername

# Disable sticky bit
chmod -t foldername

# Check
ls -la foldername
```

### Real Example

```bash
# /tmp folder always has sticky bit
ls -la /
# drwxrwxrwt   tmp
#          ↑
#          t = sticky bit

# Everyone can write to /tmp
# But cannot delete other users files! ✅
```

---

## 🎯 Real World DevOps Examples

```bash
# 1. Give execute permission to script
chmod +x deploy.sh
./deploy.sh

# 2. Secure SSH private key
chmod 600 ~/.ssh/id_rsa

# 3. Set safe permission for config file
chmod 644 /etc/nginx/nginx.conf

# 4. Set permission for web folder
chmod -R 755 /var/www/html/

# 5. Change ownership to web server user
sudo chown -R www-data:www-data /var/www/html/

# 6. Set sticky bit on shared folder
chmod +t /shared/team-folder
```

---

## 📊 Commands Summary

| Command | Purpose |
|---|---|
| `ls -l` | check permissions |
| `chmod 755 file` | set numeric permission |
| `chmod +x file` | add execute permission |
| `chmod -x file` | remove execute permission |
| `chmod -R 755 folder` | recursive permission |
| `chown user file` | change owner |
| `chown :group file` | change group |
| `chown user:group file` | change both |
| `chown -R user:group folder` | recursive ownership |
| `chmod +t folder` | enable sticky bit |
| `chmod -t folder` | disable sticky bit |

---

## 🧠 Summary

```
Permission Structure:
- = file, d = directory
rwx = owner, rwx = group, rwx = others

Permission Values:
r=4, w=2, x=1, none=0

Common Permissions:
777 → everyone full ⚠️
755 → owner full, others read+execute
644 → owner read+write, others read
600 → owner only (SSH keys)
+x  → add execute (scripts)

Ownership:
chown user:group filename
chown -R user:group folder  ← recursive

Sticky Bit:
chmod +t folder  → only delete own files
chmod -t folder  → turn off
```