---
cover: ../.gitbook/assets/stream.png
coverY: -38
---

# 🚡 Streamlining Your Reconnaissance Workflow for Effective Bug Bounty Hunting

### Leveraging Horizontal and Vertical Correlations

When embarking on a bug bounty program or a security assessment, it's essential to adopt a multi-dimensional approach. Understanding both horizontal and vertical correlations can significantly enrich your reconnaissance efforts.

**Horizontal Correlation** involves cross-referencing information across various domains, IP addresses, or ASNs. This technique helps you discover dependencies and uncover subdomains that might not be immediately apparent.

**Vertical Correlation** entails drilling deeper into a single domain or IP address to explore all available information. By delving into the specifics, you can identify potential security weaknesses and vulnerabilities.

Let's delve into the tools and techniques that can help you in your reconnaissance journey:

### Subdomain Enumeration

#### 1. Amass: The Swiss Army Knife of Subdomain Enumeration

Amass is a versatile tool that can assist in horizontal and vertical correlation of subdomains. Here's how you can utilize it for comprehensive information gathering:

*   **Discover subdomains related to an organization:**

    ```shell
    amass intel -org <company_name>
    ```
*   **Explore subdomains within a specific ASN range:**

    ```shell
    amass intel -asn <ASN_Number>
    ```
*   **Identify subdomains within a CIDR range:**

    ```shell
    amass intel -cidr <CIDR_Range>
    ```
*   **Gather WHOIS information for a domain:**

    ```shell
    amass intel -whois -d <Domain_Name>
    ```
*   **Perform passive subdomain enumeration:**

    ```shell
    amass enum -passive -d <Domain_Name>
    ```

**Useful Subdomain Brute-Forcing Tools:**

* [GitHub - Jason Haddix's Subdomain Brute-Forcing](https://gist.github.com/jhaddix/86a06c5dc309d08580a018c66354a056)
* [GitHub - Internetwache's CT Subdomains](https://github.com/internetwache/CT\_subdomains)
* [Crt.sh](https://crt.sh) for Certificate Transparency Logs

### DNS Enumeration with Gobuster and AltDNS

To uncover additional subdomains and their variations, you can combine Gobuster with wordlists and use AltDNS for horizontal and vertical correlation:

*   **Enumerate DNS subdomains with Gobuster:**

    ```shell
    gobuster dns -d starbucks.com -w subdomains.txt
    ```
*   **Generate subdomain variations using AltDNS:**

    ```shell
    altdns -i subdomains.txt -o output.txt -w words.txt
    ```

**DNS Enumeration Resources:**

* VirusTotal
* Netcraft
* DNSDumpster
* ThreatCrowd
* Shodan
* Censys
* DNSDB
* Pastebin

### Cloud Service Provider-Specific Enumeration

Incorporating cloud service provider-specific enumeration into your workflow can yield valuable information:

*   **AWS S3 bucket dorks for Amazon S3:**

    ```shell
    site:.s3.amazonaws.com "Starbucks"
    ```
*   **Google Cloud Storage enumeration:**

    ```shell
    site:storage.googleapis.com <Domain_Here>
    ```
*   **Digital Ocean Spaces enumeration:**

    ```shell
    site:digitaloceanspaces.com <Domain_Here>
    ```
*   **Exploring unauthenticated Elasticsearch databases:**

    ```shell
    port "9200" elastic [;shodan_query]
    ```
*   **Exposed Docker API:**

    ```shell
    product:docker [;shodan_query]
    ```
*   **Kubernetes API with unauthenticated REST API on port 10250:**

    ```shell
    product:"kubernetes"
    ```

### Git Enumeration

Git repositories can inadvertently expose sensitive information. Be thorough in your Git enumeration:

*   **Gather Git repositories:**

    ```shell
    gitdumper - https://github.com/internetwache/GitTools/tree/master/Dumper
    ```
*   **Enumerate Subversion repositories:**

    ```shell
    subversion (.svn) - https://github.com/anantshri/svn-extractor
    ```

### CMS and Web Application Enumeration

Identifying the Content Management Systems (CMS) and web applications in use can provide insights into potential vulnerabilities. Here are some tools to help with CMS enumeration:

*   **WordPress enumeration:**

    ```shell
    wpscan --url https://example.com
    ```
*   **Joomla enumeration:**

    ```shell
    joomscan -u https://example.com
    ```
*   **Drupal enumeration:**

    ```shell
    droopescan scan drupal -u https://example.com
    ```
*   **Adobe AEM enumeration:**

    ```shell
    aem-hacker -u https://example.com
    ```
*   **Magento enumeration:**

    ```shell
    magescan scan -u https://example.com
    ```

### URL Scanning and Security Tools

* **URL scanning with URLScan.io**
* **RapidDNS for domain and IP information**
* \*\*BlueCoat's Site

Review for reputation analysis\*\*

**Security Tools:**

* [TLDR Run for a collection of security tools](https://tools.tldr.run/)

### Shodan Queries for Efficient Reconnaissance

Shodan is a goldmine for information on exposed services and devices. Explore these valuable Shodan query resources to enhance your reconnaissance:

* [GitHub - Jake Jarvis' Awesome Shodan Queries](https://github.com/jakejarvis/awesome-shodan-queries)
* [Ultimate OSINT with Shodan: 100 Great Shodan Queries](https://www.osintme.com/index.php/2021/01/16/ultimate-osint-with-shodan-100-great-shodan-queries/)

### A Simple Reconnaissance Workflow

Putting it all together, here's a simple reconnaissance workflow for bug bounty hunting:

1. **Subdomain Enumeration**:
   * Horizontal correlation with Amass: `amass enum -brute -active -d domain.com -o amass-output.txt`
   * HTTP probing: `cat amass-output.txt | httprobe -p http:81 -p http:3000 -p https:3000 -p http:3001 -p https:3001 -p http:3000 -p http:8080 -p https:8443 -c 50 | tee online-domains.txt`
   * Identifying new subdomains: `anew - cat new-output.txt | anew old-output.txt | httprobe`
   * Generate subdomains with dnsgen: `cat amass-output.txt | dnsgen - | httprobe`
   * Aquatone for scanning domains: `cat domains-endpoints.txt | aquatone`
2. **File and Directory Bruteforcing**:
   * Use FFuF (Fuzz Faster U Fool) for file and directory bruteforcing: `ffuf -ac -v -u https://domain/FUZZ -w wordlist.txt`

With this structured approach, you can efficiently gather information and discover potential vulnerabilities, making your bug bounty hunting more effective.

### Conclusion

In conclusion, reconnaissance is a critical phase in bug bounty hunting and ethical hacking. Leveraging the right tools and techniques in a well-defined workflow enhances your chances of uncovering security flaws and earning bounties ethically.

This comprehensive article provides an organized and coherent approach to reconnaissance, with tool recommendations, examples, and additional resources to empower bug bounty hunters in their quest for uncovering vulnerabilities and improving web security. Mastering this reconnaissance workflow will set you on the path to becoming a more effective and successful bug bounty hunter.

Stay curious, stay ethical, and happy bug hunting!

***

This refined article now covers an organized and coherent approach to reconnaissance, making it easier for readers to understand and implement in bug bounty programs and security assessments. If you have any further points to add or specific areas you'd like to emphasize, please let me know.
