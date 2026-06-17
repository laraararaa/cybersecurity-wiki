# Programming Basics

## Do You Need to Learn Programming?

### The Simple Answer

You don't need to be a programmer to work in cybersecurity, but understanding programming concepts is **extremely valuable**.

You'll encounter:
- Malware written in various languages
- Web vulnerabilities in application code
- Scripts to automate security tasks
- Reverse engineering compiled programs
- Reading and writing simple automation scripts

### What You Actually Need

You need to understand:
- How programs work conceptually
- Basic programming logic (variables, loops, conditions)
- How to read and understand code
- How to write simple scripts for automation

---

## Key Programming Concepts

### Variables
Containers for storing data:

```python
username = "admin"
password = "secret123"
user_id = 42
is_admin = True
```

### Data Types

```python
string = "text"          # Text
integer = 42             # Whole number
float = 3.14             # Decimal number
boolean = True           # True/False
list = [1, 2, 3]         # Multiple values
```

### Control Flow

#### If/Else
```python
if user_is_admin:
    grant_access()
else:
    deny_access()
```

#### Loops
```python
for i in range(10):
    print(i)

while password_wrong:
    prompt_for_password()
```

### Functions
```python
def check_password(input_password):
    if input_password == stored_password:
        return True
    return False
```

---

## Programming Languages in Cybersecurity

### Python
**Best for**: Security automation, scripting

**Pros**: Easy to learn, huge security library ecosystem

**Used for**: Penetration testing tools, malware analysis

### Bash/Shell
**Best for**: Linux automation

**Pros**: Native to Linux, perfect for automation

**Used for**: System administration scripts

### C/C++
**Best for**: Low-level programming, exploit development

**Pros**: Very fast, direct hardware access

**Used for**: Malware, exploits

---

## Common Vulnerabilities in Code

### 1. SQL Injection

**Bad Code:**
```python
query = "SELECT * FROM users WHERE username='" + user_input + "'"
```

**Good Code:**
```python
query = "SELECT * FROM users WHERE username=?"
database.execute(query, (user_input,))
```

### 2. Hardcoded Credentials

**Bad Code:**
```python
password = "admin123"
```

**Good Code:**
```python
password = os.environ.get('DATABASE_PASSWORD')
```

---

## Your First Python Script

### 1. Install Python

**Linux:**
```bash
sudo apt update
sudo apt install python3
```

### 2. Write a Script

Create `hello_security.py`:

```python
#!/usr/bin/env python3

print("Welcome to cybersecurity!")

for i in range(5):
    print(f"Attempt {i+1}")

password = "secret"
user_input = input("Guess the password: ")

if user_input == password:
    print("Correct!")
else:
    print("Wrong!")
```

### 3. Run It

```bash
python3 hello_security.py
```

---

## Key Takeaways

✅ Understanding code is valuable for cybersecurity

✅ Learn Python for security automation

✅ Understand control flow (if/else, loops, functions)

✅ Recognize common vulnerabilities in code

✅ Start writing simple automation scripts

---

## Next Steps

1. Install Python on your Linux VM
2. Write simple scripts (loops, conditions, functions)
3. Learn to read code even if you can't write it yet
4. When comfortable, move to [Offensive Security](../2_Offensive_Security/README.md) or [Defensive Security](../3_Defensive_Security/README.md)
