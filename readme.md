# 🐧 Linux Cheatsheet for Curious Minds 🔥

## 📁 File & Directory Basics
| Command | What It Does |
|--------|---------------|
| `ls` | 📦 List files |
| `ls -al` | 📦🔍 List all files with details (including hidden) |
| `pwd` | 📍 Show current directory |
| `cd folder` | 🚪 Enter folder |
| `cd ..` | 🔙 Go up a directory |
| `mkdir mydir` | 🏗️ Make a new folder |
| `touch file.txt` | 📄 Create empty file |
| `rm file.txt` | ❌ Delete a file |
| `rm -r mydir` | 🧨 Delete a folder and contents |
| `cp file1 file2` | 📄➡️📄 Copy file |
| `mv file1 newfile` | 📂✂️ Rename or move file |

## 🧪 Viewing & Editing Files
| Command | What It Does |
|---------|--------------|
| `cat file.txt` | 🐱 View file content |
| `less file.txt` | 📖 View large file page by page |
| `echo "Hi"` | 📣 Print text to screen |
| `echo "hi" > hi.txt` | ✍️ Write to file |
| `nano file.txt` | 🧠 Simple file editor (if installed) |
| `vi file.txt` | 🧙‍♂️ Hardcore file editor |

## 🧠 System Info
| Command | What It Does |
|---------|--------------|
| `whoami` | 👤 Show current user |
| `hostname` | 🖥️ Show system name |
| `uname -a` | 🔧 Show kernel/system info |
| `top` / `htop` | 📊 Show running processes |
| `df -h` | 💾 Disk space usage |
| `free -m` | 🧠 Show memory usage |
| `uptime` | ⏲️ Show how long system has been up |
| `neofetch` | 🎨 Cool system summary (if installed) |

## 🧰 Power Tools
| Command | What It Does |
|---------|--------------|
| `sudo` | 🛡️ Run command as admin |
| `apt update` | 🔄 Refresh package list |
| `apt install` | 📦 Install new package |
| `find / -name file.txt 2>/dev/null` | 🔍 Find file (suppress errors) |
| `grep "word" file.txt` | 🔎 Search for text in a file |
| `chmod +x script.sh` | 🛠️ Make a file executable |
| `./script.sh` | 🚀 Run your script |

## 🧙‍♂️ Bonus: Shell Scripting Magic
```bash
#!/bin/bash
echo "Hello, Linux!"
```
Save as `hello.sh` → `chmod +x hello.sh` → `./hello.sh`

## 🌍 Networking Commands
| Command | What It Does |
|---------|--------------|
| `curl https://example.com` | 🌐 Fetch website data |
| `ping google.com` | 📡 Test connection |
| `ip a` or `ifconfig` | 🔌 See IP addresses |

## 🧹 Clean Up & Exit
| Command | What It Does |
|---------|--------------|
| `clear` | 🧼 Clean the terminal screen |
| `exit` | 👋 Exit the session |


linux_fun_commands_md = """
# 🎉 20 Fun Linux Terminal Commands

| Command | Description |
|--------|-------------|
| `cmatrix` | 💻 Hacker-style "Matrix" digital rain in terminal |
| `figlet "Hello!"` | 🔤 Turns your text into ASCII art |
| `lolcat` | 🌈 Pipe any output through it for rainbow colors (`echo Hello | lolcat`) |
| `cowsay "I'm a cow!"` | 🐄 Cow speaks your message |
| `fortune` | 🍀 Displays a random witty/wise quote |
| `fortune | cowsay` | 🧠🐄 Cow says a fortune |
| `sl` | 🚂 Type `sl` instead of `ls` and get a steam locomotive 🚆 |
| `asciiquarium` | 🐠 Live ASCII aquarium in your terminal (needs Perl dependencies) |
| `rev` | 🔁 Reverses the text (`echo hello | rev` → `olleh`) |
| `yes Linux` | 🔁 Repeats "Linux" forever until stopped with Ctrl+C |
| `cal` | 📆 Shows a calendar |
| `uptime` | ⏲️ See how long your system's been running |
| `neofetch` | 💻 Stylish system info with your OS logo |
| `screenfetch` | 🖥️ Similar to `neofetch`, but different style |
| `htop` | 📊 Interactive system monitor (like Task Manager) |
| `tree` | 🌳 Shows directory structure in tree form |
| `watch -n 1 date` | ⏰ Updates and displays the current time every second |
| `xeyes` | 👀 GUI eyeballs that follow your cursor (in desktop env) |
| `espeak "Linux is awesome"` | 🗣️ Text-to-speech from the terminal (requires audio setup) |

---

## 📦 How to Install Them

```bash
sudo apt update
sudo apt install cmatrix figlet toilet lolcat cowsay fortune sl tree neofetch htop espeak x11-utils
```

# 🐧 Linux Folder Permissions Cheatsheet

## 🔍 Understanding Permissions

Example output of `ls -l`:
```
drwxr-xr-- 1 calvin devs 4096 Jun 3 10:00 myfolder
```

- **d** – directory  
- **r** – read  
- **w** – write  
- **x** – execute  
- **Three permission groups**:
  - **User (Owner)**
  - **Group**
  - **Others**

```
rwxr-xr--
│ │ │ └─ Others: read only
│ │ └─── Group: read + execute
│ └───── User: read + write + execute
└─────── Directory flag
```

---

## 📂 Viewing Permissions

```bash
ls -l              # List with permissions
ls -ld foldername  # Show permissions of folder only
```

---

## 🛠️ Changing Permissions (chmod)

### Symbolic Mode

```bash
chmod u+x folder      # Add execute to user
chmod g-w folder      # Remove write from group
chmod o=r folder      # Set others to read-only
```

### Numeric (Octal) Mode

| Value | Permission |
|-------|------------|
| 7     | rwx        |
| 6     | rw-        |
| 5     | r-x        |
| 4     | r--        |
| 0     | ---        |

### Basically

| Permission | Value | Meaning      |
|------------|-------|--------------|
| r          | 4     | read         |
| w          | 2     | write        |
| x          | 1     | execute      |

Add the values for each group (user, group, others) to get the octal permission number.  
For example, `rwx` = 4+2+1 = **7**, `rw-` = 4+2 = **6**, `r--` = 4.

```bash
chmod 755 folder      # rwx for user, r-x for group & others
chmod 700 folder      # rwx for user only
chmod 770 folder      # rwx for user and group
```

### Recursively

```bash
chmod -R 755 folder
```

---

## 👤 Changing Ownership (chown)

```bash
chown user folder
chown user:group folder
chown -R user:group folder  # Recursive
```

---

## 👥 Changing Group Only (chgrp)

```bash
chgrp group folder
```

---

## 📦 Moving Files to Folder

```bash
mv file1 file2 folder/
mv *.txt folder/        # Move all .txt files
```

---

## ✅ Quick Summary

| Command                | Description                          |
|------------------------|--------------------------------------|
| `ls -l`                | Show permissions                     |
| `chmod 755 folder`     | Set rwx for owner, r-x for others    |
| `chown user folder`    | Change folder owner                  |
| `chmod -R 700 folder`  | Restrict all access to owner only    |
| `mv file folder/`      | Move file into folder                |

---

## 🧪 Useful Examples

- Make a folder accessible to everyone:
  ```bash
  chmod 777 public_folder
  ```

- Secure a private folder:
  ```bash
  chmod 700 secrets
  ```
