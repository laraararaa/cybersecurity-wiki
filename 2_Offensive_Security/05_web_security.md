# Web Security (Web Application Attacks)

## Why Web Security?

Web applications are everywhere:
- Banking sites
- Email
- Social media
- Internal company applications

Most data breaches involve web application vulnerabilities.

---

## OWASP Top 10

The Open Web Application Security Project maintains the top 10 web vulnerabilities.

### 1. Broken Access Control

Attackers access functions/data they shouldn't.

**Example**:
```
http://site.com/user/profile?user_id=1  # View your profile
http://site.com/user/profile?user_id=2  # View user 2's profile (should be blocked!)
```

**Fix**: Check permissions before showing data

### 2. Cryptographic Failures

Sensitive data exposed due to weak encryption.

**Example**: Passwords stored in plain text

**Fix**: Use strong encryption (AES-256), hash passwords (bcrypt)

### 3. Injection

Attacker injects malicious code into input fields.

#### SQL Injection
```
Input: admin' OR '1'='1
Query: SELECT * FROM users WHERE username='admin' OR '1'='1'
Result: All users returned
```

#### Command Injection
```
Input: 192.168.1.1; cat /etc/passwd
Command: ping 192.168.1.1; cat /etc/passwd
Result: File contents displayed
```

**Fix**: Use parameterized queries, input validation

### 4. Insecure Design

Security controls missing from the application design.

**Example**: No rate limiting on login (brute force possible)

**Fix**: Design security into the application from the start

### 5. Security Misconfiguration

Securitysettings are incorrect or missing.

**Examples**:
- Debug mode enabled in production
- Default credentials not changed
- Unnecessary services running

**Fix**: Hardening guides, secure defaults

### 6. Vulnerable and Outdated Components

Using libraries/frameworks with known vulnerabilities.

**Example**: jQuery 1.6.2 (from 2011) has RCE vulnerability

**Fix**: Keep dependencies updated

### 7. Authentication & Session Management Failures

Session/login vulnerabilities.

**Examples**:
- Predictable session IDs
- No logout
- Session fixation

**Fix**: Use framework's built-in auth, secure session handling

### 8. Software & Data Integrity Failures

Insecure updates or untrusted sources.

**Example**: Plugin auto-update without verification

**Fix**: Verify integrity, use HTTPS, code signing

### 9. Logging & Monitoring Failures

No visibility into attacks.

**Example**: No logs of failed login attempts

**Fix**: Log security events, monitor for anomalies

### 10. Server-Side Request Forgery (SSRF)

Attacker tricks server into making requests.

**Example**:
```
Input: http://internal-server/admin
Server requests it internally and returns output
Attacker gains access to internal systems
```

**Fix**: Whitelist allowed URLs, validate input

---

## Web Testing Tools

### Burp Suite

Industry-standard web vulnerability scanner and proxy.

```bash
burpsuite
```

Features:
- Intercept and modify requests
- Scan for vulnerabilities
- Replay requests
- Brute force logins

### OWASP ZAP

Free open-source web scanner.

```bash
zaproxy
```

### SQLMap

Automated SQL injection testing.

```bash
sqlmap -u "http://target.com/page.php?id=1" --dbs
```

---

## Key Takeaways

✅ Web vulnerabilities are common and exploitable

✅ Input validation is critical

✅ Use frameworks' built-in security features

✅ Keep software updated

✅ Implement logging and monitoring

---

## What's Next?

Now understand offense, let's build defense: [Defensive Security](../3_Defensive_Security/README.md)
