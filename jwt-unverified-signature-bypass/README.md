# JWT Authentication Bypass via Unverified Signature

## 🧠 Vulnerability
Broken Authentication / JWT Misconfiguration

---

## 📌 Description
The application uses JWT for session management but fails to verify the signature of the token.  
This allows an attacker to modify the token payload and escalate privileges without possessing the signing key.

---

## 🎯 Objective
Modify the JWT to gain administrator access and delete the user "carlos".

---

## ⚙️ Exploit Steps

1. Login to the application using valid credentials  

2. Intercept request using Burp Suite  

3. Capture the request:
   
4. Identify the session JWT in cookies  

5. Send the request to Repeater  

6. Decode the JWT using JSON Web Token extension  

7. Modify payload:
   "sub": "wiener"
   ➝ change to:
   "sub": "administrator"
   Access admin panel:
   Delete user:
   /admin/delete?username=carlos

   💥 Proof of Concept
Original JWT

Modified JWT

Admin Access

🚨 Impact
Authentication bypass
Privilege escalation
Full account takeover
Unauthorized administrative actions

🛡️ Mitigation
Always verify JWT signatures
Reject tokens with alg: none
Enforce strict algorithm validation
