This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The SQL query is executed asynchronously and has no effect on the application's response. However, you can trigger out-of-band interactions with an external domain.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a3c69f2f-0968-452a-9f7e-5613d067aef7)

![image](https://github.com/udayk01/Web-Security/assets/52235763/78acdde0-2a91-439f-b0be-225d9e3f29d9)

![image](https://github.com/udayk01/Web-Security/assets/52235763/cd22330d-6a41-42a9-b5b5-e187d87f2be7)


Password:  

![image](https://github.com/udayk01/Web-Security/assets/52235763/8dd0d539-2773-4abc-a7ea-46e2df32a53b)
