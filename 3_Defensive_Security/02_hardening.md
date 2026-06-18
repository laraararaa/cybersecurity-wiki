# Hardening Systems

## What is Hardening?

**Hardening** is the process of making systems resistant to attacks by:
- Removing unnecessary services
- Applying security patches
- Configuring security settings
- Setting strong access controls

---

## Linux Hardening

### 1. Update System

Keep software current to patch vulnerabilities:

```bash
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```

### 2. Disable Unnecessary Services

```bash
# List running services
sudo systemctl list-units --type=service --state=running

# Disable a service
sudo systemctl disable service_name
sudo systemctl stop service_name
```

Remove:
- Telnet (use SSH instead)
- FTP (use SFTP instead)
- NFS (if not needed)
- X11 (if headless server)

### 3. Configure Firewall

```bash
# UFW (Uncomplicated Firewall)
sudo ufw enable
sudo ufw allow 22/tcp    # Allow SSH
sudo ufw allow 80/tcp    # Allow HTTP
sudo ufw allow 443/tcp   # Allow HTTPS
sudo ufw deny 3306/tcp   # Deny MySQL to external
```

### 4. SSH Hardening

Edit `/etc/ssh/sshd_config`:

```bash
# Disable root login
PermitRootLogin no

# Use key-based auth only
PasswordAuthentication no
PubkeyAuthentication yes

# Change default port (obscurity, not security)
Port 2222

# Disable X11
X11Forwarding no

# Limit login attempts
MaxAuthTries 3
MaxSessions 10
```

Restart SSH:
```bash
sudo systemctl restart ssh
```

### 5. File Permissions

```bash
# Config files should not be world-readable
chmod 644 /etc/important_config

# Sensitive files should be owner-only
chmod 600 ~/.ssh/id_rsa
chmod 700 ~/.ssh/

# Directories should be 755
chmod 755 /var/www/html
```

### 6. User Access Control

```bash
# Remove unnecessary users
userdel olduser

# Use sudo instead of giving root access
usermod -aG sudo newuser

# Set password policy
sudo apt install libpam-pwquality
# Edit /etc/security/pwquality.conf for requirements
```

### 7. Logging

```bash
# View system logs
sudo journalctl -u ssh
sudo tail -f /var/log/auth.log

# Configure log rotation
sudo nano /etc/logrotate.d/rsyslog
```

---

## Windows Hardening

### 1. Windows Updates

```powershell
# Check for updates
PSWindowsUpdate\Get-WindowsUpdate

# Install updates
PSWindowsUpdate\Install-WindowsUpdate -AcceptAll -AutoReboot
```

### 2. Disable Unnecessary Services

```powershell
# Disable a service
Disable-NetAdapterBinding -Name "Ethernet" -ComponentID ms_tcpip6

# Or through Services GUI
services.msc
```

Disable:
- Telnet
- NetBIOS
- LLMNR (if not needed)

### 3. Enable Windows Firewall

```powershell
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled True
```

### 4. User Account Control (UAC)

Keep UAC enabled (default):
```powershell
Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System | Select ConsentPromptBehaviorAdmin
```

### 5. Strong Passwords

```powershell
# Require complex passwords
Get-ADDefaultDomainPasswordPolicy
```

Requirements:
- 12+ characters
- Mix of uppercase, lowercase, numbers, symbols
- No dictionary words

### 6. Audit Logging

```powershell
auditpol /get /category:*
auditpol /set /category:"Logon/Logoff" /success:enable
```

---

## General Hardening Principles

### Principle of Least Privilege
Users should have minimum necessary permissions

### Defense in Depth
Multiple layers of security

### Keep Systems Updated
Patches fix known vulnerabilities

### Monitor & Log
Detect unauthorized activity

### Principle of Secure Defaults
Secure settings by default

---

## Key Takeaways

✅ Hardening reduces attack surface

✅ Updates are critical

✅ Disable unnecessary services

✅ Strong access controls

✅ Logging and monitoring

---

## What's Next?

With systems hardened, control access to them: [Access Control](03_access_control.md)
