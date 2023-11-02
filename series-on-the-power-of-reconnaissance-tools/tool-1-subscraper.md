---
cover: ../.gitbook/assets/t - 1.png
coverY: -37
---

# Tool - 1 Subscraper

Subscraper is a powerful reconnaissance tool designed for gathering information from various online sources, especially social media platforms. This versatile tool is commonly used by cybersecurity professionals, researchers, and penetration testers to collect valuable data for different purposes.

**How to Use Subscraper:**

1.  **Installation:** Start by installing Subscraper on your system. It is often available as a Python package, so you can install it using pip.

    ```
    pip install subscraper
    ```
2.  **Basic Usage:**

    * To perform a basic subdomain search, use the following command:

    ```
    subscraper -u example.com
    ```

    This will provide you with a list of subdomains associated with the given domain (in this case, "example.com").
3.  **Advanced Options:**

    * Subscraper offers various options and parameters to customize your search, such as specifying the data sources, adjusting the depth of the search, and filtering results.

    ```
    subscraper -u example.com -e crt,bufferover,threatcrowd -d 2
    ```

    In this example, we're searching for subdomains of "example.com" using specific data sources (crt, bufferover, threatcrowd) and extending the search to a depth of 2 levels.

**Example:** Imagine you are a cybersecurity analyst tasked with assessing the online footprint of a target organization. Using Subscraper, you can quickly gather subdomains associated with their domain name. For instance, running the tool on "example.com" might reveal subdomains like "blog.example.com," "store.example.com," and "mail.example.com." This information can be crucial for identifying potential attack vectors or assessing the organization's digital presence.
