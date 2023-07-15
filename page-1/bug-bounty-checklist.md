# Bug-Bounty Checklist

#### Random DNS Pic <a href="#random-dns-pic" id="random-dns-pic"></a>

![](https://dz2cdn1.dzone.com/storage/temp/14019029-how-dns-works3.png)

#### Burp Regex for Scope Control

```regex
.*\.domain\.com$
```

Explanation: This regular expression is used in Burp Suite to control the scope of the target by matching subdomains of the `domain.com` domain. It is commonly used to ensure that only specific subdomains are included in the testing scope.

Title: Pull Root Subdomains from Final.txt

```bash
cat final | rev | cut -d . -f 1-3 | rev | sort -u | tee root.subdomains
```

Explanation: This command is used to extract the root subdomains from a file called `final.txt`. It performs several operations using common command-line tools (`cat`, `rev`, `cut`, `sort`) to manipulate the subdomains and then stores the unique root subdomains in a file called `root.subdomains`.

Title: Port Scanning IP Ranges

Explanation: This section provides tips for conducting port scanning on IP ranges. It suggests using tools like Basic Shodan, Google Dorks, and ASN lookups to find target CIDR ranges. It also recommends importing the scan results into a tool called IVRE for a comprehensive overview of the scanned IP addresses.

Small Tips:

1. It is recommended to run the port scanning on a virtual private server (VPS) like Linode.com.
2. Running the scan inside a screen session (`screen -SmL`) allows it to continue running even after disconnecting from the server.
3. Piping the output using `tee` allows saving the results to a file while still displaying them on the terminal.

Note: While some people suggest using masscan for faster scanning, the author finds that using a VPS along with nMap and Screen provides more reliable results, even though it may be slower.

Sn1per

Sn1per is an automated reconnaissance scanner designed for penetration testing and bug bounty hunting. It combines various tools and techniques to gather information and identify potential vulnerabilities in target systems.

How to use Sn1per:

1. Clone the Sn1per repository from GitHub:

```shell
git clone https://github.com/1N3/Sn1per.git
```

2. Navigate to the Sn1per directory:

```shell
cd Sn1per
```

3. Run the installation script to set up the required dependencies:

```shell
./install.sh
```

4. Once the installation is complete, you can start using Sn1per by running the following command:

```shell
./sn1per
```

By default, Sn1per runs in a wizard mode that guides you through the scanning process. It prompts you to enter the target URL or IP address, selects the scanning modules, and provides options for customization.

You can also use command-line arguments to specify the target and customize the scanning process. For example:

```shell
./sn1per -t example.com -m all -o output.txt
```

This command scans the target domain "example.com" using all available modules and saves the output to "output.txt".

Sn1per provides a wide range of scanning modules, including port scanning, subdomain enumeration, vulnerability scanning, and more. You can explore the documentation and usage guide in the Sn1per repository to learn about all the available options and advanced features.

Remember to use Sn1per responsibly and ethically, respecting the rules and guidelines of your engagements or bug bounty programs.

Subdomain Enumeration Techniques

Example:

Subdomain enumeration is an essential phase in reconnaissance for bug bounty hunting and penetration testing. It helps identify subdomains associated with a target domain, which can often reveal potential attack vectors or misconfigurations. Here are a few techniques and tools commonly used for subdomain enumeration:

1.  Basic Enumeration with Subfinder: Subfinder is a versatile subdomain enumeration tool. It leverages various sources to discover subdomains associated with a target domain. Make sure to populate all API keys for optimal results, including a Shodan Pro account if available. To use Subfinder, execute the following command:

    ```
    subfinder -d domain.com -o outfile.txt
    ```

`Rapid7 FDNS`: Rapid7 provides a comprehensive dataset called Sonar FDNS, which contains DNS-related information. This dataset can be used for subdomain enumeration. To utilize it, follow these steps:

*   Install the necessary dependencies by running:

    ```
    aptitude install jq pigz
    ```
*   Download the Sonar FDNS dataset in JSON format:

    ```
    wget https://opendata.rapid7.com/sonar.fdns_v2/2019-11-29-1574985929-fdns_a.json.gz
    ```
*   Extract the data and filter subdomains of interest. For example:

    ```
    cat 20170417-fdns.json.gz | pigz -dc | grep ".target.org" | jq
    ```

`Rapid7 FDNS` (Part 2): Similar to the previous technique, you can download and process the Rapid7 FDNS dataset for subdomain enumeration. Here are the steps:

*   Download the desired FDNS dataset:

    ```
    wget https://opendata.rapid7.com/sonar.fdns_v2/2019-11-29-1574985929-fdns_a.json.gz
    ```
*   Extract the data and filter subdomains based on your criteria. For example:

    ```
    2019-11-29-1574985929-fdns_a.json.gz | pigz -dc | grep ".target.org" | jq
    ```

`Rapid7 FDNS` (Part 3 with DNSGrep): The DNSGrep tool, based on Rapid7 Sonar DNS data, can help in subdomain enumeration. Please refer to the GitHub repository for more details and usage instructions: https://github.com/erbbysam/dnsgrep

`Assetfinder` by Tomnomnom: Assetfinder, developed by Tomnomnom, is a powerful tool for subdomain enumeration. It utilizes various sources to discover subdomains associated with the target domain. To use Assetfinder, execute the following command:

```
go get -u github.com/tomnomnom/assetfinder
assetfinder domain.com
```

Remember to respect the terms of service and usage policies of the respective tools and data sources. Subdomain enumeration should always be performed within the scope of authorized engagements or bug bounty programs.
