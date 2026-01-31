

## What happens when you start a computer?

When you start a computer, the first thing that executes is the firmware stored in ROM on the motherboard. Modern computers typically use one of two types:

- **BIOS (Basic Input Output System)**: The traditional firmware used in older computers
- **UEFI (Unified Extensible Firmware Interface)**: The modern replacement for BIOS, faster and more feature-rich

The firmware performs a Power-On Self Test (POST) to check hardware, then loads the **bootloader**, which is responsible for initializing the Operating System.

---

## What is a Bootloader?

A bootloader is a program that initializes and loads the Operating System into memory. Common bootloaders include GRUB (Linux) and Windows Boot Manager.

---

## What is an OS (Operating System)?

An operating system is system software that manages computer hardware, software resources, and provides common services for computer programs.

### An operating system should have:

- **Kernel**: Core component that manages system resources
- **File System**: Organizes and stores data
- **User Interface**: GUI (Graphical) and/or CLI (Command Line)
- **Ability to manipulate data**: Process commands and manage applications

---

## What is a File System?

A file system is the method or data structure that the OS uses to store and retrieve data on storage devices. Examples include ext4 (Linux), NTFS (Windows), and APFS (macOS).

---

## What is a Kernel?

The kernel is the core component of an operating system that serves as the main interface between the computer's physical hardware and the processes running on it. It acts as a bridge between software and hardware, managing:

- Memory allocation
- Process scheduling
- Device drivers
- System calls

---

## Most Popular Operating Systems

- **Microsoft Windows**: Most common desktop OS
- **macOS**: Apple's desktop OS (only on Apple hardware)
- **Linux**: Open-source, UNIX-based OS with many distributions
- **Android**: Mobile OS based on Linux
- **iOS**: Apple's mobile OS for iPhone and iPad

---

## Why Use Linux?

- **Open Source**: Free to use, modify, and distribute
- **Developer Friendly**: Supports almost all programming languages
- **Superior Terminal**: More powerful than Windows CMD
- **Bash Scripting**: Automate tasks with shell scripts
- **SSH (Secure Shell)**: Secure remote access to systems
- **Customizable**: Tailor the OS to your needs
- **Stable and Secure**: Less prone to viruses and malware

---

## History of Linux

- **1969**: First UNIX OS created by Ken Thompson and Dennis Ritchie at Bell Labs
- **1983**: Richard Stallman started the GNU Project to create a free UNIX-like operating system
- **1991**: Linus Torvalds created the Linux kernel, which became the foundation for all Linux distributions

> **Note**: Linus Torvalds is considered the father of Linux

---

## Popular Linux Distributions

- **Ubuntu**: Beginner-friendly, large community support
- **Fedora**: Cutting-edge features, sponsored by Red Hat
- **Debian**: Very stable, basis for Ubuntu
- **Arch Linux**: Rolling release, highly customizable
- **Kali Linux**: Security and penetration testing
- **Linux Mint**: User-friendly, Windows-like interface
- **Pop!_OS**: Great for developers and gamers

### Why Ubuntu for beginners?

- Beginner-friendly with extensive documentation
- Decent user interface
- Large community for support
- Easy to use for non-programmers
- Good hardware compatibility

---

## What is a Terminal?

A terminal is a text-based interface where you can type commands to interact with the operating system.

**Opening Terminal in Ubuntu**:

- `Ctrl + Alt + T`
- Or press the Super key (Windows key) and type "terminal"

---

## What is a Shell?

A shell is a command-line interpreter that executes commands line by line, similar to how Python interprets code. The shell reads your commands and tells the operating system what to do.

---

## What is BASH?

BASH (Bourne Again Shell) is the most common shell in Linux. Every command you write in the terminal is part of the BASH language. BASH also supports scripting for automation.

---

## Understanding the Shell Prompt

```
sumit@archlinux:~$
```

Let's break down what this means:

- `sumit`: Your username
- `@archlinux: The hostname (computer name)
- `~`: Current directory (tilde represents your home directory)
- `$`: Prompt symbol (indicates regular user; `#` indicates root user)

---

## Understanding Users and Permissions

- **Regular User ($)**: Limited permissions, safer for daily use
- **Root User (#)**: Administrator with full system access
- Use `sudo` before commands to execute them with root privileges

---

## Paths in Linux

### Types of Paths:

- **Absolute Path**: Starts from root directory `/`
    - Example: `/home/sumit/Documents`
- **Relative Path**: Starts from current directory
    - Example: `Documents/myfile.txt`

### Special Path Symbols:

- `~`: Home directory (`/home/username`)
- `/`: Root directory (top of file system)
- `.`: Current directory
- `..`: Parent directory
- `-`: Previous directory

---

## Linux File Hierarchy Structure

The Filesystem Hierarchy Standard (FHS) defines the directory structure in Linux:

- `/`: Root directory (top of the hierarchy)
- `/home`: User home directories
- `/root`: Root user's home directory
- `/bin`: Essential user command binaries
- `/etc`: System configuration files
- `/var`: Variable data (logs, temporary files)
- `/tmp`: Temporary files
- `/usr`: User programs and data
- `/opt`: Optional software packages

For more details, visit: [GeeksforGeeks Linux File Hierarchy](https://www.geeksforgeeks.org/linux-file-hierarchy-structure/)

---

## Basic Linux Commands

### Printing Text

```bash
echo "Hello World"
```

Output: `Hello World`

### Navigation Commands

|Command|Description|Example|
|---|---|---|
|`pwd`|Print working directory (shows current location)|`pwd`|
|`cd <directory>`|Change directory|`cd Documents`|
|`cd ~`|Go to home directory|`cd ~`|
|`cd /`|Go to root directory|`cd /`|
|`cd ..`|Go to parent directory|`cd ..`|
|`cd -`|Go to previous directory|`cd -`|

### Listing Files and Directories

|Command|Description|
|---|---|
|`ls`|List files in current directory|
|`ls -l`|List with detailed information|
|`ls -a`|List all files (including hidden)|
|`ls -la`|List all files with details|
|`ls -lh`|List with human-readable file sizes|

### File Operations

|Command|Description|Example|
|---|---|---|
|`touch <filename>`|Create an empty file|`touch myfile.txt`|
|`cat <filename>`|Display file contents|`cat myfile.txt`|
|`cp <source> <destination>`|Copy file or directory|`cp file.txt backup.txt`|
|`cp -r <source> <destination>`|Copy directory recursively|`cp -r folder1 folder2`|
|`mv <source> <destination>`|Move or rename file/directory|`mv old.txt new.txt`|
|`rm <filename>`|Remove file|`rm myfile.txt`|
|`rm -r <directory>`|Remove directory and contents|`rm -r myfolder`|
|`rm -rf <directory>`|Force remove (use carefully!)|`rm -rf myfolder`|

### Directory Operations

|Command|Description|Example|
|---|---|---|
|`mkdir <dirname>`|Create directory|`mkdir myfolder`|
|`mkdir -p <path>`|Create nested directories|`mkdir -p folder1/folder2/folder3`|
|`rmdir <dirname>`|Remove empty directory|`rmdir myfolder`|

### File Viewing and Editing

|Command|Description|Example|
|---|---|---|
|`cat <file>`|Display entire file|`cat file.txt`|
|`less <file>`|View file page by page|`less file.txt`|
|`head <file>`|Show first 10 lines|`head file.txt`|
|`tail <file>`|Show last 10 lines|`tail file.txt`|
|`nano <file>`|Open text editor (beginner-friendly)|`nano file.txt`|
|`gedit <file>`|Open graphical text editor|`gedit file.txt`|

### System Information

|Command|Description|
|---|---|
|`clear`|Clear the terminal screen|
|`history`|Show previously executed commands|
|`whatis <command>`|Short description of a command|
|`man <command>`|Manual page for a command (detailed help)|
|`whoami`|Display current username|
|`date`|Show current date and time|

---

## File Permissions in Linux

Every file has permissions for three groups:

- **Owner (u)**: The user who owns the file
- **Group (g)**: Users in the file's group
- **Others (o)**: Everyone else

### Permission Types:

- **r (read)**: Can read the file
- **w (write)**: Can modify the file
- **x (execute)**: Can run the file as a program

Example: `ls -l` output

```
-rw-r--r-- 1 sumit sumit 1024 Jan 15 10:30 myfile.txt
```

- First `-`: File type (- for file, d for directory)
- `rw-`: Owner can read and write
- `r--`: Group can only read
- `r--`: Others can only read

---

## Common Mistakes and Tips

### Common Mistakes:

1. **Case Sensitivity**: Linux is case-sensitive. `File.txt` and `file.txt` are different files
2. **Spaces in Names**: Use quotes or escape spaces: `cd "My Folder"` or `cd My\ Folder`
3. **Using `rm -rf` carelessly**: This can delete everything irreversibly
4. **Forgetting `sudo`**: Some commands need administrator privileges
5. **Not reading error messages**: Error messages usually tell you what's wrong

### Useful Tips:

- **Tab Completion**: Press Tab to auto-complete file/directory names
- **Command History**: Use ↑ and ↓ arrow keys to browse previous commands
- **Ctrl + C**: Cancel a running command
- **Ctrl + L**: Clear screen (alternative to `clear`)
- **Ctrl + A**: Move cursor to beginning of line
- **Ctrl + E**: Move cursor to end of line
- **Ctrl + R**: Search command history


---

