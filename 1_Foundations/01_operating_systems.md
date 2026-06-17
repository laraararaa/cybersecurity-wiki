# Operating Systems Basics

## What is an Operating System?

An **operating system (OS)** is software that manages computer hardware and provides services to programs. Think of it as the manager of a company—it controls resources, makes decisions about who gets access to what, and keeps everything running smoothly.

### Key Functions

1. **Hardware Management** - Controls CPU, memory, storage, network cards
2. **Resource Allocation** - Decides which programs get CPU time, memory, etc.
3. **Security** - Controls who can access what files and resources
4. **File Management** - Organizes and stores data
5. **User Interface** - Allows humans to interact with the computer

## Why This Matters in Cybersecurity

Most cybersecurity work involves:
- Finding weaknesses in operating systems
- Understanding how security features work
- Exploiting or defending OS vulnerabilities
- Managing permissions and access controls

You cannot be effective in cybersecurity without understanding operating systems.

---

## Linux Basics

### What is Linux?

Linux is a **free, open-source operating system** created by Linus Torvalds in 1991. "Open-source" means anyone can see the source code and modify it.

### Why Linux is Important for Cybersecurity

- **Servers**: ~90% of internet servers run Linux
- **Security Tools**: Most penetration testing tools run on Linux
- **Transparency**: Because it's open-source, security researchers can audit the code
- **Control**: You have complete control over the system

### Linux Distribution (Distro)

Linux is the core kernel, but different organizations package it with different tools. These "flavors" are called **distributions**.

Popular distributions:
- **Ubuntu** - User-friendly, great for beginners
- **Debian** - Stable, used as base for many distros
- **Kali Linux** - Designed for penetration testing
- **Red Hat / CentOS** - Enterprise systems
- **Arch Linux** - Lightweight, advanced users

### Linux File System

Linux organizes files in a hierarchical structure starting from `/` (root):

```
/
├── bin/        (essential command executables)
├── boot/       (files needed to boot the system)
├── etc/        (configuration files)
├── home/       (user home directories)
├── root/       (root user's home directory)
├── usr/        (user programs and data)
├── var/        (variable data like logs)
└── tmp/        (temporary files)
```

### Key Linux Concepts

#### Users and Permissions

Linux is a **multi-user** system. Different users have different permissions.

Permissions breakdown:
- **r (read)** = Can view file contents
- **w (write)** = Can modify file
- **x (execute)** = Can run the file

#### Root User

The **root** user (UID 0) has complete control over the system. In cybersecurity, gaining root access is often an attacker's goal.

#### Home Directory

Each user has a home directory (`~` or `/home/username`) where their files are stored.

### Essential Linux Commands

You'll learn these in detail in the Command Line section, but here are some basics:

```bash
ls              # List files
cd              # Change directory
pwd             # Print working directory
cat             # Display file contents
echo            # Print text
grep            # Search for text
find            # Find files
sudo            # Run as root user
chmod           # Change permissions
chown           # Change ownership
```

---

## Windows Basics

### What is Windows?

Windows is a **closed-source, proprietary operating system** created by Microsoft. Unlike Linux, you can't see the source code.

### Why Windows Matters in Cybersecurity

- **Desktops**: ~77% of desktop computers run Windows
- **Enterprises**: Many businesses rely on Windows servers and Active Directory
- **Targets**: Windows systems are frequently targeted because they're so common
- **Domain Networks**: Windows domains (Active Directory) manage access in enterprise networks

### Windows File System

Windows uses drive letters and paths:

```
C:\
├── Users/
│   ├── Administrator/
│   └── YourUsername/
│       ├── Desktop/
│       ├── Documents/
│       ├── Downloads/
│       └── AppData/
├── Program Files/
├── Windows/
│   ├── System32/  (system programs and DLLs)
│   ├── Temp/
│   └── Registry/  (configuration database)
└── ...
```

### Key Windows Concepts

#### Administrator Account

Like Linux's root user, the **Administrator** account has complete system control.

#### Registry

The **Registry** is a database that stores Windows configuration. It's critical for:
- System settings
- Installed programs
- User preferences
- Security settings

Attackers often modify the Registry to persist access or disable security features.

#### DLL Files

**DLL (Dynamic Link Library)** files contain reusable code that multiple programs can use.

#### Active Directory

In enterprise networks, **Active Directory** is Microsoft's centralized system for managing users, computers, and permissions across networks.

### Essential Windows Commands (CMD/PowerShell)

```powershell
dir             # List files
cd              # Change directory
echo            # Print text
whoami          # Show current user
ipconfig        # Show network configuration
netstat         # Show network connections
tasklist        # Show running processes
taskkill        # Stop a process
```

---

## Comparing Linux and Windows

| Aspect | Linux | Windows |
|--------|-------|----------|
| **License** | Open-source, Free | Proprietary, Paid |
| **Server Use** | ~90% of servers | Enterprise use |
| **Desktop Use** | ~1% of desktops | ~77% of desktops |
| **Root Access** | root user | Administrator |

---

## Key Takeaways

✅ Operating systems manage hardware and provide services

✅ Linux dominates servers; Windows dominates desktops

✅ Understanding permissions is fundamental

✅ Both systems have "super users" with complete control

✅ The command line is essential for cybersecurity

---

## Next Steps

1. Set up a Linux virtual machine if you haven't
2. Explore the Linux file system using commands
3. Get comfortable with basic navigation (cd, ls, pwd)
4. Move on to [Networking Basics](02_networking.md)
