# Optional folder setup (VirtualBox)

```powershell
<#
  Author: Steve Grimstead (Prohtius)
  Date: 08-20-2025
  Version: 1.0
  Target OS: Microsoft Windows
  Purpose: Creates new webclient, then uses webclient to download the MS Server 2016 ISO image and save it to the destination.  
#>

#-----------------------------------------------------
#|  Change variables in this section as needed       |
#-----------------------------------------------------

#----- Change drive letter as needed         -----
$target_drive = "C:"

$folder_path = "$($target_drive)\tmp\vBox"

#-----------------------------------------------------
#|  End change variables section                     |
#-----------------------------------------------------

$sub_folders = @(
    "vhds",
    "vms"
)

foreach ($sub_folder in $sub_folders)
{
    $target_path = "$($folder_path)\$($sub_folder)"    

    if (!(Test-Path -Path "$($target_path)")) 
    {
        Write-Host -Message "$($target_path) does not exist, creating" -ForegroundColor Yellow

        try
        {
            new-item -itemtype directory -path "$($folder_path)" -name $sub_folder
        }
        catch 
        {
            Write-Error $_.Exception.Message
        }
    }
}

```

# Installing Hypervisors

## Virtualbox
### Windows 11
### Requirements
1. [Download VirtualBox](https://download.virtualbox.org/virtualbox/7.2.2/VirtualBox-7.2.2-170484-Win.exe)<br/>
```
https://download.virtualbox.org/virtualbox/7.2.2/VirtualBox-7.2.2-170484-Win.exe
```

3. [Download Microsoft Visual C++ 2019 Redistributable](https://aka.ms/vs/17/release/vc_redist.x64.exe)<br/>
```
https://aka.ms/vs/17/release/vc_redist.x64.exe
```

5. 

1. Install the following Windows Features
   a. Virtual Machine Platform
   b. Windows Hypervisor Platform  
3. 

### Linux (Ubuntu)

## VMWare Workstation Pro
### Windows 11 

### Linux (Ubuntu)

## Hyper-V
### Windows 11 Pro

[Download Microsoft Evalutaion Links](https://github.com/Prohtius/PowerShell/blob/4239c301b6fe9a9b0a111b7dc77fb7ba355c09da/evaluation_downloads/raw_links.md)
