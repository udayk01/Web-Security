![image](https://github.com/udayk01/Web-Security/assets/52235763/83c51480-07e5-4c2f-917f-8a29d121abe5)

## Solution:

> Log in and upload an image as your avatar, then go back to your account page.

![image](https://github.com/udayk01/Web-Security/assets/52235763/cd77982b-bbf7-4fc2-82a9-4bf3eba334d1)

> In the proxy history, notice that your image was fetched using a GET request to ```/files/avatars/<YOUR-IMAGE>``` And one post request to ```/my-account/avatar``` also will be there . Send this two request to Burp Repeater.

> In POST request - ```/my-account/avatar``` we will remove the image content and change the file name to ```exploit.php``` and add a php script ```<?php echo file_get_contents('/home/carlos/secret'); ?>```

 ![image](https://github.com/udayk01/Web-Security/assets/52235763/b6266fa5-73b8-44f5-aee3-497ba7a8fe51)

> Error came saying "Sorry, only JPG & PNG files are allowed".

>> Change the value of the filename parameter to include a URL encoded null byte, followed by the .png extension:

```filename="exploit.php%00.png"```

![image](https://github.com/udayk01/Web-Security/assets/52235763/7b8d13f1-8549-49d1-b296-f4bd931ab786)

>> Send the request again and notice that the file was uploaded successfully.

> In GET request-

>> Change the file name to ```exploit.php``` and send.

![image](https://github.com/udayk01/Web-Security/assets/52235763/f896f7d9-1092-40d1-bd85-e03d1867034e)

> Secret Message: ```nIt6lALulR00UjFTlljj2YcDHOk1Tybj```

![image](https://github.com/udayk01/Web-Security/assets/52235763/e3a32737-3a82-4e88-85c9-fa3384d0f6bc)
