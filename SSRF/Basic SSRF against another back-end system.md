![image](https://github.com/udayk01/Web-Security/assets/52235763/7605317c-d665-451a-a91e-c1aaac0b80a4)

## Solution:

> Visit a product, click "Check stock", intercept the request in Burp Suite, and send it to Burp Intruder.

![image](https://github.com/udayk01/Web-Security/assets/52235763/811c09da-cf4b-4878-9a81-41a18263b7dc)

![image](https://github.com/udayk01/Web-Security/assets/52235763/5095c3b1-78e1-43e6-a46c-c7612e754f67)

> Click "Clear §", change the stockApi parameter to ```http://192.168.0.1:8080/admin``` then highlight the final octet of the IP address (the number 1), click "Add §".

![image](https://github.com/udayk01/Web-Security/assets/52235763/26738c1d-2ac0-4c10-9599-25870881ada1)

> Switch to the Payloads tab, change the payload type to Numbers, and enter 1, 255, and 1 in the "From" and "To" and "Step" boxes respectively.

![image](https://github.com/udayk01/Web-Security/assets/52235763/330355c8-5a96-45ee-aa8a-3def08aea0ed)

>> Click "Start attack".

> Click on the "Status" column to sort it by status code ascending. You should see a single entry with a status of 200, showing an admin interface.

![image](https://github.com/udayk01/Web-Security/assets/52235763/90d02a7b-fe8c-46a3-a076-4736a8ffb824)

> Click on this request, send it to Burp Repeater, and change the path in the stockApi to: ```/admin/delete?username=carlos```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b24cbf47-952a-47c0-afa7-613eb76f3857)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/1a645f38-eaee-4117-81f0-06cdd5c04f27)
