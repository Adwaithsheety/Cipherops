---
description: >-
  Discover how SMB enumeration on ports 139 and 445 reveals network resources.
  Learn about Server Message Block protocol versions and their significance in
  resource sharing.
cover: >-
  https://images.unsplash.com/photo-1523975864490-174dd4d9a41e?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHwyfHxqb3VybmV5fGVufDB8fHx8MTY5MjM1MzQwMXww&ixlib=rb-4.0.3&q=85
coverY: -55
---

# 🏇 A Journey into SMB Enumeration (Port 139, 445)

## &#x20;:heavy\_multiplication\_x: [<mark style="color:red;">Twitter</mark>](https://twitter.com/Cipher0ps\_tech?t=MlqumIay8I49eWwhjgrotg\&s=09) :link: [<mark style="color:red;">Linkedin</mark>](https://www.linkedin.com/company/cipherops/) :tv: [<mark style="color:red;">Telegram</mark>](https://t.me/cipherops\_tech) :tada: <mark style="color:red;">I</mark>[<mark style="color:red;">nstagram</mark>](https://instagram.com/cipherops\_tech?igshid=MzNlNGNkZWQ4Mg==)

## Introduction to SMB

**Server Message Block (SMB)**, as its name suggests, is a network protocol that enables the sharing of files, printers, and other resources between computers. It provides a means for computers to communicate with each other over a network. SMB operates over two primary ports: **port 139** for SMB over NetBIOS and **port 445** for SMB over IP. The protocol has undergone multiple iterations, with SMB1, SMB2, and SMB3 being the main versions.

#### Understanding SMB Versions

1. **SMB1**: The initial version of SMB is susceptible to known attacks such as EternalBlue and WannaCry. It's disabled by default in newer Windows versions due to its vulnerabilities.
2. **SMB2**: This version improves on the chattiness of SMB1, resulting in better performance. Guest access is disabled by default.
3. **SMB3:** The most secure version of SMB, it employs encryption and has guest access disabled by default.

### Enumerating SMB Versions and Windows Compatibility

Understanding the compatibility between SMB versions and Windows operating systems is essential for effective network management. Here's a breakdown:

* SMB1: Windows 2000, XP, and Windows 2003
* SMB2: Windows Vista SP1 and Windows 2008
* SMB2.1: Windows 7 and Windows 2008 R2
* SMB3: Windows 8 and Windows 2012

### Nmap Scanning for SMB Enumeration

**Nmap**, a powerful network scanning tool, plays a pivotal role in SMB enumeration. Here's a basic example of an Nmap scan for SMB enumeration:

```shell
nmap -n -v -Pn -p139,445 -sV 192.168.0.101
```

### Extracting Version Information with Nmap Scripts

Nmap's scripting capabilities allow us to extract valuable information about the target system. Let's explore a few scripts for version information extraction:

```shell
nmap 192.168.0.101 --script=smb-enum*
nmap 192.168.0.101 --script=smb-vuln*
nmap 192.1688.0.101 --script=smb-os*
```

### Listing Available Shares

Use **smbclient** to list available shares on a target system:

```shell
smbclient -L \\192.168.1.101\
```

For instances where you encounter errors like "protocol negotiation failed," try:

```shell
smbclient -L \\$ip --option='client min protocol=NT1'
```

### Exploring Shares with smbmap

The **smbmap** tool is another handy option for listing shares:

```shell
smbmap -H $ip
smbmap -H $ip -R $sharename
smbmap -u '' -p '' -H $ip 
smbmap -u guest -p '' -H $ip
smbmap -u jsmith -p password1 -d workgroup -H 192.168.0.1
```

### Connecting to Shares with smbclient

Connecting to shares using smbclient involves specifying the target share and the necessary credentials:

```shell
smbclient \\192.168.1.101\C$
smbclient \\192.168.1.101\C$ --option='client min protocol=NT1'
smbclient \\192.168.1.101\admin$ -U t-skid
```

### Downloading Multiple Files

When using **smbclient**, you can download multiple files with these commands:

```shell
smb: \> RECURSE ON
smb: \> PROMPT OFF
smb: \> mget *
```

### Efficient Enumeration with Enum4Linux

**Enum4Linux** is a versatile tool for enumerating various aspects of SMB shares:

```shell
enum4linux -a $ip
enum4linux -u 'guest' -p '' -a $ip
```

### Unveiling Secrets with Null Session and Rpcclient

A **null session** is a connection with an SMB server that doesn't require authentication. Using **rpcclient**, you can interact with SMB servers:

```shell
rpcclient -U "" <ip>
```

### Extracting Important Information with Rpcclient

You can extract valuable information using **rpcclient** commands:

```shell
rpcclient> srvinfo
rpcclient> enumdomusers
rpcclient> getdompwinfo
```

### Exploring Users through IPC$ Shares

If the IPC$ share is enabled and has anonymous access, you can enumerate users using the **lookupsid.py** script:

```shell
lookupsid.py anonymous@10.10.215.206
```

### Assessing Vulnerability

Use online resources to determine if a specific SMB version is vulnerable. Vulnerabilities can have significant security implications. For example:

* SAMBA 3.x-4.x: Vulnerable to `linux/samba/is_known_pipename`
* SAMBA 3.5.11: Vulnerable to `linux/samba/is_known_pipename`

### Capturing SMB Version with smbver.sh

The **smbver.sh** script assists in capturing SMB version when scanners fail to provide the information:

```shell
#!/bin/sh
# ... (script details provided in the prompt) ...
```

### Comprehensive Enumeration with smbenum.sh

The **smbenum.sh** script comprehensively enumerates SMB using a variety of tools:

```shell
#!/bin/bash
# ... (script details provided in the prompt) ...
```

### Ensuring Security with Brute Force Techniques

Security assessments often involve testing for weak credentials. Here are commands for performing SMB brute force attacks:

```shell
hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt $ip smb
nmap -p445 --script smb-brute --script-args userdb=userfilehere,passdb=/usr/
```

### Conclusion

SMB enumeration on ports 139 and 445 is an essential technique for understanding network resources and assessing their security. By leveraging various tools and scripts, network administrators can uncover valuable information that aids in maintaining a secure and efficient network environment.

### FAQs about SMB Enumeration

**Q1:** What is SMB enumeration?&#x20;

**A1:** SMB enumeration is the process of discovering information about shared resources on a network using the Server Message Block protocol.

**Q2:** Why is SMB enumeration important?&#x20;

**A2:** SMB enumeration helps network administrators understand the available resources, their versions, and potential vulnerabilities.

**Q3:** Can SMB enumeration be used maliciously?

**A3:** Yes, SMB enumeration techniques can be exploited by attackers to gather information for unauthorized access. Therefore, it's crucial to perform these techniques responsibly and ethically.

**Q4:** How can I protect my network from SMB vulnerabilities?&#x20;

**A4:** Keeping systems updated with the latest security patches, disabling SMB1, and implementing strong access controls are effective ways to mitigate SMB-related vulnerabilities.

**Q5:** Are there any alternatives to SMB for resource sharing?

**A5:** Yes, alternatives include NFS (Network File System) and WebDAV (Web Distributed Authoring and Versioning), among others.

**Q6: What is SMB enumeration?**

A6: Unveiling Network Secrets: SMB Enumeration Explored

**Q7: Which port is used for SMB over NetBIOS?**

**A7:** Port 139: Where NetBIOS and SMB Collide

**Q8: What role does TCP port 445 play in SMB?**

A8: Port 445: Your Gateway to Modern SMB

**Q9: How can I list available shares?**&#x20;

**A9:** `smbclient`: Your Share-Listing Guide

**Q10: What tools assist in SMB enumeration?**

**A10 :** Your SMB Arsenal: Nmap, smbclient, smbmap, enum4linux, and rpcclien

