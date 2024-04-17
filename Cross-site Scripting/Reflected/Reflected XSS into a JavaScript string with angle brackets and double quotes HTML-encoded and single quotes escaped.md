![image](https://github.com/udayk01/Web-Security/assets/52235763/7209db4d-df73-42c2-ab26-7e88cda1db89)

## Solution:

> Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ac197c75-a26a-4066-be03-b1fc830e0c69)

![image](https://github.com/udayk01/Web-Security/assets/52235763/45c10209-7148-4059-9bae-8f9a5c706e04)

> Observe that the random string has been reflected inside a JavaScript string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/32520835-1fb0-46f7-953e-f61cf1aea2a1)

> Try sending the payload ```test'payload``` and observe that your single quote gets backslash-escaped, preventing you from breaking out of the string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/09fbe0c7-43c5-494d-881a-edf1634a98bb)

> Try sending the payload test\payload and observe that your backslash doesn't get escaped.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a2d74c54-5729-4a79-abba-9959d1c50bc3)

> Replace your input with the following payload to break out of the JavaScript string and inject an alert:

```\'-alert(1)//```

![image](https://github.com/udayk01/Web-Security/assets/52235763/5b43abb8-ee89-4d0a-8095-7ec6b59a0393)

> Verify the technique worked by right clicking, selecting "Copy URL", and pasting the URL in the browser. When you load the page it should trigger an alert.

![Screenshot 2024-04-17 134833](https://github.com/udayk01/Web-Security/assets/52235763/b62b3df8-ea1c-4781-8d03-bed54cdee39d)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/3e415d7f-11de-4a47-83fb-f818a047b83a)

