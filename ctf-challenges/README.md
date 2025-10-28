# Discretionary Access Control & CTF Challenges

**Focus:** Web security, privilege escalation, authentication bypass

## Overview
Multi-level Capture The Flag challenges testing various security concepts including access control, steganography, and system exploitation.

## Challenges Completed

### 1. HTML/JS Inspection & DOM Manipulation
**Objective:** Find hidden flags in client-side code

**Techniques:**
- Browser DevTools inspection
- JavaScript console analysis
- DOM tree traversal
- Hidden element discovery

**Key Learning:** Never trust client-side security

---

### 2. Steganography
**Objective:** Extract hidden data from images and files

**Approach:**
```bash
# Check file metadata
exiftool image.jpg

# Extract hidden data
steghide extract -sf image.jpg

# Analyze file structure
hexdump -C file.png | less
```

**Key Learning:** Data can be hidden in plain sight within file structures

---

### 3. Cron Job Analysis for Privilege Escalation
**Objective:** Exploit misconfigured cron jobs to gain elevated privileges

**Methodology:**
1. Identified scheduled tasks
```bash
   cat /etc/crontab
   crontab -l
```

2. Analyzed file permissions
```bash
   ls -la /etc/cron.d/
```

3. Exploited writable scripts run as root
4. Chained vulnerabilities for privilege escalation

**Key Learning:** System administrators must carefully audit scheduled tasks

---

### 4. Broken Access Control
**Objective:** Bypass authorization checks

**Techniques:**
- URL manipulation
- Parameter tampering
- Direct object references
- Session token analysis

**Example Scenario:**
```
Original: /user/profile?id=123
Exploit: /user/profile?id=1 (access admin account)
```

**Key Learning:** Implement server-side authorization checks

---

### 5. Authentication Bypass
**Objective:** Circumvent login mechanisms

**Methods Explored:**
- SQL injection in login forms
- Cookie manipulation
- Session fixation
- Default credentials
- Logic flaws in authentication flow

**Key Learning:** Authentication must be robust at every layer

---

### 6. Vulnerability Chaining
**Objective:** Combine multiple small vulnerabilities for system compromise

**Example Chain:**
1. Information disclosure → leaked user enumeration
2. Weak session management → session hijacking
3. Privilege escalation → admin access
4. Remote code execution → full system compromise

**Key Learning:** Defense-in-depth is critical; one weakness can cascade

---

## Tools & Techniques

### Tools Used
- **Browser DevTools** - Client-side analysis
- **Burp Suite** - Web proxy and manipulation
- **curl/wget** - HTTP request crafting
- **grep/sed/awk** - Log analysis
- **steghide** - Steganography extraction
- **Linux CLI** - System exploration

### Skills Demonstrated
- Web application security testing
- Privilege escalation techniques
- Reverse engineering
- Critical thinking and creative problem-solving
- Documentation of findings

## Security Principles Learned

1. **Defense in Depth**: Multiple layers of security are essential
2. **Least Privilege**: Users should have minimum necessary permissions
3. **Input Validation**: Never trust user input
4. **Security Through Obscurity Fails**: Hiding mechanisms doesn't make them secure
5. **Assume Breach**: Design systems expecting compromise

## Ethical Framework

All challenges completed within:
- Authorized academic environment
- Controlled lab infrastructure
- Educational objectives
- Responsible disclosure principles

Knowledge gained used solely for defensive security purposes.

---

**Skills:** Web security, Linux, privilege escalation, CTF methodology, penetration testing