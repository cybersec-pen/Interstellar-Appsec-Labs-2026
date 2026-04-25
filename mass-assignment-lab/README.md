# Exploiting a Mass Assignment Vulnerability

## 🧠 Vulnerability
Mass Assignment / Broken Object Property Control

---

## 📌 Description
The application accepts user-controlled parameters without proper validation or restriction.  
Sensitive fields (such as discount/offer percentage) can be modified by the client, allowing attackers to manipulate server-side logic.

---

## 🎯 Objective
Exploit mass assignment to manipulate pricing and place an order without paying.

---

## ⚙️ Exploit Steps

1. Login to the application using valid credentials  

2. Intercept traffic using Burp Suite  

3. Navigate to homepage  
   - Observe credit balance is zero  
   - Add 5 leather jackets to cart  

4. Intercept GET request:
5. 
5. Send request to Repeater  

6. Analyze response:
- Product details  
- Price  
- Quantity  
- Offer/discount percentage  

7. Proceed to checkout  

8. Intercept POST request:
9. 
9. Modify request:
- Copy discount/offer parameter from GET response  
- Add it into POST request  
- Change value:
  ```
  "offer": 100
  ```

10. Send modified request  

11. Observe order is placed successfully without payment  

## 🚨 Impact
- Unauthorized price manipulation  
- Free purchases / financial loss  
- Business logic abuse  
- Data integrity compromise  

---

## 🛡️ Mitigation
- Use allow-listing for accepted parameters  
- Ignore client-side sensitive fields (price, discount, roles)  
- Enforce server-side validation  
- Implement proper object mapping controls  

---

## 📝 Notes
This vulnerability occurs when the backend blindly binds user input to internal object properties without filtering sensitive attributes.
