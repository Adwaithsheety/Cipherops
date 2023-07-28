# Google Hacking using Dorks

Title: Google Dorks for Targeted Information Search

People and Accounts:

1.  Search for emails based on a username:

    ```
    "username*com"
    ```
2.  Search for online resumes of a person:

    ```
    inurl:resume "john smith"
    intext:resume "john smith"
    ```
3.  Search for people with a specific job title and location on LinkedIn:

    ```
    site:http://linkedin.com/in "<job title>" ( OR ☏ OR ✆ OR
    ```
4.  Find people within GitHub code:

    ```
    site:http://github.com/orgs/*/people
    ```
5.  Search for lists of attendees or finalists:

    ```
    intitle:final.attendee.list OR inurl:final.attendee.list
    ```
6.  Search for login information on exposed Trello boards:

    ```
    site:http://trello.com password + admin OR username
    ```

Documents:

1.  Search for specific documents within a domain in PDF format:

    ```
    site:<domain> filetype:PDF
    ```
2.  Search for PDF documents containing possible email information within a specific domain:

    ```
    filetype:pdf <domain> "email"
    ```
3.  Search for XLS files within government websites:

    ```
    filetype:xls site:.gov
    ```

Cloud, Buckets, and Databases:

1.  Search for confidential or top-secret documents within open Amazon S3 buckets:

    ```
    site:http://s3.amazonaws.com confidential OR "top secret"
    ```
2.  Search for confidential login information within XLS files on Amazon buckets:

    ```
    s3 site:http://amazonaws.com filetype:xls password
    ```
3.  Search for copies of databases:

    ```
    ext:sql intext:"-- phpMyAdmin SQL Dump"
    ```

Social Media:

1.  Search for a specific tweet shared on other media, excluding Twitter:

    ```
    "text of a tweet" -site:https://twitter.com
    ```
2.  Search for links or information related to a specific username not coming directly from their Twitter timeline:

    ```
    @dutch_osintguy -site:twitter.com/dutch_osintguy
    ```

Please note that these Google Dorks are intended for authorized purposes and should be used responsibly.

```
Few top Google Dorks for hacking!

site:accounts..com/signin/ intitle:"index of" drupal intitle:"index of" admin inurl:login.cgiPages Containing Login Portals site:/joomla/administrator
inurl:"server-status" intitle:"Apache Status" intext:"Apache Server Status for"
inurl:/login/index.jsp -site:hertz.*
intitle:"Index of" inurl:wp-json/oembed
intitle:"Index of" phpmyadmin
intitle:"Index of" wp-admin
intitle:index.of.?.sql
inurl: /filemanager/dialog.php
s3 site:amazonaws.com filetype:log
inurl:cgi/login.pl
inurl:zoom.us/j and intext:scheduled for
site:*/auth intitle:login
inurl: admin/login.aspxPages Containing Login Portals
"Index of" inurl:webalizer
"Index of" inurl:phpmyadmin
"Index of" inurl:htdocs inurl:xampp
s3 site:amazonaws.com intext:dhcp filetype:txt inurl:apollo
inurl:/index.aspx/login
site:amazonaws.com inurl:login.php
intitle:"IIS Windows Server" -inurl:"IIS Windows Server"
intitle:"Apache2 Ubuntu Default Page: It works"
inurl:/filedown.php?file=
inurl:Dashboard.jspa intext:"Atlassian Jira Project Management Software"
inurl:app/kibana intext:Loading Kibana
site:https://docs.google.com/spreadsheets edit
intitle:"index of" unattend.xml
inurl:/admin/index.php
inurl:bc.googleusercontent.com intitle:index of
inurl:office365 AND intitle:"Sign In | Login | Portal"
intext:"@gmail.com" AND intext:"@yahoo.com" filetype:sql
intitle:OmniDB intext:"user. pwd. Sign in."
intitle:"qBittorrent Web UI" inurl:8080
site:com inurl:jboss filetype:log -github.com
intitle:"index of" ".cpanel/caches/config/"
inurl:'/scopia/entry/index.jsp'
inurl:/index.aspx/login
intitle: "index of" "./" "./bitcoin"
inurl:/portal/apis/fileExplorer/
intitle:"index of" "/aws.s3/"
intitle:"index of" hosts.csv | firewalls.csv | linux.csv | windows.csv
intitle:Test Page for the Nginx HTTP Server on Fedora
inurl:_cpanel/forgotpwd
intitle:"index of /" intext:/backup
intitle:"Swagger UI - " + "Show/Hide"
site:drive.google.com /preview intext:movie inurl:flv | wmv | mp4 -pdf -edit -view
intext:"class JConfig {" inurl:configuration.php
"index of" "database.sql.zip"
ext:(doc | pdf | xls | txt | ps | rtf | odt | sxw | psw | ppt | pps | xml) (intext:confidential salary | intext:"budget approved") inurl:confidentialext:inc "pwd=" "UID="
ext:ini intext:env.ini
ext:ini Version=... password
ext:ini Version=4.0.0.4 password
ext:ini eudora.ini
ext:ini intext:env.ini
ext:mdb inurl:*.mdb inurl:fpdb shop.mdb
filetype:SWF SWF
filetype:TXT TXT
filetype:XLS XLS
filetype:asp   DBQ=" * Server.MapPath("*.mdb")
filetype:asp "Custom Error Message" Category Source
filetype:asp + "[ODBC SQL"
filetype:asp DBQ=\" * Server.MapPath(\"*.mdb\") 
filetype:asp “Custom Error Message” Category Source
filetype:bak createobject sa
filetype:bak inurl:"htaccess|passwd|shadow|htusers"
filetype:conf inurl:firewall -intitle:cvs 
filetype:conf inurl:proftpd. PROFTP FTP server configuration file reveals
filetype:dat "password.dat
filetype:dat \"password.dat\" 
filetype:eml eml +intext:"Subject" +intext:"From" +intext:"To"
filetype:eml eml +intext:\"Subject\" +intext:\"From\" +intext:\"To\" 
filetype:eml eml +intext:”Subject” +intext:”From” +intext:”To”
filetype:inc dbconn 
filetype:inc intext:mysql_connect
filetype:inc mysql_connect OR mysql_pconnect 
filetype:log inurl:"password.log"
filetype:log username putty PUTTY SSH client logs can reveal usernames
filetype:log “PHP Parse error” | “PHP Warning” | “PHP Error”
filetype:mdb inurl:users.mdb
filetype:ora ora
filetype:ora tnsnames
filetype:pass pass intext:userid
filetype:pdf "Assessment Report" nessus
filetype:pem intext:private
filetype:properties inurl:db intext:password
filetype:pst inurl:"outlook.pst"
filetype:pst pst -from -to -date
filetype:reg reg +intext:"defaultusername" +intext:"defaultpassword"
filetype:reg reg +intext:\"defaultusername\" +intext:\"defaultpassword\" 
filetype:reg reg +intext:â? WINVNC3â?
filetype:reg reg +intext:”defaultusername” +intext:”defaultpassword”
filetype:reg reg HKEY_ Windows Registry exports can reveal
filetype:reg reg HKEY_CURRENT_USER SSHHOSTKEYS
filetype:sql "insert into" (pass|passwd|password)
filetype:sql ("values * MD5" | "values * password" | "values * encrypt")
filetype:sql (\"passwd values\" | \"password values\" | \"pass values\" ) 
filetype:sql (\"values * MD\" | \"values * password\" | \"values * encrypt\") 
filetype:sql +"IDENTIFIED BY" -cvs
filetype:sql password
filetype:sql password 
filetype:sql “insert into” (pass|passwd|password)
filetype:url +inurl:"ftp://" +inurl:";@"
filetype:url +inurl:\"ftp://\" +inurl:\";@\" 
filetype:url +inurl:”ftp://” +inurl:”;@”
filetype:xls inurl:"email.xls"
filetype:xls username password email
index of: intext:Gallery in Configuration mode
index.of passlist
index.of perform.ini mIRC IRC ini file can list IRC usernames and
index.of.dcim 
index.of.password 
intext:" -FrontPage-" ext:pwd inurl:(service | authors | administrators | users)
intext:""BiTBOARD v2.0" BiTSHiFTERS Bulletin Board"
intext:"# -FrontPage-" ext:pwd inurl:(service | authors | administrators | users) "# -FrontPage-" inurl:service.pwd
intext:"#mysql dump" filetype:sql
intext:"#mysql dump" filetype:sql 21232f297a57a5a743894a0e4a801fc3
intext:"A syntax error has occurred" filetype:ihtml
intext:"ASP.NET_SessionId" "data source="
intext:"About Mac OS Personal Web Sharing"
intext:"An illegal character has been found in the statement" -"previous message"
intext:"AutoCreate=TRUE password=*"
intext:"Can't connect to local" intitle:warning
intext:"Establishing a secure Integrated Lights Out session with" OR intitle:"Data Frame - Browser not HTTP 1.1 compatible" OR intitle:"HP Integrated Lights-
intext:"Fatal error: Call to undefined function" -reply -the -next
intext:"Fill out the form below completely to change your password and user name. If new username is left blank, your old one will be assumed." -edu
intext:"Generated by phpSystem"
intext:"Host Vulnerability Summary Report"
intext:"HostingAccelerator" intitle:"login" +"Username" -"news" -demo
intext:"IMail Server Web Messaging" intitle:login
intext:"Incorrect syntax near"
intext:"Index of" /"chat/logs"
intext:"Index of /network" "last modified"
intext:"Index of /" +.htaccess
intext:"Index of /" +passwd
intext:"Index of /" +password.txt
intext:"Index of /admin"
intext:"Index of /backup"
intext:"Index of /mail"
intext:"Index of /password"
intext:"SQL Server Driver][SQL Server]Line 1: Incorrect syntax near"
intext:"Thank you for your order"   +receipt
intext:"Thank you for your order" +receipt
intext:"Thank you for your purchase" +download
intext:"The following report contains confidential information" vulnerability -search
intext:"phpMyAdmin MySQL-Dump" "INSERT INTO" -"the"
intext:"phpMyAdmin MySQL-Dump" filetype:txt
intext:"phpMyAdmin" "running on" inurl:"main.php"
intextpassword | passcode)   intextusername | userid | user) filetype:csv
intextpassword | passcode) intextusername | userid | user) filetype:csv
intitle:"index of" etc/shadow
intitle:"index of" htpasswd
intitle:"index of" members OR accounts
intitle:"index of" mysql.conf OR mysql_config
intitle:"index of" passwd
intitle:"index of" people.lst
intitle:"index of" pwd.db
intitle:"index of" spwd
intitle:"index of" user_carts OR user_cart
intitle:"index.of *" admin news.asp configview.asp
inurl:admin inurl:userlist Generic userlist files
inurl:php?id=
inurl:index.php?id=site:accounts..com/signin/ intitle:"index of" drupal intitle:"index of" admin inurl:login.cgiPages Containing Login Portals site:/joomla/administrator
inurl:"server-status" intitle:"Apache Status" intext:"Apache Server Status for"
inurl:/login/index.jsp -site:hertz.*
intitle:"Index of" inurl:wp-json/oembed
intitle:"Index of" phpmyadmin
intitle:"Index of" wp-admin
intitle:index.of.?.sql
inurl: /filemanager/dialog.php
s3 site:amazonaws.com filetype:log
inurl:cgi/login.pl
inurl:zoom.us/j and intext:scheduled for
site:*/auth intitle:login
inurl: admin/login.aspxPages Containing Login Portals
"Index of" inurl:webalizer
"Index of" inurl:phpmyadmin
"Index of" inurl:htdocs inurl:xampp
s3 site:amazonaws.com intext:dhcp filetype:txt inurl:apollo
inurl:/index.aspx/login
site:amazonaws.com inurl:login.php
intitle:"IIS Windows Server" -inurl:"IIS Windows Server"
intitle:"Apache2 Ubuntu Default Page: It works"
inurl:/filedown.php?file=
inurl:Dashboard.jspa intext:"Atlassian Jira Project Management Software"
inurl:app/kibana intext:Loading Kibana
site:https://docs.google.com/spreadsheets edit
intitle:"index of" unattend.xml
inurl:/admin/index.php
inurl:bc.googleusercontent.com intitle:index of
inurl:office365 AND intitle:"Sign In | Login | Portal"
intext:"@gmail.com" AND intext:"@yahoo.com" filetype:sql
intitle:OmniDB intext:"user. pwd. Sign in."
intitle:"qBittorrent Web UI" inurl:8080
site:com inurl:jboss filetype:log -github.com
intitle:"index of" ".cpanel/caches/config/"
inurl:'/scopia/entry/index.jsp'
inurl:/index.aspx/login
intitle: "index of" "./" "./bitcoin"
inurl:/portal/apis/fileExplorer/
intitle:"index of" "/aws.s3/"
intitle:"index of" hosts.csv | firewalls.csv | linux.csv | windows.csv
intitle:Test Page for the Nginx HTTP Server on Fedora
inurl:_cpanel/forgotpwd
intitle:"index of /" intext:/backup
intitle:"Swagger UI - " + "Show/Hide"
site:drive.google.com /preview intext:movie inurl:flv | wmv | mp4 -pdf -edit -view
intext:"class JConfig {" inurl:configuration.php
"index of" "database.sql.zip"
ext:(doc | pdf | xls | txt | ps | rtf | odt | sxw | psw | ppt | pps | xml) (intext:confidential salary | intext:"budget approved") inurl:confidentialext:inc "pwd=" "UID="
ext:ini intext:env.ini
ext:ini Version=... password
ext:ini Version=4.0.0.4 password
ext:ini eudora.ini
ext:ini intext:env.ini
ext:mdb inurl:*.mdb inurl:fpdb shop.mdb
filetype:SWF SWF
filetype:TXT TXT
filetype:XLS XLS
filetype:asp   DBQ=" * Server.MapPath("*.mdb")
filetype:asp "Custom Error Message" Category Source
filetype:asp + "[ODBC SQL"
filetype:asp DBQ=\" * Server.MapPath(\"*.mdb\") 
filetype:asp “Custom Error Message” Category Source
filetype:bak createobject sa
filetype:bak inurl:"htaccess|passwd|shadow|htusers"
filetype:conf inurl:firewall -intitle:cvs 
filetype:conf inurl:proftpd. PROFTP FTP server configuration file reveals
filetype:dat "password.dat
filetype:dat \"password.dat\" 
filetype:eml eml +intext:"Subject" +intext:"From" +intext:"To"
filetype:eml eml +intext:\"Subject\" +intext:\"From\" +intext:\"To\" 
filetype:eml eml +intext:”Subject” +intext:”From” +intext:”To”
filetype:inc dbconn 
filetype:inc intext:mysql_connect
filetype:inc mysql_connect OR mysql_pconnect 
filetype:log inurl:"password.log"
filetype:log username putty PUTTY SSH client logs can reveal usernames
filetype:log “PHP Parse error” | “PHP Warning” | “PHP Error”
filetype:mdb inurl:users.mdb
filetype:ora ora
filetype:ora tnsnames
filetype:pass pass intext:userid
filetype:pdf "Assessment Report" nessus
filetype:pem intext:private
filetype:properties inurl:db intext:password
filetype:pst inurl:"outlook.pst"
filetype:pst pst -from -to -date
filetype:reg reg +intext:"defaultusername" +intext:"defaultpassword"
filetype:reg reg +intext:\"defaultusername\" +intext:\"defaultpassword\" 
filetype:reg reg +intext:â? WINVNC3â?
filetype:reg reg +intext:”defaultusername” +intext:”defaultpassword”
filetype:reg reg HKEY_ Windows Registry exports can reveal
filetype:reg reg HKEY_CURRENT_USER SSHHOSTKEYS
filetype:sql "insert into" (pass|passwd|password)
filetype:sql ("values * MD5" | "values * password" | "values * encrypt")
filetype:sql (\"passwd values\" | \"password values\" | \"pass values\" ) 
filetype:sql (\"values * MD\" | \"values * password\" | \"values * encrypt\") 
filetype:sql +"IDENTIFIED BY" -cvs
filetype:sql password
filetype:sql password 
filetype:sql “insert into” (pass|passwd|password)
filetype:url +inurl:"ftp://" +inurl:";@"
filetype:url +inurl:\"ftp://\" +inurl:\";@\" 
filetype:url +inurl:”ftp://” +inurl:”;@”
filetype:xls inurl:"email.xls"
filetype:xls username password email
index of: intext:Gallery in Configuration mode
index.of passlist
index.of perform.ini mIRC IRC ini file can list IRC usernames and
index.of.dcim 
index.of.password 
intext:" -FrontPage-" ext:pwd inurl:(service | authors | administrators | users)
intext:""BiTBOARD v2.0" BiTSHiFTERS Bulletin Board"
intext:"# -FrontPage-" ext:pwd inurl:(service | authors | administrators | users) "# -FrontPage-" inurl:service.pwd
intext:"#mysql dump" filetype:sql
intext:"#mysql dump" filetype:sql 21232f297a57a5a743894a0e4a801fc3
intext:"A syntax error has occurred" filetype:ihtml
intext:"ASP.NET_SessionId" "data source="
intext:"About Mac OS Personal Web Sharing"
intext:"An illegal character has been found in the statement" -"previous message"
intext:"AutoCreate=TRUE password=*"
intext:"Can't connect to local" intitle:warning
intext:"Establishing a secure Integrated Lights Out session with" OR intitle:"Data Frame - Browser not HTTP 1.1 compatible" OR intitle:"HP Integrated Lights-
intext:"Fatal error: Call to undefined function" -reply -the -next
intext:"Fill out the form below completely to change your password and user name. If new username is left blank, your old one will be assumed." -edu
intext:"Generated by phpSystem"
intext:"Host Vulnerability Summary Report"
intext:"HostingAccelerator" intitle:"login" +"Username" -"news" -demo
intext:"IMail Server Web Messaging" intitle:login
intext:"Incorrect syntax near"
intext:"Index of" /"chat/logs"
intext:"Index of /network" "last modified"
intext:"Index of /" +.htaccess
intext:"Index of /" +passwd
intext:"Index of /" +password.txt
intext:"Index of /admin"
intext:"Index of /backup"
intext:"Index of /mail"
intext:"Index of /password"
intext:"SQL Server Driver][SQL Server]Line 1: Incorrect syntax near"
intext:"Thank you for your order"   +receipt
intext:"Thank you for your order" +receipt
intext:"Thank you for your purchase" +download
intext:"The following report contains confidential information" vulnerability -search
intext:"phpMyAdmin MySQL-Dump" "INSERT INTO" -"the"
intext:"phpMyAdmin MySQL-Dump" filetype:txt
intext:"phpMyAdmin" "running on" inurl:"main.php"
intextpassword | passcode)   intextusername | userid | user) filetype:csv
intextpassword | passcode) intextusername | userid | user) filetype:csv
intitle:"index of" etc/shadow
intitle:"index of" htpasswd
intitle:"index of" members OR accounts
intitle:"index of" mysql.conf OR mysql_config
intitle:"index of" passwd
intitle:"index of" people.lst
intitle:"index of" pwd.db
intitle:"index of" spwd
intitle:"index of" user_carts OR user_cart
intitle:"index.of *" admin news.asp configview.asp
inurl:admin inurl:userlist Generic userlist files
inurl:php?id=
inurl:index.php?id=
```

```markdown
ext:asa | ext:bak intext:uid intext:pwd -"uid..pwd" database | server | dsn
ext:inc "pwd=" "UID="
ext:ini eudora.ini
ext:ini Version=4.0.0.4 password
ext:passwd -intext:the -sample -example
ext:txt inurl:unattend.txt
ext:yml database inurl:config
filetype:bak c reateobjec t sa
filetype:bak inurl:"htac c ess|passwd|shadow|htusers"
filetype:c fg mrtg "target
filetype:c fm "c fapplication name" password
filetype:c onf oekakibbs
filetype:c onf slapd.c onf
filetype:c onfig c onfig intext:appSettings "User ID"
filetype:dat "password.dat"
filetype:dat inurl:Sites.dat
filetype:dat wand.dat
filetype:inc dbc onn
filetype:inc intext:mysql_connec t
filetype:inc mysql_c onnec t OR mysql_pc onnec t
filetype:inf sysprep
filetype:ini inurl:"serv-u.ini"
filetype:ini inurl:flashFXP.ini
filetype:ini ServUDaemon
filetype:ini wc x_ftp
filetype:ini ws_ftp pwd
filetype:ldb admin
filetype:log "See `ipsec --copyright"
filetype:log inurl:"password.log"
filetype:mdb inurl:users.mdb
filetype:mdb wwforum
filetype:netrc password
filetype:pass pass intext:userid
filetype:pem intext:private
filetype:properties inurl:db intext:password
filetype:pwd servic e
filetype:pwl pwl
filetype:reg reg +intext:"defaultusername" +intext:"defaultpassword"
filetype:reg reg +intext:â? WINVNC3â?
filetype:reg reg HKEY_CURRENT_USER SSHHOSTKEYS
filetype:sql "insert into" (pass|passwd|password)
filetype:sql ("values * MD5" | "values * password" | "values * encrypt")
filetype:sql +"IDENTIFIED BY" -c vs
filetype:sql password
filetype:url +inurl:"ftp://" +inurl:";@"
filetype:xls username password email
htpasswd
htpasswd / htgroup
htpasswd / htpasswd.bak
intext:"enable password 7"
intext:"enable sec ret 5 $"
intext:"
EZGuestbook"
intext:"
Web Wiz Journal"
intitle:"index of" intext:c onnec t.inc
intitle:"index of" intext:globals.inc

intitle:"Index of" passwords modified
intitle:"Index of" sc _serv.conf sc _serv content
intitle:"phpinfo()" +"mysql.default_password" +"Zend s•ri•ting Language Engine"
intitle:dupic s inurl:(add.asp | default.asp | view.asp | voting.asp) -site:duware.com
intitle:index.of administrators.pwd
intitle:Index.of etc shadow
intitle:index.of intext:"sec ring.skr"|"secring.pgp"|"secring.bak"
intitle:rapidshare intext:login
inurl:"c alendars•ri•t/users.txt"
inurl:"editor/list.asp" | inurl:"database_editor.asp" | inurl:"login.asa" "are set"
inurl:"GRC.DAT" intext:"password"
inurl:"Sites.dat"+"PASS="
inurl:"slapd.c onf" intext:"credentials" -manpage -"Manual Page" -man: -sample
inurl:"slapd.c onf" intext:"rootpw" -manpage -"Manual Page" -man: -sample
inurl:"wvdial.conf" intext:"password"
inurl:/db/main.mdb
inurl:/wwwboard
inurl:/yabb/Members/Admin.dat
inurl:cc bill filetype:log
inurl:cgi-bin inurl:c alendar.cfg
inurl:chap-secrets -cvs
inurl:config.php dbuname dbpass
inurl:filezilla.xml -cvs
inurl:lilo.c onf filetype:conf password - tatercounter2000 -bootpwd -man
inurl:nuke filetype:sql
inurl:ospfd.c onf intext:password -sample -test -tutorial -download
inurl:pap-sec rets -cvs
inurl:pass.dat
inurl:perform filetype:ini
inurl:perform.ini filetype:ini
inurl:secring ext:skr | ext:pgp | ext:bak
inurl:server.c fg rc on password
inurl:ventrilo_srv.ini adminpassword
inurl:vtund.c onf intext:pass -c vs
inurl:zebra.c onf intext:password -sample -test -tutorial -download
LeapFTP intitle:"index.of./" sites.ini modified
master.passwd
mysql history files
NickServ registration passwords
passlist
passlist.txt (a better way)
passwd
passwd / etc (reliable)
people.lst
psyBNC config files
pwd.db
server-dbs "intitle:index of"
signin filetype:url
spwd.db / passwd
trillian.ini
wwwboard WebAdmin inurl:passwd.txt wwwboard|webadmin
[WFClient] Password= filetype:ic a
intitle:"remote assessment" OpenAanval Console
intitle:opengroupware.org "resistanc e is obsolete" "Report Bugs" "Username" "password"
"bp blog admin" intitle:login | intitle:admin -site:johnny.ihackstuff.com
"Emergisoft web applications are a part of our"
"Establishing a sec ure Integrated Lights Out session with" OR intitle:"Data Frame - Browser
10/11/2008 All Google Hacking Keywords
http://64.233.183.104/search?q=cac… 3/16
not HTTP 1.1 compatible" OR intitle:"HP Integrated Lights-
"HostingAcc elerator" intitle:"login" +"Username" -"news" -demo
"iCONECT 4.1 :: Login"
"IMail Server Web Messaging" intitle:login
"inspanel" intitle:"login" -"cannot" "Login ID" -site:inspediumsoft.c om
"intitle:3300 Integrated Communic ations Platform" inurl:main.htm
"Login - Sun Cobalt RaQ"
"login prompt" inurl:GM.c gi
"Login to Usermin" inurl:20000
"Mic rosoft CRM : Unsupported Browser Version"
"OPENSRS Domain Management" inurl:manage.cgi
"pc ANYWHERE EXPRESS Java Client"
"Please authentic ate yourself to get ac cess to the management interface"
"please log in"
"Please login with admin pass" -"leak" -sourc eforge
"
CuteNews" "2003..2005 CutePHP"
"
DWMail" password intitle:dwmail
"
Merak Mail Server Software" -.gov -.mil -.edu -site:merakmailserver.c om
"
Midmart Messageboard" "Administrator Login"
"
Monster Top List" MTL numrange:200-
"
UebiMiau" -site:sourc eforge.net
"site info for" "Enter Admin Password"
"SquirrelMail version" "By the SquirrelMail Development Team"
"SysCP - login"
"This is a restricted Ac c ess Server" "Javas•ri•t Not Enabled!"|"Messenger Express" -edu -ac
"This sec tion is for Administrators only. If you are an administrator then please"
"ttawlogin.c gi/?action="
"VHCS Pro ver" -demo
"VNC Desktop" inurl:5800
"Web-Based Management" "Please input password to login" -inurl:johnny.ihac kstuff.com
"WebExplorer Server - Login" "Welc ome to WebExplorer Server"
"WebSTAR Mail - Please Log In"
"You have requested ac cess to a restric ted area of our website. Please authentic ate
yourself to c ontinue."
"You have requested to ac c ess the management func tions" -.edu
(intitle:"Please login - Forums
UBB.threads")|(inurl:login.php "ubb")
(intitle:"Please login - Forums
WWWThreads")|(inurl:"wwwthreads/login.php")|(inurl:"wwwthreads/login.pl?Cat=")
(intitle:"rymo Login")|(intext:"Welcome to rymo") -family
(intitle:"WmSC e-Cart Administration")|(intitle:"WebMyStyle e-Cart Administration")
(inurl:"ars/c gi-bin/arweb?O=0" | inurl:arweb.jsp) -site:remedy.c om -site:mil
4images Administration Control Panel
allintitle:"Welc ome to the Cyclades"
allinurl:"exchange/logon.asp"
allinurl:wps/portal/ login
ASP.login_aspx "ASP.NET_SessionId"
CGI:IRC Login
ext:cgi intitle:"control panel" "enter your owner password to continue!"
ez Publish administration
filetype:php inurl:"webeditor.php"
filetype:pl "Download: SuSE Linux Openexchange Server CA"
filetype:r2w r2w
intext:""BiTBOARD v2.0" BiTSHiFTERS Bulletin Board"
intext:"Fill out the form below c ompletely to change your password and user name. If new
username is left blank, your old one will be assumed." -edu
intext:"Mail admins login here to administrate your domain."
intext:"Master Acc ount" "Domain Name" "Password" inurl:/c gi-bin/qmailadmin
intext:"Master Acc ount" "Domain Name" "Password" inurl:/c gi-bin/qmailadmin
intext:"Storage Management Server for" intitle:"Server Administration"
intext:"Welc ome to" inurl:"c p" intitle:"H-SPHERE" inurl:"begin.html" -Fee
intext:"vbulletin" inurl:adminc p
intitle:"*- HP WBEM Login" | "You are being prompted to provide login ac count information
for *" | "Please provide the information requested and press
intitle:"Admin Login" "admin login" "blogware"
intitle:"Admin login" "Web Site Administration" "Copyright"
intitle:"AlternC Desktop"
intitle:"Athens Authentic ation Point"
intitle:"b2evo > Login form" "Login form. You must log in! You will have to ac cept c ookies in
order to log in" -demo -site:b2evolution.net
intitle:"Cisc o CallManager User Options Log On" "Please enter your User ID and Password in
the spac es provided below and c lick the Log On button to c o
intitle:"ColdFusion Administrator Login"
intitle:"communigate pro * *" intitle:"entranc e"
intitle:"Content Management System" "user name"|"password"|"admin" "Mic rosoft IE 5.5" -
mambo
intitle:"Content Management System" "user name"|"password"|"admin" "Mic rosoft IE 5.5" -
mambo
intitle:"Dell Remote Ac cess Controller"
intitle:"Doc utek ERes - Admin Login" -edu
intitle:"Employee Intranet Login"
intitle:"eMule *" intitle:"- Web Control Panel" intext:"Web Control Panel" "Enter your
password here."
intitle:"ePowerSwitch Login"
intitle:"eXist Database Administration" -demo
intitle:"EXTRANET * - Identific ation"
intitle:"EXTRANET login" -.edu -.mil -.gov
intitle:"EZPartner" -netpond
intitle:"Flash Operator Panel" -ext:php -wiki -c ms -inurl:asternic -inurl:sip -intitle:ANNOUNCE
-inurl:lists
intitle:"i-sec ure v1.1" -edu
intitle:"Ic ecast Administration Admin Page"
intitle:"iDevAffiliate - admin" -demo
intitle:"ISPMan : Unauthorized Acc ess prohibited"
intitle:"ITS System Information" "Please log on to the SAP System"
intitle:"Kurant Corporation StoreSense" filetype:bok
intitle:"ListMail Login" admin -demo
intitle:"Login -
Easy File Sharing Web Server"
intitle:"Login Forum
AnyBoard" intitle:"If you are a new user:" intext:"Forum
AnyBoard" inurl:goc hat -edu
intitle:"Login to @Mail" (ext:pl | inurl:"index") -dwaffleman
intitle:"Login to Cacti"
intitle:"Login to the forums - @www.aimoo.com" inurl:login.cfm?id=
intitle:"MailMan Login"
intitle:"Member Login" "NOTE: Your browser must have cookies enabled in order to log into
the site." ext:php OR ext:cgi

intitle:"Merak Mail Server Web Administration" -ihackstuff.com
intitle:"mic rosoft certific ate servic es" inurl:c ertsrv
intitle:"MikroTik RouterOS Managing Webpage"
intitle:"MX Control Console" "If you c an't remember"
intitle:"Novell Web Services" "GroupWise" -inurl:"doc /11924" -.mil -.edu -.gov -filetype:pdf
intitle:"Novell Web Services" intext:"Selec t a servic e and a language."
intitle:"oMail-admin Administration - Login" -inurl:omnis.c h
intitle:"OnLine Rec ruitment Program - Login"
intitle:"Philex 0.2*" -s•ri•t -site:freelists.org
intitle:"PHP Advanc ed Transfer" inurl:"login.php"
intitle:"php ic alendar administration" -site:sourc eforge.net
intitle:"php ic alendar administration" -site:sourc eforge.net
intitle:"phpPgAdmin - Login" Language
intitle:"PHProjekt - login" login password
intitle:"please login" "your password is *"
intitle:"Remote Desktop Web Connec tion" inurl:tsweb
intitle:"SFXAdmin - sfx_global" | intitle:"SFXAdmin - sfx_loc al" | intitle:"SFXAdmin - sfx_test"
intitle:"SHOUTc ast Administrator" inurl:admin.c gi
intitle:"site administration: please log in" "site designed by emarketsouth"
intitle:"Supero Doc tor III" -inurl:supermic ro
intitle:"SuSE Linux Openexchange Server" "Please ac tivate Javas•ri•t!"
intitle:"teamspeak server-administration
intitle:"Tomc at Server Administration"
intitle:"TOPdesk ApplicationServer"
intitle:"TUTOS Login"
intitle:"TWIG Login"
intitle:"vhost" intext:"vHost . 2000-2004"
intitle:"Virtual Server Administration System"
intitle:"VisNetic WebMail" inurl:"/mail/"
intitle:"VitalQIP IP Management System"
intitle:"VMware Management Interfac e:" inurl:"vmware/en/"
intitle:"VNC viewer for Java"
intitle:"web-c yradm"|"by Luc de Louw" "This is only for authorized users" -tar.gz -site:web-
cyradm.org
intitle:"WebLogic Server" intitle:"Console Login" inurl:c onsole
intitle:"Welcome Site/User Administrator" "Please selec t the language" -demos
intitle:"Welcome to Mailtraq WebMail"
intitle:"welc ome to netware *" -site:novell.c om
intitle:"WorldClient" intext:"? (2003|2004) Alt-N Tec hnologies."
intitle:"xams 0.0.0..15 - Login"
intitle:"XcAuc tionLite" | "DRIVEN BY XCENT" Lite inurl:admin
intitle:"XMail Web Administration Interface" intext:Login intext:password
intitle:"Zope Help System" inurl:HelpSys
intitle:"ZyXEL Prestige Router" "Enter password"
intitle:"inc . vpn 3000 c onc entrator"
intitle:("Trac kerCam Live Video")|("TrackerCam Applic ation Login")|("Trac kerc am Remote") -
trac kerc am.c om
intitle:asterisk.management.portal web-acc ess
intitle:endymion.sak?.mail.login.page | inurl:sake.servlet
intitle:Group-Office "Enter your username and password to login"
intitle:ilohamail "
IlohaMail"
intitle:ilohamail intext:"Version 0.8.10" "
IlohaMail"
intitle:IMP inurl:imp/index.php3
intitle:Login * Webmailer
intitle:Login intext:"RT is ? Copyright"
```

<pre class="language-markdown"><code class="lang-markdown">intitle:Node.List Win32.Version.3.11
intitle:Novell intitle:WebAcc ess "Copyright *-* Novell, Inc "
intitle:open-xc hange inurl:login.pl
intitle:Ovislink inurl:private/login
intitle:phpnews.login
intitle:plesk inurl:login.php3
inurl:"/admin/c onfiguration. php?" Mystore
inurl:"/slxweb.dll/external?name=(c ustportal|webticketc ust)"
inurl:"1220/parse_xml.c gi?"
inurl:"631/admin" (inurl:"op=*") | (intitle:CUPS)
inurl:":10000" intext:webmin
inurl:"Ac tivex/default.htm" "Demo"
inurl:"c alendar.asp?ac tion=login"
inurl:"default/login.php" intitle:"kerio"
inurl:"gs/adminlogin.aspx"
inurl:"php121login.php"
inurl:"suse/login.pl"
inurl:"typo3/index.php?u=" -demo
inurl:"usysinfo?login=true"
inurl:"utilities/TreeView.asp"
inurl:"vsadmin/login" | inurl:"vsadmin/admin" inurl:.php| .asp
Code:
nurl:/admin/login.asp
inurl:/cgi-bin/sqwebmail?noframes=1
inurl:/Citrix/Nfuse17/
inurl:/dana-na/auth/welc ome.html
inurl:/eprise/
inurl:/Merchant2/admin.mv | inurl:/Merc hant2/admin.mvc | intitle:"Miva Merc hant
Administration Login" -inurl:c heap-malboro.net
inurl:/modcp/ intext:Moderator+vBulletin
inurl:/SUSAdmin intitle:"Mic rosoft Software upd•t• Servic es"
inurl:/webedit.* intext:WebEdit Professional -html
inurl:1810 "Orac le Enterprise Manager"
inurl:2000 intitle:RemotelyAnywhere -site:realvnc .com
inurl::2082/frontend -demo
inurl:administrator "welc ome to mambo"
inurl:bin.welc ome.sh | inurl:bin.welc ome.bat | intitle:eHealth.5.0
inurl:cgi-bin/ultimatebb.c gi?ubb=login
inurl:Citrix/MetaFrame/default/default.aspx
inurl:confixx inurl:login|anmeldung
inurl:coranto.c gi intitle:Login (Authorized Users Only)
inurl:csCreatePro.c gi
inurl:default.asp intitle:"WebCommander"
inurl:exchweb/bin/auth/owalogon.asp
inurl:gnatsweb.pl
inurl:ids5web
inurl:irc filetype:c gi c gi:irc
inurl:login filetype:swf swf
inurl:login.asp
inurl:login.c fm
inurl:login.php "SquirrelMail version"
inurl:metaframexp/default/login.asp | intitle:"Metaframe XP Login"
<strong>
</strong>inurl:mewebmail
inurl:names.nsf?opendatabase
inurl:oc w_login_username
inurl:orasso.wwsso_app_admin.ls_login
inurl:postfixadmin intitle:"postfix admin" ext:php
inurl:searc h/admin.php
inurl:textpattern/index.php
inurl:WCP_USER
inurl:webmail./index.pl "Interface"
inurl:webvpn.html "login" "Please enter your"
Login ("
Jetbox One CMS â?¢" | "
Jetstream ? *")
Novell NetWare intext:"netware management portal version"
Outlook Web Ac c ess (a better way)
PhotoPost PHP Upload
PHPhotoalbum Statistic s
PHPhotoalbum Upload
phpWebMail
Please enter a valid password! inurl:polladmin
INDEXU
Ultima Online loginservers
W-Nailer Upload Area
intitle:"Doc uShare" inurl:"docushare/dsweb/" -faq -gov -edu
"#mysql dump" filetype:sql
"#mysql dump" filetype:sql 21232f297a57a5a743894a0e4a801fc3
"allow_call_time_pass_referenc e" "PATH_INFO"
"Certific ate Prac tice Statement" inurl:(PDF | DOC)
"Generated by phpSystem"
"generated by wwwstat"
"Host Vulnerability Summary Report"
"HTTP_FROM=googlebot" googlebot.c om "Server_Software="
"Index of" / "c hat/logs"
"Installed Objects Sc anner" inurl:default.asp
"MacHTTP" filetype:log inurl:mac http.log
"Mecury Version" "Infastruc ture Group"
"Mic rosoft (R) Windows * (TM) Version * DrWtsn32 Copyright (C)" ext:log
"Most Submitted Forms and s•ri•ts" "this sec tion"
"Network Vulnerability Assessment Report"
"not for distribution" confidential
"not for public release" -.edu -.gov -.mil
"phone * * *" "address *" "e-mail" intitle:"c urriculum vitae"
"phpMyAdmin" "running on" inurl:"main.php"
"produced by getstats"
"Request Details" "Control Tree" "Server Variables"
"robots.txt" "Disallow:" filetype:txt
"Running in Child mode"
"sets mode: +p"
"sets mode: +s"
"Thank you for your order" +rec eipt
"This is a Shareaza Node"
"This report was generated by WebLog"
( filetype:mail | filetype:eml | filetype:mbox | filetype:mbx ) intext:password|subject
(intitle:"PRTG Traffic Grapher" inurl:"allsensors")|(intitle:"PRTG Traffic Grapher - Monitoring
Results")
(intitle:WebStatistica inurl:main.php) | (intitle:"WebSTATISTICA server") -inurl:statsoft -

inurl:statsoftsa -inurl:statsoftinc.c om -edu -software -rob
(inurl:"robot.txt" | inurl:"robots.txt" ) intext:disallow filetype:txt
+":8080" +":3128" +":80" filetype:txt
+"HSTSNR" -"netop.com"
-site:php.net -"The PHP Group" inurl:sourc e inurl:url ext:pHp
94FBR "ADOBE PHOTOSHOP"
AIM buddy lists
allinurl:/examples/jsp/snp/snoop.jsp
allinurl:c dkey.txt
allinurl:servlet/SnoopServlet
cgiirc.c onf
cgiirc.c onf
contac ts ext:wml
data filetype:mdb -site:gov -site:mil
exported email addresses
ext:(doc | pdf | xls | txt | ps | rtf | odt | sxw | psw | ppt | pps | xml) (intext:c onfidential
salary | intext:"budget approved") inurl:c onfidential
ext:asp inurl:pathto.asp
ext:cc m c c m -catac omb
ext:CDX CDX
ext:cgi inurl:editc gi.c gi inurl:file=
ext:conf inurl:rsync d.c onf -cvs -man
ext:conf NoCatAuth -cvs
ext:dat bpk.dat
ext:gho gho
ext:ics ic s
ext:ini intext:env.ini
ext:jbf jbf
ext:ldif ldif
ext:log "Software: Microsoft Internet Information Servic es *.*"
ext:mdb inurl:*.mdb inurl:fpdb shop.mdb
ext:nsf nsf -gov -mil
ext:plist filetype:plist inurl:bookmarks.plist
ext:pqi pqi -database
ext:reg "username=*" putty
ext:txt "Final enc ryption key"
ext:txt inurl:dxdiag
ext:vmdk vmdk
ext:vmx vmx
filetype:asp DBQ=" * Server.MapPath("*.mdb")
filetype:bkf bkf
filetype:blt "buddylist"
filetype:blt blt +intext:screenname
filetype:c fg auto_inst.c fg
filetype:c nf inurl:_vti_pvt ac c ess.cnf
filetype:c onf inurl:firewall -intitle:c vs
filetype:c onfig web.config -CVS
filetype:c tt Contac t
filetype:c tt ctt messenger
filetype:eml eml +intext:"Subject" +intext:"From" +intext:"To"
filetype:fp3 fp3
filetype:fp5 fp5 -site:gov -site:mil -"c vs log"
filetype:fp7 fp7
filetype:inf inurl:c apolicy.inf
filetype:lic lic intext:key
filetype:log acc ess.log -CVS
filetype:log c ron.log
10/11/2008 All Google Hacking Keywords
http://64.233.183.104/search?q=cac… 9/16
filetype:mbx mbx intext:Subject
filetype:myd myd -CVS
filetype:ns1 ns1
filetype:ora ora
filetype:ora tnsnames
filetype:pdb pdb backup (Pilot | Pluc kerdb)
filetype:php inurl:index inurl:phpicalendar -site:sourceforge.net
filetype:pot inurl:john.pot
filetype:PS ps
filetype:pst inurl:"outlook.pst"
filetype:pst pst -from -to -date
filetype:qbb qbb
filetype:QBW qbw
filetype:rdp rdp
filetype:reg "Terminal Server Client"
filetype:vcs vc s
filetype:wab wab
filetype:xls -site:gov inurl:c ontac t
filetype:xls inurl:"email.xls"
Financ ial spreadsheets: financ e.xls
Financ ial spreadsheets: financ es.xls
Ganglia Cluster Reports
haccess.c tl (one way)
haccess.c tl (VERY reliable)
ICQ c hat logs, please...
intext:"Session Start * * * *:*:* *" filetype:log
intext:"Tobias Oetiker" "traffic analysis"
intext:(password | passcode) intext:(username | userid | user) filetype:c sv
intext:gmail invite intext:http://gmail.google.c om/gmail/a
intext:SQLiteManager inurl:main.php
intext:ViewCVS inurl:Settings.php
intitle:"admin panel" +"
RedKernel"
intitle:"Apac he::Status" (inurl:server-status | inurl:status.html | inurl:apac he.html)
intitle:"AppServ Open Project" -site:www.appservnetwork.c om
intitle:"ASP Stats Generator *.*" "ASP Stats Generator" "2003-2004 weppos"
intitle:"Big Sister" +"OK Attention Trouble"
intitle:"curric ulum vitae" filetype:doc
intitle:"edna:streaming mp3 server" -forums
intitle:"FTP root at"
intitle:"index of" +myd size
intitle:"Index Of" -inurl:maillog maillog size
intitle:"Index Of" cookies.txt size
intitle:"index of" mysql.c onf OR mysql_c onfig
intitle:"Index of" upload size parent directory
intitle:"index.of *" admin news.asp configview.asp
intitle:"index.of" .diz .nfo last modified
intitle:"Joomla - Web Installer"
intitle:"LOGREP - Log file reporting system" -site:itefix.no
intitle:"Multimon UPS status page"
intitle:"PHP Advanc ed Transfer" (inurl:index.php | inurl:showrec ent.php )
intitle:"PhpMyExplorer" inurl:"index.php" -cvs
intitle:"statistic s of" "advanc ed web statistic s"
intitle:"System Statistics" +"System and Network Information Center"
intitle:"urc hin (5|3|admin)" ext:cgi
intitle:"Usage Statistics for" "Generated by Webalizer"
intitle:"wbem" compaq login "Compaq Information Tec hnologies Group"
</code></pre>

```markdown
intitle:"Web Server Statistic s for ****"
intitle:"web server status" SSH Telnet
intitle:"Welcome to F-Sec ure Policy Manager Server Welc ome Page"
intitle:"welc ome.to.squeezebox"
intitle:admin intitle:login
intitle:Bookmarks inurl:bookmarks.html "Bookmarks
intitle:index.of "Apac he" "server at"
intitle:index.of c leanup.log
intitle:index.of dead.letter
intitle:index.of inbox
intitle:index.of inbox dbx
intitle:index.of ws_ftp.ini
intitle:intranet inurl:intranet +intext:"phone"
inurl:"/axs/ax-admin.pl" -s•ri•t
inurl:"/c ricket/grapher.cgi"
inurl:"bookmark.htm"
inurl:"c acti" +inurl:"graph_view.php" +"Settings Tree View" -cvs -RPM
inurl:"newsletter/admin/"
inurl:"newsletter/admin/" intitle:"newsletter admin"
inurl:"putty.reg"
inurl:"smb.conf" intext:"workgroup" filetype:c onf conf
inurl:*db filetype:mdb
inurl:/cgi-bin/pass.txt
inurl:/_layouts/settings
inurl:admin filetype:xls
inurl:admin intitle:login
inurl:bac kup filetype:mdb
inurl:build.err
inurl:cgi-bin/printenv
inurl:cgi-bin/testcgi.exe "Please distribute TestCGI"
inurl:changepassword.asp
inurl:ds.py
inurl:email filetype:mdb
inurl:fc gi-bin/ec ho
inurl:forum filetype:mdb
inurl:forward filetype:forward -c vs
inurl:getmsg.html intitle:hotmail
inurl:log.nsf -gov
inurl:main.php phpMyAdmin
inurl:main.php Welc ome to phpMyAdmin
inurl:netsc ape.hst
inurl:netsc ape.hst
inurl:netsc ape.ini
inurl:odbc.ini ext:ini -c vs
inurl:perl/printenv
inurl:php.ini filetype:ini
inurl:preferenc es.ini "[emule]"
inurl:profiles filetype:mdb
inurl:report "EVEREST Home Edition "
inurl:server-info "Apac he Server Information"
inurl:server-status "apac he"
inurl:snitz_forums_2000.mdb
inurl:ssl.c onf filetype:conf
inurl:tdbin
inurl:vbstats.php "page generated"
inurl:wp-mail.php + "There doesn't seem to be any new mail."
inurl:XcCDONTS.asp

ipsec .conf
ipsec .secrets
ipsec .secrets
Lotus Domino address books
mail filetype:c sv -site:gov intext:name
Mic rosoft Money Data Files
mt-db-pass.c gi files
MySQL tabledata dumps
mystuff.xml - Trillian data files
OWA Public Folders (direct view)
Peoples MSN c ontac t lists
php-addressbook "This is the addressbook for *" -warning
phpinfo()
phpMyAdmin dumps
phpMyAdmin dumps
private key files (.c sr)
private key files (.key)
Quicken data files
rdbqds -site:.edu -site:.mil -site:.gov
robots.txt
site:edu admin grades
site:www.mailinator.c om inurl:ShowMail.do
SQL data dumps
Squid c ache server reports
Unreal IRCd
WebLog Referrers
Welcome to ntop!
Fic hier contenant des informations sur le r?seau :
filetype:log intext:"Connec tionManager2"
"apric ot - admin" 00h
"by Reimar Hoven. All Rights Reserved. Disclaimer" | inurl:"log/logdb.dta"
"Network Host Assessment Report" "Internet Sc anner"
"Output produced by SysWatc h *"
"Phorum Admin" "Database Connec tion" inurl:forum inurl:admin
"phpOpenTrac ker" Statistic 
"powered | performed by Beyond Security's Automated Sc anning" -kazaa -example
"Shadow Sec urity Sc anner performed a vulnerability assessment"
"SnortSnarf alert page"
"The following report c ontains c onfidential information" vulnerability -search
"The statistics were last upd•t•d" "Daily"-mic rosoft.com
"this proxy is working fine!" "enter *" "URL***" * visit
"This report lists" "identified by Internet Sc anner"
"Traffic Analysis for" "RMON Port * on unit *"
"Version Info" "Boot Version" "Internet Settings"
((inurl:ifgraph "Page generated at") OR ("This page was built using ifgraph"))
Analysis Console for Incident Databases
ext:cfg radius.c fg
ext:cgi intext:"nrg-" " This web page was c reated on "
filetype:pdf "Assessment Report" nessus
filetype:php inurl:ipinfo.php "Distributed Intrusion Detec tion System"
filetype:php inurl:nqt intext:"Network Query Tool"
filetype:vsd vsd network -samples -examples
intext:"Welc ome to the Web V.Networks" intitle:"V.Networks [Top]" -filetype:htm
10/11/2008 All Google Hacking Keywords
http://64.233.183.104/search?q=cac… 12/16
intitle:"ADSL Configuration page"
intitle:"Azureus : Java BitTorrent Client Trac ker"
intitle:"Belarc Advisor Current Profile" intext:"Clic k here for Belarc's PC Management
produc ts, for large and small c ompanies."
intitle:"BNBT Trac ker Info"
intitle:"Mic rosoft Site Server Analysis"
intitle:"Nessus Scan Report" "This file was generated by Nessus"
intitle:"PHPBTTrac ker Statistic s" | intitle:"PHPBT Trac ker Statistic s"
intitle:"Retina Report" "CONFIDENTIAL INFORMATION"
intitle:"start.managing.the.devic e" remote pbx ac c
intitle:"sysinfo * " intext:"Generated by Sysinfo * written by The Gamblers."
intitle:"twiki" inurl:"TWikiUsers"
inurl:"/c atalog.nsf" intitle:catalog
inurl:"install/install.php"
inurl:"map.asp?" intitle:"WhatsUp Gold"
inurl:"NmConsole/Login.asp" | intitle:"Login - Ipswitch WhatsUp Professional 2005" |
intext:"Ipswitch WhatsUp Professional 2005 (SP1)" "Ipswitch, Inc"
inurl:"sitescope.html" intitle:"sitesc ope" intext:"refresh" -demo
inurl:/adm-cfgedit.php
inurl:/cgi-bin/finger? "In real life"
inurl:/cgi-bin/finger? Enter (ac count|host|user|username)
inurl:/counter/index.php intitle:"+PHPCounter 7.*"
inurl:CrazyWWWBoard.c gi intext:"detailed debugging information"
inurl:login.jsp.bak
inurl:ovc gi/jovw
inurl:phpSysInfo/ "created by phpsysinfo"
inurl:portsc an.php "from Port"|"Port Range"
inurl:proxy | inurl:wpad ext:pac | ext:dat findproxyforurl
inurl:statrep.nsf -gov
inurl:status.c gi?host=all
inurl:testcgi xitami
inurl:webalizer filetype:png -.gov -.edu -.mil -opendarwin
inurl:webutil.pl
Looking Glass
site:netc raft.c om intitle:That.Site.Running Apache
"A syntax error has oc c urred" filetype:ihtml
"access denied for user" "using password"
"An illegal c haracter has been found in the statement" -"previous message"
"ASP.NET_SessionId" "data sourc e="
"Can't c onnect to loc al" intitle:warning
"Chatologica MetaSearch" "stac k trac king"
"detec ted an internal error [IBM][CLI Driver][DB2/6000]"
"error found handling the request" c oc oon filetype:xml
"Fatal error: Call to undefined function" -reply -the -next
"Incorrect syntax near"
"Incorrect syntax near"
"Internal Server Error" "server at"
"Invision Power Board Database Error"
"ORA-00933: SQL c ommand not properly ended"
"ORA-12541: TNS:no listener" intitle:"error occurred"
"Parse error: parse error, unexpected T_VARIABLE" "on line" filetype:php
"PostgreSQL query failed: ERROR: parser: parse error"
"Supplied argument is not a valid MySQL result resourc e"
"Syntax error in query expression " -the
"The s•ri•t whose uid is " "is not allowed to ac cess"
"There seems to have been a problem with the" " Please try again by c licking the Refresh
button in your web browser."

"Unable to jump to row" "on MySQL result index" "on line"
"Unc losed quotation mark before the c harac ter string"
"Warning: Bad arguments to (join|implode) () in" "on line" -help -forum
"Warning: Cannot modify header information - headers already sent"
"Warning: Division by zero in" "on line" -forum
"Warning: mysql_connec t(): Ac c ess denied for user: '*@*" "on line" -help -forum
"Warning: mysql_query()" "invalid query"
"Warning: pg_connec t(): Unable to c onnec t to PostgreSQL server: FATAL"
"Warning: Supplied argument is not a valid File-Handle resource in"
"Warning:" "failed to open stream: HTTP request failed" "on line"
"Warning:" "SAFE MODE Restriction in effect." "The s•ri•t whose uid is" "is not allowed to
ac c ess owned by uid 0 in" "on line"
"SQL Server Driver][SQL Server]Line 1: Inc orrec t syntax near"
An unexpected token "END-OF-STATEMENT" was found
Coldfusion Error Pages
filetype:asp + "[ODBC SQL"
filetype:asp "Custom Error Message" Category Sourc e
filetype:log "PHP Parse error" | "PHP Warning" | "PHP Error"
filetype:php inurl:"logging.php" "Discuz" error
ht://Dig htsearch error
IIS 4.0 error messages
IIS web server error messages
Internal Server Error
intext:"Error Message : Error loading required libraries."
intext:"Warning: Failed opening" "on line" "include_path"
intitle:"Apac he Tomc at" "Error Report"
intitle:"Default PLESK Page"
intitle:"Error Oc curred While Processing Request" +WHERE (SELECT|INSERT) filetype:cfm
intitle:"Error Oc curred" "The error occ urred in" filetype:c fm
intitle:"Error using Hypernews" "Server Software"
intitle:"Exec ution of this s•ri•t not permitted"
intitle:"Under c onstruction" "does not currently have"
intitle:Configuration.File inurl:softc art.exe
MYSQL error message: supplied argument....
mysql error with query
Netscape Applic ation Server Error page
ORA-00921: unexpected end of SQL c ommand
ORA-00921: unexpected end of SQL c ommand
ORA-00936: missing expression
PHP application warnings failing "include_path"
sitebuilderc ontent
sitebuilderfiles
sitebuilderpictures
Snitz! forums db path error
SQL syntax error
Supplied argument is not a valid PostgreSQL result
warning "error on line" php sablotron
Windows 2000 web server error messages
"ftp://" "www.eastgame.net"
"html allowed" guestbook
"
: vBulletin Version 1.1.5"
"Select a database to view" intitle:"filemaker pro"
"set up the administrator user" inurl:pivot
"There are no Administrators Ac c ounts" inurl:admin.php -mysql_fetc h_row
"Welc ome to Administration" "General" "Loc al Domains" "SMTP Authentic ation" inurl:admin
"Welc ome to Intranet"
10/11/2008 All Google Hacking Keywords
http://64.233.183.104/search?q=cac… 14/16
"Welc ome to PHP-Nuke" congratulations
"Welc ome to the Prestige Web-Based Configurator"
"YaBB SE Dev Team"
"you c an now password" | "this is a special page only seen by you. your profile visitors"
inurl:imc haos
("Indexed.By"|"Monitored.By") hAc xFtpSc an
(inurl:/shop.cgi/page=) | (inurl:/shop.pl/page=)
allinurl:"index.php" "site=sglinks"
allinurl:install/install.php
allinurl:intranet admin
filetype:c gi inurl:"fileman.cgi"
filetype:c gi inurl:"Web_Store.cgi"
filetype:php inurl:vAuthentic ate
filetype:pl intitle:"Ultraboard Setup"
Gallery in c onfiguration mode
Hassan Consulting's Shopping Cart Version 1.18
intext:"Warning: * am able * write ** configuration file" "inc ludes/c onfigure.php" -
intitle:"Gateway Configuration Menu"
intitle:"Horde :: My Portal" -"[Tickets"
intitle:"Mail Server CMailServer Webmail" "5.2"
intitle:"MvBlog powered"
intitle:"Remote Desktop Web Connec tion"
intitle:"Samba Web Administration Tool" intext:"Help Workgroup"
intitle:"Terminal Services Web Connec tion"
intitle:"Uploader - Uploader v6" -pixloads.c om
intitle:osCommerc e inurl:admin intext:"redistributable under the GNU" intext:"Online Catalog"
-demo -site:oscommerce.com
intitle:phpMyAdmin "Welcome to phpMyAdmin ***" "running on * as root@*"
intitle:phpMyAdmin "Welcome to phpMyAdmin ***" "running on * as root@*"
inurl:"/NSearc h/AdminServlet"
inurl:"index.php? module=ew_filemanager"
inurl:aol*/_do/rss_popup?blogID=
inurl:footer.inc .php
inurl:info.inc .php
inurl:ManyServers.htm
inurl:newsdesk.cgi? inurl:"t="
inurl:pls/admin_/gateway.htm
inurl:rpSys.html
inurl:searc h.php vbulletin
inurl:servlet/webac c
natterc hat inurl:home.asp -site:natterchat.c o.uk
XOOPS Custom Installation
inurl:htpasswd filetype:htpasswd
inurl:yapboz_detay.asp
+ View Webcam User Accessing
allinurl:control/multiview
inurl:"ViewerFrame?Mode="
intitle:"WJ-NT104 Main Page"
inurl:netw_tcp.shtml
intitle:"supervisioncam protocol"
```

Thanks and let me know if you guys find any new operators.
