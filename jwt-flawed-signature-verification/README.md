# JWT Authentication Bypass via Flawed Signature Verification

## 🧠 Vulnerability
Broken Authentication / JWT Misconfiguration

## 📌 Description
The application uses JSON Web Tokens (JWT) for session management but fails to properly verify the token signature. Due to this flaw, the server accepts tokens with the `alg: none` algorithm, allowing attackers to bypass signature verification and modify token claims.

## 🎯 Objective
Gain administrator access by modifying the JWT and delete the user "carlos".

## ⚙️ Exploit Steps
1. Login to the application using valid credentials (e.g., wiener:peter)  
2. Intercept the request using Burp Suite  
3. Capture the request: GET /my-account  
4. Identify the JWT in the session cookie  
5. Send the request to Repeater  
6. Decode the JWT using JSON Web Token extension  
7. Modify the payload: {"sub":"administrator"}
In the JSON Web Token extension, go to the **Attack** section, select the **"none" algorithm**, which sets `"alg":"none"` and indicates to the server to accept the token without verifying its signature 

8. Modify the header: {"alg":"none"}  
9. Remove the signature and rebuild the token as: <base64(header)>.<base64(payload)>.  
10. Replace the original JWT with the modified token  
11. Send the request → Response returns 200 OK  
12. Access the admin panel: /admin  
13. Delete the user: /admin/delete?username=carlos  
14. Lab solved  


## 🚨 Impact
Authentication bypass, privilege escalation, full administrative access, and unauthorized user deletion.

## 🛡️ Mitigation
Always verify JWT signatures, reject tokens using `alg:none`, enforce strict algorithm validation.

## 📝 Notes
This vulnerability occurs because the server trusts unsigned JWTs and fails to validate their integrity, allowing attackers to manipulate authentication data.
