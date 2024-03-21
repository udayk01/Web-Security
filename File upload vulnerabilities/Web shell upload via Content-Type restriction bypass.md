![image](https://github.com/udayk01/Web-Security/assets/52235763/6601fc25-f06a-40d1-ae73-2656ceca1380)

## Solution

> Login to account with the credentials ``` wiener:peter ```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b8106aee-f16d-41d0-ae46-86db3aa4c00d)

> Click on ``` choose file ``` then choose an image and click on ```upload```.

![Screenshot 2024-03-21 104124](https://github.com/udayk01/Web-Security/assets/52235763/52e91229-8862-4ed0-b5df-7b714f16bdb6)

> Then click on go back to my account

![image](https://github.com/udayk01/Web-Security/assets/52235763/38b50a23-6d52-4d2f-9bb5-153935506f07)

> As we can see the avatar is uploaded.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9f6b6bf7-3b5f-4333-8c31-5b5ced32bd39)

> In the proxy history, notice that your image was fetched using a GET request to /files/avatars/ And one post request to /my-account/avatar also will be there . Send this two request to Burp Repeater.

``` /files/avatars/<YOUR-IMAGE>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/d22eb9d3-e91e-4aae-9b5e-ce749540ce4a)

```/my-account/avatar```

![image](https://github.com/udayk01/Web-Security/assets/52235763/461ab9b5-75ce-4616-b6d0-0c30c42f778c)

> Send this two request to Burp Repeater.

>> In POST request ```/my-account/avatar``` we will remove the image content and change the file name and add a php script ```<?php echo file_get_contents('/home/carlos/secret'); ?>``` 

> Orginal ```/my-account/avatar``` post request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/622cdd9b-7cd5-4359-809b-b0c808ed57f1)

> After inserting the payload script and changing the file name to ```exploit.php```.

![image](https://github.com/udayk01/Web-Security/assets/52235763/f185d2fe-7d59-4d52-adb4-4a7c6b83c164)

> Now go to GET request  ```/files/avatars/<YOUR-IMAGE>``` and change the file name to ```exploit.php``` and send.

![image](https://github.com/udayk01/Web-Security/assets/52235763/4cc584fe-fee9-4062-a695-53320498a734)

> The secret content is : ``` UrpmpdKEpy1SoBzAPNQATEX80iEuM4Mg ```

![image](https://github.com/udayk01/Web-Security/assets/52235763/adb270c8-6e27-4d44-a0bc-638321598b1c)


