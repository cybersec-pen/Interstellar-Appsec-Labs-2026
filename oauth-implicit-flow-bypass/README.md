# Authentication Bypass via OAuth Implicit Flow

## 🧠 Vulnerability
Broken Authentication / OAuth Misconfiguration

---

## 📌 Description
The application incorrectly implements the OAuth implicit flow and fails to properly validate authentication tokens.  
As a result, an attacker can gain access to another user's account by manipulating authentication requests without needing the victim’s password.

---

## 🎯 Objective
Exploit OAuth misconfiguration to bypass authentication and access another user account.

---

## ⚙️ Exploit Steps

1. Login to the application using your own account  

2. Open Burp Suite and enable interception  

3. Perform OAuth login flow  

4. Capture the authentication request  

5. Send the request to Repeater  

6. Analyze the request parameters:
   - email  
   - username  
   - access_token / id_token (if present)  

7. Modify the request:
   - Replace your email/username with victim's email  
   - Remove or tamper with authentication validation fields  

8. Send modified request  

9. Observe that authentication succeeds without requiring the victim’s password  

10. Access to victim account is granted  

## 🚨 Impact
- Full account takeover  
- Authentication bypass  
- Unauthorized access to user data  
- Loss of user trust and security  

---

## 🛡️ Mitigation
- Properly validate OAuth tokens (signature, issuer, audience)  
- Do not trust client-controlled identity parameters  
- Use secure OAuth flows (Authorization Code Flow with PKCE)  
- Bind authentication strictly to verified tokens  

---

## 📝 Notes
This vulnerability occurs due to improper validation in OAuth implicit flow, allowing attackers to impersonate other users.
