![image](https://github.com/udayk01/Web-Security/assets/52235763/fdb1899d-56b7-4fb3-98a6-9c829dcba8e1)

## Solution:

> Home Page

![image](https://github.com/udayk01/Web-Security/assets/52235763/5c4d250c-c128-437c-8ec3-bb63b3aa269b)

> We need to get admin privilage to delete the user carlos. So first we try /admin and observe that you can't access the admin panel

![image](https://github.com/udayk01/Web-Security/assets/52235763/e8b76594-7162-4613-a8c2-eeddf94265f4)

> It says we can view only if we are admin. We have a login credential wiener:peter lets try with that.

![image](https://github.com/udayk01/Web-Security/assets/52235763/50bdf0ed-4040-471e-9bd0-fc0039f26098)

>> Logged in but admin panel is not visible.

> So we need to check the request we made while login.

> In POST request-

![image](https://github.com/udayk01/Web-Security/assets/52235763/814c51ad-3206-4f42-b28a-9ed564837962)

>> It is saying adimn= false thats why we are not getting admin panel.

> We will change this to True in GET request and try to get admin panel.

> In GET request-

![image](https://github.com/udayk01/Web-Security/assets/52235763/ed4c621b-11d6-4127-be09-d8317a95f74a)

> We searched but the admin panel is not given, now we will send the get request to repeter and change the Admin=true.

![image](https://github.com/udayk01/Web-Security/assets/52235763/41a5b024-cb98-4181-b2f4-c7597f16104e)

> Now admin panel is visble now send this request and access the admin privilage.

> For that select inspect go to application then go to cookie and change from admin= false to admin= true .

![image](https://github.com/udayk01/Web-Security/assets/52235763/727fa280-df2e-4262-8f1a-133b4cd07883)

![image](https://github.com/udayk01/Web-Security/assets/52235763/9448c764-228e-4342-8cc4-a9ec12fefb6d)

> Admin panel is now visible

![image](https://github.com/udayk01/Web-Security/assets/52235763/3380f9aa-bb95-47b9-a2e4-d00c22d5227f)

> Click on the Admin Panel

![image](https://github.com/udayk01/Web-Security/assets/52235763/593d8d2b-6d0d-44c2-9620-66fa3fd6066a)

> Delete the user carlos

![image](https://github.com/udayk01/Web-Security/assets/52235763/8247d953-f024-49fa-a630-4b4b7c8098b5)
