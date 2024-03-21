![image](https://github.com/udayk01/Web-Security/assets/52235763/cefba533-e51c-4098-b180-011f7e6127f2)

## Solution:

> On your system, create a file called ```exploit.php``` containing a script for fetching the contents of Carlos's secret.

>> For example:```<?php echo file_get_contents('/home/carlos/secret'); ?>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/9869d537-9887-42f4-b1e9-d5333e1314fe)

> Log in and attempt to upload the script as your avatar.

![image](https://github.com/udayk01/Web-Security/assets/52235763/2adade27-62fb-4a69-898f-64efe0a0d495)

> Observe that the server appears to successfully prevent you from uploading files that aren't images.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a0d44345-d792-401c-a2e0-4daa96f92803)

> Now what we need to do is we will have a time gap between checking the file and unlinking the file. We need to find that gap and extract the content from that.

>> The vulnerable code that introduces this race condition is as follows:
```
<?php
$target_dir = "avatars/";
$target_file = $target_dir . $_FILES["avatar"]["name"];

// temporary move
move_uploaded_file($_FILES["avatar"]["tmp_name"], $target_file);

if (checkViruses($target_file) && checkFileType($target_file)) {
    echo "The file ". htmlspecialchars( $target_file). " has been uploaded.";
} else {
    unlink($target_file);
    echo "Sorry, there was an error uploading your file.";
    http_response_code(403);
}

function checkViruses($fileName) {
    // checking for viruses
    ...
}

function checkFileType($fileName) {
    $imageFileType = strtolower(pathinfo($fileName,PATHINFO_EXTENSION));
    if($imageFileType != "jpg" && $imageFileType != "png") {
        echo "Sorry, only JPG & PNG files are allowed\n";
        return false;
    } else {
        return true;
    }
}
?>
```
> For that go to http history and the "post" request that we tried to upload the file and send this to the repeter.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d6077713-9ff9-4f16-85ba-ebb5989e6fc1)

> Simlary find any Get request and give the file directory as ```/files/avatars/exploit.php``` this because it should give the content.

>> Send this get request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/844f5f34-ca7f-44c7-a7d0-b719f30c2f0a)

> Now 1 post request and 8 get request(of same content) are there. So what we are doing here we are uploading one time abd calling serveral time in that time gap. We dont know one reqest may come or other won't . We need excute is all this reqest simultaneously . So for that click on new tab option in the repeater from that click on ```create tab group```

![image](https://github.com/udayk01/Web-Security/assets/52235763/f43426d0-ec17-4067-90cd-3f8d851a2225)

> Then one new tab is created with the all tabs.

![image](https://github.com/udayk01/Web-Security/assets/52235763/848bea1d-1fa9-4d12-b948-ea57cf4c59a8)

> Now we need to excute it for that select send group in parallel.

![image](https://github.com/udayk01/Web-Security/assets/52235763/93a292d3-58bd-46d4-a0df-78b5aa938912)

> The post request that we ran remains the same , and aas for the GET request : Some were able to retrieve the secret message within the small time frame and some others could not.

![image](https://github.com/udayk01/Web-Security/assets/52235763/07bc3285-aad1-4003-9930-d3f3e61e9c39)

> Secret Message: ``` 0h6Fvqoy2F9IX1rxersltViioDe7L8PF```

![image](https://github.com/udayk01/Web-Security/assets/52235763/02667fe3-74db-4521-940b-f79a44ae26fd)





