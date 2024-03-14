This lab contains a blind OS command injection vulnerability in the feedback function.

The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response. However, you can use output redirection to capture the output from the command. There is a writable folder at:

/var/www/images/
The application serves the images for the product catalog from this location. You can redirect the output from the injected command to a file in this folder, and then use the image loading URL to retrieve the contents of the file.

To solve the lab, execute the whoami command and retrieve the output.

![image](https://github.com/udayk01/Web-Security/assets/52235763/cd23ac81-8c53-4bbc-af24-92347ebf1d0e)

![image](https://github.com/udayk01/Web-Security/assets/52235763/4ce869c3-3831-479c-98f1-ad864f55c034)

![image](https://github.com/udayk01/Web-Security/assets/52235763/211c824d-21f3-477b-b263-3307a8707fee)

![image](https://github.com/udayk01/Web-Security/assets/52235763/c67c6d97-a1d1-404f-9a6a-5d791e7b9814)

![image](https://github.com/udayk01/Web-Security/assets/52235763/0340463d-a93a-4017-b963-5d319394dc43)


