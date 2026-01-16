# Linux File System

## File Type Characteristics

| Symbol | Type | Description |
|------|------|-------------|
| `d` | Directory | Collection of files and directories |
| `l` | Link | Reference to another file or directory |
| `-` | File | Regular file (stream of data) |
| `c` | Character Device | Transfers data character by character |
| `b` | Block Device | Transfers data in blocks |
| `p` | Pipe | Connects output of one process to input of another |
| `s` | Socket | Similar to pipe but supports multiple processes |

### Common Command
```bash
ls -l /dev
```

---

## Filesystem Hierarchy

| Directory | Purpose |
|---------|---------|
| `/` | Root directory |
| `/bin` | Essential user binaries |
| `/boot` | Bootloader files |
| `/dev` | Device files |
| `/etc` | Configuration files |
| `/home` | User home directories |
| `/lib` | Shared libraries |
| `/mnt` | Temporary mount point |
| `/opt` | Optional software packages |
| `/proc` | Process and kernel information |
| `/root` | Home directory of root user |
| `/sbin` | System binaries used by root |

---

## Journaling

Journaling helps repair filesystem inconsistencies caused by improper shutdowns.

For example, if a file copy operation is interrupted due to a crash or power failure, journaling allows the filesystem to identify and recover corrupted or incomplete data.

---

## Disk / Filesystem Types

| Filesystem | Description |
|-----------|-------------|
| `ext4` | Standard Linux filesystem; supports large disks (up to ~1 EB) and file sizes up to ~16 TB |
| `Btrfs` | B-tree filesystem; advanced features but less stable than ext4 |
| `XFS` | High-performance journaling filesystem, commonly used on servers |
| `NTFS`, `FAT` | Windows filesystems |
| `HFS` | macOS filesystem |

### Check Filesystem Type
```bash
df -T
```

A disk can be divided into multiple **partitions**, and each partition acts as an independent **block device** with its own filesystem.

---

## Inodes and Inode Tables

Inode tables act like a database for file management.

- Each file or directory has a unique **inode**
- The inode stores metadata about the file
- Filenames are stored separately in directory entries

---

## Partition Table

To understand how a disk is partitioned, Linux uses partition tables.

### Partition Schemes
- **MBR (Master Boot Record)**
- **GPT (GUID Partition Table)**

---

## MBR (Master Boot Record)

- Traditional partitioning scheme
- Supports disks up to **2 TB**
- Allows only **4 primary partitions**
- One primary partition can be an **extended partition**
- Extended partitions can contain multiple **logical partitions**

---

## GPT (GUID Partition Table)

- Modern partitioning standard
- Each partition has a **Globally Unique Identifier (GUID)**
- Supports very large disks
- Commonly used with **UEFI** systems

---

## Filesystem Structure

A filesystem is an organized collection of files and directories.

It consists of four major components:

1. **Boot Block**
2. **Superblock**
3. **Inode Table**
4. **Data Blocks**

---

# Inode

An **inode (index node)** is a data structure used to store metadata about a file.

### Inode Contains
- File type and permissions
- Owner and group ID
- File size
- Timestamps
- Pointers to data blocks

> An inode contains everything **except** the filename and file contents.

When a filesystem is created, space for inodes is allocated in advance.

### Check Available Inodes
```bash
df -i
```

### Check Inode Number of a File
```bash
ls -li
```

---

## How Inodes Work

- Each inode contains **15 pointers** to data blocks
- These pointers help locate the actual file data
- When a file is created:
  - A new inode is assigned
  - Metadata is stored in the inode
  - Data blocks are allocated and linked via pointers

Inodes allow the filesystem to efficiently locate and manage file data on disk.
