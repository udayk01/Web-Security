This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The command is executed asynchronously and has no effect on the application's response. It is not possible to redirect output into a location that you can access. However, you can trigger out-of-band interactions with an external domain.

To solve the lab, execute the whoami command and exfiltrate the output via a DNS query to Burp Collaborator. You will need to enter the name of the current user to complete the lab.

> Burp Suite to intercept and modify the request that submits feedback.

![image](https://github.com/udayk01/Web-Security/assets/52235763/c7e3d8d6-f46a-49ab-a710-4d651df05f53)

> Modifying the email parameter, changing it as follows, and insert Burp Collaborator subdomain

![image](https://github.com/udayk01/Web-Security/assets/52235763/f64754ef-caea-416a-8774-84d32faba746)

> The name is peter-XVxe7L

![image](https://github.com/udayk01/Web-Security/assets/52235763/9d728d1c-0ae2-4532-9eac-15d692e05da3)

![image](https://github.com/udayk01/Web-Security/assets/52235763/e9eb39b6-0e3d-41bd-8d3e-bcd0562c4238)


