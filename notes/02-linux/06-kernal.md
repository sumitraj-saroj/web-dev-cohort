# Linux Boot Process

## Stages of the Boot Process

### 1. BIOS (Basic Input Output System)
- Initializes system hardware during startup
- Performs **POST (Power-On Self Test)**:
  - Checks memory
  - Detects HDD/SSD
  - Verifies essential hardware
- The main role of BIOS is to **locate and load the bootloader**

> On modern systems, BIOS is often replaced by **UEFI**, but the boot concept remains similar.

---

### 2. Bootloader
- Loads the **Linux kernel** into memory
- Passes kernel parameters
- Places the kernel code into RAM

**Common bootloader:**
- **GRUB (Grand Unified Bootloader)**

---

### 3. Kernel
- Initializes:
  - Memory management
  - CPU scheduling
  - Device drivers
- Mounts the root filesystem
- Starts the **init process (mother process)**

The init process is the **first user-space process** and is responsible for starting and stopping essential system services.

---

# Levels of Abstraction in Linux OS

### 1. Hardware
- Physical components such as:
  - CPU
  - Memory
  - HDD / SSD
  - I/O ports

---

### 2. Kernel
- Core of the operating system
- Responsible for:
  - Process management
  - Memory management
  - Device communication
  - Filesystem initialization
  - Handling system calls

---

### 3. User Space
- Contains all user-facing applications
- Programs run with limited privileges
- Interacts with the kernel using system calls

---

## Privilege Levels and Protection Rings

- **Kernel Mode**
  - Full access to hardware
  - Executes privileged instructions

- **User Mode**
  - Restricted access
  - Cannot directly interact with hardware

For security reasons, operations like:
- Reading/writing hardware
- Controlling network ports
- Managing memory

are handled only in **kernel mode**.

---

## System Calls

A **system call** allows a user-space process to:
- Request a privileged operation from the kernel
- Temporarily switch to kernel mode
- Safely return back to user mode

### System Call API
- Provides an interface for user-space applications
- Allows processes to request services from the kernel
- These services are exposed through **system calls**

---

# Init Process Implementations

There are three major init systems in Linux:

| Init System | Description |
|------------|-------------|
| **System V (SysV)** | Traditional init system |
| **Upstart** | Event-based init system (older Ubuntu) |
| **systemd** | Modern standard init system |

---

## System V Init

- Starts and stops services **sequentially**
- Uses predefined **runlevels**
- Slower due to one-by-one service handling

### System V Runlevels

| Runlevel | Description |
|--------|-------------|
| `0` | Shutdown |
| `1` | Single-user mode |
| `2` | Multi-user (without networking) |
| `3` | Multi-user (with networking) |
| `4` | Unused |
| `5` | Multi-user with networking & GUI |
| `6` | Reboot |

### Check Service Status
```bash
service --status-all
```

### Start / Stop / Restart a Service
```bash
sudo service whoopsie start
sudo service whoopsie stop
sudo service whoopsie restart
```

---

## Upstart Init

- Designed to improve System V
- Uses an **event-driven model**
- Services are defined as **jobs**

### Concepts
- **Jobs** → Actions performed
- **Events** → Signals/messages received from the system

---

## systemd

- Modern init system
- Starts services in parallel
- Uses **targets** to bring the system to a desired state

### Targets (systemd)

| Target | Description |
|-------|-------------|
| `poweroff.target` | Shutdown |
| `rescue.target` | Single-user mode |
| `multi-user.target` | Multi-user with networking |
| `graphical.target` | Multi-user with GUI |
| `reboot.target` | Reboot |

---

## Managing Power State

```bash
sudo shutdown -h now   # Shutdown immediately
sudo reboot            # Reboot system
```
