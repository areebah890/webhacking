# 💻 Command Injection – Task Breakdown

## 📝 Room Overview
The **Command Injection** room taught me how attackers can exploit vulnerabilities that allow arbitrary command execution on the server via user input. I learned how to detect, exploit, and mitigate these vulnerabilities safely.

---

## 📌 Tasks & Learnings

### 1. Understanding Command Injection
- **Task:** Learn what command injection is and why it happens.  
- **Learning:** I learned that command injection occurs when user input is passed unsanitized to system commands. Attackers can execute arbitrary commands on the server, often leading to full compromise.

---

### 2. Identifying Vulnerable Input
- **Task:** Test input fields for command injection vulnerabilities.  
- **Learning:** I explored input parameters in forms or URL parameters to see if the application executed commands on the server. Common tests included appending:
; whoami
&& ls
- **Takeaway:** Vulnerable inputs often include fields that interact with system-level functions (ping, traceroute, file lookups).

---

### 3. Exploiting Simple Command Injection
- **Task:** Execute basic system commands through the vulnerable input.  
- **Learning:** I successfully executed commands like `whoami` or `id` and received output, confirming the vulnerability.  
- **Takeaway:** The server was executing my input directly in the shell, which is a critical security flaw.

---

### 4. Bypassing Input Filters
- **Task:** Test for input sanitization or filtering.  
- **Learning:** Some inputs had simple filters like blocking `;` or `&`. I experimented with alternate payloads, such as `| whoami` or backticks, to bypass restrictions.  
- **Takeaway:** Input sanitization must be robust; otherwise, attackers can still inject commands with creative payloads.

---

### 5. Gaining Deeper Access
- **Task:** Use command injection to explore the system.  
- **Learning:** I enumerated directories, read sensitive files (like `/etc/passwd`), and gathered system information. This demonstrated the potential impact of the vulnerability if exploited in the real world.

---

### 6. Defensive Measures
- **Task:** Learn how to prevent command injection vulnerabilities.  
- **Learning:** Key defenses include:
- Validating and sanitizing all user input.
- Using safe APIs or functions instead of passing user input directly to system commands.
- Employing parameterized functions or libraries that do not invoke the shell.
- Implementing the principle of least privilege for system-level operations.

---

## 🎯 Key Takeaways
- Command injection is a **critical server-side vulnerability** allowing arbitrary system command execution.  
- Testing requires careful input experimentation and understanding of system behavior.  
- Proper **input validation, safe function usage, and least privilege** are essential to prevent exploitation.  
- Documenting both exploitation and mitigation strategies demonstrates strong web security awareness.
# 💻 Command Injection Payload Cheat-Sheet

This cheat-sheet helps test command injection vulnerabilities in web applications safely.

---

## 1. Command Separators

| Separator | Purpose | Example | Effect |
|-----------|---------|---------|--------|
| `;`       | Ends current command, runs next regardless of success | `; whoami` | Executes `whoami` after the original command |
| `&&`      | Runs next command only if previous succeeds | `whoami && ls` | Runs `ls` only if `whoami` succeeds |
| `||`      | Runs next command only if previous fails | `false || echo "failed"` | Executes `echo` if `false` fails |
| `|`       | Pipes output of first command to the second | `whoami | tee out.txt` | Sends `whoami` output to `tee` |

---

## 2. Inline Execution

| Payload | Purpose | Example | Effect |
|---------|---------|---------|--------|
| Backticks | Executes command inside backticks | `` `whoami` `` | Outputs result of `whoami` |
| `$()`      | Executes command inside `$()` | `$(ls)` | Outputs result of `ls` |
| Combination | Chain commands | `whoami && ls; cat /etc/passwd` | Executes `whoami`, then `ls` if successful, then `cat /etc/passwd` |

---

## 3. Target Examples in Labs

| Lab Input | Expected Result |
|-----------|----------------|
| `; whoami` | Prints web server username |
| `; ls` | Lists files in the current directory |
| `whoami && ls` | Prints username, then lists files if `whoami` succeeds |
| `` `id` `` | Shows user and group ID of the web server process |
| `$(cat /etc/passwd)` | Prints the contents of `/etc/passwd` |

---

## 4. Tips for Safe Testing

1. Start simple: `whoami` or `id` to confirm command execution.  
2. Try different separators if input is filtered (`;`, `&&`, `|`, backticks, `$()`).  
3. Consider OS differences:  
   - **Linux/Unix**: `;`, `&&`, `|`, backticks, `$()`  
   - **Windows**: `&`, `&&`, `|`  
4. Avoid destructive commands in labs (e.g., `rm`, `shutdown`). Stick to enumeration.  
5. Document your payloads and effects in your writeups—employers like structured results.  

---

## 5. Example Chain

```bash
; whoami && ls; cat /etc/passwd
; → ends any previous command.

whoami → prints server username.

&& ls → lists files if whoami succeeds.

; cat /etc/passwd → prints password file contents regardless.
