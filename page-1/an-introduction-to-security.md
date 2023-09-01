# AN INTRODUCTION TO SECURITY

As security researchers and pentesters know, Information Gathering has been overlooked by some, and not given the proper attention it deserves. Nevertheless, it remains to be a vital phase in the pentesting process.\
This blog post will give different tools to do basic recon in a pentest engagement since no one only relies on one tool. More advanced recon techniques will be covered in part 2 of this blog.

### The Tools-set Under Different Categories

### Subject 1. Sub domain Enumeration.

In most cases, say in a bug bounty play, most vulnerabilities may not lie in the main domain. Sub domain hunting comes in handy. Lets look at some ways of sub domain enumeration and discovery.

#### a. Knockpy

Knockpy is a handy tool for this purpose. It uses a wordlist that can be customized to fit your target attack.\
![](https://sylarsec.com/wp-content/uploads/2018/06/screenshot-from-2018-06-15-10-55-22-1.png?w=756)

#### b. Sublist3r

As a tool mentioned by pentesters and bug bounty hunters all over the internet, this is a must try.\
[Sublist3r](https://github.com/aboul3la/Sublist3r) relies purely on OSINT techniques. It crawls different search engines including Google, Baidu, Yahoo, Ask  etc. Sub domain enumeration also possible via DNSdumpster, Netcraft, Virus total among others.\
![](https://sylarsec.com/wp-content/uploads/2018/06/screenshot-from-2018-06-17-16-31-17-1.png?w=656)

#### c. Google dorks

Google as the most popular search engine caches all sorts of websites. This makes it a good tool to find sub domains visited. We just need to know how to ask. Using ‘google.com’ as an example, we can easily do this, exposing the sub domains.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-15-14-21-1.png?w=740)\
Some good scripts also exist that automate google dorking. Here are 2:

* **GoogD0rker**

This one automatically launches a series of queries against the specified target. Great OSINT tool. The tool is able to find documents, login pages, backdoors, files by extension, pastebin posts, subdomains etc.\
Download it [here](https://github.com/ZephrFish/GoogD0rker).\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-22-43-13-1.png)

* **GooHak**

Similar to the above. Find it [here](https://github.com/1N3/Goohak/).

#### d. Amass

An OWASP tool for sub domain discovery that uses multiple sources to do this. More info can be found on their [git](https://github.com/OWASP/Amass) page.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-15-29-01-1.png)

#### e. Curl one liner

This is a cool script i found on twitter from [Ben Sadeghipour](https://twitter.com/NahamSec)‘s tweet. Its pretty simple and uses _archive.org_ to scrape the sub domains.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-15-37-27-1.png?w=740)\
\==>”_curl -s “https://web.archive.org/cdx/search/cdx?url=\*.testfire.net/\*\&output=text\&fl=original\&collapse=urlkey” |sort| sed -e ‘s\_https\*://\_\_’ -e “s/\\/.\*//” -e ‘s/:.\*//’ -e ‘s/^www\\.//’ | uniq_“<==

#### f. Confirm live domains

During my hunts, i found out a number of the domains discovered from tools that do mass scraping do not resolve. In this case, i wrote a simple bash script that given a text file with all the valid sub domains, goes through them all and tries to resolve them and find out which ones don’t. Download it [here.](https://github.com/i-sylar/Useful-linux-scripts/blob/master/curl/url\_exists.sh)\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-16-48-29-1.png?w=740)

### &#x20;Subject 2. Web Server Fingerprinting.

### culprit: HTTP Methods

#### a. Curl

Curl is a pretty powerful CLI tool. Despite being used by pentesters to exploit file inclusions (RFI, LFI), command injections, HTTP file uploads etc, it can also be used to identify a HTTP methods allowed on the server. Some servers however have OPTIONS disabled, we can use HEAD instead.\
![](https://sylarsec.com/wp-content/uploads/2018/06/screenshot-from-2018-06-17-17-04-11-1.png?w=656)\
Dangerous methods like TRACE and PUT should not be allowed. On exploitation of PUT, check out NMAP [scripts,](https://nmap.org/nsedoc/scripts/http-put.html) tools like burp and browser add-ons like [poster.](https://addons.mozilla.org/en-US/firefox/addon/poster/)

#### b. NMAP

Weaponizing nmap scripts can come in handy.\
![](https://sylarsec.com/wp-content/uploads/2018/06/screenshot-from-2018-06-17-17-08-03-1.png?w=656)

#### c. My rudimentary curl script

I wrote this simple script to print out the response headers for a list of servers in a text file. However if the OPTIONS method is enabled on the server, we can get the list of allowed methods on the server. See it [here](https://github.com/i-sylar/Useful-linux-scripts/blob/master/curl/curl\_them\_all.sh). This includes a simple http(s) check using wget for the list of servers. As usual, this can be improved/modified.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-17-37-31-1.png?w=740)\
_N/B. netcat, nikto can also be used for this._\
&#x20;

### culprit: Application Mapping

In an attempt to attack an application, we have to understand its working, architecture and underlying technologies.

#### Identifying technology used

* Wappalyzer

This is a browser extension that identifies an applications underlying technologies. This may include the language used, development frameworks, CMS, analytics frameworks etc. It runs on both firefox and google chrome.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-18-04-24-1.png)

* Whatruns

Another browser plugin that works the same way. Just a bit more aggressive.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-09-18-05-21-1.png)

* WafW00f (Firewall discovery)

So we want to actively interact with the target. However different probes might get blocked by a possible security solution like a WAF. If so we can identify the WAF in use by using [sandrogauci ](https://twitter.com/sandrogauci)‘s tool, WafW00f that can be found [here](https://github.com/EnableSecurity/wafw00f).\
![](https://sylarsec.com/wp-content/uploads/2019/01/firewall-1.png?w=740)

#### Content discovery

* dirb

Very comprehensive directory/file bruteforce tool that uses a custom word list to find the directories or files that exists. This happens to be my favorite.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-10-00-17-40-1.png?w=740)

* dirsearch

Similar to dirb but with some fancy colors for easier status identification. Searches for both files and directories as well. This has the ability to specify extensions. e.g php, txt, rar, zip etc.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-10-00-13-52-1.png?w=740)

* dir buster

Another one by OWASP. With a cool looking GUI, it does file and content discovery with an option to specify custom word list. Also comes with a cool set of word lists. Can be found [here](https://www.owasp.org/index.php/Category:OWASP\_DirBuster\_Project)\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-12-00-23-56-1.png)

* nikto

From banner grabbing, header analysis, light default directory/file discovery, nikto is pretty handy. Also offers some suggestions and advisory info for why the discovered issues are dangerous.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-00-39-22-1-1.png?w=740)

* Aquatone

It gives a visual representation of the websites listed on a text file. This helps easily map out the best attack surface. For example, makes it easy to find login pages without manually visiting the pages. It takes screenshots of the pages and saves them to a folder. Also includes headers.\
It also has other modules i.e. scan, discovery, gather, takeover that will be discussed on part 2 of this blog.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-10-01-21-31-1.png?w=740)

* burp intruder

Burp’s intruder also serves as a multipurpose tool. In this context it can be used to bruteforce files, directories, GET params etc while observing status codes as well as content length.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-21-35-41-1.png)

* **The perfect wordlist for the job**

All these tools wont give a heavy punch without a good set of word lists. From my research i discovered [seclist](https://github.com/danielmiessler/SecLists). Probably as comprehensive as it gets. Coupled with different usernames, passwords, URLs, payloads etc. It earns the ‘ultimate wordlist’ title.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-18-36-04-1.png)

#### **N/B: Discovering ‘hidden’ GET/POST parameters.**

During pentesting or bug bounty hunting, the best way to attack a page is on inputs. Hence parameters are really important. If we cant find them on the first look, its possible to try and find the ‘_hidden_‘ parameters using different tools.

* Arjun

One tool by [UltimateHackers](https://github.com/UltimateHackers/Arjun) comes to mind. Arjun is a script that helps bruteforce these parameters using a word list that can be customized.\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-13-08-11-1.png)

* Parameth

This one worked for me a while back. Does the same. But i still prefer Arjun.

### culprit: Other search engines

While google might be the most popular search engine, its not the only one. And if you’re gonna be finding vulnerabilities, then you most likely need these 2 as well…

* shodan ([shodan.io](https://www.shodan.io/))

Hands down the ultimate IoT search engine. Same as Google, it uses ‘dorks’ for smarter searches and improve on what it finds. Its right [here](https://www.shodan.io/).\
![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-12-35-26-1.png)

&#x20; Some common dorks may include:

> * _country_: find devices in a certain country
> * _hostname_: find devices matching the given hostname
> * _port_: find devices on given open ports
> * _os_: return results that match the given OS
> * _before/after_: find results within a given time frame
> * _city_: find devices in a certain city

* **Censys (**[**censys.io**](https://censys.io/)**)**

Kinda like shodan, it compares to the fact that it can also search for devices accessible from the internet.\
Lets find _debian_ servers running _ssh_ from _Africa_ using the query

> “_22.ssh.v2.metadata.product:”OpenSSH” AND metadata.os:”Debian” AND location.continent:”Europe”_

![](https://sylarsec.com/wp-content/uploads/2019/01/screenshot-from-2019-01-11-16-22-03-1.png)

&#x20; Have fun with the 100 ways of discovery. Part 2 coming soon.
