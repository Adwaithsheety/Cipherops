---
cover: ../.gitbook/assets/t - 1(1).png
coverY: -28
---

# 🔧 Tool - 2 Findomain Subdomain Enumeration Tool

**Findomain Subdomain Enumeration Tool**

**Table of Contents:**

1. Introduction
2. Installation
3. Basic Usage
4. Advanced Options
5. Examples
6. Best Practices
7. Conclusion

**1. Introduction:**

Findomain is a versatile subdomain enumeration tool designed to discover subdomains associated with a given domain. It is widely used by cybersecurity professionals, penetration testers, and researchers to identify potential entry points and assess the online presence of websites.

**2. Installation:**

To get started with Findomain, follow these installation steps:

* Open your terminal.
*   Clone the Findomain repository and build it:

    ```
    git clone https://github.com/Edu4rdSHL/findomain.git
    cd findomain
    cargo build --release
    ```
* Findomain is now ready for use on your system.

**3. Basic Usage:**

To perform a basic subdomain search using Findomain, use the following command:

```
findomain -t example.com
```

Replace "example.com" with the domain you want to investigate. Findomain will provide a list of subdomains associated with that domain.

**4. Advanced Options:**

Findomain offers various advanced options for customization. Here are some of the most commonly used options:

* `-q`: Quiet mode, suppresses unnecessary information.
* `-u <output_file>`: Specify an output file to save results.
* `-o <format>`: Set the output format (e.g., json).
* `-r`: Include additional sources for subdomain discovery.

**5. Examples:**

Let's explore some examples to demonstrate how to use Findomain effectively:

*   Basic subdomain search:

    ```
    findomain -t example.com
    ```
*   Save results to a file in JSON format:

    ```
    findomain -t example.com -u output.json -o json
    ```
*   Perform a quiet search with additional sources:

    ```
    findomain -t example.com -q -r
    ```

**6. Best Practices:**

* Always ensure you have proper authorization before using Findomain for security assessments.
* Respect the laws and ethical guidelines governing web reconnaissance and security testing.

**7. Conclusion:**

Findomain is a valuable tool for subdomain enumeration, helping security professionals and researchers uncover potential vulnerabilities and understand a website's online presence. Use it responsibly and ethically, with proper authorization, to enhance the security of web applications and websites.

Please note that the tool's features and options may evolve, so it's a good practice to refer to the official documentation for the most up-to-date information.
