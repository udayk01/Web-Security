This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. The first step of such an attack is to determine the number of columns that are being returned by the query. You will then use this technique in subsequent labs to construct the full attack.

To solve the lab, determine the number of columns returned by the query by performing a SQL injection UNION attack that returns an additional row containing null values.

<img width="960" alt="image" src="https://github.com/udayk01/Web-Security/assets/52235763/79ae0fe2-22c8-4091-b29c-3a1b8c369a29">

Using Burp Suite to intercept and modify the request that sets the product category filter.

<img width="960" alt="image" src="https://github.com/udayk01/Web-Security/assets/52235763/5fcfc144-8deb-4e82-9b69-aa93fe34584a">

> Initially gave the payload +UNION+SELECT+NULL,NULL-- we got the internal error

<img width="944" alt="image" src="https://github.com/udayk01/Web-Security/assets/52235763/b209f1e6-fb22-487f-a20c-70351f6addbb">

now modified the payload to '+UNION+SELECT+NULL,NULL,NULL--

Only after giving three NULL values the error disappeared, so the number of columns that are being returned by the query is 3.

<img width="960" alt="image" src="https://github.com/udayk01/Web-Security/assets/52235763/b4d7cca6-778d-40f9-9bee-ddfde4c6df38">
