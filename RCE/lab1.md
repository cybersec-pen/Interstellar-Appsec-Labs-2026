# 🚨 Remote Code Execution via File Upload

## 📌 Overview
Application allows uploading files without proper validation, leading to Remote Code Execution.

---

## 🧪 Exploitation
- Logged in and intercepted request using Burp Suite  
- Uploaded a malicious PHP file (web shell)  
- Sent request to Repeater and analyzed response  
- Accessed uploaded file via modified GET request  
- Executed file and retrieved solution token  

---

## 🔓 Impact
- Remote Code Execution on server  
- Access to sensitive data  

---

