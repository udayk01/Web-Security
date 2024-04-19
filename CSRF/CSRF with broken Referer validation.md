![image](https://github.com/udayk01/Web-Security/assets/52235763/cc50214a-7a07-43fd-92ac-9e545acb3d9d)

## Solution:

> Open Burp's browser and log in to your account. Submit the "Update email" form, and find the resulting request in your Proxy history.

![image](https://github.com/udayk01/Web-Security/assets/52235763/dcabf9af-3919-4eed-bd6e-8c05164a5ff0)

![image](https://github.com/udayk01/Web-Security/assets/52235763/79895432-26c2-4289-8a8c-28cba038dee1)

> Send the request to Burp Repeater. Observe that if you change the domain in the Referer HTTP header, the request is rejected.

![image](https://github.com/udayk01/Web-Security/assets/52235763/7788f4bb-85d4-47ff-9c8e-12844b19c068)

![image](https://github.com/udayk01/Web-Security/assets/52235763/d8751162-2468-4cda-9a15-a76dce53f4b3)

> Copy the original domain of your lab instance and append it to the Referer header in the form of a query string. The result should look something like this:

- Referer: ```https://arbitrary-incorrect-domain.net?YOUR-LAB-ID.web-security-academy.net```

> Send the request and observe that it is now accepted. The website seems to accept any Referer header as long as it contains the expected domain somewhere in the string.

![image](https://github.com/udayk01/Web-Security/assets/52235763/974320f4-a9e2-43a4-b37b-6075829d1ed4)

> Create a CSRF proof of concept exploit as described in the solution to the CSRF vulnerability with no defenses lab and host it on the exploit server. Edit the JavaScript so that the third argument of the history.pushState() function includes a query string with your lab instance URL as follows:

```history.pushState("", "", "/?YOUR-LAB-ID.web-security-academy.net")```

![Screenshot 2024-04-20 000048](https://github.com/udayk01/Web-Security/assets/52235763/7d0c2966-7644-4a48-b2ce-51cd846a89b7)

>> This will cause the Referer header in the generated request to contain the URL of the target site in the query string, just like we tested earlier.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e6364ccb-78ae-4661-9d63-edb2dfb9906f)

![image](https://github.com/udayk01/Web-Security/assets/52235763/f5881535-5a41-40ba-8398-b8dcbef807b5)

> If you store the exploit and test it by clicking "View exploit", you may encounter the "invalid Referer header" error again. This is because many browsers now strip the query string from the Referer header by default as a security measure. To override this behavior and ensure that the full URL is included in the request, go back to the exploit server and add the following header to the "Head" section:

```Referrer-Policy: unsafe-url```

![image](https://github.com/udayk01/Web-Security/assets/52235763/398cbbf2-b82b-4eb1-bc74-498a3f8defdb)

> Note that unlike the normal Referer header, the word "referrer" must be spelled correctly in this case.

> Change the email address in your exploit so that it doesn't match your own.

![image](https://github.com/udayk01/Web-Security/assets/52235763/b4ddee9e-0aae-44c8-8a06-e2683852c88a)

> Store the exploit, then click "Deliver to victim" to solve the lab.

![image](https://github.com/udayk01/Web-Security/assets/52235763/299fab36-fd87-49c4-b82b-2302e3da22b1)
