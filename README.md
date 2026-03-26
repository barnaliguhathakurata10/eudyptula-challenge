# Eudyptula Challenge — Selected Tasks

A series of Linux kernel programming exercises from the Eudyptula Challenge,
focused on building practical kernel development skills through progressively
challenging tasks — from writing a simple hello world module to working with
sysfs and kobjects.

---

## Completed Tasks

| Task | Topic | Description |
|------|-------|-------------|
| 01 | Hello world kernel module | Write a kernel module with a standalone Makefile that prints "Hello World!" to the kernel debug log on load and can be cleanly unloaded |
| 02 | Custom kernel build | Download Linus's latest kernel git tree, build and boot it with CONFIG_LOCALVERSION_AUTO=y |
| 03 | Kernel Makefile patch | Modify the kernel Makefile EXTRAVERSION field so the running kernel contains "-eudyptula" in its version string |
| 04 | Kernel coding style | Fix two kernel modules that violate the Linux kernel coding style as described in Documentation/CodingStyle, verified using checkpatch.pl |
| 08 | Debugfs interface | Extend the hello world module to create a debugfs directory "eudyptula" with three virtual files: "id" (read/write), "jiffies" (read-only, returns current jiffies value), and "foo" (root-writable, world-readable, with proper locking) |
| 09 | Sysfs and kobjects | Move the debugfs implementation from task 08 to sysfs, placing the "eudyptula" directory under /sys/kernel/ using kobjects |

---

## Environment

- Kernel version: 6.x and 7.x
- Architecture: ppc64le

---

## How to Build and Test

Each task has its own directory with a `Makefile`. To build and load any module:

```bash
cd taskXX

# Build the module
make

# Load the module
sudo insmod <module_name>.ko

# Check kernel log output
dmesg | tail -10

# Unload the module
sudo rmmod <module_name>

# Clean build files
make clean
```

---

## Key Concepts Covered

- Kernel module init/exit lifecycle
- Kernel debug logging with `printk`
- Building and booting a custom kernel from source
- Linux kernel coding style and `checkpatch.pl`
- Debugfs interface (`debugfs_create_dir`, `debugfs_create_file`)
- Kernel synchronization and locking (mutex) for concurrent read/write
- Sysfs and kobjects (`kobject_create_and_add`, `sysfs_create_file`, show/store callbacks)

---

## About the Eudyptula Challenge

The Eudyptula Challenge was a private series of Linux kernel programming
exercises designed to help developers learn kernel programming through
progressively harder tasks — from writing a simple hello world module all
the way to contributing patches to the mainline kernel. The challenge is
no longer active but remains a well-known learning path in the kernel
community.

---

## Author

Barnali Guha Thakurata
- Software Engineer, Linux Technology Center — IBM (Linux on Power)
