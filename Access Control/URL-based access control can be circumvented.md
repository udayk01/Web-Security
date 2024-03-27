![image](https://github.com/udayk01/Web-Security/assets/52235763/a8d8ca80-78af-46fd-b642-3014f1206007)

## Solution:

>  load /admin and observe that you get blocked. Notice that the response is very plain, suggesting it may originate from a front-end system.

![image](https://github.com/udayk01/Web-Security/assets/52235763/74923e01-76c8-4693-8ce9-2d3d1d06bf7c)

![image](https://github.com/udayk01/Web-Security/assets/52235763/88017a14-a7ac-400c-a894-d92fa302112c)

> Send the request to Burp Repeater. Change the URL in the request line to / and add the HTTP header ```X-Original-URL: /invalid```. Observe that the application returns a ```"not found"``` response. This indicates that the back-end system is processing the URL from the ```X-Original-URL header```.

![image](https://github.com/udayk01/Web-Security/assets/52235763/515158c0-db7d-4209-8c9f-47a298b24f04)

> Change the value of the ```X-Original-URL``` header to ```/admin```. Observe that you can now access the admin page.

![image](https://github.com/udayk01/Web-Security/assets/52235763/e944987d-23cd-45cf-90e0-6260f9cf083c)

> To delete carlos, add ```?username=carlos ```to the real query string, and change the ```X-Original-URL``` path to ```/admin/delete```.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c3badcc8-0eaf-416d-9d0f-d3013a07e361)

> And hence the user carlos is deleted.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a3615ebb-1a83-4cfd-8816-3e5e93c49599)
