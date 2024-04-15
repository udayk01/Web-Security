![image](https://github.com/udayk01/Web-Security/assets/52235763/213f0bfc-f96b-40af-bc20-f7c3e40ecccf)

## Solution:

> Submit a random alphanumeric string in the search box, then use Burp Suite to intercept the search request and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/437ce965-4b1b-40e9-bd50-85b4df678091)

> Observe that the random string has been reflected inside a JavaScript string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/396dd139-65ac-4dab-ab37-4c9c7ebf29fc)

> Replace your input with the following payload to break out of the JavaScript string and inject an alert:

```'-alert(1)-'```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b897ccb9-c405-4d2d-977e-cf1f4d17ec12)

> Verify the technique worked by right clicking, selecting "Copy URL", and pasting the URL in the browser. When you load the page it should trigger an alert.

![Screenshot 2024-04-15 190135](https://github.com/udayk01/Web-Security/assets/52235763/86678adf-7faa-49aa-bca8-8a94e1c42d34)

> Lab solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/71cbce85-76e3-4b48-ae7a-2ff0bbcb4605)
