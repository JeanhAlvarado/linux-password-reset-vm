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
- Add this at the end:

![Screenshot 2025-05-17 195243](https://github.com/user-attachments/assets/ea79f92f-b69d-4bb4-a5dc-656dacbb3a5c)

### 3. Enter Root Shell
Press **Ctrl + X** or **F10** to boot into a root shell.

### 4. Remount File System as Read/Write
```bash
mount -o remount,rw /
```
### 5. Find Username and Reset Password
If you forgot your username:

 ls /home
# or
 cat /etc/passwd | grep '/home'

### 6. Reset Password
 passwd yourusername

### 7. Reboot
 exec /sbin/init
 or
 reboot -f


Outcome

I successfully reset the password and regained access to my Linux virtual machine without reinstalling anything.
