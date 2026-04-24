# 2FA Simple Bypass

## 🧠 Vulnerability
Broken Authentication / 2FA Bypass

---

## 📌 Description
The application does not properly enforce two-factor authentication (2FA).  
Due to improper session handling, it allows access to a victim account without completing the 2FA verification step.

---

## 🎯 Objective
Demonstrate how an attacker can bypass 2FA and gain unauthorized access.

---

## ⚙️ Exploit Steps

1. Login using attacker account  
2. Complete 2FA successfully  

3. Go back to login page  

4. Login using victim credentials  
5. Application asks for 2FA code  

6. Do NOT enter the code  
7. Refresh the page or navigate back  

8. Access account/dashboard  

9. Observe that victim account is accessible without 2FA  

---

## 🚨 Impact
- Account takeover  
- Authentication bypass  
- Unauthorized access  

---

## 🛡️ Mitigation
- Bind 2FA to session properly  
- Invalidate sessions on account switch  
- Enforce 2FA before granting access  

---
