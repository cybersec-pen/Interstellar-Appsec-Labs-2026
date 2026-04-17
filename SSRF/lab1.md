# 🔓 SSRF – Accessing Local Server (Admin Panel)

## 📌 Vulnerability
Server-Side Request Forgery (SSRF)

## 🧠 Main Idea
The application fetches data from a user-supplied URL without proper validation.  
By modifying the URL, an attacker can make the server send requests to internal services (localhost), which are not accessible externally.

---

## ⚙️ Steps to Reproduce
1. Opened the lab application in browser  
2. Intercepted the request using Burp Suite  
3. Navigated to any product page  
4. Clicked on "Check Stock" functionality  
5. Captured the request containing the `stockApi` parameter  
6. Sent the request to Burp Repeater  
7. Modified the `stockApi` URL to point to internal admin endpoint:  
   `http://localhost/admin`  
8. Sent the request  

---

## 💥 Result
- Successfully accessed the internal admin panel  
- Performed unauthorized action (deleted user "carlos")  

---

## ⚠️ Impact
- Access to internal services (localhost / internal network)  
- Unauthorized admin actions  
- Potential full system compromise  

---

## 🛡️ Recommendation
- Validate and whitelist allowed URLs  
- Block requests to internal IP ranges (127.0.0.1, localhost)  
- Disable unnecessary internal endpoints  
