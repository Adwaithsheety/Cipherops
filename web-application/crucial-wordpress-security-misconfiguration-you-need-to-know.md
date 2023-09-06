---
cover: >-
  https://images.unsplash.com/photo-1599305445671-ac291c95aaa9?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw4fHx3b3JkcHJlc3N8ZW58MHx8fHwxNjkzOTg0MTM0fDA&ixlib=rb-4.0.3&q=85
coverY: 0
---

# 📃 Crucial WordPress Security Misconfiguration You Need to Know

## :heavy\_multiplication\_x: [<mark style="color:red;">Twitter</mark>](https://twitter.com/Cipher0ps\_tech?t=MlqumIay8I49eWwhjgrotg\&s=09) :link: [<mark style="color:red;">Linkedin</mark>](https://www.linkedin.com/company/cipherops/) :tv: [<mark style="color:red;">Telegram</mark>](https://t.me/cipherops\_tech) :tada: [<mark style="color:red;">Instagram</mark>](https://instagram.com/cipherops\_tech?igshid=MzNlNGNkZWQ4Mg==)

```markdown
# Common WordPress Security Misconfigurations

This document outlines various common security misconfigurations in WordPress, providing insights into how these issues can be detected, exploited, and references to learn more about them.

## Table of Contents
* [WordPress Detection](#wordpress-detection)
* [General Scan Tools](#general-scan-tools)
* [Admin Panel](#admin-panel)
* [CVE-2018-6389](#cve-2018-6389)
* [xmlrpc.php](#xmlrpcphp)
* [Denial of Service via Cronjob](#denial-of-service-via-cronjob)
* [Denial of Service via load-scripts.php (CVE-2018-6389)](#denial-of-service-via-load-scriptsphp-cve-2018-6389)
* [WP User Enumeration](#wp-user-enumeration)
* [Sensitive Files Exposed](#sensitive-files-exposed)
* [Bypassing 403 Errors](#bypassing-403-errors)
* [Enumerating Plugins](#enumerating-plugins)
* [Finding the Origin IP in WordPress](#finding-the-origin-ip-in-wordpress)
* [References](#references)

### WordPress Detection<a name="wordpress-detection"></a>
markdown
# WordPress Detection
# To identify if a website is using WordPress, employ technology detection tools such as:
# - Wappalyzer
# - WhatRuns
# - BuiltWith
```

#### General Scan Tools <a href="#general-scan-tools" id="general-scan-tools"></a>

```markdown
# General Scan Tools
# Various tools can help you scan WordPress installations for potential vulnerabilities, including:
# - WpScan
# - WPrecon
# - cms-checker
# - wpsec.com
# For more options, consult Infosec Matter.
```

#### Admin Panel <a href="#admin-panel" id="admin-panel"></a>

```markdown
# Admin Panel
# To locate the WordPress admin panel, simply append /login/ or /admin/ to the site's URL. 
# Example: www.example.com/admin/ or www.example.com/login/
# If the login URL doesn't function correctly, try accessing /wp-login.php.
# Alternatively, you can directly access the admin area via URLs like:
# - www.example.com/admin/
# - www.example.com/wp-admin/
# In case the admin panel is not found, visit /wp-admin/install.php.
```

#### CVE-2018-6389 <a href="#cve-2018-6389" id="cve-2018-6389"></a>

```markdown
# CVE-2018-6389
# This vulnerability can lead to a DoS (Denial of Service) attack on WordPress sites running versions prior to 4.9.3.
# Detection:
# Utilize the URL from the "loadsxploit" gist to receive an extensive JS data response.
# - loadsxploit
# Exploit:
# To exploit this vulnerability, you can employ a DoS tool such as "Doser," which quickly shuts down the web server.
# Example command:
# - python3 doser.py -t 999 -g 'https://site.com/fullUrlFromLoadsxploit'
# References:
# - HackerOne Report
# - CVE Details
# - Blog Post
```

#### xmlrpc.php <a href="#xmlrpcphp" id="xmlrpcphp"></a>

```markdown
# xmlrpc.php
# XML-RPC is a common vulnerability in WordPress that can be exploited for various purposes.
# Detection:
# To detect it, visit site.com/xmlrpc.php and look for error messages related to POST requests.
# Exploit:
# Intercept the request and modify the method from GET to POST.
# You can either list all methods or check for the presence of "pingback.ping" and perform actions like DDoS or SSRF.
# Tools for Automation:
# - XMLRPC-Scan
# References:
# - Bug Bounty Cheat Sheet
# - Medium Writeup
# - WpEngine Blog Post
```

#### Denial of Service via Cronjob <a href="#denial-of-service-via-cronjob" id="denial-of-service-via-cronjob"></a>

```markdown
# Denial of Service via Cronjob
# This vulnerability can be exploited to perform a DoS attack on a WordPress site.
# Detection:
# To detect it, visit site.com/wp-cron.php and look for a blank page with a 200 HTTP status code.
# Exploit:
# You can use the same tool, "Doser," to exploit this vulnerability.
# Example command:
# - python3 doser.py -t 999 -g 'https://site.com/wp-cron.php'
# Reference:
# - GitHub Issue
# - Medium Writeup
```

#### Denial of Service via load-scripts.php (CVE-2018-6389) <a href="#denial-of-service-via-load-scriptsphp-cve-2018-6389" id="denial-of-service-via-load-scriptsphp-cve-2018-6389"></a>

```markdown
# Denial of Service via load-scripts.php (CVE-2018-6389)
# In WordPress versions through 4.9.2, an attacker can load multiple JS and CSS files through "load-scripts.php" files at once.
# This can lead to resource depletion and launch DoS attacks.
# Exploit:
# Example URL:
# - http://example.com/wp-admin/load-scripts.php?load=react,react-dom,moment,lodash...
# Reference:
# - HackerOne Report
```

#### WP User Enumeration <a href="#wp-user-enumeration" id="wp-user-enumeration"></a>

```markdown
# WP User Enumeration
# This issue becomes significant when a target WordPress website hides user information or restricts public access.
# Methods:
# - CVE-2017-5487
#   - Visit site.com/wp-json/wp/v2/users/ to retrieve user info in JSON format.
#   - If you encounter a 403 error, you can attempt bypass methods.
# - /?author=1
#   - Example URL: http://target.com/?author=1

 (increment the number for more)
# - User Enumeration with Admin Panel
#   - Access to the admin panel can reveal valid usernames.
# Exploit:
# If you have xmlrpc.php and user enumeration both present, you can chain them together by collecting usernames from wp-json and performing brute-force attacks via xmlrpc.php.
# Example XMLRPC brute-force request:
# <methodCall>
#     <methodName>wp.getUsersBlogs</methodName>
#     <params>
#         <param><value>admin</value></param>
#         <param><value>pass</value></param>
#     </params>
# </methodCall>
# References:
# - HackerOne Report
```

#### Sensitive Files Exposed <a href="#sensitive-files-exposed" id="sensitive-files-exposed"></a>

```markdown
# Sensitive Files Exposed
# Here's a list of files that can expose sensitive data on a WordPress site.
# - wp-includes
# - wp-content/uploads
# - wp-content/debug.log
# - Wp-load
# - Wp-json
# - index.php
# - wp-login.php
# - wp-links-opml.php
# - wp-activate.php
# - ...
```

#### Bypassing 403 Errors <a href="#bypassing-403-errors" id="bypassing-403-errors"></a>

```markdown
# Bypassing 403 Errors
# To bypass WordPress 403 pages, you can use the following techniques:
# - X-Rewrite-Url Header: Use the X-Rewrite-Url header to specify URLs like xmlrpc.php, wp-json/v2/users, or wp-login.php.
# Example:
# POST /xmlrpc HTTP/1.1        
# Host: http://target.com
# X-Rewrite-Url: xmlrpc.php
# X-Rewrite-Url: wp-json/v2/users
# X-Rewrite-Url: wp-login.php
# Authorization Bypass: Explore endpoint bypass payloads to bypass 403 errors.
# Example endpoint bypass payloads:
# - ?
# - ??
# - &
# - ...
# Tools for Bypassing 403:
# - 403bypasser
# - bypass-403
# References:
# - GitHub Repositories
```

#### Enumerating Plugins <a href="#enumerating-plugins" id="enumerating-plugins"></a>

```markdown
# Enumerating Plugins
# Don't forget to enumerate plugins on a WordPress target by checking "/wp-content/plugins/FUZZ/readme.txt."
# Look for the stable tag and find CVEs or exploits for those plugin versions.
# You can also use the following command:
# - grep all "wp-content/plugins/" from html
# Explore common exploits at:
# - WordPress Exploits Repository
# References:
# - GitHub Repository
```

#### Finding the Origin IP in WordPress <a href="#finding-the-origin-ip-in-wordpress" id="finding-the-origin-ip-in-wordpress"></a>

```markdown
# Finding the Origin IP in WordPress
# If a WordPress site is protected by a Web Application Firewall (WAF), you can brute force "GET /wp-json/wp/v2/media/§1§" to uncover the real IP address.
# In some cases, you might receive a 200 OK response, revealing the real IP in routing.
```

#### References <a href="#references" id="references"></a>

```markdown
# References
# This section contains valuable resources and references for further learning and research.
# - Twitter Handles
# - GitHub Repositories
# - Medium Posts
# - Bug Bounty Reports
# - WordPress Security Blogs
# - ...
```

Please note that this document provides information and commands in a structured and professional format for addressing common WordPress security misconfiguration.
