# SMB Checklist

Enumeration Checklist

1.  **Retrieve Hostname Information** - Employ 'nmblookup -A \[ip]' to obtain hostname details.

    Example:

    ```bash
    root@kali:~# nmblookup -A [ip]
    Looking up status of [ip]
            [hostname]      <00> -         M <ACTIVE>
            [hostname]      <20> -         M <ACTIVE>
            WORKGROUP       <00> - <GROUP> M <ACTIVE>
            WORKGROUP       <1e> - <GROUP> M <ACTIVE>
                            <03> -         M <ACTIVE>
            INet~Services   <1c> - <GROUP> M <ACTIVE>
            IS~[hostname]   <00> -         M <ACTIVE>

            MAC Address = 00-50-56-XX-XX-XX
    ```
2.  **List Available Shares** - Employ 'smbmap -H \[ip/hostname]' to unveil the shares on the host and determine your access privileges.

    Example:

    ```bash
    root@kali:/# smbmap -H [ip]
    [+] Finding open SMB ports....
    [+] User SMB session establishd on [ip]...
    [+] IP: [ip]:445        Name: [ip]                                      
            Disk                                                    Permissions
            ----                                                    -----------
            ADMIN$                                                  NO ACCESS
            C$                                                      NO ACCESS
            IPC$                                                    NO ACCESS
            NETLOGON                                                NO ACCESS
            Replication                                             READ ONLY
            SYSVOL                                                  NO ACCESS
    ```
3.  **Retrieve Share Information Using smbclient** - Use 'echo exit | smbclient -L \\\\\[ip]' to fetch a list of shares for the given host.

    Example:

    ```bash
    root@kali:~# smbclient -L \\[ip]
    Enter WORKGROUP\root's password:

            Sharename       Type      Comment
            ---------       ----      -------
            IPC$            IPC       Remote IPC
            share           Disk
            wwwroot         Disk
            ADMIN$          Disk      Remote Admin
            C$              Disk      Default share
    Reconnecting with SMB1 for workgroup listing.

            Server               Comment
            ---------            -------

            Workgroup            Master
            ---------            -------
    ```
4.  **Utilize nmap for SMB Enumeration** - Execute 'nmap --script smb-enum-shares -p 139,445 \[ip]' to run specific SMB enumeration scripts on the specified ports.

    Example:

    ```bash
    root@kali:~# nmap --script smb-enum-shares -p 139,445 [ip]
    Starting Nmap 7.70 ( https://nmap.org ) at 2018-09-27 16:25 EDT
    Nmap scan report for [ip]
    Host is up (0.037s latency).

    PORT    STATE SERVICE
    139/tcp open  netbios-ssn
    445/tcp open  microsoft-ds
    MAC Address: 00:50:56:XX:XX:XX (VMware)

    Host script results:
    | smb-enum-shares:
    |   account_used: guest
    |   \\[ip]\ADMIN$:
    |     Type: STYPE_DISKTREE_HIDDEN
    |     Comment: Remote Admin
    |     Anonymous access: <none>
    |     Current user access: <none>
    |   \\[ip]\C$:
    |     Type: STYPE_DISKTREE_HIDDEN
    |     Comment: Default share
    |     Anonymous access: <none>
    |     Current user access: <none>
    |   \\[ip]\IPC$:
    |     Type: STYPE_IPC_HIDDEN
    |     Comment: Remote IPC
    |     Anonymous access: READ
    |     Current user access: READ/WRITE
    |   \\[ip]\share:
    |     Type: STYPE_DISKTREE
    |     Comment:
    |     Anonymous access: <none>
    |     Current user access: READ/WRITE
    |   \\[ip]\wwwroot:
    |     Type: STYPE_DISKTREE
    |     Comment:
    |     Anonymous access: <none>
    |_    Current user access: READ

    Nmap done: 1 IP address (1 host up) scanned in 10.93 seconds
    ```
5.  **Check for Null Sessions** - Utilize 'smbmap -H \[ip/hostname]' or 'rpcclient -U "" -N \[ip]' to inspect for null sessions.

    Example:

    ```bash
    root@kali:~# rpcclient -U "" -N [ip]
    rpcclient $>
    ```
6.  **Explore Vulnerabilities with nmap** - Probe for vulnerabilities using 'nmap --script smb-vuln\* -p 139,445 \[ip].'

    Example:

    ```bash
    root@kali:~# nmap --script smb-vuln* -p 139,445 [ip]
    Starting Nmap 7.70 ( https://nmap.org ) at 2018-09-27 16:37 EDT
    Nmap scan report for [ip]
    Host is up (0.030s latency).

    PORT    STATE SERVICE
    139/tcp open  netbios-ssn
    445/tcp open  microsoft-ds
    MAC Address: 00:50:56:XX:XX:XX (VMware)

    Host script results:
    | smb-vuln-ms06-025:
    |   VULNERABLE:
    |   RRAS Memory Corruption vulnerability (MS06-025)
    |     State: VULNERABLE
    |     IDs:  CVE:CVE-2006-2370
    |           A buffer overflow vulnerability in the Routing and Remote Access service (RRAS) in Microsoft Windows 2000 SP4, XP SP1
    |           and SP2, and Server 2003 SP1 and earlier allows remote unauthenticated or authenticated attackers to
    |           execute arbitrary code via certain crafted "RPC related requests"
    ```

AKA the "RRAS Memory Corruption Vulnerability." | | Disclosure date: 2006-6-27 | References: | https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-2370 |\_ https://technet.microsoft.com/en-us/library/security/ms06-025.aspx

{% code overflow="wrap" %}
```
**Conduct an Overall Scan with enum4linux** - Run 'enum4linux -a [ip]' for comprehensive SMB enumeration.
```
{% endcode %}

````

8. **Manual Inspection**

a. **Samba Version Identification**

   To determine the Samba version, you can use a tool like 'ngrep' to grep network data. For example, running:

   ```bash
   ngrep -i -d tap0 's.?a.?m.?b.?a.*[[:digit:]]' port 139
   ```

   and then executing:

   ```bash
   echo exit | smbclient -L [IP]
   ```

   will provide a wealth of information, including the Samba version.

   Additionally, you can employ the following script by 'rewardone' to conveniently obtain Samba versions:

   ```bash
   #!/bin/sh
   #Author: rewardone
   #Description:
   # Requires root or enough permissions to use tcpdump
   # Will listen for the first 7 packets of a null login
   # and grab the SMB Version
   #Notes:
   # Will sometimes not capture or will print multiple
   # lines. May need to run a second time for success.
   if [ -z $1 ]; then echo "Usage: ./smbver.sh RHOST {RPORT}" && exit; else rhost=$1; fi
   if [ ! -z $2 ]; then rport=$2; else rport=139; fi
   tcpdump -s0 -n -i tap0 src $rhost and port $rport -A -c 7 2>/dev/null | grep -i "samba\|s.a.m" | tr -d '.' | grep -oP 'UnixSamba.*[0-9a-z]' | tr -d '\n' & echo -n "$rhost: " &
   echo "exit" | smbclient -L $rhost 1>/dev/null 2>/dev/null
   sleep 0.5 && echo ""
   ```

   When executed on a system running Samba, this script will yield results like:

   ```bash
   [IP]: UnixSamba 227a
   ```

b. **Windows SMB Inspection**

   Windows SMB is a bit more intricate than a simple version number. To glean information about the connection, you can utilize Wireshark to filter on 'ntlmssp.ntlmv2_response' to observe NTLMv2 traffic, among other details.

````

{% code overflow="wrap" %}
```
This checklist should aid you in navigating the complexities of SMB enumeration effectively and comprehensively. Remember to employ these tools judiciously and in adherence to ethical guidelines.
```
{% endcode %}
