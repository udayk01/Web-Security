![image](https://github.com/udayk01/Web-Security/assets/52235763/6f1f043d-c1f2-40e8-b508-7f048f369490)

## Solution:

> Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3d7225e1-1c91-4c09-b0ec-a1091836cfd7)

![image](https://github.com/udayk01/Web-Security/assets/52235763/07783846-2ff7-4318-8451-7d92035a4b95)

> Observe that the random string has been reflected inside a quoted attribute.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a8232cd5-4622-4f10-8a8a-d27773ce1a8d)

> Replace your input with the following payload to escape the quoted attribute and inject an event handler:

```"onmouseover="alert(1)```

![image](https://github.com/udayk01/Web-Security/assets/52235763/6e919c88-72a1-48c5-ace6-9e45cee2faee)

> Verify the technique worked by right-clicking, selecting "Copy URL", and pasting the URL in the browser. When you move the mouse over the injected element it should trigger an alert.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9f37605f-c2b7-4299-8a12-cbdf57139f61)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/d2d14655-29a0-4ef1-a92a-2594db75bc92)
