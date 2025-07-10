# 🗂️ Linux – File & Directory Management

---

## 1. Recursively Change Ownership

```bash
chown -R username:groupname /path/to/directory
```

---

## 2. Find All `.log` Files Modified in Last 24 Hours

```bash
find /var/log -name "*.log" -mtime -1
```

---

## 3. Difference Between `find` and `locate`

| Feature      | `find`              | `locate`                  |
|--------------|---------------------|---------------------------|
| Real-time    | Yes                 | No (uses a database)      |
| Speed        | Slower              | Faster                    |
| Dependency   | None                | `updatedb` required       |
| Accuracy     | Always up-to-date   | Based on last DB update   |

---

## 4. Mount and Unmount a Filesystem

```bash
sudo mount /dev/sdX1 /mnt/mydrive
sudo umount /mnt/mydrive
```

---

## 5. What Is `/etc/fstab`?

A configuration file for persistent filesystem mounts across reboots.

**Example entry:**

```ini
UUID=xxxx-xxxx  /mnt/data  ext4  defaults  0  2
```
