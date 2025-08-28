#  IDOR Room – Learnings & Tasks

##  Room Overview
In the **IDOR** room, I learned how Insecure Direct Object Reference (IDOR) vulnerabilities work and how I can exploit them to access data I shouldn't have access to. The room teaches various IDOR techniques including predictable IDs, encoded or hashed IDs, and identifying vulnerable endpoints.

---

##  Tasks & What I Learned

### 1. Understanding IDOR
- **Task:** Define what IDOR means.
- **Learning:** IDOR stands for **Insecure Direct Object Reference**—it occurs when an application uses user-supplied input (like an ID) to retrieve objects without verifying if the user is permitted to view them :contentReference[oaicite:2]{index=2}.

---

### 2. Identifying a Simple IDOR
- **Task:** Modify object IDs in a URL to access another user's data.
- **Learning:** By changing `user_id=1305` to `user_id=1000`, I was able to see another user's profile, thus confirming an IDOR vulnerability :contentReference[oaicite:3]{index=3}.

---

### 3. Finding IDORs in Encoded IDs
- **Task:** Recognize and manipulate base64-encoded IDs.
- **Learning:** I identified base64-encoded parameters (e.g., ending with `=`) and decoded them using online tools, modified them, then re-encoded and retried to expose data belonging to other users :contentReference[oaicite:4]{index=4}.

---

### 4. Finding IDORs in Hashed IDs
- **Task:** Identify and manipulate hashed IDs like MD5.
- **Learning:** I encountered hashed identifiers (e.g., md5 of `1` → `c4ca4238a0b923820dcc509a6f75849b`). I recognized the hashing method and, using tools like CrackStation or CyberChef, reversed or tested other IDs to exploit potential IDORs :contentReference[oaicite:5]{index=5}.

---

### 5. Finding IDORs in Unpredictable IDs
- **Task:** Use multiple accounts to detect IDOR.
- **Learning:** I created two separate accounts and tried to access data from one while authenticated as the other. Being able to view the other user’s data confirmed an IDOR vulnerability, with just two accounts required :contentReference[oaicite:6]{index=6}.

---

### 6. Locating Potential IDOR Vulnerabilities
- **Task:** Identify where IDORs are likely located in the application.
- **Learning:** I learned to look in several places:
  - URL/query parameters (e.g., `?id=123`)
  - Form data (e.g., hidden `user_id` fields)
  - HTTP Headers or Cookies
  - API endpoints authenticated via tokens or sessions
  :contentReference[oaicite:7]{index=7}

---

### 7. Practical IDOR Exploitation (Lab Example)
- **Task:** Exploit IDOR in a live lab environment.
- **Learning:** In the lab, I observed an API request like:
GET /api/v1/customer?id=1
This returned JSON user details (ID, username, email). By switching the ID to 3, I retrieved another user's data:
- `username`: `john911`
- `email`: `j@fakemail.thm`
:contentReference[oaicite:8]{index=8}

---

##  Key Takeaways

- Before exploitation, always **understand the vulnerability**—what it is and how to recognize it.
- IDOR vulnerabilities can be hidden in various data flows—**URLs, form data, APIs, cookies**.
- Even **encoded or hashed IDs** can be manipulated if not securely validated.
- Always perform **authorization checks on every user-supplied object reference** on the server side.

---

##  Skills and Tools Sharpened

- Recognizing and exploiting **IDORs via URL manipulation, encoding, hashing**.
- Using tools like **base64 decoders, CyberChef, CrackStation**.
- Inspecting **API endpoints and observing JSON responses** using developer tools or Burp.
- Practicing **systematic enumeration with logic** to discover access flaws.
