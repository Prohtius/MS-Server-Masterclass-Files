# Table of Contents
[PowerShell Commands](#powershell-commands)<br/>
[Check Event Logs (id: 4112)](#check-event-logs-for-event-id-4112)


# Folder Structure
```
D:/
├── Public-Shares
│   ├── Jedi
│   │   ├── Jedi Knights
│   │   ├── Jedi Masters
│   │   └── Padawans
│   └── Senate
│       ├── Senators
│       ├── Committees
│       └── Chancellor
├── Private-Shares
│   ├── Jedi
│   │   └── Secret Stuff
│   └── Senate
│       └── Other Secret Stuff
└── DFS-Links
    ├── Public-Shares
    │   ├── Jedi
    │   └── Senate
    └── Private-Shares
        ├── Jedi
        └── Senate
```

# Preseed Initial Replication

## PowerShell Commands
### New Replication Group
```powershell
New-DFSReplicationGroup -GroupName "<group_name>"
```
###### *New-DFSReplicationGroup -GroupName "DFS-Replication"*

### Add folder to Replication Group
```powershell
New-DFSRmember -GroupName "<group_name>" -FolderName "<folder_name>"
```
###### *New-DFSReplicationGroup -GroupName "DFS-Replication" -FolderName "Public-Shares"*

### Add server to Replication Group
```powershell
Add-DFSRMember -GroupName "<group_name>" -ComputerName "<server_name>"
```
###### *New-DFSReplicationGroup -GroupName "DFS-Replication" -ComputerName "republic-fs01"*

### Set primary server of Replication Group
```powershell
$set_membership_settings = @{
  GroupName      = "<group_name>"
  FolderName     = "<folder_name>"
  ContentPath    = "<path_to_folder>"
  ComputerName   = "<server_name>"
  PrimaryMember  = $true
}

Set-DFSRMembership @set_membership_settings
```
###### *New-DFSReplicationGroup -GroupName "DFS-Replication" -FolderName "Public-Shares" -ContentPath "D:\Public-Shares" -ComputerName "republic-fs01" -PrimaryMember $true*

## Check event logs for event ID 4112
```powershell
Get-WinEvent "DFS Replication" -MaxEvents 5 | fl
```
