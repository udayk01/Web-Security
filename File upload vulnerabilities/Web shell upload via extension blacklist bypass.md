![image](https://github.com/udayk01/Web-Security/assets/52235763/160ff52e-71fa-4c29-b7e1-bf50f7dc57dc)

## Solution:

> Log in and upload an image as your avatar, then go back to your account page.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a4317ecc-f357-4ab0-9729-598b07f22aca)

> In the proxy history, notice that your image was fetched using a GET request to ```/files/avatars/<YOUR-IMAGE>``` And one post request to ```/my-account/avatar``` also will be there . Send this two request to Burp Repeater.

> In POST request - ```/my-account/avatar``` we will remove the image content and change the file name to ```exploit.php``` and add a php script ```<?php echo file_get_contents('/home/carlos/secret'); ?>```

 ![image](https://github.com/udayk01/Web-Security/assets/52235763/ff7c8786-5850-4a78-994e-8400733fecb5)

> But now in post request it is saying it php files are not allowed.

> So we will be changing the value of the filename parameter to ```.htaccess```

> Change the value of the Content-Type header to ```text/plain```. ANd Replace the contents of the file (your PHP payload) with the following Apache directive:

```AddType application/x-httpd-php .shell```

> This maps an arbitrary extension (.shell) to the executable MIME type ```application/x-httpd-php```. As the server uses the mod_php module, it knows how to handle this already.

![image](https://github.com/udayk01/Web-Security/assets/52235763/7573a8ce-c067-4958-b268-72a36675304f)

> Use the back arrow in Burp Repeater to return to the original request for uploading your PHP exploit.And Change the value of the filename parameter from exploit.php to exploit.shell then

![image](https://github.com/udayk01/Web-Security/assets/52235763/f2c39701-4f04-419b-99b3-93e847dac855)

> Send the request again and notice that the file was uploaded successfully.

> In GET request-

>> Change the file name to ```exploit.shell``` and send.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b42d991d-08a9-4802-bf3d-42e7e521375f)

> Secret message: ```yUTPrroKU4yjRsp1OqUojtC87iZAZotA```

![image](https://github.com/udayk01/Web-Security/assets/52235763/46b91ff7-126a-4cdc-8743-605577e520e9)

