---
description: https://github.com/0xPugazh/Awesome-Dorks Reference
---

# Shodan Dorks

```
ssl:"target.com" http.html:"Login, username, password"
http.title:"Admin"
ssl:"target.com" org:"Cloudflare, Inc." product:"nginx" 200
kibana content-length:217 net:"cidr"
org:"Amazon" ssl:"target"
ssl:"target"
html:"Dashboard Jenkins" http.component:"jenkins"
http.title:"302 Found"
X-Amz-Bucket-Region
x-jenkins 200
X-Generator: Drupal 7
ssl:Google
all:"mongodb server information" all:"metrics"
port:27017 -all:"partially" all:"fs.files"
port:"9200" all:"elastic indices"
product:elastic port:9200
product: CouchDB
title:"system dashboard" html:jira
product: "apache tomcat"
ssl%3A”development”+org%3A”Amazon.com”+port%3A”number”
http.component:ruby port:3000
html:”secret_key_base”
html:”rack.version”
http.html:QUERY ssl:”domain.com”
http.favicon.hash:81586312 200
html:/dana-na/ Pulse Secure VPN exploit
"MongoDB Server Information" port:27017 -authentication
"Set-Cookie: mongo-express=" "200 OK"
mysql port:"3306"
port:"9200" all:"elastic indices"
port:5432 PostgreSQL
"220" "230 Login successful." port:21
proftpd port:21
port:"25" product:"exim"
port:"11211" product:"Memcached"
"X-Jenkins" "Set-Cookie: JSESSIONID" http.title:"Dashboard"
"port: 53" Recursion: Enabled
product:"Apache httpd" port:"80"
product:"Microsoft IIS httpd"
ssl.cert.issuer.cn:example.com ssl.cert.subject.cn:example.com
ssl.cert.expired:true
"Authentication: disabled" port:445
"220" "230 Login successful." port:21

city:
Find devices in a particular city.
city:"Bangalore"
country:

Find devices in a particular country.
country:"IN"
geo:

Find devices by giving geographical coordinates.
geo:"56.913055,118.250862"
hostname:

Find devices matching the hostname.
server: "gws" hostname:"google"
net:

Find devices based on an IP address or /x CIDR.
net:210.214.0.0/16
os:

Find devices based on operating system.
os:"windows 7"
port:

Find devices based on open ports.
proftpd port:21
before/after:

Find devices before or after between a given time.
apache after:22/02/2009 before:14/3/2010
Citrix:

Find Citrix Gateway.
title:"citrix gateway"
Wifi Passwords:

Helps to find the cleartext wifi passwords in Shodan.
html:"def_wirelesspassword"
Surveillance Cams:

With username:admin and password: :P
NETSurveillance uc-httpd
Fuel Pumps connected to internet:

No auth required to access CLI terminal.
"privileged command" GET
Windows RDP Password:

But may contain secondary windows auth
"\x03\x00\x00\x0b\x06\xd0\x00\x00\x124\x00"
Mongo DB servers:

It may give info about mongo db servers and dashboard
"MongoDB Server Information" port:27017 -authentication
FTP servers allowing anonymous access:

Complete Anon access
"220" "230 Login successful." port:21
Jenkins:

Jenkins Unrestricted Dashboard
x-jenkins 200
Hacked routers:

Routers which got compromised
hacked-router-help-sos
Open ATM:

May allow for ATM Access availability
NCR Port:"161"
Telnet Access:

NO password required for telnet access.
port:23 console gateway
Misconfigured Wordpress Sites:

The wp-config.php if accessed can give out the database credentials.
http.html:"* The wp-config.php creation script uses this file"
Hiring:

Find sites hiring.
"X-Recruiting:"
Android Root Bridge:

Find android root bridges with port 5555.
"Android Debug Bridge" "Device" port:5555
Etherium Miners:

Shows the miners running ETH.
"ETH - Total speed"
Tesla Powerpack charging Status:

Helps to find the charging status of tesla powerpack.
http.title:"Tesla PowerPack System" http.component:"d3" -ga3ca4f2
```

{% @github-files/github-code-block %}
