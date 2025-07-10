# 🐧 Linux – Intermediate Level Interview Questions

---

## 1. What is a zombie process, and how do you kill it?

A **zombie process** is a process that has finished execution but still remains in the process table because its parent hasn't read its exit status. You can't kill a zombie directly—terminate the **parent process** or reboot the system to remove it.

---

## 2. How Do File Permissions Work in Linux?

Permissions are set for:

- **Owner**
- **Group**
- **Others**

Each can have:

- **Read (r)** = 4
- **Write (w)** = 2
- **Execute (x)** = 1

Example:

```bash
-rwxr-xr--
```

This equals `chmod 754`.

---

## 3. Difference Between `cron` and `at`

- **cron**: Schedules recurring tasks.
- **at**: Schedules one-time tasks.

---

## 4. How to View Logs in Linux?

System logs are typically found in `/var/log/`. Common logs include:

- `syslog` or `messages`
- `auth.log`
- Output of `dmesg`

---

## 5. What is a Runlevel?

Runlevels define the system state:

- `0`: Halt
- `1`: Single-user mode
- `3`: Multi-user mode (no GUI)
- `5`: Graphical mode
- `6`: Reboot

Check the current runlevel with:

```bash
runlevel
```

---

## 6. Find Process Using a Specific Port

```bash
sudo lsof -i :<port>
sudo netstat -tulnp | grep <port>
```

---

## 7. Check Real-Time CPU and Memory Usage

```bash
top
htop
vmstat 1
```

---

## 8. Set Environment Variables

- **Temporary** (current session):

    ```bash
    export VAR=value
    ```

- **Permanent**: Add to `~/.bashrc` or `/etc/environment`.

---

## 9. Difference Between `>` and `>>`

- `>`: Overwrites the file.
- `>>`: Appends to the file.

---

## 10. `nice` and `renice`

- `nice`: Set the initial priority of a process.
- `renice`: Change the priority of a running process.

Lower values mean higher priority (range: -20 to 19).
