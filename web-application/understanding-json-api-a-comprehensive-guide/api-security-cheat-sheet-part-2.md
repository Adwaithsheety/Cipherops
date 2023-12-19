# 🧞♀ API Security Cheat Sheet PART - 2

11. **Unicode in Credentials**

    ```json
    {
      "login": "\u0061\u0064\u006D\u0069\u006E",
      "password": "\u0070\u0061\u0073\u0073\u0077\u006F\u0072\u0064"
    }
    ```

    _Description:_ This scenario uses Unicode representations for credentials, emphasizing the need for APIs to interpret and handle Unicode correctly to maintain security integrity.
12. **Credentials with Escape Characters**

    ```json
    {
      "login": "ad\\nmin",
      "password": "pa\\ssword"
    }
    ```

    _Description:_ Features escape characters within credentials, pointing to the necessity of accurately processing escape sequences to prevent security loopholes.
13. **Credentials with White Space**

    ```json
    {
      "login": " ",
      "password": " "
    }
    ```

    _Description:_ Demonstrates credentials consisting of white space, highlighting the importance of trimming and handling empty or space-only strings in authentication systems.
14. **Overlong Values in Credentials**

    ```json
    {
      "login": "a"*10000,
      "password": "b"*10000
    }
    ```

    _Description:_ Involves excessively long strings, underscoring the need for input length validation to protect against buffer overflow attacks.
15. **Malformed JSON (Missing Brace)**

    ```json
    {"login": "admin",
    "password": "admin"
    ```

    _Description:_ Represents a case of malformed JSON due to a missing brace, indicating the significance of robust JSON parsing and error handling.
16. **Malformed JSON (Extra Comma)**

    ```json
    {
      "login": "admin",
      "password": "admin",
    }
    ```

    _Description:_ Another example of malformed JSON with an extra comma, requiring careful JSON structure validation.
17. **Missing 'login' Key**

    ```json
    {
      "password": "admin"
    }
    ```

    _Description:_ Highlights a scenario where the 'login' key is missing, emphasizing the need for complete credential checks.
18. **Missing 'password' Key**

    ```json
    {
      "login": "admin"
    }
    ```

    _Description:_ Focuses on the absence of the 'password' key, underlining the importance of ensuring both login and password fields are present for authentication.
19. **Swapped Key Values**

    ```json
    {
      "admin": "login",
      "password": "password"
    }
    ```

    _Description:_ Illustrates a situation where key names are swapped with values, pointing out the necessity of correct key-value pairing in JSON structures.
20. **Extra Keys in Credentials**

    ```json
    {
      "login": "admin",
      "password": "admin",
      "extra": "extra"
    }
    ```

    _Description:_ Showcases additional, unnecessary keys, stressing the importance of validating expected keys in authentication payloads.

***

This extended cheat sheet serves as a guide for developers and security professionals to understand and prepare for a wide range of authentication scenarios in API security. Each point illustrates a different challenge or potential vulnerability, emphasizing the importance of comprehensive and meticulous handling of authentication data in APIs to maintain robust security.
