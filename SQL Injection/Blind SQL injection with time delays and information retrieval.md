This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and the application does not respond any differently based on whether the query returns any rows or causes an error. However, since the query is executed synchronously, it is possible to trigger conditional time delays to infer information.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ca06a8cf-df66-49ea-9afe-a822d8fc9cae)

![image](https://github.com/udayk01/Web-Security/assets/52235763/231a6fda-b7b3-4610-8b74-2ddc27d4a918)

![image](https://github.com/udayk01/Web-Security/assets/52235763/e517f02f-fb51-4532-9b78-22e1f5f082e6)

![image](https://github.com/udayk01/Web-Security/assets/52235763/0e1de938-018d-4d86-b1dc-71ae5711f4cf)

![image](https://github.com/udayk01/Web-Security/assets/52235763/00b1def0-0e6b-4af3-819b-900d738cac23)

![image](https://github.com/udayk01/Web-Security/assets/52235763/7e705304-ee1c-41a4-9164-fb5f79384e7f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/64bfa202-dd1d-43ec-91cd-2a329de71fa0)

Hence, we can make sure that password length is between 1-22 , characters in length.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c0bb4f38-3172-4866-9657-95a64060afff)

![image](https://github.com/udayk01/Web-Security/assets/52235763/a2492e50-c348-41f7-a70c-5ba504b74408)

![image](https://github.com/udayk01/Web-Security/assets/52235763/26d2f0b9-1361-4a68-935d-08b4aad766c2)

![image](https://github.com/udayk01/Web-Security/assets/52235763/e4e3ba75-f819-4076-bfe5-9c7fa5f5eb45)

From the performed attack we can conclude that the length of the password is 20 characters in length.

![image](https://github.com/udayk01/Web-Security/assets/52235763/20fdda18-3472-424d-81bc-6946830ed3b6)

![image](https://github.com/udayk01/Web-Security/assets/52235763/aa624678-b3d1-4798-aa53-9256e55c73d7)

![image](https://github.com/udayk01/Web-Security/assets/52235763/98bd7466-8777-4564-bce2-85173e70bccd)

After the attack is finished the resulting password is: 7n06x1yt4n356zq1w77t

![image](https://github.com/udayk01/Web-Security/assets/52235763/be9be8ea-cf21-487d-981b-bc01fc9a618c)

![image](https://github.com/udayk01/Web-Security/assets/52235763/cb0b5fc2-2c32-4961-b521-6d2f5ee435cb)




