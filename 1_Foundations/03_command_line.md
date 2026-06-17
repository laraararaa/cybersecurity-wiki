# Command Line Essentials

## Why Command Line Matters

In cybersecurity, the command line (terminal/shell) is your primary tool. You'll use it to:
- Navigate systems
- Run security tools
- Analyze data
- Automate tasks
- Exploit vulnerabilities

**If you can't use the command line effectively, you'll struggle in cybersecurity.**

---

## Shell vs Terminal

### Terminal
The **terminal** is the program that displays text input/output. It's just a window.

### Shell
The **shell** is the program that interprets your commands. Popular shells:
- **bash** (Bourne Again Shell) - Most common on Linux
- **zsh** (Z Shell) - Modern, popular on macOS
- **PowerShell** - Windows modern shell

---

## Basic Linux Commands

### Navigation

```bash
pwd              # Print working directory
ls               # List files
cd folder        # Change directory
mkdir newfolder  # Create directory
```

### File Operations

```bash
cat file.txt          # Display file contents
echo "text" > file.txt # Write to file
cp source dest        # Copy file
mv old new            # Move/rename file
rm file.txt           # Delete file
grep "text" file.txt  # Search for text
find / -name "file"   # Find files
```

### Permissions

```bash
chmod 755 script.sh    # Change permissions
chown user file.txt    # Change owner
sudo command           # Run as root
```

### Process Management

```bash
ps aux              # List processes
top                 # Monitor processes
kill PID            # Stop process
whoami              # Show current user
```

### System Information

```bash
uname -a            # System info
df -h               # Disk space
du -sh folder/      # Folder size
ifconfig            # Network config
```

---

## Advanced Concepts

### Pipes (|)
Send output from one command to another:

```bash
ls -la | grep "file"
ps aux | grep bash
cat users.txt | wc -l
```

### Redirection
Redirect input/output:

```bash
command > file.txt        # Write to file
command >> file.txt       # Append to file
command < input.txt       # Read from file
```

### Wildcards
```bash
ls *.txt              # All .txt files
ls file??.txt         # file + 2 chars + .txt
rm file*              # All files starting with "file"
```

---

## Key Takeaways

✅ The command line is essential for cybersecurity

✅ Master navigation and file operations

✅ Understand permissions and processes

✅ Use pipes and redirection to chain commands

✅ Practice until commands become automatic

---

## Next Steps

1. Spend time in the command line
2. Practice the commands above
3. Use the command line for all file operations
4. Move on to [Programming Basics](04_programming.md)
