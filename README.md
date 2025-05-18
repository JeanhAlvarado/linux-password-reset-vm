# linux-password-reset-vm
How I reset my forgotten username/password on a Linux VM using GRUB
# 🔐 Linux Password Reset in a VirtualBox VM

## 📘 Overview

This project documents how I reset a forgotten **Linux username and password** on a virtual machine using **GRUB and bash**. This is part of my hands-on learning in Linux system administration and cybersecurity.

## 🧰 Tools Used

- VirtualBox
- Ubuntu/Kali Linux
- GRUB bootloader
- Terminal / Command Line

---

## 🛠️ Step-by-Step Process

### 1. Boot into GRUB
Restart the Linux VM and hold `Shift` (if needed) to show the GRUB bootloader menu.

![Screenshot 2025-05-17 195133](https://github.com/user-attachments/assets/55d2e7b8-b22f-4174-b4b3-b2143e4e3688)

### 2. Edit Boot Entry
- Highlight the default entry
- Press `e` to edit
- Find the line that starts with `linux /boot/vmlinuz...`
- Add this at the end: init=/bin/bash

![Screenshot 2025-05-17 195243](https://github.com/user-attachments/assets/ea79f92f-b69d-4bb4-a5dc-656dacbb3a5c)

### 3. Enter Root Shell
Press **Ctrl + X** or **F10** to boot into a root shell.

![Screenshot 2025-05-17 203110](https://github.com/user-attachments/assets/ea27245c-f420-4f44-9f62-54e7a7b2a2d1)


### 4. Remount File System as Read/Write
```bash
mount -o remount,rw /
```
### 5. Find Username and Reset Password
If you forgot your username:

 ls /home

![Screenshot 2025-05-17 203231](https://github.com/user-attachments/assets/e8032df6-d3e5-43c6-aee9-2ef305f5401c)

 # or If you're unsure, you can also list all users with:
 cat /etc/passwd | grep '/home'

<img width="334" alt="image" src="https://github.com/user-attachments/assets/528a36c0-f72a-4034-9103-ff674af76475" />

### 6. Reset Password
Type: passwd 

<img width="294" alt="image" src="https://github.com/user-attachments/assets/a83b8501-62f5-4678-899a-5d313c741e45" />

### 7. Reboot
Type: exec /sbin/init
 or
 reboot -f

<img width="626" alt="image" src="https://github.com/user-attachments/assets/821781d4-dba2-40f2-b65a-5595ac5e588d" />



Outcome

I successfully reset the password and regained access to my Linux virtual machine without reinstalling anything.
