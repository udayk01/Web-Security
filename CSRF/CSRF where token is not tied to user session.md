![image](https://github.com/udayk01/Web-Security/assets/52235763/4f8709af-3a10-4eac-b22b-473813387b81)

## Solution:

> Open Burp's browser and log in to your account. Submit the "Update email" form, and intercept the resulting request.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9b3b154e-b422-4865-93b4-ef5bb538ddfe)

![image](https://github.com/udayk01/Web-Security/assets/52235763/09822345-e291-4af4-80f2-a32c86fde994)

> Make a note of the value of the CSRF token, then drop the request.

csrf: KKpzGYSCbQlAUuqWmjwzbf253n9ubhLw

> Open a private/incognito browser window, log in to your other account, and send the update email request into Burp Repeater.

![image](https://github.com/udayk01/Web-Security/assets/52235763/be961886-3dad-4ac6-a566-a6b4dc39ac31)

![image](https://github.com/udayk01/Web-Security/assets/52235763/85622e36-ec8c-4f0f-9816-47dd667f8832)

> Observe that if you swap the CSRF token with the value from the other account, then the request is accepted.

![image](https://github.com/udayk01/Web-Security/assets/52235763/a37fd139-e32a-4daa-8113-74518c68fb3f)

> Create and host a proof of concept exploit . Note that the CSRF tokens are single-use, so you'll need to include a fresh one.

```wiener```

![image](https://github.com/udayk01/Web-Security/assets/52235763/512dd26d-e95f-4aa8-a75f-a2425084b2e7)

![image](https://github.com/udayk01/Web-Security/assets/52235763/f14ab8f7-e426-43d1-93bc-fd2ccd42781e)

```carlos```

![image](https://github.com/udayk01/Web-Security/assets/52235763/ef8f9790-5347-4775-a2b5-25f688e2f43b)

![image](https://github.com/udayk01/Web-Security/assets/52235763/51f56a38-d7dc-4199-9093-5d7b238214db)

> Create the csrf token and drop it because csrf token can only be used once.

> CSRF poc

![image](https://github.com/udayk01/Web-Security/assets/52235763/597c050c-3e34-41cf-854b-71c0dfebf52f)

![Screenshot 2024-04-19 102944](https://github.com/udayk01/Web-Security/assets/52235763/eeee0991-7218-4c8b-94b5-d23973ca38c1)

change the csrf token : zk5ZsWT4xtsAzSRXvc5NvBfQxgkZmewG

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/ff558254-ab54-4078-89fd-1328b7048a68)

