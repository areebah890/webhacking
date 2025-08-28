# 🌐 Intro to SSRF – Task Breakdown

## 📝 Room Overview
The **Intro to SSRF** room taught me how Server-Side Request Forgery (SSRF) vulnerabilities work, how to exploit them to access internal resources, and how attackers can abuse them in real-world scenarios like targeting cloud metadata endpoints.

---

## 📌 Tasks & Learnings

### 1. What is SSRF?
- **Task:** Understand the definition and concept of SSRF.
- **Learning:** I learned that SSRF occurs when a server takes user input (like a URL) and uses it to make requests on behalf of the server. If not validated, this allows attackers to force the server to fetch arbitrary URLs.

---

### 2. Basic SSRF Exploitation
- **Task:** Exploit a simple SSRF vulnerability.
- **Learning:** By changing a parameter like:
?url=http://example.com
to:
?url=http://127.0.0.1:8080
I was able to make the server reach into its internal network. This showed me how SSRF can bypass firewalls and expose hidden services.
<img width="754" height="551" alt="image" src="https://github.com/user-attachments/assets/d377c8b3-d35f-464c-add8-9ec852dc8a40" />


---

### 3. Accessing Internal Applications
- **Task:** Use SSRF to explore internal services.
- **Learning:** I discovered how SSRF can be used to enumerate and access **admin panels** or **APIs** that are only bound to localhost or private IP ranges. For example:
?url=http://localhost/admin
gave me access to restricted functionality.

---

### 4. Cloud Metadata SSRF
- **Task:** Exploit SSRF against a cloud metadata endpoint.
- **Learning:** I targeted the AWS metadata service at:
http://169.254.169.254/latest/meta-data/
and retrieved sensitive information like IAM role names and API keys. I understood why this is one of the most dangerous uses of SSRF in cloud environments.

---

### 5. Blind SSRF
- **Task:** Learn to detect and confirm blind SSRF.
- **Learning:** Some SSRF vulnerabilities don’t return responses to the attacker. Instead, I set up an external listener (e.g., Burp Collaborator or DNS logging) and supplied a payload like:
?url=http://myburpcollaborator.net
to confirm the server made the request. This showed me how blind SSRF can still leak information and prove exploitability.

---

### 6. Preventing SSRF
- **Task:** Review defensive best practices.
- **Learning:** I learned that developers can prevent SSRF by:
- Validating and sanitizing all user input.  
- Restricting requests to whitelisted domains/IPs.  
- Blocking access to internal IP ranges (e.g., 127.0.0.1, 169.254.169.254).  
- Monitoring for suspicious outbound traffic.  

---

## 🎯 Key Takeaways
- SSRF lets attackers abuse the **trust of the server** to access otherwise hidden resources.  
- It can be used for **internal service discovery, cloud exploitation, and metadata exposure**.  
- Even **blind SSRF** can be detected using out-of-band interactions.  
- Strong **input validation, whitelisting, and monitoring** are critical to defending against SSRF.  
