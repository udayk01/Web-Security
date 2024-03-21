![image](https://github.com/udayk01/Web-Security/assets/52235763/40527437-8469-4600-b139-11fc74036e8c)

## Solution:

> Log in and upload an image as your avatar, then go back to your account page.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b12b16a4-5dce-4627-9a82-b7d5ed703025)

> In Burp, go to Proxy > HTTP history and notice that your image was fetched using a GET request to ```/files/avatars/<YOUR-IMAGE>```. Send this request to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/60ec184a-18f8-4790-b98d-624d94f76cce)

> On your system, create a file called exploit.php, containing a script for fetching the contents of Carlos's secret. For example:

```<?php echo file_get_contents('/home/carlos/secret'); ?>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/ab27b49e-c557-4f4f-ae67-437afc515f1d)

> In Burp Repeater, go to the tab containing the GET ```/files/avatars/<YOUR-IMAGE>``` request. In the path, replace the name of your image file with ```exploit.php``` and send the request. Observe that instead of executing the script and returning the output, the server has just returned the contents of the PHP file as plain text.

![image](https://github.com/udayk01/Web-Security/assets/52235763/2459deb4-e9dd-4ce2-815f-039e92fafaab)

> In Burp's proxy history, find the POST /my-account/avatar request that was used to submit the file upload and send it to Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d6ff90f0-1071-4de8-8bb8-961a20b50d2c)

> In Burp Repeater, go to the tab containing the POST ```/my-account/avatar``` request and find the part of the request body that relates to your PHP file. In the Content-Disposition header, change the filename to include a directory traversal sequence:

```Content-Disposition: form-data; name="avatar"; filename="../exploit.php"```

![image](https://github.com/udayk01/Web-Security/assets/52235763/fdeffa09-9281-41ac-abb6-d824201fb6e9)

> Notice that the response says ```The file avatars/exploit.php has been uploaded.``` This suggests that the server is stripping the directory traversal sequence from the file name.

> Obfuscate the directory traversal sequence by URL encoding the forward slash (/) character, resulting in:

```filename="..%2fexploit.php"```

![image](https://github.com/udayk01/Web-Security/assets/52235763/ab9835ab-610f-4e4f-a07d-19af02155752)

> Observed that the message now says ```The file avatars/../exploit.php has been uploaded.``` This indicates that the file name is being URL decoded by the server.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ea648512-82ef-4a1e-a2cd-48bd1817e20d)

> In Burp's proxy history, find the GET ```/files/avatars/..%2fexploit.php``` request. Observe that Carlos's secret was returned in the response. This indicates that the file was uploaded to a higher directory in the filesystem hierarchy (/files), and subsequently executed by the server. Note that this means you can also request this file using GET ```/files/exploit.php.```

> Secret message: ``` HzPURKCFXupEweGDp4oL1PgBrbIKiUMh```
![image](https://github.com/udayk01/Web-Security/assets/52235763/20758b27-03e3-49fa-8ac5-c903f12da429)

