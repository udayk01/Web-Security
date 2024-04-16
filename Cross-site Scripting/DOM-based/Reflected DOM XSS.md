![image](https://github.com/udayk01/Web-Security/assets/52235763/fcff4280-619a-4df9-bdc7-e9122ba02209)

## Solution:

> In Burp Suite, go to the Proxy tool and make sure that the Intercept feature is switched on.

![image](https://github.com/udayk01/Web-Security/assets/52235763/80dd039e-820b-4cfd-b5df-d5884eb84cc2)

> Back in the lab, go to the target website and use the search bar to search for a random test string, such as ```"XSS"```.

![image](https://github.com/udayk01/Web-Security/assets/52235763/3d8d758e-8838-4509-b121-611dcf1b3536)

> Return to the Proxy tool in Burp Suite and forward the request.

> On the Intercept tab, notice that the string is reflected in a JSON response called search-results.

![image](https://github.com/udayk01/Web-Security/assets/52235763/672c50cd-09fb-4107-b89d-3696248ea5b8)

> From the Site Map, open the ```searchResults.js``` file and notice that the JSON response is used with an ```eval()``` function call.

![image](https://github.com/udayk01/Web-Security/assets/52235763/8923b36d-abd5-417e-afba-45a392720710)

> By experimenting with different search strings, you can identify that the JSON response is escaping quotation marks. However, backslash is not being escaped.

> To solve this lab, enter the following search term:

```\"-alert(1)}// ```

![image](https://github.com/udayk01/Web-Security/assets/52235763/2fc46893-efe6-4be4-addc-b3de8c667a09)

> As you have injected a backslash and the site isn't escaping them, when the JSON response attempts to escape the opening double-quotes character, it adds a second backslash. The resulting double-backslash causes the escaping to be effectively canceled out. This means that the double-quotes are processed unescaped, which closes the string that should contain the search term.

An arithmetic operator (in this case the subtraction operator) is then used to separate the expressions before the alert() function is called. Finally, a closing curly bracket and two forward slashes close the JSON object early and comment out what would have been the rest of the object. As a result, the response is generated as follows:

```{"searchTerm":"\\"-alert(1)}//", "results":[]}```

![image](https://github.com/udayk01/Web-Security/assets/52235763/b5623252-6659-4449-9f76-2e3ecedbf54d)

> Lab Solved

![image](https://github.com/udayk01/Web-Security/assets/52235763/54e97bc2-46a6-42a0-b1c1-c4f2fab8ddbd)
