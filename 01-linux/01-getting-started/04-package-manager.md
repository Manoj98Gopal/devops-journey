[<-Back](03-linux-distribution.md) | [Index](../../README.md) | [Next->](../02-folder-structure/01-folder-structure.md) 


# 📦 Package Manager

## 📌 What is a Package Manager?
A package manager is a **tool** in Linux
used to install, update and delete software
It automatically handles everything for you!

---

## 💡 Simple Analogy
Think of package manager like **Swiggy** 🍔

```
You (User)          →  wants software
Swiggy App          →  apt (package manager)
Restaurant          →  Ubuntu Repository
Food + sides        →  Software + Dependencies

You order food → Swiggy finds restaurant
→ delivers food + sides → to your door!

Same way →
You type apt install → apt finds repository
→ downloads software + dependencies
→ installs to your system! ✅
```

---

## ⚙️ What Package Manager Does

| Job | Meaning |
|---|---|
| **Install** | downloads and installs software |
| **Update** | updates package list from repository |
| **Upgrade** | upgrades outdated packages |
| **Remove** | deletes software from system |
| **Dependencies** | automatically installs required packages |

---

## 📌 apt update vs apt upgrade

> Very important difference!

| Command | What it does |
|---|---|
| `apt update` | updates package **list** only — checks what is new |
| `apt upgrade` | actually **installs** the new versions |

```
apt update   →  checking the menu for new items
apt upgrade  →  actually ordering the new items
```

> 💡 Always run both before installing anything!
```bash
sudo apt update
sudo apt upgrade -y
sudo apt install docker
```

---

## 📌 What is a Repository?

> Repository is like an **App Store**
> maintained by Ubuntu team
> Contains thousands of verified and safe packages

```
Your System  →  asks Ubuntu Repository
Repository   →  sends package + dependencies
apt          →  installs everything ✅
```

| Type | Meaning |
|---|---|
| **Official Repository** | maintained by Ubuntu team |
| **PPA** | maintained by third party developers |

---

## 📌 What are Dependencies?

```
You want to install → Docker
Docker needs        → containerd
containerd needs    → runc
runc needs          → libseccomp

apt automatically installs ALL of these! ✅
You don't have to worry about it!
```

> 💡 Without package manager
> you would manually install
> every dependency yourself! 😓

---

## 📦 Package Manager for Each Distro

| Linux OS | Family | Package Manager | Install Command |
|---|---|---|---|
| **Ubuntu** | Debian | `apt` | `apt install nginx` |
| **Debian** | Debian | `apt` | `apt install nginx` |
| **Linux Mint** | Debian | `apt` | `apt install nginx` |
| **Kali Linux** | Debian | `apt` | `apt install nginx` |
| **CentOS** | Red Hat | `yum` | `yum install nginx` |
| **Red Hat (RHEL)** | Red Hat | `dnf` | `dnf install nginx` |
| **Fedora** | Red Hat | `dnf` | `dnf install nginx` |
| **Amazon Linux** | Red Hat | `yum` | `yum install nginx` |
| **Alpine** | Alpine | `apk` | `apk add nginx` |
| **Arch Linux** | Arch | `pacman` | `pacman -S nginx` |
| **openSUSE** | SUSE | `zypper` | `zypper install nginx` |

---

## 🎯 Most Important apt Commands

```bash
# Update package list
sudo apt update

# Upgrade all packages
sudo apt upgrade -y

# Install a software
sudo apt install nginx

# Remove a software
sudo apt remove nginx

# Remove software + config files
sudo apt purge nginx

# Search for a software
sudo apt search nginx

# Check if software is installed
apt list --installed | grep nginx

# Clean unused packages
sudo apt autoremove
```

---

## 🎯 DevOps — Which Package Manager You Will Use

| Where | OS | Package Manager |
|---|---|---|
| Your local machine | Ubuntu | `apt` ✅ |
| AWS EC2 servers | Amazon Linux | `yum` |
| Docker containers | Alpine | `apk` |
| Enterprise servers | CentOS / RHEL | `yum` / `dnf` |

---

