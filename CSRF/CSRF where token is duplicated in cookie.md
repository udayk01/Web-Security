![image](https://github.com/udayk01/Web-Security/assets/52235763/22cd568e-1c2f-4df9-ad8d-c2cebca84362)

## Solution:

>  Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/04d38ef4-f632-4a3d-8929-e6c970824602)

![image](https://github.com/udayk01/Web-Security/assets/52235763/5ebcfbb9-e487-43f0-96eb-1d6d5bcfe9e3)

> Send the request to Burp Repeater and observe that the value of the csrf body parameter is simply being validated by comparing it with the csrf cookie.

![Screenshot 2024-04-19 112221](https://github.com/udayk01/Web-Security/assets/52235763/52c722b1-7436-4664-aafc-d4ebb4fb6024)

![image](https://github.com/udayk01/Web-Security/assets/52235763/8ebe4818-2990-48f3-8d31-242932f56eb7)

> Perform a search, send the resulting request to Burp Repeater, and observe that the search term gets reflected in the Set-Cookie header. Since the search function has no CSRF protection, you can use this to inject cookies into the victim user's browser.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c2a1b33b-cdc1-4851-9cc6-e43f1a927fb6)

> Create a URL that uses this vulnerability to inject a fake csrf cookie into the victim's browser:

```/?search=test%0d%0aSet-Cookie:%20csrf=fake%3b%20SameSite=None```

![Screenshot 2024-04-19 112839](https://github.com/udayk01/Web-Security/assets/52235763/33ea7a3a-803d-4226-963a-c84970c92bb0)

> Create and host a proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab, ensuring that your CSRF token is set to "fake". The exploit should be created from the email change request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ee3c62cc-b692-4775-b06b-0e9bb2d93b78)

> Remove the auto-submit <script> block and instead add the following code to inject the cookie and submit the form:

```<img src="https://YOUR-LAB-ID.web-security-academy.net/?search=test%0d%0aSet-Cookie:%20csrf=fake%3b%20SameSite=None" onerror="document.forms[0].submit();"/>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/2f2ef728-54c6-4ca3-8945-069038bd7afb)

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c05dbf9c-4644-41dd-9ec5-d8417e4ac4a2)

> Store the exploit, then click "Deliver to victim" to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/dd0f8022-fd5a-4b36-9870-3decc76995a1)

