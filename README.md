# Linux Tutorial For Beginners

A complete beginner-friendly guide to Linux — covering installation, essential commands, users & permissions, package management, processes, environment variables, archiving, cron jobs, the filesystem, Nginx, and file transfer.

## Table of Contents
- [What is Linux?](#what-is-linux)
- [History of Linux](#history-of-linux)
- [Getting an Online Linux Server](#getting-an-online-linux-server)
- [Installing Linux through VirtualBox on Windows](#installing-linux-through-virtualbox-on-windows)
- [Installing Linux on Windows using WSL](#installing-linux-on-windows-using-wsl)
- [Installing Linux through VirtualBox on Mac](#installing-linux-through-virtualbox-on-mac)
- [Basic Linux Commands](#basic-linux-commands)
- [Creating Users](#creating-users)
- [Package Management](#package-management)
- [Groups & Permissions](#groups--permissions)
- [Processes & Services](#processes--services)
- [Environment Variables, PATH and Bashrc](#environment-variables-path-and-bashrc)
- [Archives and Compression](#archives-and-compression)
- [Cronjobs](#cronjobs)
- [Understanding the Linux Filesystem](#understanding-the-linux-filesystem)
- [Understanding Nginx](#understanding-nginx)
- [Using FileZilla to Transfer Files](#using-filezilla-to-transfer-files)
- [Conclusion](#conclusion)

---

## What is Linux?

Linux is an open-source operating system kernel that lets you communicate directly with the hardware.

Open source means software whose source code is publicly available to use, study, modify, and share.

## History of Linux

Linux originated from Unix, which was created by Ken Thompson and Dennis Ritchie in 1969.

## Getting an Online Linux Server

You can get one via a VPS (Virtual Private Server) by taking hosting from Hostinger.

Choose the **KVM 2** plan and select **Ubuntu** with an **LTS** version.

## Installing Linux through VirtualBox on Windows

1. Go to [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) and click on **Windows host**.
2. Install it with the default settings, clicking **Yes** on all options without changing anything.
3. To create a new VM, download Ubuntu from the official site.
4. Download the **Intel or AMD 64-bit** architecture ISO from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop) — make sure it's an **LTS** version of Ubuntu.
5. After downloading the ISO, click **New** in VirtualBox and add the ISO file under **ISO Image**.
6. Name the VM (e.g., "ubuntu" or whatever you prefer).
7. Click **Next**.
8. Enter your username and password, then click **Next**.
9. Assign at least **4GB RAM**, **2 CPU cores** (50% of your CPU), and **35GB storage** to the VM.
10. The terminal lets you work by issuing commands.

## Installing Linux on Windows using WSL

1. Open PowerShell as **Administrator**.
2. Run:
   ```
   wsl --install
   ```
3. List available distributions:
   ```
   wsl --list --online
   ```
4. Install Ubuntu.

> *(Detailed step-by-step instructions to be added.)*

## Installing Linux through VirtualBox on Mac

> *(Step-by-step guide to be added.)*

## Basic Linux Commands

- `pwd` — present working directory
- `cd` — change directory
  - `cd ../` moves one step back
- `ls` — display listings
- Press **Tab** to autocomplete a folder name.
- `mkdir [folder-name]` — create a directory
- `mkdir -p folder1/folder2/folder3` — create nested directories
- `touch [filename]` — create an empty file
- `vim [filename]` — edit a file
  - If you see an error like `Command 'vim' not found`, run: `sudo apt install vim`
  - Open the file again with `vim [filename]`, press `i` to enter insert mode, type your content, then press `Esc`, type `:wq`, and press Enter to save and exit.
  - To exit without saving, use `:q!` instead of `:wq`.
- `cp [filename1] [destination-path/filename2]` — copy the content of filename1 to filename2
- `cat [filename]` — display the content of a file in the terminal
- `cat -n [filename]` — display the content of a file with line numbers
- `less [filename]` — display the content of a file in the terminal (press `q` to exit)
  - `cat` is useful for small files; `less` is useful for large files.
- `clear` — clear the terminal screen
- `history` — view command history
  - You can also use the **Up/Down arrow keys** to browse command history — useful for retyping long commands.
- `cd ~` — go back to the user's home directory
- `cd /` — go to the root of the machine
- `cd .` — current directory
- `cd ../[DirectoryName]` — parent directory

## Creating Users

- `whoami` — check who you are: the main user (root) or a sub-user.
  - The root user can create multiple users.
- `sudo adduser [username]` — create a sub-user in Ubuntu.
  - `sudo` means run this command with full privileges.
- `su - [username]` — log in as that user.
  - Note: this user cannot do everything the main user can. For example, it cannot run `sudo apt update`.
- `exit` — go back to the root user.
- `sudo usermod -aG sudo [username]` — grant a user sudo privileges (i.e., full privileges).

## Package Management

Advanced Package Tool (APT) is a free software tool for installing and removing software on Debian-based Linux distributions.

Ubuntu is Debian-based, and Debian is one of the most popular Linux-based operating systems.

- `sudo apt update` — update Ubuntu's package listing. All available software and package versions are refreshed.
- `sudo apt install apache2` — install Apache2, used to host HTML files on your machine.
- `sudo apt upgrade` — upgrade all software on your machine.
- `sudo apt remove apache2` — remove Apache2 from your machine.
- `sudo apt install nginx` — install Nginx on your machine.
- `sudo apt show nginx` — show information about Nginx; useful for debugging if the package crashes or an error occurs.
- `sudo apt install curl git python3` — install curl, git, and python3 at the same time. You can install multiple packages in a single command.
- `sudo apt purge apache2` — remove software along with all its configuration files; used to completely remove software from your machine.
- `apt list --installed` — display all installed packages with their version numbers.
- `sudo apt-get update` — used on older Ubuntu machines; now shortened to `sudo apt update`.

## Groups & Permissions

- `sudo groupadd [groupname]` — create a group of users.
- `sudo useradd -m [username]` — create a user inside a group. The `-m` flag creates a home directory for the user.
- `sudo passwd [username]` — set the password for the user.
- `sudo usermod -aG [groupname] [username]` — add a user to a group.
  - `-aG` means append the user to this group.
- `groups [username]` — see which groups a user belongs to.
  - Output format: `[username] : [primary group (name of user)] [supplementary group]`
- `ls -l` — list the owner, group, and permissions of files/directories.
  - Example output: `drwxr-x---`. `d` means directory, and `rwxr-x---` represents permissions, split into three parts:
    - `rwx` — owner can read, write, and execute.
    - `r-x` — group can read and execute only.
    - `---` — others can do nothing.
- `sudo chown [username] [directoryname]` — change the owner of the directory.
- `sudo chgrp [groupname] [directoryname]` — change the group of the directory.
- `chmod g+w [directoryname]` — grant the group write permission on the folder.
  - `u+w` — grant write permission to the owner.
  - `g+w` — grant write permission to the group.
  - `o+w` — grant write permission to others.
  - `a+w` — grant write permission to everyone.
  - `a-w` — remove write permission from everyone.
  - `u-w` — remove write permission from the owner.
- `chmod [number] [directoryname]` — assign permissions to a directory using octal numbers.
  - You can calculate the number using the octal system or an online "chmod calculator."
  - `read = 4`, `write = 2`, `execute = 1`.

## Processes & Services

A process is a running program. Every process has an ID called a PID.

- `ps` — check running processes.
- `ps aux` — view all processes run by all users.
- `ps aux | grep nginx` — view all processes containing "nginx."
- `top` — view all running processes in real time, sorted by resource usage.
  - Press `q` to exit.
- `htop` — a fancier, more graphical version of `top`.
  - Press `F6` to sort by any column. Press `F10` or `q` to quit.
  - If `htop` isn't found, install it with `sudo apt install htop`.
- `kill [PID]` — kill the process with the specified PID.
- `kill -9 [PID]` — forcefully kill the process with the specified PID. Use this if `kill [PID]` doesn't work.
- `pkill [package-name]` — kill all processes matching a specific package name (e.g., git, python).

A service is a program that runs automatically in the background.

- `systemctl status nginx` — check the status of the Nginx service.
- `systemctl stop nginx` — stop the Nginx service.
- `systemctl start nginx` — start the Nginx service.
- `systemctl restart nginx` — restart the Nginx service. Recommended after making configuration changes.
- `sudo systemctl restart nginx` — the safer approach to restart the Nginx service.
- `sudo systemctl reload nginx` — reload the configuration without bringing the server down.
- `sudo systemctl enable nginx` — automatically start the service on boot/login.
- `sudo systemctl disable nginx` — automatically disable the service on boot/login.

## Environment Variables, PATH and Bashrc

- `echo $HOME` — print the value of the `HOME` environment variable (referenced with `$`).
- `printenv` or `env` — display all environment variables in the terminal.

One of the most important variables is `PATH`.

- To access any environment variable: `echo $[variable-name]`
- You can also create your own shell variable:
  ```
  name="Zeeshan"
  echo $name
  ```
- `export [variable-name]="[value]"` — turn a shell variable into an environment variable, e.g.:
  ```
  export friend="value"
  echo $friend
  ```
- Environment variables are used to configure applications.
- `echo $PATH` — display the value of `PATH`: a colon-separated list of directories containing binaries that can be run without specifying their full path.
- `ls` — displays its result.
- `which ls` — displays the path from which the `ls` command is being executed.
- `vim zeeshan.sh` — create a bash file named "zeeshan."
  - Bash is a shell that executes commands line by line, also known as "bash scripting."
  - Bash scripting includes constructs like `IF`, `ELSE`, and `FOR` loops, similar to a programming language.
- `chmod +x [bash-file-name]` — make a bash file executable.
- `./[bash-file-name]` — execute a bash file.
- `mv [file-name] [filepath]` — move a file to the given path.
  - If `mv` doesn't work, try `sudo mv [file-name] [filepath]`.
- `export PATH="$PATH:[filepath]"` — append a filepath to the end of the `PATH` variable, keeping all previous paths intact.
  - Now you can run `[filename].sh` directly, without `./` at the start.
  - This change won't persist after logging out and back in — add it to your `.bashrc` file to make it permanent.
- `vim .bashrc` — create/edit the `.bashrc` file.
- `source .bashrc` — reload the `.bashrc` file.

## Archives and Compression

- **Archiving** means combining multiple files into a single container file, similar to creating a zip file.
- **Compression** means reducing file size.

Commands:
- `tar -cf [tar-name] [folder-name]` — create a tar file from the given folder.
- `rm -rf [folder-name]` — remove an entire folder, its subfolders, and contents.
  - `rm -rf` can permanently delete files and directories — use it carefully.
- `tar -tf [tar-name]` — preview the contents of a tar file.
- `tar -xf [tar-name]` — extract a tar file.
- `tar -xvf [tar-name]` — extract a tar file while showing each file as it's extracted.
- `gzip [tar-name]` — compress a tar file.
- `gunzip [tar-name].gz` — decompress a tar file.

> If these commands aren't preinstalled, run: `sudo apt install gzip gunzip tar zip unzip`

- The `zip` command can both archive and compress in the Linux terminal, and is also usable on Windows and Mac.
- `zip -r [name.zip] [folder-name]` — zip a folder.
- `unzip [filename]` — unzip a zip file.

## Cronjobs

Cron is a background service that runs tasks on a scheduled interval. A specific scheduled task is called a cronjob.

- `crontab -l` — check if a task is scheduled.
- `sudo systemctl status cron` — check if the cron service is running.
- `sudo systemctl start cron` — start the cron service if it isn't running.
- `sudo systemctl restart cron` — restart the cron service.
- `sudo systemctl stop cron` — stop the cron service (not recommended).
- `crontab -e` — schedule a new task.

A crontab has five fields:

| Field | Range |
|---|---|
| Minute | 0–59 |
| Hour | 0–23 |
| Day of Month | 1–31 |
| Month | 1–12 |
| Day of Week | 0–6 (0 = Sunday) |

[crontab.guru](https://crontab.guru) is a great website for learning and practicing cron schedules.

## Understanding the Linux Filesystem

- `/` — the root of your Linux machine; the outermost directory you can't go back beyond. (It also contains the root user's own home folder.)
- `home` — the directory containing all user home folders. Use `cd ~` to go to your home directory.
- `etc` — contains configuration files. Use `tail /etc/hosts` to check IP mappings.
- `var` — contains variable files that change frequently.
- `usr` — stands for "Unix System Resources"; contains a large number of software packages, commands, and libraries.
- `tmp` — contains temporary files.

## Understanding Nginx

Nginx is used to host multiple sites on the same server.

- `sudo apt update` — update your package directory.
- `sudo apt install nginx` — install Nginx on your machine.
- `cd /var/www` — navigate to where your website's code is stored.
- `sudo ufw status` — check the status of the firewall.
  - UFW (Uncomplicated Firewall) is a user-friendly tool for managing firewall rules in Linux.
- `sudo vim [filename]` — make changes to a file inside the HTML folder.

Read the Nginx docs to dive deeper — it's quite time-consuming to learn all of Nginx.

## Using FileZilla to Transfer Files

FileZilla is a free tool used to transfer files between a server and a client (e.g., Windows to Linux or Linux to Windows).

> *(Step-by-step configuration guide to be added.)*

## Conclusion

You should learn at least the basics of Linux in 2026 — whether you're aiming to become an AI Engineer, ML Engineer, Web Developer, DevOps Engineer, or any other tech role.
