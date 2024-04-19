![image](https://github.com/udayk01/Web-Security/assets/52235763/1fdc8672-04c1-4656-a957-eaac090ab20a)

## Solution:

> Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/412c2988-3114-490e-9c41-d26f6b31b209)

![image](https://github.com/udayk01/Web-Security/assets/52235763/e6cd7eb9-bfec-4a5e-af95-a2263d07db23)

> Send the request to Burp Repeater and observe that if you change the value of the csrf parameter then the request is rejected.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1abdecf5-1b54-46bd-9875-4006674caf20)

![image](https://github.com/udayk01/Web-Security/assets/52235763/e559f6bc-1b6f-4f86-a04c-2d381f2a6082)

> Delete the csrf parameter entirely and observe that the request is now accepted.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c391b89a-cbc2-4033-8775-f808428db127)

> If you're using Burp Suite Professional, right-click on the request, and from the context menu select Engagement tools / Generate CSRF PoC. Enable the option to include an auto-submit script and click "Regenerate".

![image](https://github.com/udayk01/Web-Security/assets/52235763/c04e8fb4-8875-467e-b1a8-03a2ffa6a6d7)

> Go to the exploit server, paste your exploit HTML into the "Body" section, and click "Store".

![image](https://github.com/udayk01/Web-Security/assets/52235763/646b02e5-53ee-43cd-83d1-64fff47a14c1)

> To verify if the exploit will work, try it on yourself by clicking "View exploit" and checking the resulting HTTP request and response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e36562db-9877-43e0-87e9-b387812fa6c8)

![image](https://github.com/udayk01/Web-Security/assets/52235763/aaeb6e8d-8d82-4ff3-b4de-0fc003f26e21)

>> Exploit is working

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/52ac1e3d-e401-406b-a281-ca55b0c2cc5d)

> Store the exploit, then click "Deliver to victim" to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/2400fdec-ceae-4841-970c-9cc6981f936f)

