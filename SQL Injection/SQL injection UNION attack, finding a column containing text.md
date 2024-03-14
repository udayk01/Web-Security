This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you first need to determine the number of columns returned by the query. You can do this using a technique you learned in a previous lab. The next step is to identify a column that is compatible with string data.

The lab will provide a random value that you need to make appear within the query results. To solve the lab, perform a SQL injection UNION attack that returns an additional row containing the value provided. This technique helps you determine which columns are compatible with string data.

> *  Using Burp Suite we intercept and modify the request that sets the product category filter.
> * Determine the number of columns that are being returned by the query.
> * Verify that the query is returning three columns, using the following payload in the category parameter
>> '+UNION+SELECT+NULL,NULL,NULL--

We didn't get any error so the query is returning three columns.

Now we will try retrieving the string given in the lab GF7tfy

![image](https://github.com/udayk01/Web-Security/assets/52235763/4e99eece-e101-466d-80eb-dc90f90cedbf)

By replacing the second NULL with the given string we were able to retrieve the given string, so the second column contains the text here.

![image](https://github.com/udayk01/Web-Security/assets/52235763/241d64c5-e21d-46a2-bb8e-674b08f22553)

