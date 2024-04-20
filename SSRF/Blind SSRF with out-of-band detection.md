![image](https://github.com/udayk01/Web-Security/assets/52235763/7e03666e-aa46-47c4-bdb4-bb5cd387603c)

## Solution:

> Visit a product, intercept the request in Burp Suite, and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/8f29c125-d610-42f6-a671-b4780b9ac422)

![image](https://github.com/udayk01/Web-Security/assets/52235763/1e7d1ff9-0930-44c7-a562-df5afd7f5a73)

> Go to the Repeater tab. Select the Referer header, right-click and select "Insert Collaborator Payload" to replace the original domain with a Burp Collaborator generated domain. Send the request.

![Screenshot 2024-04-20 093015](https://github.com/udayk01/Web-Security/assets/52235763/151f5437-a6e6-4345-9070-5163c0adaf8b)

> Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again, since the server-side command is executed asynchronously.

![image](https://github.com/udayk01/Web-Security/assets/52235763/022643ed-59da-4bda-8f18-2cc7983c7139)

>> You should see some DNS and HTTP interactions that were initiated by the application as the result of your payload.

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/0e142908-d5f2-400b-924f-be3600604719)
