
# 1 powershell 

https://github.com/sk82jack/GcloudTabComplete

Installing the module
You can install it using:
```powershell
PS> Install-Module -Name GcloudTabComplete
```

Updating GcloudTabComplete
Once installed from the PowerShell Gallery, you can update it using:
```powershell
PS> Update-Module -Name GcloudTabComplete
```

Uninstalling GcloudTabComplete
To uninstall GcloudTabComplete:
```powershell
PS> Uninstall-Module -Name GcloudTabComplete
```


powershell configuration file 中加入

```
# Import google cloud CLI autocompeltion
Import-Module GcloudTabComplete

```


# 2 bash zsh fish 

https://cloud.google.com/distributed-cloud/hosted/docs/latest/gdch/resources/gdcloud-auto-completion

