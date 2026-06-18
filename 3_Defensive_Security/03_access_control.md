# Access Control (Authentication & Authorization)

## What is Access Control?

**Access Control** determines:
- **Authentication**: Who are you?
- **Authorization**: What can you do?

---

## Authentication Methods

### Single-Factor Authentication (Passwords)

**Weaknesses**:
- Users reuse passwords
- Weak passwords (123456, password)
- Phishing steals credentials

**Best Practices**:
```bash
# Require strong passwords
# Minimum 12 characters
# Mix of uppercase, lowercase, numbers, symbols
# Not dictionary words or personal info
```

### Multi-Factor Authentication (MFA)

Require multiple proof of identity:

#### Something You Know
- Password
- PIN
- Security question

#### Something You Have
- Phone (SMS code)
- Hardware token
- Authenticator app (Google Authenticator)

#### Something You Are
- Fingerprint
- Face recognition
- Iris scan

**Example MFA Flow**:
```
1. Enter username/password
2. Enter SMS code from phone
3. Authenticate
```

### SSH Key Authentication

**Setup**:
```bash
# Generate key pair
ssh-keygen -t rsa -b 4096

# Copy public key to server
ssh-copy-id user@host

# Connect (no password needed)
ssh user@host
```

**Advantages**:
- No password to intercept
- Stronger than passwords
- Automatable

---

## Authorization & Permissions

### Role-Based Access Control (RBAC)

Assign permissions based on roles:

```
Admin Role: Can create/delete users, view logs, change configs
Manager Role: Can view reports, approve requests
User Role: Can view own data, change password
```

### Attribute-Based Access Control (ABAC)

More granular control based on attributes:

```
If (user.department == "IT" AND user.location == "NYC" AND time < 18:00)
  ALLOW access to database
ELSE
  DENY
```

### Least Privilege Principle

Give users minimum necessary permissions:

**Bad**:
```bash
chmod 777 /var/www        # Everyone can read/write/execute
ALL users are administrators
```

**Good**:
```bash
chmod 755 /var/www        # Owner: full, Others: read+execute
Specific users have specific roles
```

---

## Access Control Implementation

### Linux File Permissions

```bash
# Check permissions
ls -la
# drwxr-xr-x user group
# Owner: rwx (read, write, execute)
# Group: r-x (read, execute)
# Others: r-x (read, execute)

# Change permissions
chmod 640 sensitive_file
# Owner: rw, Group: r, Others: nothing
```

### Linux Sudo

Allow specific users to run specific commands as root:

```bash
# Edit sudo configuration
sudo visudo

# Example entries:
john ALL=(ALL) /usr/bin/restart_service  # Run one command
IT_TEAM ALL=(ALL) NOPASSWD: /usr/bin/*   # Run all commands
```

### Windows Access Control Lists (ACLs)

```powershell
# Get file ACL
Get-Acl C:\sensitive\file.txt

# Set permissions
$acl = Get-Acl C:\sensitive\file.txt
$ar = New-Object System.Security.AccessControl.FileSystemAccessRule("DOMAIN\User","FullControl","Allow")
$acl.SetAccessRule($ar)
$acl | Set-Acl C:\sensitive\file.txt
```

### Active Directory (Windows Enterprise)

Centralized access control for enterprise networks:

```powershell
# Create user
New-ADUser -Name "John Smith" -SamAccountName john.smith

# Add to group
Add-ADGroupMember -Identity "IT_Department" -Members john.smith

# Group has permissions on resources
```

---

## Key Takeaways

✅ Authentication verifies identity

✅ Authorization controls access

✅ MFA significantly improves security

✅ Use SSH keys instead of passwords when possible

✅ Implement least privilege

✅ Use roles to manage permissions

---

## What's Next?

With access controlled, detect attacks in progress: [Monitoring & Detection](04_monitoring.md)
