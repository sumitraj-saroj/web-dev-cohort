# Linux Commands Cheatsheet

## Navigation Commands

```bash
pwd                          # Print working directory
cd <directory>               # Change directory
cd                           # Go to home directory
cd ~                         # Go to home directory
cd /                         # Go to root directory
cd ..                        # Go up one directory
cd -                         # Go to previous directory
```

## File and Directory Listing

```bash
ls                           # List directory contents
ls -l                        # Long format listing
ls -a                        # Show hidden files
ls -la                       # Long format with hidden files
ls -lh                       # Long format with human-readable sizes
ls -R                        # Recursive listing
ls -t                        # Sort by modification time
ls -S                        # Sort by file size
```

## Creating Files and Directories

```bash
touch <filename>             # Create empty file
mkdir <dirname>              # Create directory
mkdir -p <path>              # Create nested directories
```

## Copying and Moving

```bash
cp <source> <dest>           # Copy file
cp -r <source> <dest>        # Copy directory recursively
cp -i <source> <dest>        # Interactive copy (prompt before overwrite)
mv <old> <new>               # Move or rename file/directory
mv <source> <directory>      # Move file to directory
```

## Deleting Files and Directories

```bash
rm <filename>                # Delete file
rm -i <filename>             # Interactive delete
rm -r <dirname>              # Delete directory and contents
rm -rf <dirname>             # Force delete directory
rmdir <dirname>              # Delete empty directory
```

## File Viewing and Editing

```bash
cat <file>                   # Display file contents
cat <file1> <file2>          # Concatenate and display multiple files
less <file>                  # View file with pagination
more <file>                  # View file page by page
head <file>                  # Show first 10 lines
head -n 20 <file>            # Show first N lines
tail <file>                  # Show last 10 lines
tail -n 20 <file>            # Show last N lines
tail -f <file>               # Follow file updates (for logs)
```

## System Information

```bash
uname -a                     # Show system and kernel information
cat /etc/os-release          # Show OS release information
lscpu                        # Display CPU information
lsmem                        # Display memory information
free -h                      # Show memory usage
df -h                        # Show disk space usage
du -sh <directory>           # Show directory size
hostname                     # Show system hostname
uptime                       # Show system uptime
whoami                       # Show current username
date                         # Show current date and time
```

## Process Management

```bash
ps                           # Show running processes
ps aux                       # Show all running processes
top                          # Real-time process monitoring
htop                         # Interactive process viewer
kill <PID>                   # Terminate process by PID
kill -9 <PID>                # Force kill process
killall <name>               # Kill all processes by name
bg                           # Send process to background
fg                           # Bring process to foreground
jobs                         # List background jobs
```

## Search and Find

```bash
grep <pattern> <file>        # Search for pattern in file
grep -r <pattern> <dir>      # Recursive search in directory
grep -i <pattern> <file>     # Case-insensitive search
grep -n <pattern> <file>     # Show line numbers
find <dir> -name <pattern>   # Find files by name
find <dir> -type d           # Find directories only
find <dir> -type f           # Find files only
locate <filename>            # Quick file search
which <command>              # Find location of command
```

## Piping and Redirection

```bash
command1 | command2          # Pipe output to another command
command > file               # Redirect output to file (overwrite)
command >> file              # Redirect output to file (append)
command < file               # Redirect input from file
command 2> file              # Redirect error output
command &> file              # Redirect both output and error
command1 ; command2          # Run commands sequentially
command1 && command2         # Run next if previous succeeds
command1 || command2         # Run next if previous fails
```

## Utility Commands

```bash
clear                        # Clear terminal screen
history                      # Show command history
history | grep <term>        # Search command history
!!                           # Repeat last command
!<number>                    # Run command from history by number
echo <text>                  # Print text to terminal
wc -l <file>                 # Count lines in file
sort <file>                  # Sort file contents
uniq <file>                  # Remove duplicate lines
diff <file1> <file2>         # Compare files
tar -czf <archive.tar.gz> <dir>    # Create compressed archive
tar -xzf <archive.tar.gz>    # Extract compressed archive
zip -r <archive.zip> <dir>   # Create zip archive
unzip <archive.zip>          # Extract zip archive
wget <url>                   # Download file from URL
curl <url>                   # Transfer data from URL
```

## Network Commands

```bash
ping <host>                  # Test network connectivity
ifconfig                     # Show network interfaces
ip addr                      # Show IP addresses
netstat -tuln                # Show listening ports
ss -tuln                     # Show socket statistics
ssh <user>@<host>            # Connect via SSH
scp <source> <user>@<host>:<dest>    # Secure copy to remote host
```

## Package Management (APT)

```bash
apt update                   # Update package list
apt upgrade                  # Upgrade all installed packages
apt full-upgrade             # Upgrade packages and remove/install dependencies
apt search <package>         # Search for a package
apt show <package>           # Show package details
apt install <package>        # Install a package
apt install <pkg1> <pkg2>    # Install multiple packages
apt remove <package>         # Remove package
apt purge <package>          # Remove package and config files
apt autoremove               # Remove unnecessary dependencies
apt list --installed         # List all installed packages
apt list --upgradable        # List upgradable packages
```

## VIM Commands

### Basic Operations
```bash
vim <file>                   # Open file in VIM
i                            # Enter insert mode (before cursor)
a                            # Enter insert mode (after cursor)
A                            # Jump to end of line and enter insert mode
o                            # Open new line below and enter insert mode
O                            # Open new line above and enter insert mode
Esc                          # Return to normal mode
```

### Navigation
```bash
h                            # Move left
j                            # Move down
k                            # Move up
l                            # Move right
w                            # Move to next word
b                            # Move to previous word
0                            # Jump to beginning of line
$                            # Jump to end of line
gg                           # Jump to first line of file
G                            # Jump to last line of file
12G                          # Jump to line 12
:12                          # Jump to line 12
Ctrl+f                       # Page down
Ctrl+b                       # Page up
```

### Editing
```bash
x                            # Delete character under cursor
dd                           # Delete entire line
10dd                         # Delete next 10 lines
d10d                         # Delete next 10 lines
dw                           # Delete word
d$                           # Delete to end of line
yy                           # Yank (copy) line
p                            # Paste after cursor
P                            # Paste before cursor
u                            # Undo last change
Ctrl+r                       # Redo
.                            # Repeat last command
```

### Search and Replace
```bash
/pattern                     # Search forward for pattern
?pattern                     # Search backward for pattern
n                            # Jump to next match
N                            # Jump to previous match
:%s/old/new                  # Replace first occurrence in each line
:%s/old/new/g                # Replace all occurrences in file
:%s/old/new/gc               # Replace all with confirmation
:s/old/new/g                 # Replace all in current line
```

### Saving and Quitting
```bash
:w                           # Save file
:w <filename>                # Save as new filename
:q                           # Quit
:q!                          # Quit without saving
:wq                          # Save and quit
:x                           # Save and quit
ZZ                           # Save and quit (shortcut)
ZQ                           # Quit without saving (shortcut)
```

### Other VIM Commands
```bash
:set number                  # Show line numbers
:set nonumber                # Hide line numbers
:syntax on                   # Enable syntax highlighting
:help                        # Open help documentation
v                            # Enter visual mode (character selection)
V                            # Enter visual line mode
Ctrl+v                       # Enter visual block mode
```

## Other Text Editors

```bash
nano <file>                  # Open file in nano
emacs <file>                 # Open file in emacs
gedit <file>                 # Open file in gedit (GUI)
kate <file>                  # Open file in kate (GUI)
```

## User Management

```bash
adduser <username>           # Create new user (interactive)
useradd <username>           # Create new user (non-interactive)
useradd -m -s /bin/bash <user>    # Create user with home directory and shell
passwd <username>            # Set or change user password
deluser <username>           # Delete user
userdel <username>           # Delete user
userdel -r <username>        # Delete user and home directory
su - <username>              # Switch to another user
su -                         # Switch to root user
sudo -i                      # Open root shell
sudo <command>               # Execute command with superuser privileges
whoami                       # Show current username
id <username>                # Show user ID and group IDs
users                        # Show currently logged-in users
w                            # Show who is logged in
exit                         # Logout current user
```

## Group Management

```bash
groupadd <groupname>         # Create new group
groupdel <groupname>         # Delete group
groups <username>            # List user's groups
groups                       # List current user's groups
```

## Modifying Users and Groups

```bash
usermod -g <group> <user>    # Change user's primary group
usermod -G <group> <user>    # Set user's secondary groups (overwrites)
usermod -aG <group> <user>   # Add user to group (append)
usermod -l <newname> <oldname>    # Rename usps aux | grep pacman
er
usermod -d <dir> <user>      # Change home directory
usermod -s <shell> <user>    # Change login shell
usermod -L <user>            # Lock user account
usermod -U <user>            # Unlock user account
gpasswd -d <user> <group>    # Remove user from group
gpasswd -a <user> <group>    # Add user to group
```

## File Ownership

```bash
chown <user> <file>          # Change file owner
chown <user>:<group> <file>  # Change owner and group
chown -R <user> <dir>        # Change owner recursively
chgrp <group> <file>         # Change file group
chgrp -R <group> <dir>       # Change group recursively
```

## File Permissions (Symbolic Mode)

```bash
chmod u+x <file>             # Add execute permission for owner
chmod g+w <file>             # Add write permission for group
chmod o+r <file>             # Add read permission for others
chmod u-x <file>             # Remove execute permission for owner
chmod g-w <file>             # Remove write permission for group
chmod o-r <file>             # Remove read permission for others
chmod a+x <file>             # Add execute permission for all
chmod -x <file>              # Remove execute permission for all
chmod g=rwx <file>           # Set exact permissions for group
chmod u+x,g-w <file>         # Multiple changes at once
chmod -R u+w <dir>           # Recursive permission change
```

## File Permissions (Numeric Mode)

```bash
chmod 755 <file>             # rwxr-xr-x (Owner: all, Group/Others: read+execute)
chmod 644 <file>             # rw-r--r-- (Owner: read+write, Others: read only)
chmod 777 <file>             # rwxrwxrwx (All permissions for everyone)
chmod 700 <file>             # rwx------ (Owner: all, Others: none)
chmod 600 <file>             # rw------- (Owner: read+write, Others: none)
chmod 666 <file>             # rw-rw-rw- (Everyone: read+write)
chmod 4755 <file>            # rwsr-xr-x (setuid)
chmod 2755 <dir>             # rwxr-sr-x (setgid)
chmod 1777 <dir>             # rwxrwxrwt (sticky bit)
```

## Viewing Permissions

```bash
ls -l <file>                 # View file permissions
ls -ld <directory>           # View directory permissions
stat <file>                  # Detailed file information
getfacl <file>               # View Access Control Lists
```

## Compression and Archives

```bash
tar -cf archive.tar <files>  # Create tar archive
tar -czf archive.tar.gz <files>    # Create compressed tar.gz archive
tar -xf archive.tar          # Extract tar archive
tar -xzf archive.tar.gz      # Extract tar.gz archive
tar -tf archive.tar          # List contents of tar archive
gzip <file>                  # Compress file with gzip
gunzip <file.gz>             # Decompress gzip file
bzip2 <file>                 # Compress file with bzip2
bunzip2 <file.bz2>           # Decompress bzip2 file
zip <archive.zip> <files>    # Create zip archive
zip -r <archive.zip> <dir>   # Create zip archive recursively
unzip <archive.zip>          # Extract zip archive
unzip -l <archive.zip>       # List contents of zip archive
```

## Disk Management

```bash
df -h                        # Show disk space usage
du -h <directory>            # Show directory size
du -sh <directory>           # Show total directory size
du -ah <directory>           # Show all files and directories with sizes
fdisk -l                     # List disk partitions
mount <device> <mountpoint>  # Mount a device
umount <mountpoint>          # Unmount a device
lsblk                        # List block devices
```

## System Control

```bash
shutdown -h now              # Shutdown immediately
shutdown -r now              # Reboot immediately
reboot                       # Reboot system
poweroff                     # Power off system
halt                         # Halt system
init 0                       # Shutdown system
init 6                       # Reboot system
```

## Service Management (systemd)

```bash
systemctl start <service>    # Start a service
systemctl stop <service>     # Stop a service
systemctl restart <service>  # Restart a service
systemctl reload <service>   # Reload service configuration
systemctl status <service>   # Check service status
systemctl enable <service>   # Enable service at boot
systemctl disable <service>  # Disable service at boot
systemctl list-units         # List all units
systemctl list-unit-files    # List all unit files
```

## File Links

```bash
ln <source> <link>           # Create hard link
ln -s <source> <link>        # Create symbolic (soft) link
readlink <link>              # Show where symbolic link points
unlink <link>                # Remove link
```

## File Comparison and Manipulation

```bash
diff <file1> <file2>         # Compare files
diff -u <file1> <file2>      # Unified diff format
comm <file1> <file2>         # Compare sorted files line by line
cmp <file1> <file2>          # Compare files byte by byte
cut -d':' -f1 <file>         # Cut fields from file
paste <file1> <file2>        # Merge lines of files
join <file1> <file2>         # Join lines based on common field
tr 'a-z' 'A-Z' < file        # Translate characters
sed 's/old/new/g' <file>     # Stream editor
awk '{print $1}' <file>      # Pattern scanning and processing
```

## Miscellaneous Commands

```bash
alias ll='ls -la'            # Create command alias
unalias ll                   # Remove alias
printenv                     # Print environment variables
export VAR=value             # Set environment variable
env                          # Show all environment variables
echo $PATH                   # Show PATH variable
source <file>                # Execute commands from file
. <file>                     # Execute commands from file
sleep <seconds>              # Delay for specified time
watch <command>              # Execute command periodically
xargs                        # Build and execute commands
tee <file>                   # Read from stdin and write to stdout and file
```

## Help and Documentation

```bash
man <command>                # Show manual page
info <command>               # Show info page
<command> --help             # Show command help
whatis <command>             # Show one-line description
apropos <keyword>            # Search manual pages
type <command>               # Show command type
```

## Keyboard Shortcuts

```bash
Ctrl+C                       # Cancel current command
Ctrl+Z                       # Suspend current command
Ctrl+D                       # Exit shell or end of input
Ctrl+L                       # Clear screen
Ctrl+A                       # Move to beginning of line
Ctrl+E                       # Move to end of line
Ctrl+U                       # Delete from cursor to beginning of line
Ctrl+K                       # Delete from cursor to end of line
Ctrl+W                       # Delete word before cursor
Ctrl+R                       # Reverse search through history
Tab                          # Autocomplete
Up/Down Arrow                # Navigate command history
```

---






