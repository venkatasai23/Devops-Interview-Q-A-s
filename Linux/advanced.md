# 🐧 Linux – Advanced Level Interview Questions

---

## 1. How Does `strace` Work and When to Use It?

`strace` traces system calls and signals made by a process.

**Use cases:**

- Debugging binary behavior
- Monitoring I/O operations
- Detecting segmentation faults

**Example:**

```bash
strace ./app
```

---

### 2. What Are cgroups and namespaces?

- **Cgroups:** Limit and isolate resource usage (CPU, memory, etc.)
- **Namespaces:** Provide process isolation (PID, NET, MNT, etc.)

Together, they enable Linux containers.

---

### 3. Linux Memory Management

**Key components:**

- Pages (swapping)
- Cache
- Slab Allocator

Linux uses demand paging and virtual memory.

**Check usage:**

```bash
free -h
vmstat
```

---

### 4. Linux Boot Process

1. BIOS/UEFI
2. Bootloader (GRUB)
3. Kernel
4. `init` or `systemd`
5. Target runlevel

---

### 5. What Are ulimits?

Control system resource usage for users/processes.

**Examples:**

```bash
ulimit -n    # max open files
ulimit -a    # all limits
```

---

### 6. Troubleshooting High I/O Wait

**Check with:**

```bash
iostat
iotop
vmstat
```

- Identify slow disk operations
- Check for overloaded applications (e.g., large writes)

---

### 7. Check Disk Usage & Find Large Files

```bash
df -h         # disk usage
du -sh *      # folder sizes
find / -type f -size +100M
```

---

### 8. Check & Repair Filesystem Errors

```bash
fsck /dev/sdX
```

Run in unmounted or recovery mode.

---

### 9. SELinux vs AppArmor

- **SELinux:** RedHat/CentOS based, strict policies
- **AppArmor:** Ubuntu/Debian based, profile-based

Both provide access control beyond file permissions.

---

### 10. Role of init system

- **SysVinit:** Serial startup, uses init scripts.
- **systemd:** Parallel service startup, uses unit files.

**To check status:**

```bash
systemctl status
```
