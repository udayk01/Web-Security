![image](https://github.com/udayk01/Web-Security/assets/52235763/58aa20b6-fd7b-49bd-9d3a-dc73a14c93b4)

## Solution: 

> Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/259f104c-36a8-445e-8e00-24a03ce07921)

![image](https://github.com/udayk01/Web-Security/assets/52235763/a2c321f8-3b06-4826-a200-290bed8a5603)

![image](https://github.com/udayk01/Web-Security/assets/52235763/38cf77e1-142f-4282-94dc-1e1f82ac22da)

> Change the URL in the stockApi parameter to ```http://127.0.0.1/``` and observe that the request is blocked.

![image](https://github.com/udayk01/Web-Security/assets/52235763/81cfba9f-2981-44ee-9e38-b058ae800931)

> Bypass the block by changing the URL to:  ```http://127.1/```

![image](https://github.com/udayk01/Web-Security/assets/52235763/63be65f4-c148-49be-ab59-0c691876001d)

> Change the URL to ```http://127.1/admin``` and observe that the URL is blocked again.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0b313489-7d33-4142-b8a1-4e2d1314ae25)

> Obfuscate the "a" by double-URL encoding it to ```%2561``` to access the admin interface and delete the target user.

![Screenshot 2024-04-20 094314](https://github.com/udayk01/Web-Security/assets/52235763/24b0dba5-3073-4677-93b9-e75b0e736a57)

> Delete the target user

![image](https://github.com/udayk01/Web-Security/assets/52235763/78a76221-6bd7-4c08-9294-e58c28d07f46)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/a16740ef-78be-49e7-8d66-48d128506d11)


