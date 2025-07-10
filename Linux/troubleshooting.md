# 🛠️ Linux – Troubleshooting & Scenarios

---

## 1. Disk 100% Full – Cannot Write/Delete

**Check:**

```bash
df -h
du -sh /*
lsof | grep deleted
```

- Clean up logs or orphaned files.
- Move or delete temporary data.

---

## 2. SSH Not Working – But Network Is Fine

**Check:**

- Firewall rules: `ufw status` or `iptables -L`
- SSHD status: `systemctl status sshd`
- `/etc/ssh/sshd_config` for errors
- Authentication logs: `/var/log/auth.log`

---

## 3. Service Fails After Reboot

**Check:**

```bash
systemctl status <service>
journalctl -xe
```

**Enable service to start on boot:**

```bash
systemctl enable <service>
```

---

## 4. Application Slow, CPU Low, Memory High

**Check:**

```bash
top
free -m
vmstat 1
```

- Look for memory leaks or high swap usage.

---

## 5. Kernel Panic

**Check:**

- Logs: `journalctl -k`
- Output: `dmesg`
- Boot into recovery mode if needed.
- Inspect hardware (RAM, disk).

---

## 6. Cron Job Not Running

**Check:**

- List jobs: `crontab -l`
- Logs: `/var/log/cron` or `/var/log/syslog`
- Ensure script has executable permissions.

---

## 7. Load Average High, CPU Low

**Likely I/O wait. Check:**

```bash
iostat
vmstat
iotop
```

---

## 8. Recover Forgotten Root Password

1. Boot into GRUB.
2. Edit kernel parameters: add `init=/bin/bash`.
3. Remount root as read-write:

    ```bash
    mount -o remount,rw /
    ```

4. Change password:

    ```bash
    passwd
    ```

---

## 9. Migrate Data Between Servers (Zero Downtime)

- Use `rsync` with `--partial --inplace`.
- Use `screen` or `tmux` for session persistence.
- Perform a final `rsync` after stopping the application.

---

## 10. Check and Repair Filesystem Errors

**Run in recovery or unmounted mode:**

```bash
sudo fsck /dev/sdX
```
