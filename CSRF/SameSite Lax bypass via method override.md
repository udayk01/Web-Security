![image](https://github.com/udayk01/Web-Security/assets/52235763/96227870-af91-43a3-a3a5-2e53b6aadf44)

## Solution:

### Study the change email function

> In Burp's browser, log in to your own account and change your email address.

![image](https://github.com/udayk01/Web-Security/assets/52235763/70ece721-447d-484b-a21f-668741c01a1f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/1a88e201-b423-4d5d-82f2-905c90de2ddf)

> In Burp, go to the Proxy > HTTP history tab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b48517ee-8763-44d8-9112-a41d063068cd)

> Study the POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass the SameSite cookie restrictions.

![image](https://github.com/udayk01/Web-Security/assets/52235763/13690d24-492a-43ff-9f7c-b60b5f8cabd2)

> Look at the response to your POST /login request. Notice that the website doesn't explicitly specify any SameSite restrictions when setting session cookies. As a result, the browser will use the default Lax restriction level.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1b472abb-ddcd-4608-8a19-8583d83af7ab)

> Recognize that this means the session cookie will be sent in cross-site GET requests, as long as they involve a top-level navigation.

### Bypass the SameSite restrictions

> Send the POST /my-account/change-email request to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/436c3910-fe39-4a36-a7b1-5062c1ede19e)

> In Burp Repeater, right-click on the request and select Change request method. Burp automatically generates an equivalent GET request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/af1fd89d-0d97-4c2b-bb35-73774c2021ee)

>> Send the request. Observe that the endpoint only allows POST requests.

> Try overriding the method by adding the _method parameter to the query string:

```GET /my-account/change-email?email=foo%40web-security-academy.net&_method=POST HTTP/1.1```

>> Send the request. Observe that this seems to have been accepted by the server.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1310715e-7dcd-40c6-ac3b-2f3789a09f0c)

> In the browser, go to your account page and confirm that your email address has changed.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0197ded1-89d3-4877-a1c3-4d5b41e6df50)

### Craft an exploit

> In the browser, go to the exploit server.

![image](https://github.com/udayk01/Web-Security/assets/52235763/56d98f52-06b7-4d17-8dc2-d6982d5a51ae)

> In the Body section, create an HTML/JavaScript payload that induces the viewer's browser to issue the malicious GET request. Remember that this must cause a top-level navigation in order for the session cookie to be included. The following is one possible approach:
```
<script>
    document.location = "https://YOUR-LAB-ID.web-security-academy.net/my-account/change-email?email=pwned@web-security-academy.net&_method=POST";
</script>
```
>> Store and view the exploit yourself. Confirm that this has successfully changed your email address on the target site.

![Screenshot 2024-04-19 202921](https://github.com/udayk01/Web-Security/assets/52235763/635901f1-25fe-4b2d-a7ec-c5de818f8a30)

![image](https://github.com/udayk01/Web-Security/assets/52235763/b2d2eeb7-f251-49b5-8bf0-4c88aaee439c)

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c20ad8cd-85b9-45a9-9f39-2941e82d0362)

> Deliver the exploit to the victim to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/221b1627-f26f-40fa-b59c-ea613b035c8e)

