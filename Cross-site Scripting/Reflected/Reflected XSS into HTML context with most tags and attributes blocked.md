![image](https://github.com/udayk01/Web-Security/assets/52235763/5ad057c9-725c-4340-924a-9c54d7a10176)

## Solution:

> Inject a standard XSS vector, such as:

```<img src=1 onerror=print()>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/3b00d231-8eb7-4b7c-9065-cb6967631f38)

> Observe that this gets blocked. In the next few steps, we'll use use Burp Intruder to test which tags and attributes are being blocked.

![image](https://github.com/udayk01/Web-Security/assets/52235763/37760303-4700-4e90-a99e-ea5c055ee04f)

> Open Burp's browser and use the search function in the lab. Send the resulting request to Burp Intruder.

![image](https://github.com/udayk01/Web-Security/assets/52235763/bc5ada88-5826-47f3-b284-2352715ff0e6)

> In Burp Intruder, in the Positions tab, replace the value of the search term with: <>

![image](https://github.com/udayk01/Web-Security/assets/52235763/17c6619e-90ff-4378-8c78-a09a332e84f6)

> Place the cursor between the angle brackets and click "Add §" twice, to create a payload position. The value of the search term should now look like: ```<§§>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/869d2d53-6a6d-4de3-8541-519f31f18186)

> Visit the XSS cheat sheet and click "Copy tags to clipboard".

![image](https://github.com/udayk01/Web-Security/assets/52235763/e70bcf0a-e195-4d2e-bb4f-b38c7510d9ba)

> In Burp Intruder, in the Payloads tab, click "Paste" to paste the list of tags into the payloads list. Click "Start attack".

![image](https://github.com/udayk01/Web-Security/assets/52235763/eceaad98-d71a-4965-8394-140a802dfda1)

![image](https://github.com/udayk01/Web-Security/assets/52235763/a55fb70a-f0cc-4839-a6dd-bfcc28bf0922)

> When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the body payload, which caused a 200 response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a38cc8d6-21a0-4e00-9239-af59c323a86e)

> Go back to the Positions tab in Burp Intruder and replace your search term with:

```<body%20=1>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/33f51e8a-e82c-449b-87c7-7613b951dde3)

> Place the cursor before the = character and click "Add §" twice, to create a payload position. The value of the search term should now look like:
```<body%20§§=1>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/6373323c-4ffb-44fc-b57d-bf4de50679e2)

> Visit the XSS cheat sheet and click "copy events to clipboard".

![image](https://github.com/udayk01/Web-Security/assets/52235763/915205b9-586b-4ba6-871c-33508e353265)

> In Burp Intruder, in the Payloads tab, click "Clear" to remove the previous payloads. Then click "Paste" to paste the list of attributes into the payloads list. Click "Start attack".

![image](https://github.com/udayk01/Web-Security/assets/52235763/492c2b50-a06e-472c-a819-b57256840462)

> When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the ```onresize``` payload, which caused a 200 response.

![Screenshot 2024-04-17 123658](https://github.com/udayk01/Web-Security/assets/52235763/3fd4a7b5-99ae-404d-8d74-2b4e9a11c82a)

> Go to the exploit server and paste the following code, replacing YOUR-LAB-ID with your lab ID:

```<iframe src="https://YOUR-LAB-ID.web-security-academy.net/?search=%22%3E%3Cbody%20onresize=print()%3E" onload=this.style.width='100px'>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/7a8dd031-9b91-4dc8-af46-7726488c67af)

> Click "Store" and "Deliver exploit to victim".


> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/279bcc7d-7f82-4e35-9a32-4fc608467a75)
