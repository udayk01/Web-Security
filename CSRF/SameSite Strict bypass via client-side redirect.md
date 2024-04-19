![image](https://github.com/udayk01/Web-Security/assets/52235763/b53ded92-2161-4dff-8b4f-f510746a0a14)

## Solution:

### Study the change email function

> In Burp's browser, log in to your own account and change your email address.

![image](https://github.com/udayk01/Web-Security/assets/52235763/2a6833f3-c04e-46c4-90e9-3119519b6635)

> In Burp, go to the Proxy > HTTP history tab.

> Study the POST /my-account/change-email request and notice that this doesn't contain any unpredictable tokens, so may be vulnerable to CSRF if you can bypass any SameSite cookie restrictions.

![image](https://github.com/udayk01/Web-Security/assets/52235763/61a0395b-7d39-411d-9ab1-48be75607ba6)

> Look at the response to your POST /login request. Notice that the website explicitly specifies SameSite=Strict when setting session cookies. This prevents the browser from including these cookies in cross-site requests.

![image](https://github.com/udayk01/Web-Security/assets/52235763/2abbd26c-0bda-449f-b073-9128a1347e5b)

### Identify a suitable gadget

> In the browser, go to one of the blog posts and post an arbitrary comment. Observe that you're initially sent to a confirmation page at ```/post/comment/confirmation?postId=x``` but, after a few seconds, you're taken back to the blog post.

![image](https://github.com/udayk01/Web-Security/assets/52235763/337a1a8a-eef3-44e8-b530-e46f15b2c84f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/bdb70538-4549-4c2b-ac33-688e12e6e180)

![image](https://github.com/udayk01/Web-Security/assets/52235763/ec2433cd-2952-4649-b4c4-89e4c5e144ac)

> In Burp, go to the proxy history and notice that this redirect is handled client-side using the imported JavaScript file ```/resources/js/commentConfirmationRedirect.js```.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9cfdac3d-334b-4904-8425-5845d6145667)

>> Study the JavaScript and notice that this uses the postId query parameter to dynamically construct the path for the client-side redirect.

> In the proxy history, right-click on the GET /post/comment/confirmation?postId=x request and select Copy URL.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3a90c7a5-7f47-4d10-9b24-5a1416e97a18)

> In the browser, visit this URL, but change the postId parameter to an arbitrary string.

```/post/comment/confirmation?postId=foo```

> Observe that you initially see the post confirmation page before the client-side JavaScript attempts to redirect you to a path containing your injected string, for example, /post/foo.

![Screenshot 2024-04-19 205007](https://github.com/udayk01/Web-Security/assets/52235763/8f704a2d-b2e4-4b6a-a04e-737c7d2c8fd5)

![image](https://github.com/udayk01/Web-Security/assets/52235763/0d1bda7f-5c61-4c79-9937-289245fe11c3)

> Try injecting a path traversal sequence so that the dynamically constructed redirect URL will point to your account page:

```/post/comment/confirmation?postId=1/../../my-account```

![image](https://github.com/udayk01/Web-Security/assets/52235763/ed5a7dd3-5e35-4fe5-9e5f-232707e799fc)

> Observe that the browser normalizes this URL and successfully takes you to your account page. This confirms that you can use the postId parameter to elicit a GET request for an arbitrary endpoint on the target site.

![Screenshot 2024-04-19 205407](https://github.com/udayk01/Web-Security/assets/52235763/8f8acd39-0f91-44a0-8a26-e29a180043b6)

![image](https://github.com/udayk01/Web-Security/assets/52235763/6f0b2b03-6331-4ea9-9d5b-b457255f4b59)

### Bypass the SameSite restrictions

> In the browser, go to the exploit server and create a script that induces the viewer's browser to send the GET request you just tested. The following is one possible approach:
```
<script>
    document.location = "https://YOUR-LAB-ID.web-security-academy.net/post/comment/confirmation?postId=../my-account";
</script>
```

![Screenshot 2024-04-19 205752](https://github.com/udayk01/Web-Security/assets/52235763/5ed2cb9a-1eea-4264-bb69-8b8b2e1e8454)

> Store and view the exploit yourself.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3bdb3eb3-f59b-486f-9d92-bfc16983e8c3)

>> Observe that when the client-side redirect takes place, you still end up on your logged-in account page. This confirms that the browser included your authenticated session cookie in the second request, even though the initial comment-submission request was initiated from an arbitrary external site.

### Craft an exploit
> Send the POST /my-account/change-email request to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3b04ae6b-8c13-44f5-a613-43c7cf573bee)

> In Burp Repeater, right-click on the request and select Change request method. Burp automatically generates an equivalent GET request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/784100d8-53f4-4e69-933b-d38fd4afadfb)

> Send the request. Observe that the endpoint allows you to change your email address using a GET request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/6e9c9515-868c-4592-934e-e3d6743ba5ed)

![image](https://github.com/udayk01/Web-Security/assets/52235763/5a939ce1-fb0c-4c0f-8b0e-4aacc521730e)

> Go back to the exploit server and change the postId parameter in your exploit so that the redirect causes the browser to send the equivalent GET request for changing your email address:
```
<script>
    document.location = "https://YOUR-LAB-ID.web-security-academy.net/post/comment/confirmation?postId=1/../../my-account/change-email?email=pwnednow%40web-security-academy.net%26submit=1";
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/26b4d7da-e7c2-47ea-8453-d084b2c6fc9f)

>> Note that you need to include the submit parameter and URL encode the ampersand delimiter to avoid breaking out of the postId parameter in the initial setup request.

> Test the exploit on yourself and confirm that you have successfully changed your email address.

![image](https://github.com/udayk01/Web-Security/assets/52235763/fe5b8940-7f3d-4bd2-b057-6a8e025d1394)

> Change the email address in your exploit so that it doesn't match your own.

![Screenshot 2024-04-19 210448](https://github.com/udayk01/Web-Security/assets/52235763/0d941b65-1844-409e-95c5-3a7793518013)

> Deliver the exploit to the victim. After a few seconds, the lab is solved.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e7bca3b1-b2ff-4364-9597-f10ffdbd5a65)

