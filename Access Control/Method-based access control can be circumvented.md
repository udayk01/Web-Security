![image](https://github.com/udayk01/Web-Security/assets/52235763/363e13b4-f7d6-46d8-945e-cf6b6d1d7768)

## Solution:

> Log in using the admin credentials.using ```administrator:admin```

![image](https://github.com/udayk01/Web-Security/assets/52235763/352bffdc-6665-4f28-86e3-01f4fa682a61)

> Browse to the admin panel, promote carlos, and send the HTTP request to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3bfab939-ac06-47e3-82d7-20639c46135f)

> capture the request and send it top repeater .

![image](https://github.com/udayk01/Web-Security/assets/52235763/af264684-c26a-4aab-8d7a-4f9dfb71ce6b)

>> We can see that in this POST request we have a parameter called ```username=carlos & action=upgrade``` The above request upgrades the privileges of carlos user

> log in with the non-admin credentials ```wiener:peter```

![image](https://github.com/udayk01/Web-Security/assets/52235763/73c77240-ef48-43c3-b7ae-e4ac10f0bc0b)

> Our goal is to exploit the flawed access controls to promote ourself (wiener) to become an administrator.

> So we can try to perform the role changing action as wiener by pasting the cookie value of wiener in the request made by admin to change the privileges !

> Cookie of admin - ```jIxtEgW4qdP7w9Gn6le8M428HmvPdN1a``` Cookie of wiener - ```xXAoAVeAZE6Qiql9M1kT4bm3Z9XHTD77```

> So we change the cookie value of admin with wiener & send the request, we get the response as 401 - Unauthorized

![image](https://github.com/udayk01/Web-Security/assets/52235763/0c69cdc2-61a3-4d8f-95fd-1a681a9e1d7e)

> Since this lab is based on Method-Based-Access control bypass, we can try to change the request from POST to GET. We can do this by Right click on request -> Click Change request method option.

> Now it changes to a GET request-

![image](https://github.com/udayk01/Web-Security/assets/52235763/a1a1cf5f-09ee-4c1b-801c-a3656cc61380)

> Lab solved Wiener became an Admin

![image](https://github.com/udayk01/Web-Security/assets/52235763/99454f1b-3265-4899-9b5f-a0502d8fbb5b)

