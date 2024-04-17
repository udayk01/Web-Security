![image](https://github.com/udayk01/Web-Security/assets/52235763/7e3b09dc-ba9b-4fa8-a48f-17c0ad022ef7)

## Solution:

> Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/4ca372db-da2f-469e-acba-44ed02f2a714)

![image](https://github.com/udayk01/Web-Security/assets/52235763/d5521c75-91b0-4612-86f4-0b5e51b3d7d4)

> Observe that the random string has been reflected inside a JavaScript string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b2d96526-ada7-413f-ab69-99bdc91564e8)

> Try sending the payload ```test'payload``` and observe that your single quote gets backslash-escaped, preventing you from breaking out of the string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1d837061-7197-43b7-9f80-3628ba1fa80e)

> Replace your input with the following payload to break out of the script block and inject a new script:

```</script><script>alert(1)</script>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/6d0b72ba-55c9-4d87-a220-d9213ec399c3)

> Verify the technique worked by right clicking, selecting "Copy URL", and pasting the URL in the browser. When you load the page it should trigger an alert.

![Screenshot 2024-04-17 133726](https://github.com/udayk01/Web-Security/assets/52235763/aaafcffa-06e3-4ed3-95fe-e5c7a7e1f8ee)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/c1db16f3-53e5-4e5d-b195-6993de830f2a)
