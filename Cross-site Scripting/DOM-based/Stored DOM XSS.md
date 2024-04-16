![image](https://github.com/udayk01/Web-Security/assets/52235763/ef469734-6226-49a8-908a-003d00a3a3a7)

## Solution:

![image](https://github.com/udayk01/Web-Security/assets/52235763/318a9095-3cce-4bf1-9401-2865c61cc37a)

> Post a comment containing the following vector:

```<><img src=1 onerror=alert(1)>```

>> In an attempt to prevent XSS, the website uses the JavaScript replace() function to encode angle brackets. However, when the first argument is a string, the function only replaces the first occurrence. We exploit this vulnerability by simply including an extra set of angle brackets at the beginning of the comment. These angle brackets will be encoded, but any subsequent angle brackets will be unaffected, enabling us to effectively bypass the filter and inject HTML.
>>
>> ![image](https://github.com/udayk01/Web-Security/assets/52235763/bde09c4d-cfbb-48db-9584-e01d03cd7eea)
>>
>> > Back to blog Alert generated
>>
>> ![image](https://github.com/udayk01/Web-Security/assets/52235763/827f4f3a-8480-4edc-bdbe-2dd85888940c)
>>
>> > Lab Solved
>>
>> ![image](https://github.com/udayk01/Web-Security/assets/52235763/c308744d-65ce-4e4b-bdcf-9d583397afb1)


