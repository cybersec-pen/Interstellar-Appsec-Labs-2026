SQL Injection vulnerability lab demonstrating data retrieval via manipulated WHERE clause using Burp Suite. 📸 Proof of Concept (PoC) 🔓 SQL Injection in WHERE Clause – Hidden Data Retrieval

(PortSwigger Web Security Academy Lab)

⚙️ Description

This issue was identified in a SQL Injection lab where the application fails to properly sanitize input in the WHERE clause, allowing manipulation of SQL queries.

💥 Exploitation 🔹 Step 1: Intercept Request

Request was intercepted using Burp Suite Proxy while accessing the gift/product section.

🔹 Step 2: Modify Parameter

The vulnerable parameter was modified with the payload:

OR 1=1--

🔹 Step 3: Send Request

The modified request was forwarded using Burp Repeater.

📌 Result Application returned hidden / additional records SQL filtering logic was successfully bypassed

