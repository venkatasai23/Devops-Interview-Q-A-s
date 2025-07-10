# 🐧 Linux – Basic Level Interview Questions

---

## 1. What is Linux?

Linux is an open-source, Unix-like operating system based on the Linux kernel. It is widely used in servers, cloud systems, embedded devices, and more due to its stability and flexibility.

---

## 2. Differences Between Linux and Unix

| Feature      | Linux                          | Unix                        |
|--------------|-------------------------------|-----------------------------|
| Source       | Open source                   | Mostly closed source        |
| Distribution | Many (Ubuntu, CentOS, etc.)   | Few (AIX, HP-UX, etc.)     |
| Usage        | Widespread: personal & server | Mostly enterprise servers   |
| Cost         | Free                          | Often paid                  |

---

## 3. Process vs Thread

- **Process**: An independent execution unit with its own memory space.
- **Thread**: A lightweight unit within a process, sharing memory with other threads.

---

## 4. What is a Linux Distribution?

A Linux distribution (distro) is a packaged version of the Linux OS, bundled with software, package managers, and UI tools.

**Examples:**

- Ubuntu
- CentOS
- Fedora
- Arch Linux

---

## 5. Linux File System Hierarchy

- `/`      : Root directory
- `/bin`   : Essential binaries
- `/etc`   : Configuration files
- `/home`  : User home directories
- `/var`   : Variable data/logs
- `/opt`   : Optional applications
- `/tmp`   : Temporary files

---

## 6. What Are Inodes?

Inodes are data structures that store metadata about files (permissions, timestamps, ownership, etc.). They do **not** store file names or actual data.

---

## 7. Check Current Directory

```bash
pwd
```

---

## 8. su vs sudo

- **su**: Switch user (requires the target user's password, often root).
- **sudo**: Run a command as another user (usually root) using your own password.

---

## 9. Symbolic vs Hard Links

- **Symbolic (Soft) Link**: Points to a file path. Breaks if the target file is removed.
- **Hard Link**: Points directly to the inode. Persists even if the original file is deleted.

---

## 10. chmod 755 filename Explanation

Sets permissions as follows:

- **Owner**: Read, write, execute (`7`)
- **Group & Others**: Read, execute (`5`)

Equivalent permission string: `rwxr-xr-x`

```bash
chmod 755 filename
```
