# Stored XSS into HTML Context (No Encoding)

## 🧠 Vulnerability
Stored Cross-Site Scripting (XSS)

## 📌 Description
The application stores user input without sanitization or encoding. This allows attackers to inject malicious scripts that execute in other users' browsers.

---

## ⚙️ Exploit Steps

1. Login to the application
2. Navigate to homepage
3. Open any blog post
4. Enter payload in comment field:

   <script>alert('XSS')</script>

5. Enter name and email
6. Click **Post Comment**
7. Reload page → Payload executes

---

## 💥 Impact
- Session hijacking  
- Credential theft  
- Account takeover  
- Malicious actions as victim  

---

## 🛡️ Mitigation
- Input validation
- Output encoding
- Use Content Security Policy (CSP)

---
