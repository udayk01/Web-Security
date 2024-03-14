This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

To solve the lab, display the database version string.

> First we need to check how many columns are there.

> Now we check which of the columns returns the text value using payload `UNION+SELECT+'a','b'#

Finally used the payload '+UNION+SELECT+@@version,+NULL# to retrieve the version

![image](https://github.com/udayk01/Web-Security/assets/52235763/8e2d4383-d844-445d-b567-760897fd9640)

![image](https://github.com/udayk01/Web-Security/assets/52235763/1829fc1d-44f8-425c-8583-923091f02865)
