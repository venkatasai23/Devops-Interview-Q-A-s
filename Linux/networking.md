# 🌐 Linux – Networking

---

## 1. View IP Address and Interface Details

```bash
ip addr
ip a
```

---

## 2. Purpose of `/etc/hosts` and `/etc/resolv.conf`

- **/etc/hosts**: Static name resolution (maps hostnames to IP addresses locally)
- **/etc/resolv.conf**: DNS resolver configuration (lists nameserver IPs for DNS lookups)

---

## 3. Check DNS Resolution

```bash
nslookup google.com
dig google.com
host google.com
```

---

## 4. Test Remote Server Connectivity

```bash
ping <hostname>
telnet <hostname> <port>
nc -zv <hostname> <port>
```

---

## 5. Create Persistent Static IP

Configure in:

- `/etc/network/interfaces` (Debian-based)
- `/etc/sysconfig/network-scripts/ifcfg-*` (RHEL-based)
- Or use **netplan** (`/etc/netplan/*.yaml`) on Ubuntu 18.04+
