# Cloud Pen-testing Part-1

````markdown
## Microsoft Azure & O365 CLI Tool Cheatsheet

### Az PowerShell Module

Import-Module Az

### Authentication

Connect to Azure with account credentials

```powershell
Connect-AzAccount
````

Alternatively, if MFA restrictions are in place

```powershell
$credential = Get-Credential
Connect-AzAccount -Credential $credential
```

#### Import a context file

```powershell
Import-AzContext -Profile 'C:\Temp\Live Tokens\StolenToken.json'
```

#### Export a context file

```powershell
Save-AzContext -Path C:\Temp\AzureAccessToken.json
```

#### Account Information

List the current Azure contexts available

```powershell
Get-AzContext -ListAvailable
```

Get context details

```powershell
$context = Get-AzContext
$context.Name
$context.Account
```

List subscriptions

```powershell
Get-AzSubscription
```

Choose a subscription

```powershell
Select-AzSubscription -SubscriptionID "SubscriptionID"
```

Get the current user's role assignment

```powershell
Get-AzRoleAssignment
```

#### List all resources and resource groups

```powershell
Get-AzResource
Get-AzResourceGroup
```

#### List storage accounts

```powershell
Get-AzStorageAccount
```

#### WebApps & SQL

List Azure web applications

```powershell
Get-AzAdApplication
Get-AzWebApp
```

List SQL servers

```powershell
Get-AzSQLServer
```

Individual databases can be listed with information retrieved from the previous command

```powershell
Get-AzSqlDatabase -ServerName $ServerName -ResourceGroupName $ResourceGroupName
```

List SQL Firewall rules

```powershell
Get-AzSqlServerFirewallRule –ServerName $ServerName -ResourceGroupName $ResourceGroupName
```

List SQL Server AD Admins

```powershell
Get-AzSqlServerActiveDirectoryAdminstrator -ServerName $ServerName -ResourceGroupName $ResourceGroupName
```

#### Runbooks

List Azure Runbooks

```powershell
Get-AzAutomationAccount
Get-AzAutomationRunbook -AutomationAccountName <AutomationAccountName> -ResourceGroupName <ResourceGroupName>
```

Export a runbook

```powershell
Export-AzAutomationRunbook -AutomationAccountName $AccountName -ResourceGroupName $ResourceGroupName -Name $RunbookName -OutputFolder .\Desktop\
```

