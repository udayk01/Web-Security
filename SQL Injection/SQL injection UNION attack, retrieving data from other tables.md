This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you need to combine some of the techniques you learned in previous labs.

The database contains a different table called users, with columns called username and password.

To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user.

![image](https://github.com/udayk01/Web-Security/assets/52235763/18aeb503-bd3d-4e27-95cd-06332f26d75a)

> First determine the number of columns that are being returned by the query and which columns contain text data.

![image](https://github.com/udayk01/Web-Security/assets/52235763/09abb82c-a246-4696-a5bc-c3957278211a)

> We were able to identify that two columns are being returned by the query which contains the text data. Now we have to retrieve the contents of the users table

![image](https://github.com/udayk01/Web-Security/assets/52235763/dbfc65b6-43db-49be-be89-495a172c0014)

> By using the payload 'UNION+SELECT+username,+password+FROM+users-- we were able to retrieve the user data form the table. Now tried to log in as the administrator using the corresponding password

![image](https://github.com/udayk01/Web-Security/assets/52235763/97b546a3-9e1f-4155-99a4-63e9063b8459)
