
# 🐧 Daily Log – October 30, 2026

## Linux Server Administration – Day 1

**Project:** Linux Learning Journal

**Topic:** Ubuntu Server Installation and SSH Configuration

**Status:** Completed ✅

---

## 1. Today's Objectives

- [x] Install Oracle VirtualBox.
- [x] Download Ubuntu Server ISO.
- [x] Create Ubuntu Server virtual machine.
- [x] Install Ubuntu Server.
- [x] Install OpenSSH Server.
- [x] Configure VirtualBox NAT port forwarding.
- [x] Test network connectivity.
- [x] Establish SSH connection from Windows.

---

## 2. Environment Setup

| Component | Configuration |
|---|---|
| Host OS | Windows |
| Virtualization | Oracle VirtualBox |
| Guest OS | Ubuntu Server 24.04 LTS |
| RAM | 4 GB |
| CPU | 2 cores |
| Virtual Disk | 25 GB |
| Network Mode | NAT |
| SSH Port | 22 |
| Windows Host Port | 2222 |

---

## 3. Ubuntu Server Installation

Downloaded Ubuntu Server ISO from:

https://ubuntu.com/download/server

Created a virtual machine with the following configuration:

- Name: Ubuntu Server
- Type: Linux
- Version: Ubuntu (64-bit)
- Memory: 4096 MB
- Processors: 2
- Virtual Hard Disk: 25 GB
- Network Adapter: NAT

Completed the guided Ubuntu Server installation.

Created a hostname, username, and password.

---

## 4. OpenSSH Server Installation

### Problem Encountered

Initially, running the SSH status command returned:

```text
ssh.service could not be found
```

### Solution

Updated Ubuntu packages:

```bash
sudo apt update
```

Installed OpenSSH Server:

```bash
sudo apt install openssh-server -y
```

Started and enabled SSH:

```bash
sudo systemctl enable --now ssh
```

Verified the service:

```bash
sudo systemctl status ssh
```

**Result:** SSH service successfully started.

---

## 5. Verify SSH Listening on Port 22

Executed:

```bash
sudo ss -ltn
```

Observed listening ports:

```text
LISTEN  0  4096  0.0.0.0:22
LISTEN  0  4096  [::]:22
```

This confirmed that SSH was listening on IPv4 and IPv6 interfaces.

---

## 6. VirtualBox NAT Port Forwarding

Configured VirtualBox port forwarding.

| Setting | Value |
|---|---|
| Name | SSH |
| Protocol | TCP |
| Host IP | 127.0.0.1 |
| Host Port | 2222 |
| Guest IP | Blank |
| Guest Port | 22 |

### Connection Flow

```text
Windows Host
127.0.0.1:2222
       |
       v
VirtualBox NAT
       |
       v
Ubuntu Server VM
Port 22
       |
       v
OpenSSH Server
```

**Result:** NAT port forwarding successfully configured.

---

## 7. Windows Connectivity Testing

Opened Windows PowerShell.

Executed:

```powershell
Test-NetConnection 127.0.0.1 -Port 2222
```

Result:

```text
TcpTestSucceeded : True
```

**Result:** Windows successfully reached the forwarded port.

---

## 8. SSH Connection from Windows

Executed:

```powershell
ssh -p 2222 username@127.0.0.1
```

Replaced `username` with the Ubuntu account username.

Accepted the SSH fingerprint and entered the Ubuntu password.

**Result:** Successfully connected to Ubuntu Server from Windows using SSH.

---

## 9. Troubleshooting and Lessons Learned

### Issue 1: SSH Service Not Found

**Problem:** OpenSSH Server was not installed.

**Solution:**

```bash
sudo apt install openssh-server -y
sudo systemctl enable --now ssh
```

### Issue 2: SSH Listening Test Errors

**Problem:** Encountered command syntax errors.

**Solution:**

```bash
sudo ss -ltn
```

Successfully verified that SSH was listening on port 22.

### Issue 3: SSH Connection Timeout

**Problem:** Initial SSH connection attempts timed out.

**Troubleshooting:**

1. Verified SSH service status.
2. Confirmed SSH was listening on port 22.
3. Checked VirtualBox NAT port forwarding.
4. Tested Windows connectivity.

**Final Solution:** Correctly configured NAT port forwarding and verified TCP connectivity.

---

## 10. What I Learned Today

1. Virtualization using Oracle VirtualBox.
2. Installing Ubuntu Server.
3. Installing and managing OpenSSH Server.
4. Managing Linux services using systemctl.
5. Understanding SSH and TCP port 22.
6. Configuring VirtualBox NAT networking.
7. Testing network connectivity using PowerShell.
8. Troubleshooting SSH connection problems.
9. Remotely administering Linux servers from Windows.

---

## 11. Final Results Checklist

- [x] Installed Oracle VirtualBox.
- [x] Downloaded Ubuntu Server ISO.
- [x] Created Ubuntu Server VM.
- [x] Installed Ubuntu Server.
- [x] Installed OpenSSH Server.
- [x] Enabled SSH service.
- [x] Verified SSH listening on port 22.
- [x] Configured NAT port forwarding.
- [x] Tested Windows connectivity.
- [x] Successfully connected through SSH.

**Overall Status: DAY 1 COMPLETED 🎉**

---

## 12. Next Learning Objectives

### Linux Fundamentals
- Learn basic Linux commands.
- Navigate Linux directories.
- Create, copy, move, and delete files.

### User and Permission Management
- Create and manage Linux users.
- Configure groups.
- Learn chmod and chown.

### Linux Networking
- Learn IP addressing.
- Configure static IP addresses.
- Understand DNS and gateways.

### Server Administration
- Install Apache Web Server.
- Host a website.
- Install Docker.
- Explore firewall configuration.

---

## Daily Summary

Today I successfully installed Ubuntu Server inside Oracle VirtualBox and configured remote SSH access from Windows.

I learned how to install OpenSSH Server, manage Linux services, verify listening ports, configure NAT port forwarding, and troubleshoot network connectivity.

The biggest accomplishment was successfully establishing an SSH connection from Windows to Ubuntu Server.

**Day 1: Completed successfully! 🚀**

---

*Linux Learning Journal | October 30, 2026*
