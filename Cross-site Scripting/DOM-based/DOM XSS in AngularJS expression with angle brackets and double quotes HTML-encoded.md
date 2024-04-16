![image](https://github.com/udayk01/Web-Security/assets/52235763/4791b27a-3a53-45b0-8c60-436540f1ce56)

## Solution:

> Enter a random alphanumeric string into the search box.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1698fcd4-92ee-4e52-bc03-da41dd3a2810)

> View the page source and observe that your random string is enclosed in an ng-app directive.

![image](https://github.com/udayk01/Web-Security/assets/52235763/68861973-0165-47c0-b6df-6aab7395cd66)

> Enter the following AngularJS expression in the search box:

```{{$on.constructor('alert(1)')()}}```

![image](https://github.com/udayk01/Web-Security/assets/52235763/ed298352-40a6-49ff-b316-4b0ef4e340b3)

> Click search

![image](https://github.com/udayk01/Web-Security/assets/52235763/f93a879f-43cd-40b4-a863-3ec3b7d1a3aa)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/2665d7b9-8684-4a62-bb7f-a44e582b6739)
