# 🧪 Comprehensive Web Application Testing Checklist

```markdown
### Infrastructure Penetration Testing Checklist

Resourse by: Purab Parihar
Contact him : 
LinkedIn: [Purab Parihar](https://www.linkedin.com/in/purabparihar/)
Twitter: [@purab_parihar](https://twitter.com/purab_parihar)

#### Recon

##### External Infrastructure

- [ ] Performing Subdomain Scans
- [ ] Performing recon on Company's LinkedIn Page
- [ ] Listing Employees from Company Profile
- [ ] Extracting email addresses from Employees' Profile for Identifying email formats
- [ ] Google Dorking on Email's Found/Guessed Patterns
- [ ] Gathering Breached Credentials
- [ ] Performing Port Scan on IPs
- [ ] Using Shodan on Public Facing IPs

##### Internal Infrastructure

- [ ] Using Responder in Analyze Mode
- [ ] Using Wireshark for monitoring Network Traffic
- [ ] Performing Network Range Scan
- [ ] Fingerprinting
- [ ] Performing Whois on IPs
- [ ] Performing ASN Discovery
- [ ] Gathering DNS Records
- [ ] Bruteforcing Hostnames with DNS
- [ ] Google Dorking
- [ ] Searching for specific filetypes on the target domain
- [ ] Reverse DNS Lookup
- [ ] Mapping Network
- [ ] Identifying Live Hosts
- [ ] Port Scan
- [ ] Service Scan
- [ ] Version Scan
- [ ] Scanning with NSE/Scripts
- [ ] OS Scan
- [ ] UDP as well as TCP Scan
- [ ] SNMP Enumeration
- [ ] NetBIOS Enumeration
- [ ] Visualizing Network on MindMaps

#### Vulnerability Assessment and PT

##### FTP (Port 21)

- [ ] Grabbing Banner for Versions
- [ ] Anonymous Login
- [ ] FTP Bounce
- [ ] Testing Default or Guessable Passwords

##### SSH (Port 22)

- [ ] Grabbing Banner for Versions
- [ ] Testing Null Password
- [ ] Testing Default or Guessable Passwords

##### SMTP (Port 25)

- [ ] Grabbing Banner for Versions
- [ ] Connecting with Telnet
- [ ] Testing SMTP Relay
- [ ] User Enumeration

##### DNS (Port 53)

- [ ] DNS Hostname Bruteforce
- [ ] DNS Reverse Lookup
- [ ] DNS Service Record Enumeration
- [ ] DNS Service Discovery
- [ ] DNS Zone Transfer

##### Jenkins

- [ ] Checking pages accessible without authentication
- [ ] Exploiting vulnerable versions

##### IIS

- [ ] Enumerating .config files
- [ ] Checking for Trace.AXD enabled debugging
- [ ] Path Traversal
- [ ] Source Code Disclosure
- [ ] Downloading DLLs
- [ ] Exploiting vulnerabilities in specific IIS DLLs
- [ ] Testing for IIS tilde character "~" Vulnerability
- [ ] Bypassing Basic Authentication
- [ ] Directory Brute Force

##### Kerberos (Port 88)

- [ ] Enumerating Active Directory Attacks

##### RPC (Port 111)

- [ ] Enumerating Basic Information using rpcinfo
- [ ] Connecting to RPC with RPC Client
- [ ] Enumerating Rusers
- [ ] Checking for accessible NFS mounts

##### LDAP (Port 389)

- [ ] Listing public information
- [ ] Checking Null Credentials
- [ ] Extracting Users, Computers, and other information
- [ ] Enumerating Domain Admins and Enterprise Admins
- [ ] Enumerating Administrators and Remote Desktop Groups

##### SMB (Port 445)

- [ ] Testing Anonymous Credentials
- [ ] Grabbing Banner for Versions
- [ ] Testing Null Sessions
- [ ] Exploiting vulnerabilities with RPCClient
- [ ] Listing shares and mounting them

##### MSSQL (Port 1433)

- [ ] Grabbing Banner for Versions
- [ ] Basic Information Gathering
- [ ] Executing Commands with MSSQL
- [ ] Privilege Escalation

##### MySQL (Port 3306)

- [ ] Enumerating with nmap
- [ ] Grabbing Banner for Versions
- [ ] Enumerating Privileges and File Privileges
- [ ] Extracting User Information
- [ ] Writing and Reading Files
- [ ] Changing User Passwords

##### Postgresql (Port 5432)

- [ ] Grabbing Banner for Versions
- [ ] Injecting DB Name Flags

##### VNC (Port 5900)

- [ ] Testing Unauthenticated VNC Access
- [ ] Checking for VNC Passwords

##### Redis (Port 6379)

- [ ] Grabbing Banner for Versions
- [ ] Attempting access to Redis without credentials
- [ ] Enumerating information after login
- [ ] Extracting connected clients
- [ ] Gathering configuration details
- [ ] Dumping the database

##### PJL (Port 9100)

- [ ] Interacting with PJL using tools like `PRET`
- [ ] Testing for vulnerabilities and misconfigurations

##### Memcache (Port 11211)

- [ ] Extracting statistics using `memcstat`
- [ ] Dumping data from Memcache using `memccat`

```
