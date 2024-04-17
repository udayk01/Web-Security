![image](https://github.com/udayk01/Web-Security/assets/52235763/2df53c12-974e-441e-93af-6816af41dcd5)

## Solution:

> Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/53dbe3fa-cba1-4fd1-89aa-82abac575acb)

![image](https://github.com/udayk01/Web-Security/assets/52235763/bd3b2557-210e-4985-a212-d808361bff54)

> Observe that the random string has been reflected inside a JavaScript template string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/7140319c-03cc-4aa3-a4e1-5cf64a05cf8c)

> Replace your input with the following payload to execute JavaScript inside the template string:
```${alert(1)}```

![image](https://github.com/udayk01/Web-Security/assets/52235763/75547065-961d-4822-915f-2bfabe88b23e)

> Verify the technique worked by right clicking, selecting "Copy URL", and pasting the URL in the browser. When you load the page it should trigger an alert.

![Screenshot 2024-04-17 143214](https://github.com/udayk01/Web-Security/assets/52235763/44227f4f-f07d-49d5-bdaa-c5ad1c0a0da1)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/b41b30da-d774-4158-8248-3a5f2fe749ef)
