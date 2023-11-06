---
cover: ../../.gitbook/assets/t - 3.png
coverY: -26
---

# 🏹 Tool - 3 Assetfinder: Subdomain Enumeration Tool Manual

**Description:** Assetfinder is a tool designed to simplify the process of discovering subdomains associated with a target domain. It is a valuable asset for cybersecurity professionals, researchers, and penetration testers to identify potential entry points, assess a website's online footprint, and enhance security.

**How to Use Assetfinder:**

1.  **Installation:** Begin by installing Assetfinder on your system. You can typically install it using the following command:

    ```
    go get -u github.com/tomnomnom/assetfinder
    ```
2.  **Basic Usage:** To perform a basic subdomain search, use the following command:

    ```
    assetfinder example.com
    ```

    Replace "example.com" with the domain you want to investigate. Assetfinder will provide a list of subdomains associated with that domain.
3.  **Advanced Options:** Assetfinder offers various options for customizing your search. For example, you can specify an output file for the results:

    ```
    assetfinder example.com > output.txt
    ```

    This command will save the results to a file named "output.txt."

**Example:** Imagine you are a cybersecurity analyst tasked with assessing the online presence of a website, "example.com." Using Assetfinder, you can quickly obtain a list of subdomains, such as "blog.example.com," "store.example.com," and "mail.example.com." These subdomains can be crucial for identifying potential vulnerabilities and security weaknesses in the website's online infrastructure.

**Manual for Assetfinder Subdomain Enumeration Tool:**

**1. Introduction:**

Assetfinder is a valuable tool used for subdomain enumeration. This manual will guide you through the tool's installation and usage.

**2. Installation:**

To install Assetfinder, follow these steps:

* Ensure you have Go (Golang) installed on your system.
*   Open your terminal and run the following command to install Assetfinder:

    ```
    go get -u github.com/tomnomnom/assetfinder
    ```

**3. Basic Usage:**

Assetfinder is simple to use. To perform a basic subdomain search, enter the following command:

```
assetfinder example.com
```

Replace "example.com" with the domain you want to explore. Assetfinder will generate a list of subdomains related to the specified domain.

**4. Advanced Options:**

Assetfinder offers additional options for customization:

*   **Output to a file:** To save the results to a file, use the ">" operator:

    ```
    assetfinder example.com > output.txt
    ```

This command will save the subdomains in a file named "output.txt."

This should then give you the following output:

```ruby
Usage of ./assetfinder:
  -subs-only
    Only include subdomains of search domain
```

### 5.Testing and Results

Using AssetFinder is quite easy. It utilizes the following command syntax:

```xml
./assetfinder [--subs-only] <domain>
```

For example, to find both subdomains and domains associated with GE.com, use:

```ruby
root@kali ~ # ./assetfinder ge.com
blizzard000.ge.com
blizzard00.ge.com
ns0.ge.com
milan1-1.ge.com
milan2-1.ge.com
na2001.ge.com
crpeomusanyca01.ge.com
corpuwb01.ge.com
consind01.ge.com
blizzard01.ge.com
....
...
..
```

If you wish to find only the subdomains associated with GE.com, use:

```ruby
root@Kali ~ # ./assetfinder --subs-only ge.com
blizzard00.ge.com
ns0.ge.com
na2001.ge.com
corpuwb01.ge.com
blizzard01.ge.com
lmindobedge1.ge.com
lmcnqhdedge1.ge.com
lmbrspiedge1.ge.com
namedge1.ge.com
lmdkjupedge1.ge.com
....
...
..
```

**6. Conclusion:**

Assetfinder is a powerful tool for subdomain discovery, aiding cybersecurity professionals and researchers in their efforts to enhance security and assess a website's online presence. Always use it responsibly and ethically, ensuring you have proper authorization for your assessments.
