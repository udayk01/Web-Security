![image](https://github.com/udayk01/Web-Security/assets/52235763/c57b6659-7f04-4112-b1e8-266b23e4e5a6)

## Solution:

> Inject a standard XSS payload, such as:

```<img src=1 onerror=alert(1)>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/ba223f26-401e-4ec0-9ba9-2a31e1fcaf61)

> Observe that this payload gets blocked. In the next few steps, we'll use Burp Intruder to test which tags and attributes are being blocked.

![image](https://github.com/udayk01/Web-Security/assets/52235763/4d9ee8ab-7c58-4110-9c8b-2ba2686a03ea)

> Open Burp's browser and use the search function in the lab. Send the resulting request to Burp Intruder.

![image](https://github.com/udayk01/Web-Security/assets/52235763/6427f315-7132-4ad9-ab3c-11d1034f3920)

> In Burp Intruder, in the Positions tab, click "Clear §".

> In the request template, replace the value of the search term with: <>

> Place the cursor between the angle brackets and click "Add §" twice to create a payload position. The value of the search term should now be: <§§>

![image](https://github.com/udayk01/Web-Security/assets/52235763/8e28d7aa-c2fc-4cf8-a828-f62605cc39d9)

> Visit the XSS cheat sheet and click "Copy tags to clipboard".

![image](https://github.com/udayk01/Web-Security/assets/52235763/be16a329-5713-4b8b-9560-458c3a61d050)

> In Burp Intruder, in the Payloads tab, click "Paste" to paste the list of tags into the payloads list. Click "Start attack".

![image](https://github.com/udayk01/Web-Security/assets/52235763/0155f73e-b60c-4af2-a2ee-07bd7315fc7a)

> When the attack is finished, review the results. Observe that all payloads caused an HTTP 400 response, except for the ones using the ```<svg>```, ```<animatetransform>```, ```<title>```, and ```<image>``` tags, which received a 200 response.

 ![image](https://github.com/udayk01/Web-Security/assets/52235763/06aff095-094d-48bc-81ad-f7cd39e18490)

> Go back to the Positions tab in Burp Intruder and replace your search term with:

```<svg><animatetransform%20=1> ```

> Place the cursor before the = character and click "Add §" twice to create a payload position. The value of the search term should now be:

```<svg><animatetransform%20§§=1>```

![image](https://github.com/udayk01/Web-Security/assets/52235763/2ccaffb8-6871-4617-8a99-ba1eddcfbc7a)

> Visit the XSS cheat sheet and click "Copy events to clipboard".

> In Burp Intruder, in the Payloads tab, click "Clear" to remove the previous payloads. Then click "Paste" to paste the list of attributes into the payloads list. Click "Start attack".

![image](https://github.com/udayk01/Web-Security/assets/52235763/17623ba4-0d84-426c-a1c0-8a8e2bc64fbf)

> When the attack is finished, review the results. Note that all payloads caused an HTTP 400 response, except for the onbegin payload, which caused a 200 response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/bd5b4c47-f6bf-4081-b47a-b531f45987da)

> Visit the following URL in the browser to confirm that the alert() function is called and the lab is solved:

```https://YOUR-LAB-ID.web-security-academy.net/?search=%22%3E%3Csvg%3E%3Canimatetransform%20onbegin=alert(1)%3E```

![image](https://github.com/udayk01/Web-Security/assets/52235763/8b7cc109-15c9-4f3a-a630-999f2f35c2f6)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/cc6463ef-4621-4a6e-997d-4b48e379d724)
