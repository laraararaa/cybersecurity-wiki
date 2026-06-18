# Scanning & Enumeration

## What is Scanning & Enumeration?

**Scanning** is actively probing a target to find open ports and services.

**Enumeration** is gathering detailed information about those services (versions, configurations, vulnerabilities).

After reconnaissance, this is the next step in the attack process.

---

## Port Scanning

### What is Nmap?

**Nmap** (Network Mapper) is the standard tool for network discovery and port scanning.

### Basic Scan

```bash
nmap 192.168.1.1
```

Output:
```
Starting Nmap 7.80 ( https://nmap.org )
Nmap scan report for 192.168.1.1
Host is up (0.0015s latency).
NOT shown: 995 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https
3306/tcp open mysql
```

### Common Nmap Scans

#### TCP Connect Scan
```bash
nmap -sT 192.168.1.1  # Full connection (slower, logged)
```

#### SYN Scan (Stealth)
```bash
nmap -sS 192.168.1.1  # Half-open connection (faster, less logged)
```

#### Ping Sweep
```bash
nmap -sn 192.168.1.0/24  # Find all hosts on network
```

#### Specific Ports
```bash
nmap -p 22,80,443 192.168.1.1      # Scan specific ports
nmap -p 1-65535 192.168.1.1         # Scan all ports
nmap -p- 192.168.1.1                # Scan all ports (shorthand)
```

#### Version Detection
```bash
nmap -sV 192.168.1.1  # Detect service versions
```

Output:
```
22/tcp  open  ssh     OpenSSH 7.4 (protocol 2.0)
80/tcp  open  http    Apache httpd 2.4.6
443/tcp open  https   Apache httpd 2.4.6
```

#### OS Detection
```bash
nmap -O 192.168.1.1   # Attempt to detect OS
```

#### Aggressive Scan
```bash
nmap -A 192.168.1.1   # Version, OS, script scanning
```

---

## Service Enumeration

Once you find open ports, enumerate the services:

### SSH (Port 22)

```bash
ssh -v username@192.168.1.1  # Connect with verbose output
```

Look for:
- SSH version (old versions have vulnerabilities)
- Supported authentication methods

### HTTP/HTTPS (Ports 80/443)

```bash
curl -I http://192.168.1.1          # Get headers
curl -v http://192.168.1.1          # Verbose (see everything)
openssl s_client -connect 192.168.1.1:443  # Check SSL/TLS
```

Look for:
- Web server version
- Technologies used (WordPress, Apache, etc.)
- SSL/TLS version and certificate info

### Database (Port 3306 MySQL, 5432 PostgreSQL)

```bash
mysql -h 192.168.1.1 -u root        # Try to connect
psql -h 192.168.1.1 -U postgres     # PostgreSQL
```

Look for:
- Default credentials
- Unprotected databases
- Database version

---

## Vulnerability Scanning

### Nessus
Professional vulnerability scanner (commercial, free tier available)

### OpenVAS
Open-source vulnerability scanner

### Nikto
Web server scanner

```bash
nikto -h http://192.168.1.1  # Scan web server
```

---

## Key Takeaways

✅ Scanning finds open ports and services

✅ Enumeration gathers detailed information

✅ Nmap is the standard scanning tool

✅ Service versions often reveal vulnerabilities

✅ Combine multiple tools for thorough results

---

## What's Next?

Now that you've identified vulnerabilities, let's exploit them: [Exploitation](03_exploitation.md)
