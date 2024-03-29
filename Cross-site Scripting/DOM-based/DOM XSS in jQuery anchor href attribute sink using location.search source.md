![image](https://github.com/udayk01/Web-Security/assets/52235763/99cc4ed2-1f60-43fd-ac30-d719e9e4108f)

## Solution:

![image](https://github.com/udayk01/Web-Security/assets/52235763/715b4263-b465-479d-9043-5851418a150c)

> On the Submit feedback page, change the query parameter returnPath to / followed by a random alphanumeric string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/dbb37c89-22f1-424c-9f1c-8fe39167bb01)

> Right-click and inspect the element, and observe that your random string has been placed inside an a ```href``` attribute.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9ab7578f-9efa-4018-b19e-ac5c33ac1f96)

> Change returnPath to:

```javascript:alert(document.cookie)```

![image](https://github.com/udayk01/Web-Security/assets/52235763/0cc0f3a8-bc3f-4458-b779-efe1721478d1)

> Click on Back

![image](https://github.com/udayk01/Web-Security/assets/52235763/8463a45b-f144-44ff-81e0-661888b0ae9b)


