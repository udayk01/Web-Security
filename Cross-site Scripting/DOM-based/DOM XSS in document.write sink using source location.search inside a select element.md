![image](https://github.com/udayk01/Web-Security/assets/52235763/3d6fb054-c504-418e-91bf-e1873e6991b3)

## Solution:

> On the product pages, notice that the dangerous JavaScript extracts a storeId parameter from the ```location.search``` source. It then uses ```document.write``` to create a new option in the select element for the stock checker functionality.

![image](https://github.com/udayk01/Web-Security/assets/52235763/90147b4c-cc97-4eb1-8666-f14584c7ef72)

> Add a storeId query parameter to the URL and enter a random alphanumeric string as its value. Request this modified URL.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e500488a-b199-4b9e-82bf-24f00478fcc6)

> In the browser, notice that your random string is now listed as one of the options in the drop-down list.

![image](https://github.com/udayk01/Web-Security/assets/52235763/655cca6a-e1a6-49c1-a4d4-b061ea38f997)

> Right-click and inspect the drop-down list to confirm that the value of your storeId parameter has been placed inside a select element.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9a0583e5-75b5-4219-b09e-115165b63015)

> Change the URL to include a suitable XSS payload inside the storeId parameter as follows:

```product?productId=1&storeId="></select><img%20src=1%20onerror=alert(1)>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/92437e79-2300-4d3c-91d0-0b8c3e2f904d)

![image](https://github.com/udayk01/Web-Security/assets/52235763/9578eefd-cdaa-44f8-b51f-1636d71cf681)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/ff4c2bc7-5883-4d6b-9748-88f72a975e0c)
