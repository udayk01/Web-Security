![image](https://github.com/udayk01/Web-Security/assets/52235763/95b18a28-ef32-4b35-812d-80b1ee226d89)

## Solution:

> Post a comment with a random alphanumeric string in the "Website" input, then use Burp Suite to intercept the request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b63462cb-05e3-415a-9ff0-e94045ec67d4)

![image](https://github.com/udayk01/Web-Security/assets/52235763/29607c34-ecb0-48fa-8850-4bc47b02e937)

> Make a second request in the browser to view the post and use Burp Suite to intercept the request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/f9119a57-029e-4fc8-a9a4-c872e818bb1e)

> Observe that the random string in the second Repeater tab has been reflected inside an ```onclick``` event handler attribute.

![image](https://github.com/udayk01/Web-Security/assets/52235763/60261551-ce6a-4831-beac-204f8468e16c)

> Repeat the process again but this time modify your input to inject a JavaScript URL that calls alert, using the following payload:

```http://foo?&apos;-alert(1)-&apos;```

![image](https://github.com/udayk01/Web-Security/assets/52235763/d9931aad-d25c-4b6a-9003-1e8a518cb08a)

> Click on the newly posted comment

![image](https://github.com/udayk01/Web-Security/assets/52235763/8e9cf5de-f15c-4ffa-ad5f-3bb4001cf0e6)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/e6329b90-9c5d-4269-849f-30d5088b931b)

