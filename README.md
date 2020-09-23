<div align="center">

## Get users currently logged in


</div>

### Description

Get all users currently logged into to a system
 
### More Info
 
user names

You must have the proper rights to acces the HKEY_USERS.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Jan ten Hove](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/jan-ten-hove.md)
**Level**          |Intermediate
**User Rating**    |4.0 (40 globes from 10 users)
**Compatibility**  |VB\.NET
**Category**       |[Security](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/security__10-14.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/jan-ten-hove-get-users-currently-logged-in__10-292/archive/master.zip)





### Source Code

```
Dim reg As RegistryKey   'the reg key
  Dim user, subKeyName As String 'key names
  reg = Registry.Users
  If Not reg Is Nothing Then  'always do this check, maybe keys does not exists
   For Each subKeyName In reg.GetSubKeyNames
    reg = Registry.Users.OpenSubKey(subKeyName & "\Software\Microsoft\Windows\CurrentVersion\Explorer", False) 'open the subkey
    If Not reg Is Nothing Then 'check
     If reg.GetValue("Logon User Name", Nothing) = Nothing Then 'read
      'no user found in this subkey
     Else
      Msgbox(reg.GetValue("Logon User Name", Nothing))
     End If
    End If
   Next
  Else
   Msgbox("No users found")
  End If
```

