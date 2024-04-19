![image](https://github.com/udayk01/Web-Security/assets/52235763/0d2a5f94-6eb9-4e96-b454-d5e8cc84067a)

## Solution:

> Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/86bbb68f-3057-4750-84e6-99aa1f57f0c5)

![image](https://github.com/udayk01/Web-Security/assets/52235763/7059eb39-1a6c-41a6-bea5-378c6792c74a)

> Send the request to Burp Repeater and observe that changing the session cookie logs you out, but changing the csrfKey cookie merely results in the CSRF token being rejected. This suggests that the csrfKey cookie may not be strictly tied to the session.

>> Changing session cookie

![image](https://github.com/udayk01/Web-Security/assets/52235763/bb0648bc-b440-4a67-96c9-8ae0bbf64c05)

>> Changing CSRF token

![image](https://github.com/udayk01/Web-Security/assets/52235763/502a4717-e35c-4bd1-b663-a71c8c51cf0f)

> Open a private/incognito browser window, log in to your other account, and send a fresh update email request into Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/719bb4f6-b6ad-400a-848f-23b295c6039c)

![image](https://github.com/udayk01/Web-Security/assets/52235763/1e684043-d0da-4257-9fa6-8a82f451c11c)

> Observe that if you swap the csrfKey cookie and csrf parameter from the first account to the second account, the request is accepted.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3bf6af01-6f96-4671-99e8-67c3746361fa)

> Close the Repeater tab and incognito browser.

> Back in the original browser, perform a search, send the resulting request to Burp Repeater, and observe that the search term gets reflected in the Set-Cookie header. Since the search function has no CSRF protection, you can use this to inject cookies into the victim user's browser.

![image](https://github.com/udayk01/Web-Security/assets/52235763/26efc870-241f-4de0-92f0-13e03ffd90ad)

> Create a URL that uses this vulnerability to inject your csrfKey cookie into the victim's browser:

```/?search=test%0d%0aSet-Cookie:%20csrfKey=GtchtSSOfcPD5FoEbPlUTLoBqsF3xX1O%3b%20SameSite=None```

![image](https://github.com/udayk01/Web-Security/assets/52235763/dee803b1-cb05-42da-b923-8912c32a8787)

> Create and host a proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab, ensuring that you include your CSRF token. The exploit should be created from the email change request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/863f8969-734f-4437-80f6-7f0904c44312)

![image](https://github.com/udayk01/Web-Security/assets/52235763/dac67c96-1b82-4ab5-b9ff-ad606197bf9c)

> Open engagemet tools and create csrf poc

![image](https://github.com/udayk01/Web-Security/assets/52235763/a7eed662-5d85-4b26-be0e-10d99a140dd4)

> Remove the auto-submit <script> block, and instead add the following code to inject the cookie:

```<img src="https://YOUR-LAB-ID.web-security-academy.net/?search=test%0d%0aSet-Cookie:%20csrfKey=YOUR-KEY%3b%20SameSite=None" onerror="document.forms[0].submit()">```

![Screenshot 2024-04-19 111109](https://github.com/udayk01/Web-Security/assets/52235763/ba38dd1c-41a1-47d9-8a97-68d2b5f9ab25)

> Change the email address of the exploit

![image](https://github.com/udayk01/Web-Security/assets/52235763/0c49e233-1074-4248-bb11-077623be5d9a)

> Store the exploit, then click "Deliver to victim" to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/8c41d61d-f754-4954-b006-754c96ef65d0)
