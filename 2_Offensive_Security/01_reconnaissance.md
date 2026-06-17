# Reconnaissance (Information Gathering)

## What is Reconnaissance?

**Reconnaissance** (or "recon") is gathering information about a target BEFORE attempting any exploits.

This is like a burglar casing a building:
- Where are the doors and windows?
- What's the security like?
- Who works there?
- When are they busy/empty?

Attackers often spend 50%+ of their time on reconnaissance.

## Why Reconnaissance?

- **Reduces risk**: Know what you're attacking before you attack
- **Increases success**: Better information = better planning
- **Finds the easiest path**: Most targets have weak spots
- **Avoids detection**: More stealthy than scanning blindly

---

## Passive Reconnaissance

**Passive recon** gathers information WITHOUT directly contacting the target. The target doesn't know you're looking.

### 1. Public Records

**DNS Records**: Who owns the domain?
```bash
whois example.com
dig example.com
nslookup example.com
```

This tells you:
- Domain registrant
- Registrar
- Name servers
- Creation date

### 2. Search Engines

**Google Dorking**: Advanced Google searches
```
site:example.com filetype:pdf
inurl:admin
site:example.com "password"
cache:example.com
```

Why? Companies accidentally leak documents, credentials, and configuration files in search results.

### 3. Social Engineering

**Gathering information from people**:
- LinkedIn: Employee names, titles, relationships
- Social media: Interests, locations, routines
- Email patterns: firstname.lastname@company.com
- Phone numbers: Often follow patterns

### 4. Public Databases

- **Shodan**: Search engine for connected devices
- **Censys**: Internet-wide scanning data
- **Have I Been Pwned**: Check if emails were in breaches
- **Pastebin**: Leaked data

### 5. Web Archives

**Wayback Machine** (archive.org): Historical snapshots of websites

You might find:
- Old IP addresses
- Removed pages with information
- Old configuration

---

## Active Reconnaissance

**Active recon** directly contacts the target. The target might detect you.

### 1. Ping Sweep

Find which hosts are alive on a network:
```bash
for i in {1..254}; do ping -c 1 192.168.1.$i | grep "bytes from"; done
```

Why? Know which IPs have active computers.

### 2. Network Scanning

```bash
nmap -sn 192.168.1.0/24  # What's alive?
nmap 192.168.1.1         # What services?
```

### 3. Website Analysis

Visit the target website and look for:
- Technology stack (WordPress, Java, etc.)
- Forms and inputs (potential vulnerabilities)
- File uploads
- Login pages
- API endpoints

Tools:
- **Wappalyzer**: Identify technologies used
- **Burp Suite**: Analyze web traffic
- Browser developer tools (F12)

---

## Information Organization

Know what to do with what you find.

### Create a Target Profile

```
TARGET: example.com

Domain Info:
- Registrant: John Smith
- Registrar: GoDaddy
- Name Servers: ns1.example.com, ns2.example.com
- Founded: 2015

Employees (from LinkedIn):
- John Smith - CEO
- Sarah Jones - CTO
- Mike Brown - Network Admin

Technologies:
- WordPress 5.8
- Apache 2.4.41
- Ubuntu 20.04 (guessed from headers)

Subdomains:
- mail.example.com
- admin.example.com
- api.example.com
- www.example.com

Potential Vulnerabilities:
- WordPress 5.8 has known vulnerabilities
- Apache 2.4.41 is outdated
- admin.example.com accessible (should be internal)
```

---

## Tools Summary

| Tool | Purpose |
|------|----------|
| whois | Domain information |
| dig / nslookup | DNS lookups |
| Shodan | Find exposed devices |
| Google | Public information |
| nmap (ping sweep) | Find active hosts |
| Wappalyzer | Identify technologies |
| Burp Suite | Web analysis |

---

## Key Takeaways

1. **Passive recon first**: No detection risk
2. **Organization matters**: Keep track of findings
3. **Multiple sources**: Cross-reference data
4. **Time investment**: Good recon is time-consuming
5. **Documentation**: Write everything down

---

## What's Next?

Once you understand the target, let's scan it for vulnerabilities: [Scanning & Enumeration](02_scanning_enumeration.md)
