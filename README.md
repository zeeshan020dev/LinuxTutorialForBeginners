# Linux Tutorial for Beginners

> Learn Linux step by step—from setup to commands, permissions, automation, and basic web hosting.

![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-121011?style=for-the-badge&logo=gnubash&logoColor=white)
![WSL](https://img.shields.io/badge/WSL-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white)
![Beginner Friendly](https://img.shields.io/badge/Beginner%20Friendly-2ea44f?style=for-the-badge)

## Overview

This repository is a practical Linux learning guide for beginners. It follows a clear sequence: understand Linux, set up a learning environment, learn daily commands, manage users and permissions, automate with cron, and deploy with Nginx.

## Who this is for

- Students starting Linux for development or DevOps
- Windows/macOS users who want a Linux practice setup
- Beginners preparing for cloud, backend, or sysadmin learning

## Prerequisites

- A computer (Windows/macOS/Linux)
- Internet connection
- Around 4 GB RAM and ~35 GB free disk space for a VM
- Willingness to practice commands in a safe test environment

> [!TIP]
> Use a virtual machine or test server while learning. Avoid practicing risky commands on your main system.

## Recommended Learning Path

Follow this exact sequence:

1. [What is Linux?](#what-is-linux)
2. [History of Linux](#history-of-linux)
3. [Getting an online Linux Server](#getting-an-online-linux-server)
4. [Installing Linux through VirtualBox on Windows](#installing-linux-through-virtualbox-on-windows)
5. [Installing Linux on Windows using WSL](#installing-linux-on-windows-using-wsl)
6. [Installing Linux through VirtualBox on Mac](#installing-linux-through-virtualbox-on-mac)
7. [Basic Linux Commands](#basic-linux-commands)
8. [Creating Users](#creating-users)
9. [Package Management](#package-management)
10. [Groups & Permissions](#groups--permissions)
11. [Processes & Services](#processes--services)
12. [Environment Variables, PATH and Bashrc](#environment-variables-path-and-bashrc)
13. [Archives and Compression](#archives-and-compression)
14. [Cronjobs](#cronjobs)
15. [Understanding Linux Filesystem](#understanding-linux-filesystem)
16. [Understanding Nginx](#understanding-nginx)
17. [Using FileZilla to Transfer Files](#using-filezilla-to-transfer-files)
18. [Conclusion](#conclusion)

---

## What is Linux?

Linux is an open-source operating system kernel. In simple terms, it is the core software layer that connects your hardware with the software you run.

- **Open source** means the code is publicly available
- Anyone can study, improve, and distribute Linux-based systems
- Popular Linux distributions include Ubuntu, Debian, Fedora, and Arch

## History of Linux

Linux has roots in Unix (1969). In 1991, Linus Torvalds started Linux as a free and open kernel project. Over time, Linux became a foundation for servers, cloud systems, Android, and development environments worldwide.

## Getting an online Linux Server

You can practice Linux on a cloud VPS (Virtual Private Server).

Typical beginner path:

1. Choose a VPS provider
2. Select Ubuntu LTS image
3. Start with a small plan (for learning)
4. Connect via SSH and begin command practice

> [!NOTE]
> The original learning path recommends choosing an Ubuntu LTS server plan for stability.

## Installing Linux through VirtualBox on Windows

1. Download VirtualBox from [virtualbox.org](https://www.virtualbox.org/wiki/Downloads) (`Windows hosts`)
2. Download Ubuntu Desktop LTS ISO from [ubuntu.com](https://ubuntu.com/download/desktop)
3. Create a new VM in VirtualBox
4. Attach the Ubuntu ISO
5. Set username/password during setup
6. Allocate resources (recommended learning baseline):
   - 4 GB RAM
   - 2 CPU cores
   - 35 GB storage
7. Complete installation and open terminal

### Practice check

```bash
pwd
whoami
ls
```

## Installing Linux on Windows using WSL

Quick start:

```bash
wsl --install
wsl --list --online
```

Then install Ubuntu from the list (or Microsoft Store).

> [!IMPORTANT]
> 🚧 **Work in progress:** detailed step-by-step WSL setup is still being expanded in this tutorial.

## Installing Linux through VirtualBox on Mac

Install VirtualBox for macOS, download Ubuntu ISO, and create a VM using a similar flow to Windows (adjusting host-specific permissions/settings).

> [!IMPORTANT]
> 🚧 **Work in progress:** detailed step-by-step macOS VirtualBox instructions are still being added.

## Basic Linux Commands

### Navigation

| Command | Purpose |
|---|---|
| `pwd` | Show current working directory |
| `ls` | List files and directories |
| `cd <dir>` | Move into a directory |
| `cd ..` | Move to parent directory |
| `cd ~` | Move to your home directory |
| `cd /` | Move to filesystem root (`/`) |
| `cd .` | Refer to current directory |

> [!NOTE]
> `/` is the top-level filesystem root. `~` is your current user's home directory.

### Files and editing

| Command | Purpose |
|---|---|
| `mkdir project` | Create directory |
| `mkdir -p a/b/c` | Create nested directories |
| `touch notes.txt` | Create empty file |
| `vim notes.txt` | Edit file in Vim |
| `cp src.txt dst.txt` | Copy file |
| `mv file.txt /path/` | Move file |
| `cat file.txt` | Print file content |
| `cat -n file.txt` | Print content with line numbers |
| `less file.txt` | View large file interactively |
| `clear` | Clear terminal screen |
| `history` | Show command history |

If Vim is missing:

```bash
sudo apt update
sudo apt install vim
```

### Practice exercise

```bash
mkdir linux-practice
cd linux-practice
touch notes.txt
echo "My first Linux note" > notes.txt
cat -n notes.txt
cd ..
```

## Creating Users

| Command | Purpose |
|---|---|
| `whoami` | Show current user |
| `sudo adduser <username>` | Create user (Ubuntu) |
| `su - <username>` | Switch to that user login shell |
| `exit` | Return to previous shell |
| `sudo usermod -aG sudo <username>` | Grant sudo access |

> [!WARNING]
> `sudo` runs commands with elevated privileges. Double-check every command before pressing Enter.

### Practice exercise

```bash
sudo adduser learner1
su - learner1
whoami
exit
```

## Package Management

Ubuntu uses APT (Advanced Package Tool).

| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh package index |
| `sudo apt upgrade` | Upgrade installed packages |
| `sudo apt install apache2` | Install Apache |
| `sudo apt remove apache2` | Remove package |
| `sudo apt purge apache2` | Remove package + config |
| `sudo apt install nginx` | Install Nginx |
| `sudo apt show nginx` | Show package details |
| `sudo apt install curl git python3` | Install multiple packages |
| `apt list --installed` | List installed packages |
| `sudo apt-get update` | Legacy equivalent of apt update |

## Groups & Permissions

| Command | Purpose |
|---|---|
| `sudo groupadd <group>` | Create group |
| `sudo useradd -m <user>` | Create user with home directory |
| `sudo passwd <user>` | Set user password |
| `sudo usermod -aG <group> <user>` | Add user to group |
| `groups <user>` | Show user groups |
| `ls -l` | Show ownership + permission bits |
| `sudo chown <user> <path>` | Change owner |
| `sudo chgrp <group> <path>` | Change group |
| `chmod g+w <path>` | Add group write permission |
| `chmod <octal> <path>` | Set octal permissions |

Permission math:

- `r = 4`, `w = 2`, `x = 1`
- Example: `755` = owner `rwx`, group `r-x`, others `r-x`

> [!WARNING]
> `chmod`, `chown`, and `chgrp` can lock users out or expose files. Apply changes only to intended paths.

## Processes & Services

A **process** is a running program (with a PID). A **service** is a managed background process.

| Command | Purpose |
|---|---|
| `ps` | Show current shell processes |
| `ps aux` | Show all processes |
| `ps aux | grep nginx` | Filter processes |
| `top` | Real-time process view |
| `htop` | Improved interactive process view |
| `kill <PID>` | Stop process gracefully |
| `kill -9 <PID>` | Force kill process |
| `pkill <name>` | Kill by process name |
| `systemctl status nginx` | Service status |
| `systemctl start nginx` | Start service |
| `systemctl stop nginx` | Stop service |
| `systemctl restart nginx` | Restart service |
| `sudo systemctl reload nginx` | Reload config without full stop |
| `sudo systemctl enable nginx` | Start service at boot |
| `sudo systemctl disable nginx` | Disable auto-start |

> [!WARNING]
> `kill -9` should be a last resort. It force-stops without graceful cleanup.

## Environment Variables, PATH and Bashrc

| Command | Purpose |
|---|---|
| `echo $HOME` | Show HOME variable |
| `printenv` / `env` | List environment variables |
| `echo $PATH` | Show executable search paths |
| `which ls` | Show command binary path |
| `export NAME=value` | Export environment variable |
| `export PATH="$PATH:/new/path"` | Append directory to PATH |
| `vim .bashrc` | Edit shell startup file |
| `source .bashrc` | Reload .bashrc now |

Example:

```bash
name="Zeeshan"
echo $name
export friend="value"
echo $friend
```

Simple script flow:

```bash
vim hello.sh
chmod +x hello.sh
./hello.sh
```

## Archives and Compression

- **Archive**: bundle files together
- **Compression**: reduce size

| Command | Purpose |
|---|---|
| `tar -cf archive.tar folder/` | Create tar archive |
| `tar -tf archive.tar` | List tar contents |
| `tar -xf archive.tar` | Extract tar |
| `tar -xvf archive.tar` | Extract tar verbosely |
| `gzip archive.tar` | Compress tar to `.gz` |
| `gunzip archive.tar.gz` | Decompress `.gz` |
| `zip -r name.zip folder/` | Create zip archive |
| `unzip name.zip` | Extract zip |
| `rm -rf folder/` | Recursively delete directory |

> [!CAUTION]
> `rm -rf` permanently deletes data. Verify the path before running it.

If tools are missing:

```bash
sudo apt update
sudo apt install gzip tar zip unzip
```

## Cronjobs

Cron schedules recurring tasks.

| Command | Purpose |
|---|---|
| `crontab -l` | List current cron jobs |
| `crontab -e` | Edit cron jobs |
| `sudo systemctl status cron` | Check cron service |
| `sudo systemctl start cron` | Start cron service |
| `sudo systemctl restart cron` | Restart cron service |
| `sudo systemctl stop cron` | Stop cron service |

Cron fields:

| Field | Allowed values | Notes |
|---|---|---|
| Minute | `0-59` | Minute of the hour |
| Hour | `0-23` | 24-hour format |
| Day of Month | `1-31` | Calendar day |
| Month | `1-12` or `JAN-DEC` | Month |
| Day of Week | `0-7` or `SUN-SAT` | `0` and `7` = Sunday |

Example cron entry (runs daily at 02:30):

```bash
30 2 * * * /home/user/backup.sh
```

Helpful reference: [crontab.guru](https://crontab.guru)

## Understanding Linux Filesystem

Common directories:

| Path | Meaning |
|---|---|
| `/` | Filesystem root (top of directory tree) |
| `/home` | User home directories |
| `/etc` | System configuration files |
| `/var` | Variable data (logs, spool, cache) |
| `/usr` | Userland programs and libraries |
| `/tmp` | Temporary files |

Examples:

```bash
cd ~
cd /
cd ..
ls /etc
```

## Understanding Nginx

Nginx is a high-performance web server and reverse proxy.

| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh packages |
| `sudo apt install nginx` | Install Nginx |
| `systemctl status nginx` | Check service status |
| `sudo systemctl restart nginx` | Restart after config changes |
| `sudo systemctl reload nginx` | Reload safely |
| `cd /var/www` | Typical web root location |
| `sudo ufw status` | Check firewall state |

> [!SECURITY]
> Review firewall and server config changes carefully. Misconfiguration can expose services publicly.

## Using FileZilla to Transfer Files

FileZilla helps transfer files between local and remote systems (typically over SFTP).

Basic flow:

1. Install FileZilla client
2. Open Site Manager
3. Set host, username, and port (usually `22` for SFTP)
4. Connect and transfer files

> [!IMPORTANT]
> 🚧 **Work in progress:** detailed FileZilla step-by-step screenshots and configuration walkthrough are still being added.

## Conclusion

Great progress—if you complete these 18 topics with hands-on practice, you will have a strong Linux foundation.

### Suggested next steps

- Bash scripting projects
- Git + GitHub workflows
- SSH and Linux networking basics
- Docker and container basics
- Nginx site and reverse proxy configuration
- Linux hardening and monitoring fundamentals

If this tutorial helped you, consider giving this repository a ⭐.
