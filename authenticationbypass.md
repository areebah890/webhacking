# 🔑 Authentication Bypass Room – Learnings & Tasks

## 📌 Room Summary
In the **Authentication Bypass** room, I learned how authentication mechanisms can be misconfigured or poorly implemented, and how attackers can exploit these weaknesses to gain unauthorized access. I practiced identifying flaws in login forms, session handling, and logic checks, while also learning defensive techniques to prevent these issues.

---

## 📝 Tasks & What I Learned

### 1. Exploring Login Pages
- **Task:** Identify how the login form works and what parameters are submitted.
- **Learning:** I learned how to intercept requests with Burp Suite, analyze POST/GET parameters, and spot weaknesses such as client-side only validation or hidden fields.

---

### 2. SQL Injection in Authentication
- **Task:** Test login fields for SQL injection payloads.
- **Learning:** I discovered how SQLi can be used to bypass authentication (e.g., `' OR '1'='1`), and I learned how to safely test inputs to avoid false positives.

---

### 3. Default / Weak Credentials
- **Task:** Try common usernames and passwords.
- **Learning:** I realized that many applications are vulnerable simply due to poor credential hygiene (e.g., `admin:admin`, `test:test`). I practiced testing weak or default logins systematically.

---

### 4. Parameter Tampering
- **Task:** Manipulate hidden form fields or parameters in requests.
- **Learning:** I saw how developers sometimes rely on client-side enforcement (like `isAdmin=false`) which can be modified. I learned the importance of always validating authentication logic on the server.

---

### 5. Cookie & Session Manipulation
- **Task:** Inspect and modify authentication cookies or session tokens.
- **Learning:** I learned how weak session implementations (like Base64-encoded usernames) can allow privilege escalation by tampering with values directly.

---

### 6. Capturing the Flag
- **Task:** Successfully bypass authentication to access protected resources.
- **Learning:** I applied the above techniques to gain access, capture the flag, and confirm how an attacker could abuse poor authentication security.

---

## 🛡️ Defensive Takeaways
- Always enforce authentication and authorization on the **server side**.
- Use **prepared statements** to prevent SQLi in login forms.
- Enforce **strong password policies** and disable default accounts.
- Securely generate and validate **session tokens**.
- Never rely on hidden fields or cookies for access control.

---

## 🎯 Key Skills Gained
- Practical use of Burp Suite for login testing.
- Identifying and exploiting SQLi for authentication bypass.
- Manipulating requests, parameters, and cookies to test logic flaws.
- Understanding how real-world authentication systems fail and how to secure them.
