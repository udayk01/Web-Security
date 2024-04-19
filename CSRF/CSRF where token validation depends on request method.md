![image](https://github.com/udayk01/Web-Security/assets/52235763/fc8591a2-289b-45e1-a807-8a14064ff8b8)

## Solution:

> Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1bcaac1b-3c49-4fe7-a2aa-82fbde62bae7)

> Send the request to Burp Repeater and observe that if you change the value of the csrf parameter then the request is rejected.

![image](https://github.com/udayk01/Web-Security/assets/52235763/28c1bd8e-8f33-45c8-b869-29d091e60583)

![image](https://github.com/udayk01/Web-Security/assets/52235763/f5fc02d7-b82f-4a39-bcef-e50490f95298)

> Use "Change request method" on the context menu to convert it into a GET request and observe that the CSRF token is no longer verified.

![image](https://github.com/udayk01/Web-Security/assets/52235763/16197086-1fbe-41a2-a6c0-59929db744a6)

> If you're using Burp Suite Professional, right-click on the request, and from the context menu select Engagement tools / Generate CSRF PoC. Enable the option to include an auto-submit script and click "Regenerate".

![image](https://github.com/udayk01/Web-Security/assets/52235763/298de1c5-0fec-4dd1-b6d0-10d13e986fbb)

> Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".

![image](https://github.com/udayk01/Web-Security/assets/52235763/82acb521-2ddd-4e8d-bfb3-ab51966b3ebc)

> To verify if the exploit will work, try it on yourself by clicking "View exploit" and checking the resulting HTTP request and response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/80ef3c59-49fd-4b6c-8839-ed5de875ad72)

>> Exploit is working

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/5624ee50-c077-43ee-b3e2-342962ef0d5f)

> Click deliver to the victim to Solve the lab

![image](https://github.com/udayk01/Web-Security/assets/52235763/a8f4266e-67bb-4d59-983c-407ec55c6d1b)

