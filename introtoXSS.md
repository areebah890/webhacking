# 🌐 Intro to Cross-Site Scripting (XSS) – Summary

## 📝 Room Overview
In the **Intro to XSS** room, I learned about **Cross-Site Scripting (XSS)** vulnerabilities, how they occur when an application improperly handles user-supplied input, and how attackers can exploit them to control other visitors’ browsers. The room introduced both **reflected** and **stored XSS**, and showed practical ways to identify and exploit these vulnerabilities safely.

---

## 🔍 What I Learned

### 1. Understanding XSS
- **Lesson:** XSS occurs when user input is injected into a web page without proper sanitization.  
- **Example:** Entering `<script>alert('XSS')</script>` in a search bar or comment field can execute code in the browser.  
- **Takeaway:** XSS is a client-side vulnerability that can steal cookies, hijack sessions, or redirect users.

---

### 2. Reflected XSS
- **Lesson:** I learned that reflected XSS appears in the response immediately after a user submits input.  
- **Example:** A search field returns my input in the URL and page content without escaping it.  
- **Takeaway:** Reflected XSS is often used in phishing attacks or malicious links.

---

### 3. Stored XSS
- **Lesson:** Stored XSS occurs when malicious input is saved on the server and delivered to all users viewing the page.  
- **Example:** Posting `<script>alert('XSS')</script>` in a comment section triggers the script for anyone visiting that page.  
- **Takeaway:** Stored XSS is more dangerous than reflected XSS because it affects multiple users and persists.

---

### 4. Defensive Awareness
- **Key Lessons:**  
  - Always sanitize and encode user input before rendering it on a page.  
  - Use frameworks that automatically escape content (e.g., React, Angular).  
  - Implement Content Security Policy (CSP) headers to mitigate XSS impact.  
  - Validate input both on the client and server side.

---

## 🎯 Key Skills Gained
- Detecting reflected and stored XSS vulnerabilities in web applications.  
- Safely testing XSS using input fields, query parameters, and comment sections.  
- Understanding the consequences of XSS (cookie theft, session hijacking, browser manipulation).  
- Applying defensive techniques like input sanitization, output encoding, and CSP headers.
