---
description: Further Authentication Techniques and Their Security Implications
cover: ../../.gitbook/assets/(4).png
coverY: 0
---

# 🧞♀ API Security Cheat Sheet PART - 3

21. **Missing Colon in JSON**

    ```json
    {"login" "admin",
    "password": "password"}
    ```

    _Description:_ Showcases a JSON formatting error with a missing colon, highlighting the need for strict adherence to JSON syntax standards.
22. **Invalid Boolean as Credentials**

    ```json
    {"login": yes,
    "password": no}
    ```

    _Description:_ Utilizes unrecognized boolean values as credentials, emphasizing the importance of data type validation.
23. **All Keys, No Values**

    ```json
    {"": "",
    "": ""}
    ```

    _Description:_ Represents a case with empty keys and values, underscoring the need to handle edge cases in JSON parsing.
24. **Nested Objects in Credentials**

    ```json
    {"login": {"innerLogin": "admin",
    "password": {"innerPassword": "password"}}}
    ```

    _Description:_ Demonstrates nested objects for authentication, posing challenges in parsing and validating nested structures.
25. **Case Sensitivity Testing**

    ```json
    {"LOGIN": "admin",
    "PASSWORD": "password"}
    ```

    _Description:_ Focuses on case sensitivity in JSON keys, stressing the importance of consistent key naming conventions.
26. **Login as a Number, Password as a String**

    ```json
    {"login": 1234,
    "password": "password"}
    ```

    _Description:_ Highlights mixed data types for login and password, underscoring the need for flexible data handling.
27. **Login as a String, Password as a Number**

    ```json
    {"login": "admin",
    "password": 1234}
    ```

    _Description:_ Inverts the data types of login and password, again emphasizing the importance of handling different data types.
28. **Repeated Keys**

    ```json
    {"login": "admin",
    "login": "user",
    "password": "password"}
    ```

    _Description:_ Illustrates a scenario with duplicate keys, pointing to the necessity of handling such anomalies in JSON structures.
29. **Single Quotes Instead of Double**

    ```json
    {'login': 'admin',
    'password': 'password'}
    ```

    _Description:_ Uses single quotes, which are invalid in JSON, highlighting the need for correct quote usage.
30. **Login and Password with Only Special Characters**

    ```json
    {"login": "@#$%^&*",
    "password": "!@#$%^&*"}
    ```

    _Description:_ Consists of special characters only, showcasing the importance of robust character handling in authentication.



