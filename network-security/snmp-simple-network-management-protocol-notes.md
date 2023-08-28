# SNMP (Simple Network Management Protocol) Notes

### SNMP is a protocol used for monitoring various devices on a network, including routers, switches, printers, and IoT devices.

**Port Information**

* SNMP uses two ports:
  * Port 161/UDP is used for SNMP queries.
  * Port 162/UDP is used for SNMP traps, which are data packets sent from the SNMP server to the client without being explicitly requested.

**MIB (Management Information Base)**

* MIB is essential for ensuring SNMP access works across manufacturers and different client-server combinations.
* It's an independent format for storing device information, typically in a text file.
* MIB contains Object Identifiers (OIDs) that provide unique addresses, names, types, access rights, and descriptions for queryable SNMP objects.

**OIDs (Object Identifiers)**

* OIDs uniquely identify managed objects in a MIB hierarchy.
* OIDs are organized hierarchically, often depicted as a tree.
* Top-level OIDs belong to different standard organizations.
* Vendors define private branches with managed objects for their own products.

**SNMP Versions**

* There are two important SNMP versions:
  * SNMPv1: The most common version. It uses a community string for authentication, which travels in plain text.
  * SNMPv3: Offers improved authentication and encrypts information, making dictionary attacks more challenging.

**Community Strings**

* In SNMPv1 and SNMPv2/2c, community strings are used for access.
* There are two types:
  * Public (read-only functions).
  * Private (read/write in general).
* Some objects are always "read-only."
* Writing an object with the wrong community string results in a noSuchName or readOnly error.

**Ports**

* SNMP agent receives requests on UDP port 161.
* Manager receives notifications (Traps and InformRequests) on port 162.
* When using TLS or DTLS, requests are received on port 10161, and notifications are sent to port 10162.

**Brute-Force Community String (v1 and v2c)**

* A dictionary attack can be used to guess community strings.
* A frequently used community string is "public."

**Enumerating SNMP**

* Install snmp-mibs-downloader to understand gathered OIDs.

```bash
apt-get install snmp-mibs-downloader
download-mibs
```

* Comment the line saying "mibs:" in `/etc/snmp/snmp.conf`

```bash
sudo vi /etc/snmp/snmp.conf
```

* If you know a valid community string, you can access the data using SNMPWalk or SNMP-Check:

```bash
# SNMPWalk Example
snmpbulkwalk -c [COMM_STRING] -v [VERSION] [IP]

# SNMP-Check Example
snmp-check [IP] -p [PORT] -c [COMM_STRING]
```

**SNMP Brute Force**

* To guess the community string, you could perform a dictionary attack.

```bash
hydra -P [PASSWORD_LIST] -v [IP] snmp
```

**SNMP Enumeration**

* With a valid community string, you can use tools like SNMPWalk to enumerate information:

```bash
# Enumerate all OIDs
snmpbulkwalk -c public -v2c [IP] .

# Enumerate specific OIDs
snmpwalk -v [VERSION_SNMP] -c [COMM_STRING] [DIR_IP] 1.3.6.1.2.1.4.34.1.3
```

**SNMP Spoofing**

* If an ACL only allows specific IPs to query SNMP, you can spoof an allowed IP inside the UDP packet and sniff the traffic.

**Examine SNMP Configuration Files**

* Check configuration files for SNMP settings:
  * `snmp.conf`
  * `snmpd.conf`
  * `snmp-config.xml`

**HackTricks Automatic Commands **<mark style="color:red;">**Ref**</mark> [<mark style="color:red;">**https://book.hacktricks.xyz/network-services-pentesting/pentesting-snmp**</mark>](https://book.hacktricks.xyz/network-services-pentesting/pentesting-snmp)<mark style="color:red;">**.**</mark>&#x20;

Here are some useful commands:

```bash
# Enumerate SNMP
snmp-check [IP]

# Crack SNMP passwords
onesixtyone -c /usr/share/seclists/Discovery/SNMP/common-snmp-community-strings-onesixtyone.txt [IP] -w 100

# Nmap for SNMP (no brute)
nmap --script "snmp* and not snmp-brute" [target]
```

**Braa - Mass SNMP Scanner**

* Braa is a tool for fast SNMP querying of multiple hosts simultaneously.
* It doesn't require SNMP libraries like net-snmp.

```bash
# Syntax
braa [Community-string]@[IP of SNMP server]:[iso id]

# Example
braa ignite123@192.168.1.125:.1.3.6.*
```

* Braa can extract a large amount of information that may be challenging to process manually.

**Identifying Interesting Information**

* You can identify important information in SNMP data:
  * Look for keywords like "trap," "login," or "fail" to find relevant data.
  * Extract email addresses: `grep -E -o "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" *.snmp`

**Modifying SNMP Values**

* NetScanTools can be used to modify SNMP values, but you need to know the private string.

**Cisco Equipment**

* For Cisco equipment, explore potential vulnerabilities and RCE opportunities.

**Massive SNMP Enumeration**

* Braa is a mass SNMP scanner that efficiently queries multiple hosts simultaneously.
* It implements its own SNMP stack and consumes minimal system resources, making it very fast.

## **Exploring SNMP MIB Trees: Uncover the Secrets of Networked Devices**

In the realm of network management, SNMP (Simple Network Management Protocol) stands as a sentinel, overseeing the performance of various devices like routers, switches, printers, and more. To navigate this intricate network, we delve into the fascinating world of SNMP MIB (Management Information Base) Trees, each branch laden with valuable information:

1. **1.3.6.1.2.1.25.1.6.0 - System Processes:** This branch reveals the heartbeat of your device, showcasing the myriad processes that keep it alive and operational.
2. **1.3.6.1.2.1.25.4.2.1.2 - Running Programs:** A sneak peek into the currently running programs on your networked device, shedding light on its real-time activities.
3. **1.3.6.1.2.1.25.4.2.1.4 - Processes Path:** This branch unravels the intricate pathways to where your device's processes call home.
4. **1.3.6.1.2.1.25.2.3.1.4 - Storage Units:** Delve into the storage landscape of your device, exploring the units that hold your precious data.
5. **1.3.6.1.2.1.25.6.3.1.2 - Software Name:** Discover the names of the software components that power your device's functionality.
6. **1.3.6.1.4.1.77.1.2.25 - User Accounts:** This branch unveils the secrets of user accounts, providing insights into who holds the keys to your device's kingdom.
7. **1.3.6.1.2.1.6.13.1.3 - TCP Local Ports:** Explore the terrain of TCP local ports, where communication on your device takes shape.

But how can we embark on this quest for information? SNMPwalk is our trusty guide. It's a versatile tool to query MIB values and extract data from managed devices. However, it requires a valid SNMP read-only community string for access.

```bash
# SNMPwalk Example: Querying with Multiple Community Strings
for community in public private manager; do snmpwalk -c $community -v1 $ip; done

# SNMPwalk Example: Using a Single Community String
snmpwalk -c public -v1 $ip

# SNMPwalk Example: SNMPv2c
snmpwalk -c public -v2c <target-ip>
```

When SNMPwalk provides us the treasure map, SNMPcheck transforms it into a vivid picture. This tool offers a more readable and user-friendly output of SNMP information.

```bash
# SNMPcheck Example
snmpcheck -t 192.168.1.X -c public
```

Yet, what if the gates to this information are locked, guarded by a secret passphrase? Fear not, for there exists a tool that can breach these gates: OneSixtyOne. This nimble tool swiftly and relentlessly brute-forces SNMP community strings, harnessing the connectionless nature of SNMP.

```bash
# OneSixtyOne Example: Brute Force SNMP Community Strings
onesixtyone -c dict.txt <ip>
```

Here, "dict.txt" represents a dictionary of potential community strings, and "ip" is the target's IP address.

But wait, there's more! We've compiled a list of wordlists to aid you in your quest:

* `/usr/share/seclists/Discovery/SNMP/common-snmp-community-strings-onesixtyone.txt`
* `/usr/share/metasploit-framework/data/wordlists/snmp_default_pass.txt`

For those who seek more automation, NSE Scripts in Nmap offer an array of possibilities for SNMP exploration:

```bash
# List SNMP NSE Scripts
ls -l /usr/share/nmap/scripts/snmp*
```

Lastly, for those who dare to venture into SNMPv3, a more robust and secure version, we've provided a link to a script that can aid in SNMPv3 enumeration:

```bash
# Download SNMPv3 Enumeration Script
wget https://raw.githubusercontent.com/raesene/TestingScripts/master/snmpv3
```

As you embark on your SNMP journey, remember that knowledge is power. With SNMP and its tools, you can unlock the secrets of your networked devices, revealing their inner workings and fortifying their security.

Explore, discover, and safeguard. SNMP MIB Trees await your curiosity.
