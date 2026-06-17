# Security Principles

## The CIA Triad

The foundation of security is three core principles:

### Confidentiality
**Only authorized people can access data.**

Example:
- Your password should only be known by you
- Medical records should only be seen by doctors
- Encryption protects data so only intended recipients can read it

Violation: An attacker reads your private emails

### Integrity
**Data cannot be modified without authorization.**

Example:
- A bank transfer amount shouldn't be changed mid-transaction
- Files shouldn't be secretly modified
- Hashing verifies data hasn't been tampered with

Violation: An attacker changes your bank balance

### Availability
**Systems and data must be accessible when needed.**

Example:
- A website should stay up and responsive
- Database should answer queries
- Backups ensure data isn't lost

Violation: A DDoS attack brings down a website

---

## AAA Framework

Three more critical concepts:

### Authentication
**Verify someone is who they claim to be.**

Methods:
- **Something you know**: Password, PIN
- **Something you have**: Key, phone, security token
- **Something you are**: Fingerprint, face, iris

Example:
```
Username: john_smith
Password: correct_password
→ Authenticated! (verified as John Smith)
```

### Authorization
**What authenticated users are allowed to do.**

After authentication, the system checks permissions.

Example:
```
John is authenticated as admin
→ Can read all files (authorized)
→ Can delete files (authorized)
→ Cannot see CEO salary (not authorized)
```

### Accounting (Auditing)
**Recording who did what and when.**

Important for:
- Detecting attacks
- Compliance
- Investigating incidents

Example:
```
[2026-06-17 10:30:15] User: admin - Action: Delete file sales.csv
[2026-06-17 10:30:20] User: john - Action: Failed login attempt (3/5)
[2026-06-17 10:30:25] User: admin - Action: Create backup
```

---

## The Principle of Least Privilege

Users should have **only the minimum permissions** they need to do their job.

### Bad Example
```
Everyone is an administrator on company computers
→ Anyone can install malware
→ Anyone can access others' files
→ Viruses spread easily
```

### Good Example
```
Users have limited permissions
→ Can only run approved applications
→ Can't access other users' files
→ Can't install software
→ System is more secure
```

---

## Defense in Depth

Don't rely on a single security measure. Use **multiple layers**.

### Bad Example (Single Layer)
```
Password is the only protection
→ If password is guessed, attacker has full access
```

### Good Example (Multiple Layers)
```
Password (Layer 1)
  ↓ (if breached)
Two-Factor Authentication (Layer 2)
  ↓ (if breached)
Network monitoring (Layer 3)
  ↓ (if breached)
Incident response team (Layer 4)
```

Even if one layer fails, others protect you.

---

## Key Takeaways

✅ **CIA Triad**: Confidentiality, Integrity, Availability

✅ **AAA**: Authentication, Authorization, Accounting

✅ **Least Privilege**: Give minimum necessary permissions

✅ **Defense in Depth**: Multiple layers of security

✅ **These principles apply to everything**: Networks, systems, applications, physical security

---

## What's Next?

Now that you understand the principles, let's learn how to implement them: [Hardening Systems](02_hardening.md)
