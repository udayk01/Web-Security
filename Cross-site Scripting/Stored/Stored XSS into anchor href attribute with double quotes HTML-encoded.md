![image](https://github.com/udayk01/Web-Security/assets/52235763/4dea5a67-5f58-410e-904e-3ebc661e119e)

## Solution:

> Post a comment with a random alphanumeric string in the "Website" input, then use Burp Suite to intercept the request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0c94a2c2-ca66-4450-bf79-95d704a0e411)

![image](https://github.com/udayk01/Web-Security/assets/52235763/c80949d1-0608-4307-a517-29649ca993ad)

![image](https://github.com/udayk01/Web-Security/assets/52235763/6a2b76e2-43f2-459d-a68a-ee3795c08de5)

> Make a second request in the browser to view the post and use Burp Suite to intercept the request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3db68e39-8bb3-4e50-89b1-8cf26f0f3bbf)

> Observe that the random string in the second Repeater tab has been reflected inside an anchor href attribute.

![image](https://github.com/udayk01/Web-Security/assets/52235763/037fe90a-e0ee-4a44-9fc4-989c0f35f3b9)

> Repeat the process again but this time replace your input with the following payload to inject a JavaScript URL that calls alert:

```javascript:alert(1)```

![image](https://github.com/udayk01/Web-Security/assets/52235763/f1c64283-8283-4615-aafb-ec08846d90cb)

> Verify the technique worked by right-clicking, selecting "Copy URL", and pasting the URL in the browser. Clicking the name above your comment should trigger an alert.

![Screenshot 2024-04-15 184449](https://github.com/udayk01/Web-Security/assets/52235763/4b05856d-236a-4f03-8953-6f452d1b47bf)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/284e7464-6816-4eb7-a06e-3af9f8b23ee2)
