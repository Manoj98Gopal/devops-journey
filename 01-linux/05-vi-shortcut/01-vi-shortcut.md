[<-Back](../04-file-management/01-file-management.md) | [Index](../../README.md) | [Next->]() 

# 📝 VI Editor in Linux

## 📌 What is VI Editor?
VI is a **text editor** in Linux
Available on every Linux system by default
DevOps engineers use it to
edit config files on remote servers!

> 💡 There is also **VIM** — improved version of VI
> Most systems use VIM when you type `vi`

```bash
# Open or create a file
vi filename.txt

# Open with VIM
vim filename.txt
```

---

## 🔄 Three Modes of VI

```
┌─────────────────────────────────────┐
│           Normal Mode               │
│      (Default when you open)        │
│   navigate, copy, paste, delete     │
├─────────────────────────────────────┤
│           Insert Mode               │
│        (Press i to enter)           │
│         type and edit text          │
├─────────────────────────────────────┤
│          Command Mode               │
│       (Press : to enter)            │
│    save, quit, search, replace      │
└─────────────────────────────────────┘
```

| Mode | How to Enter | Purpose |
|---|---|---|
| **Normal Mode** | default / press `Esc` | navigate and edit |
| **Insert Mode** | press `i` | type text |
| **Command Mode** | press `:` | save, quit, search |

---

## 🔄 Mode Switching

```
Open VI
    ↓
Normal Mode (default)
    ↓          ↑
press i      press Esc
    ↓          ↑
Insert Mode ──┘
    
Normal Mode
    ↓
press :
    ↓
Command Mode
```

---

## ✍️ Insert Mode — How to Enter

```bash
i    →  insert before cursor
a    →  insert after cursor
o    →  insert new line below
O    →  insert new line above
I    →  insert at beginning of line
A    →  insert at end of line
```

> 💡 Most commonly used is `i`
> Press `Esc` to come back to Normal Mode

---

## 💾 Command Mode — Save and Quit

```bash
:w       →  save file
:w!      →  force save file
:q       →  quit (only if no changes)
:q!      →  quit without saving
:wq      →  save and quit
:wq!     →  force save and quit
:x       →  save and quit (same as :wq)
```

| Command | Meaning |
|---|---|
| `:w!` | save only |
| `:q!` | quit without saving |
| `:wq!` | save and quit |

---

## 🧭 Navigation in Normal Mode

```bash
# Basic movement
h    →  move left
l    →  move right
k    →  move up
j    →  move down

# Word movement
w    →  move to next word
b    →  move to previous word

# Line movement
0    →  go to beginning of line
$    →  go to end of line

# File movement
gg   →  go to first line
G    →  go to last line
:100 →  go to line 100
```

---

## ✂️ Edit in Normal Mode

```bash
# Delete
x    →  delete single character
dd   →  delete entire line
5dd  →  delete 5 lines

# Copy (yank)
yy   →  copy entire line
5yy  →  copy 5 lines

# Paste
p    →  paste below cursor
P    →  paste above cursor

# Undo and Redo
u        →  undo last action
Ctrl + r →  redo last action
```

---

## 🔍 Search in Normal Mode

```bash
# Search forward
/keyword    →  search keyword forward
n           →  go to next result
N           →  go to previous result

# Search backward
?keyword    →  search keyword backward
```

---

## 🔄 Search and Replace in Command Mode

```bash
# Replace first occurrence in current line
:s/oldword/newword/

# Replace all occurrences in current line
:s/oldword/newword/g

# Replace all occurrences in entire file
:%s/oldword/newword/g

# Replace with confirmation
:%s/oldword/newword/gc
```

---

## 📊 Show Line Numbers

```bash
# Show line numbers
:set nu

# Hide line numbers
:set nonu
```

---

## 🎯 Real World DevOps Examples

```bash
# 1. Edit nginx config
vi /etc/nginx/nginx.conf

# 2. Edit SSH config
vi /etc/ssh/sshd_config

# 3. Edit hosts file
vi /etc/hosts

# 4. Edit crontab
vi /etc/crontab

# 5. Edit bash profile
vi ~/.bashrc
```

---

## 🎯 Most Used VI Workflow in DevOps

```
1. Open file         →  vi filename
2. Enter insert mode →  press i
3. Edit the file     →  type your changes
4. Exit insert mode  →  press Esc
5. Save and quit     →  :wq!
```

---

## 📊 Commands Summary

| Category | Command | Purpose |
|---|---|---|
| **Open** | `vi filename` | open file |
| **Insert** | `i` | enter insert mode |
| **Exit Insert** | `Esc` | back to normal mode |
| **Save** | `:w!` | save file |
| **Quit** | `:q!` | quit without save |
| **Save+Quit** | `:wq!` | save and quit |
| **Navigate** | `gg` | go to first line |
| **Navigate** | `G` | go to last line |
| **Navigate** | `:100` | go to line 100 |
| **Delete** | `dd` | delete line |
| **Copy** | `yy` | copy line |
| **Paste** | `p` | paste |
| **Undo** | `u` | undo |
| **Search** | `/keyword` | search in file |
| **Replace** | `:%s/old/new/g` | replace all |
| **Line Numbers** | `:set nu` | show line numbers |

---

## 🧠 Summary

```
VI has 3 modes:
Normal Mode   →  default — navigate and edit
Insert Mode   →  press i — type text
Command Mode  →  press : — save and quit

Most used commands:
i      →  start typing
Esc    →  stop typing
:wq!   →  save and quit
:q!    →  quit without saving
/word  →  search
dd     →  delete line
yy     →  copy line
p      →  paste
u      →  undo
```