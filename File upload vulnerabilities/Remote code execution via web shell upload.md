![image](https://github.com/udayk01/Web-Security/assets/52235763/03deed0f-99bf-4f7f-bd89-c2e8c920e056)

## Solution:

> Login to your account using ```wiener:peter```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b99d34cd-471f-4ab7-a497-ab640122bf56)

> Notice an option for uploading an avatar image.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0a2edd9d-712b-4b8e-ad0b-23e811a9e428)

> Upload an image.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ca57857c-96ac-4095-a6e7-cf7abe77ef14)

> Then return to your account page. Notice that a preview of your avatar is now displayed on the page.

![image](https://github.com/udayk01/Web-Security/assets/52235763/624be1ae-a5e9-415e-82a4-588b007f82d3)

> In Burp, go to Proxy > HTTP history. Click the filter bar to open the Filter settings dialog. Under Filter by MIME type, enable the Images checkbox, then apply your changes.

![image](https://github.com/udayk01/Web-Security/assets/52235763/82ccc8b1-3d28-4ebb-9675-29db8a0c1a3e)

> In the proxy history, notice that your image was fetched using a GET request to /files/avatars/ And one post request to /my-account/avatar also will be there . Send this two request to Burp Repeater.

``` /files/avatars/<YOUR-IMAGE>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/d6951da9-8e92-4b21-b4a2-71b7e1e2d12d)

```/my-account/avatar```

![image](https://github.com/udayk01/Web-Security/assets/52235763/563bd6e4-a07b-484c-8b2f-84a7d761521f)

> Send this two request to Burp Repeater.

>> In POST request ``` /my-account/avata```r we will remove the image content and change the file name and add a php script ```<?php echo file_get_contents('/home/carlos/secret'); ?> ```

> Orginal ```/my-account/avatar``` post request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a8f89801-fbba-46c1-83cb-caa51abeb738)

> After inserting the payload script and changing the file name to ```exploit.php```.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b07d3f43-5407-4533-a69f-ee476723e9ca)

> Now go to GET request  ```/files/avatars/<YOUR-IMAGE>``` and change the file name to ```exploit.php``` and send.

> Before changing the name the qurey was like this.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d63ee844-e47f-4e72-941e-418f7f489280)

> After change the file name to ```exploit.php``` to see the secret content of the of folder in ```/home/carlos/secret``` with help of that php script ```<?php echo file_get_contents('/home/carlos/secret'); ?>``` .

![image](https://github.com/udayk01/Web-Security/assets/52235763/971461c5-2448-4212-8857-61d60cd00b40)

> The secret content is: ```FFwBS9VsTUjbw8Rfht4aVpLCydhBzUit```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b74e8886-9392-47ae-9585-6d95b23e4acd)





