# Cloud Pen-testing Part -4

````markdown
## Other AWS Tools

### WeirdAAL
https://github.com/carnal0wnage/weirdAAL

Run recon against all AWS services to enumerate access for a set of keys

```shell
python3 weirdAAL.py -m recon_all -t <name>
````

#### Pacu

AWS exploitation framework https://github.com/RhinoSecurityLabs/pacu

Install Pacu

```shell
sudo apt-get install python3-pip
git clone https://github.com/RhinoSecurityLabs/pacu
cd pacu
sudo bash install.sh
```

Import AWS keys for a specific profile

```shell
import_keys <profile name>
```

Detect if keys are honey token keys

```shell
run iam__detect_honeytokens
```

Enumerate account information and permissions

```shell
run iam__enum_users_roles_policies_groups
run iam__enum_permissions
whoami
```

Check for privilege escalation

```shell
run iam__privesc_scan
```

### Google Cloud Platform CLI Tool Cheatsheet

#### Authentication

Authentication with gcloud

```shell
# User identity login
gcloud auth login

# Service account login
gcloud auth activate-service-account --key-file creds.json
```

List accounts available to gcloud

```shell
gcloud auth list
```

#### Account Information

Get account information

```shell
gcloud config list
```

List organizations

```shell
gcloud organizations list
```

Enumerate IAM policies set ORG-wide

```shell
gcloud organizations get-iam-policy <org ID>
```

Enumerate IAM policies set per project

```shell
gcloud projects get-iam-policy <project ID>
```

List projects

```shell
gcloud projects list
```

Set a different project

```shell
gcloud config set project <project name>
```

Gives a list of all APIs that are enabled in the project

```shell
gcloud services list
```

Get source code repos available to the user

```shell
gcloud source repos list
```

Clone repo to home dir

```shell
gcloud source repos clone <repo_name>
```
