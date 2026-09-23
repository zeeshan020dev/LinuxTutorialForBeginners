# Linux Tutorial for Beginners

> Learn Linux step by step — from setup to commands, permissions, automation, and basic web hosting.

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

**Linux is a free and open-source operating system kernel** that manages a computer's hardware and allows software to interact with it.

The kernel is the core component of an operating system. It manages essential resources such as the CPU, memory, storage, and running processes.

### How Linux Works

```text
User → Applications / Shell → Linux Kernel → Hardware
```

| Component | Purpose |
|-----------|---------|
| Hardware | Physical components such as CPU, RAM, and storage. |
| Kernel | Manages hardware resources and communication with software. |
| Shell | Allows users to interact with the operating system through commands. |
| Applications | Programs that perform tasks for users. |

### What Does the Linux Kernel Manage?

| Resource | Responsibility |
|----------|----------------|
| CPU | Schedules processes and allocates processing time. |
| Memory | Manages RAM allocation between programs. |
| Storage | Supports filesystem operations and access to storage devices. |
| Processes | Creates, schedules, and terminates running programs. |
| Permissions | Enforces access controls for users and processes. |

### Linux Kernel vs. Linux Distribution

Technically, **Linux refers to the kernel**, not the complete operating system.

A **Linux distribution (distro)** combines the Linux kernel with system utilities, a package manager, and other software to provide a usable operating system.

Popular Linux distributions include Ubuntu, Debian, Fedora, Arch Linux, and Kali Linux.

> **Example:** Ubuntu is a complete operating system built around the Linux kernel.

### Check Your Linux System

Run these commands in your Linux terminal:

```bash
uname -s              # Display the kernel name
uname -r              # Display the kernel release
uname -a              # Display detailed system information
cat /etc/os-release   # Identify your Linux distribution
```

### Why Learn Linux?

Linux is widely used in servers, cloud computing, cybersecurity, DevOps, software development, and Android devices. Learning Linux helps you understand how modern computing infrastructure works and how to manage systems through the command line.

---

## History of Linux

Linux was inspired by **Unix**, combined with tools from the **GNU Project**, and developed into one of the most widely used foundations for operating systems today.

### Linux Evolution

```text
Unix (1969) → GNU (1983) → Linux Kernel (1991) → Linux Distributions → Android & Cloud Computing
```

| Year | Milestone | Significance |
|------|-----------|--------------|
| **1969** | Unix developed at Bell Labs by Ken Thompson and Dennis Ritchie. | Introduced multi-user, multitasking, and hierarchical filesystem concepts. |
| **1983** | Richard Stallman announced the GNU Project. | Developed free software tools such as GCC, Bash, and core utilities. |
| **1991** | Linus Torvalds created the Linux kernel at the University of Helsinki. | Started Linux as a personal project that grew through community contributions. |
| **1993–1994** | Debian and Red Hat emerged. | Helped make Linux accessible through packaged operating systems called distributions. |
| **2004** | Ubuntu was released. | Introduced a Debian-based Linux distribution focused on usability. |
| **2005** | Google acquired Android Inc. | Helped bring the Linux kernel into mainstream mobile computing. |

### How GNU and Linux Work Together

The Linux kernel manages hardware and system resources, while GNU provides many essential tools needed to operate the system.

```text
Linux Kernel + GNU Tools + System Software
                  ↓
        Linux Distribution
                  ↓
       Ubuntu, Debian, Fedora
```

> **Note:** Linux is Unix-like, not Unix itself. It follows many Unix design principles but was independently developed.

### Why Linux Became Popular

- **Open Source:** Users can study, modify, and distribute the Linux kernel under its license.
- **Cost-Effective:** Most Linux distributions are available without operating system license fees.
- **Customizable:** Developers can modify and configure systems according to their needs.
- **Widely Adopted:** Linux powers servers, cloud infrastructure, supercomputers, Android devices, and embedded systems.

**Today, Linux is a fundamental technology for software development, cloud computing, DevOps, cybersecurity, and system administration.**

---


## Getting an Online Linux Server

### What is a VPS?

A **VPS (Virtual Private Server)** is a virtual machine hosted in the cloud that you can access remotely through the internet.

It allows you to practice Linux, deploy websites, run applications, and automate tasks without installing Linux on your personal computer.

### Step 1: Choose a VPS Provider

For this tutorial, we will use [Hostinger](https://www.hostinger.com/) as an example.

1. Visit Hostinger and select a suitable VPS hosting plan.
2. Choose **Ubuntu LTS (Long Term Support)** as your operating system.
3. Complete the purchase and configure your VPS.
4. Set a strong root password and store it securely.
5. Wait for the VPS installation to complete.

> **Note:** You can use any VPS provider that supports Linux. A small VPS is sufficient for practicing basic Linux commands.

### Step 2: Connect to Your VPS Using SSH

**SSH (Secure Shell)** allows you to securely access and manage a remote Linux server through your terminal.

Open PowerShell, Windows Terminal, or your macOS/Linux terminal and run:

```bash
ssh root@203.0.113.10
```

Replace \`203.0.113.10\` with your VPS's actual public IP address.

Other SSH connection methods:

```bash
# Connect using a specific port
ssh -p 22 root@203.0.113.10

# Connect using an SSH private key
ssh -i ~/.ssh/id_rsa root@203.0.113.10
```

On your first connection, SSH may ask you to verify the server's identity. Confirm that its fingerprint matches the one provided by your hosting provider before accepting it.

Enter your root password when prompted. Your password will not appear on the screen while typing.

> **Security Tip:** SSH key authentication is recommended for long-term server access. After initial setup, use a regular user with sudo privileges instead of working as root for everyday tasks.

### Step 3: Verify Your Linux Server

Once connected, run the following commands:

```bash
hostname             # Display the server's hostname
uname -a             # Display kernel and system information
cat /etc/os-release  # Identify your Linux distribution
whoami               # Display the currently logged-in user
```

If the commands return your server information, you have successfully connected to your Linux VPS.

> **Remember:** Commands executed through SSH run on your remote Linux server, not your personal computer. Your VPS continues running even after you close your terminal.

### Troubleshooting

If you cannot connect to your VPS, open your hosting provider's dashboard and verify the server status, IP address, SSH port, and login credentials.

Most VPS providers also offer a browser-based terminal for accessing your server when SSH is unavailable.

---

## Installing Linux Through VirtualBox on Windows

### What is Virtualization?

**Virtualization** allows you to run another operating system inside your existing computer without replacing Windows.

Using VirtualBox, you can create a **Virtual Machine (VM)** to run Ubuntu Linux independently.

- **Host OS:** Your original operating system (Windows).
- **Guest OS:** The operating system running inside VirtualBox (Ubuntu Linux).

### Step 1: Install VirtualBox

1. Visit the official [VirtualBox Downloads](https://www.virtualbox.org/wiki/Downloads) page.
2. Download VirtualBox for **Windows hosts**.
3. Run the installer and follow the installation instructions.
4. Complete the installation and launch VirtualBox.

### Step 2: Download Ubuntu

1. Visit the official [Ubuntu Desktop Download](https://ubuntu.com/download/desktop) page.
2. Select an Ubuntu **LTS (Long Term Support)** release.
3. Download the AMD64 (Intel/AMD 64-bit) ISO file.

> **Note:** The ISO file contains the Ubuntu operating system required to install Linux inside your virtual machine.

### Step 3: Create a Virtual Machine

1. Open VirtualBox and click **New**.
2. Enter a name for your VM, such as \`Ubuntu\`.
3. Select the downloaded Ubuntu ISO file.
4. Set your username and password.
5. Allocate the following resources according to your computer's available hardware:

| Resource | Recommended Allocation |
|----------|------------------------|
| RAM | 4 GB (or 50% of your Memory) |
| CPU | 2 Cores (or 50% of your CPU) |
| Storage | 35 GB minimum; allocate more if available |
| Operating System | Ubuntu LTS (64-bit) |

6. Complete the VM configuration and click **Finish**.
7. Start your virtual machine and complete the Ubuntu installation.

> **Important:** Do not allocate all your computer's RAM or CPU cores to the VM. Windows needs enough resources to continue running smoothly.

### Step 4: Open the Linux Terminal

Once Ubuntu starts, log in with your username and password.

Open the terminal using:

```text
Ctrl + Alt + T
```

Alternatively, search for **Terminal** in Ubuntu's Activities menu.

### Step 5: Verify Your Linux Installation

Run these commands inside the Ubuntu terminal:

```bash
uname -a             # Display kernel and system information
cat /etc/os-release  # Identify your Linux distribution
ls                   # List files and directories
ls -l                # Display detailed file information
ls -la               # Include hidden files and directories
```

> **Remember:** Windows Terminal runs commands on your Windows host, while the Ubuntu terminal runs commands inside your Linux virtual machine. Use the Ubuntu terminal throughout this handbook.

---

## Installing Linux on Windows Using WSL

### What is WSL?

**WSL (Windows Subsystem for Linux)** allows you to run Linux directly inside Windows without installing a separate operating system or creating a virtual machine using VirtualBox.

WSL is ideal for beginners who want to practice Linux commands, Bash scripting, and development through the terminal.

### Step 1: Install WSL

1. Open **Windows PowerShell as Administrator**.
2. Run the following command:

```powershell
wsl --install
```

This installs WSL along with the default Linux distribution, typically Ubuntu.

To view available Linux distributions:

```powershell
wsl --list --online
```

To install Ubuntu explicitly:

```powershell
wsl --install -d Ubuntu
```

> **Note:** You do not need to run both installation commands. Use \`wsl --install -d Ubuntu\` when you specifically want Ubuntu. Restart Windows if prompted.

### Step 2: Configure Ubuntu

1. Open **Ubuntu** from the Windows Start menu.
2. Wait for the initial installation to complete.
3. Create your Linux username and password.
4. Once configured, the Ubuntu terminal will be ready to use.

> **Important:** Your Linux username and password are separate from your Windows login credentials.

### Step 3: Verify Your Linux Installation

Run these commands inside the Ubuntu terminal:

```bash
uname -a             # Display kernel and system information
cat /etc/os-release  # Identify your Linux distribution
ls -la               # List files, including hidden files
```

### Useful WSL Commands

Run these commands in Windows PowerShell:

| Command | Purpose |
|---------|---------|
| `wsl --list --online` | List available Linux distributions. |
| `wsl --list --verbose` | Display installed distributions and their WSL versions. |
| `wsl -d Ubuntu` | Launch Ubuntu. |
| `wsl --shutdown` | Shut down all running WSL distributions. |

### Access Windows Files from Linux

Windows drives are accessible inside WSL through the `mnt` directory.

For example, to access your Windows C drive:

```bash
cd /mnt/c
ls
```

> **Remember:** WSL runs Linux locally on your Windows computer. It is not a cloud VPS or a publicly accessible Linux server by default.

---

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
