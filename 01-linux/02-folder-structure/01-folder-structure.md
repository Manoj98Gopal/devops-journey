[<-Back](../01-getting-started/04-package-manager.md) | [Index](../../README.md) | [Next->](../03-user-management/01-user-management.md) 

# 📁 Linux Folder Structure

## 📌 What is Folder Structure?
When you login to Linux
everything is organized in a **tree structure**
starting from one point called **root** `/`

```
vithamas@vithamas:~$    ← you are in /home/vithamas
root@vithamas:~#        ← you are in /root
root@vithamas:/#        ← you are in / (root of everything)
```

---

## 🌳 Complete Structure

```
/                       ← root of everything
├── etc                 ← all config files
├── home                ← all user folders
├── root                ← root user home
├── var                 ← logs and cache
├── tmp                 ← temporary files
├── bin                 ← basic commands
├── sbin                ← admin commands
├── usr/
│   ├── bin             ← user programs
│   └── sbin            ← admin programs
├── lib                 ← shared libraries
├── boot                ← boot files
├── dev                 ← device files
├── proc                ← process and kernel info
├── sys                 ← system configuration
├── srv                 ← server data
└── opt                 ← third party software
```

---

## 📂 Folders — Order of Importance for DevOps

---

### 1️⃣ /etc — Configuration Files
> Most important folder for DevOps!
> All system and software settings live here

```bash
# See what is inside
ls /etc

# Examples
/etc/nginx/nginx.conf     ← nginx config
/etc/ssh/sshd_config      ← ssh config
/etc/hosts                ← hostname config
/etc/passwd               ← all users list
/etc/group                ← all groups list
/etc/crontab              ← scheduled tasks
```

> 💡 Whenever you install any software
> its config file will be in /etc
> DevOps engineers spend most time here!

---

### 2️⃣ /var — Logs and Variable Data
> Second most important for DevOps!
> All log files live here
> Used for debugging and monitoring

```bash
# See what is inside
ls /var

# Examples
/var/log/syslog           ← system logs
/var/log/auth.log         ← login and auth logs
/var/log/nginx/           ← nginx logs
/var/log/docker/          ← docker logs
/var/cache/               ← cached data
/var/lib/                 ← application data
```

> 💡 When something goes wrong on a server
> first place DevOps engineers check is /var/log!

---

### 3️⃣ /home — User Home Folders
> Every human user has a folder here

```bash
# See what is inside
ls /home

# Examples
/home/manoj/              ← your files
/home/testuser/           ← testuser files

# Your home shortcut
cd ~                      ← goes to /home/manoj
```

> 💡 When you SSH into a server
> you land in your /home folder first!

---

### 4️⃣ /root — Root User Home
> Special home folder for root user only
> Separate from /home

```bash
# Switch to root
sudo su -

# You are now here
/root/

# Come back to your user
exit
```

> 💡 Root user does NOT have folder in /home
> Root user has its own special folder /root

---

### 5️⃣ /bin — Basic Commands
> Contains all basic Linux commands
> Available to all users

```bash
# See what is inside
ls /bin

# Examples — all these live in /bin
/bin/ls
/bin/cd
/bin/pwd
/bin/cat
/bin/echo
/bin/mkdir
```

> 💡 When you type ls or cd
> Linux runs the program from /bin!

---

### 6️⃣ /sbin — Admin Commands
> Contains administrative commands
> Only root or sudo users can use these

```bash
# See what is inside
ls /sbin

# Examples
/sbin/useradd             ← create users
/sbin/reboot              ← reboot system
/sbin/ifconfig            ← network config
/sbin/fdisk               ← disk management
```

> 💡 Regular users cannot run these commands
> You need sudo before every command here!

---

### 7️⃣ /usr — Unix System Resources
> Contains programs and tools
> installed for all users

```bash
# See what is inside
ls /usr

# Examples
/usr/bin/                 ← installed programs
/usr/sbin/                ← installed admin programs
/usr/lib/                 ← program libraries
/usr/local/               ← manually installed software

# When you install docker
# it goes here
/usr/bin/docker
```

> 💡 When you install any software using apt
> it gets installed under /usr/bin!

---

### 8️⃣ /tmp — Temporary Files
> Stores temporary files created by programs
> Automatically cleared on every reboot!

```bash
# See what is inside
ls /tmp

# Create a temp file
touch /tmp/test.txt

# It will be deleted on reboot!
```

> 💡 Used during software installations
> and file transfers
> Never store important files here!

---

### 9️⃣ /opt — Third Party Software
> Optional software installed manually
> Not installed via apt

```bash
# Examples
/opt/google/chrome/       ← Google Chrome
/opt/java/                ← Java manually installed
/opt/myapp/               ← your custom application
```

> 💡 In DevOps when you install software
> manually without apt
> it goes into /opt!

---

### 🔟 /lib — Shared Libraries
> Contains shared libraries
> used by /bin and /sbin programs
> Like helper code shared between programs

```bash
# See what is inside
ls /lib

# Examples
/lib/x86_64-linux-gnu/    ← 64 bit libraries
/lib/modules/             ← kernel modules
```

> 💡 Think of /lib like
> npm node_modules in JavaScript!
> Shared code used by many programs

---

### 1️⃣1️⃣ /boot — Boot Files
> Contains files needed to start Linux
> Very important — never delete anything here!

```bash
# See what is inside
ls /boot

# Examples
/boot/grub/               ← bootloader
/boot/vmlinuz             ← Linux kernel file
/boot/initrd.img          ← initial RAM disk
```

> ⚠️ Never modify or delete files in /boot
> Your system will not start!

---

### 1️⃣2️⃣ /dev — Device Files
> In Linux everything is a file
> even hardware devices!

```bash
# See what is inside
ls /dev

# Examples
/dev/sda                  ← your hard disk
/dev/sda1                 ← first partition
/dev/null                 ← black hole
/dev/random               ← random data generator
```

> 💡 /dev/null is very useful in DevOps!
> Send unwanted output here to discard it
```bash
command > /dev/null 2>&1  ← discard all output
```

---

### 1️⃣3️⃣ /proc — Process Information
> Virtual folder — does NOT exist on disk!
> Linux creates it in RAM on every boot
> Shows real time process and kernel info

```bash
# See CPU info
cat /proc/cpuinfo

# See RAM info
cat /proc/meminfo

# See system uptime
cat /proc/uptime

# See running processes
ls /proc
```

> 💡 Used for monitoring and debugging
> in DevOps!

---

### 1️⃣4️⃣ /sys — System Configuration
> Contains kernel and hardware information
> Used for system configuration

```bash
# See what is inside
ls /sys

# Examples
/sys/class/net/           ← network interfaces
/sys/block/               ← block devices
```

---

### 1️⃣5️⃣ /srv — Server Data
> Contains data served by your server
> Used for web servers and FTP servers

```bash
# Examples
/srv/www/                 ← web server files
/srv/ftp/                 ← ftp server files
```

---

## 🎯 Quick Reference — Switch Between Folders

```bash
# Go to root
cd /

# Go to home
cd ~
cd /home/manoj

# Switch to root user
sudo su -

# Go to etc
cd /etc

# Go to logs
cd /var/log

# Go to opt
cd /opt
```

---

## 🎯 DevOps Most Used Folders

| Priority | Folder | Why |
|---|---|---|
| ⭐⭐⭐ | `/etc` | all config files |
| ⭐⭐⭐ | `/var/log` | all log files |
| ⭐⭐⭐ | `/home` | user files |
| ⭐⭐ | `/opt` | third party software |
| ⭐⭐ | `/usr/bin` | installed programs |
| ⭐⭐ | `/tmp` | temporary files |
| ⭐ | `/boot` | boot files |
| ⭐ | `/dev` | device files |
| ⭐ | `/proc` | process info |

---
