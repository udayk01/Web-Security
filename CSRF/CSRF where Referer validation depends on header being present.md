![image](https://github.com/udayk01/Web-Security/assets/52235763/3feb64b8-736d-4e50-82b2-d5221cb5e132)

## Solution:

> Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d73ed48d-43f9-480c-83ad-b97c7f11560e)

![image](https://github.com/udayk01/Web-Security/assets/52235763/dad1addd-f964-4b9a-9aa6-e505912d0a0a)

> Send the request to Burp Repeater and observe that if you change the domain in the Referer HTTP header then the request is rejected.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e26df36e-6750-4e3f-9c65-cd874066d43f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/92296756-8c0b-41d8-8518-7039dd27b2a3)

> Delete the Referer header entirely and observe that the request is now accepted.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0f935711-0130-4269-b21d-2e52cf4d36f1)

> Create and host a proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab. Include the following HTML to suppress the Referer header:
```
<meta name="referrer" content="no-referrer">
```
![image](https://github.com/udayk01/Web-Security/assets/52235763/d229b401-a7c0-4c39-9566-d95ef4105780)

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9e99de9d-48af-4b0b-bf0c-1326be18ee34)

> Store the exploit, then click "Deliver to victim" to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/62761705-74bf-4563-92e7-c5d598b68d91)
