![image](https://github.com/udayk01/Web-Security/assets/52235763/74b90245-b15b-4dc2-b3f3-9191c379ad85)

## Solution:

> Log in using the admin credentials.

![image](https://github.com/udayk01/Web-Security/assets/52235763/08872b76-ae22-4c03-8dca-5b137502ffa4)

> Browse to the admin panel, promote carlos, and send the HTTP request to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a7c58fee-c2da-41c5-9f03-7765f2157fac)

>> admin roles

![image](https://github.com/udayk01/Web-Security/assets/52235763/89201685-ca65-42bd-b0c0-4376f280a5df)

> Open a private/incognito browser window, and log in with the non-admin credentials.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0cd4741a-f629-4469-aa11-9244de959fd5)

> Browse to ```/admin-roles?username=carlos&action=upgrade``` and observe that the request is treated as unauthorized due to the absent Referer header.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e7bad0f4-0a47-4038-bb99-7883f0ca3e5a)

![image](https://github.com/udayk01/Web-Security/assets/52235763/d4cabeb8-9a37-4128-b0cc-d6bbc18b3975)

> Copy the non-admin user's session cookie into the existing Burp Repeater request, change the username to yours, and replay it.
 
![image](https://github.com/udayk01/Web-Security/assets/52235763/85fa531b-7f10-419d-b09c-d5cef976c3e9)

>> Wiener cookie: ```pj8dueI7qMZ1HNHMROblYbxcISEmXF1P```

![image](https://github.com/udayk01/Web-Security/assets/52235763/934c9bc2-043b-4f4a-92aa-c7a1acfe5954)

> Lab Solved upgraded wiener to admin

![image](https://github.com/udayk01/Web-Security/assets/52235763/f4226102-9cae-4c47-9a28-01c233236169)
