---
Description: 'Retrieves a collection of excluded user accounts.'
audience: developer
author: 'REDMOND\\markl'
manager: 'REDMOND\\mbaldwin'
ms.assetid: 'eb0c2850-9236-48e5-857a-b061bb780b83'
ms.prod: 'windows-server-dev'
ms.technology: 'active-directory-rights-management'
ms.tgt_platform: multiple
title: 'ExclusionPolicy.UserAccounts property'
---

# ExclusionPolicy.UserAccounts property

The **UserAccounts** property retrieves a collection of excluded user accounts.

This property is read-only.

## Syntax


```VB
ExclusionPolicy.UserAccounts
```



## Property value

This property returns an [**ExcludedUserAccountCollection**](excludeduseraccountcollection-object.md) object.

## Remarks

User account exclusion prohibits AD RMS from issuing an end-user license or a client licensor certificate to a requesting user if the user account is on the exclusion list and the account exclusion collection has been enabled.

## Examples


```VB
DIM config_manager
DIM admin_role

' *******************************************************************
' Create and initialize a ConfigurationManager object.

SUB InitObject()

  CALL WScript.Echo( "Create ConfigurationManager object...")
  SET config_manager = CreateObject _
    ("Microsoft.RightsManagementServices.Admin.ConfigurationManager")      
  CheckError()
    
  CALL WScript.Echo( "Initialize...")
  admin_role=config_manager.Initialize(false,"localhost",80,"","","")
  CheckError()

END SUB

' *******************************************************************
' Exclude user accounts.

SUB ExcludeUser()

  DIM exclusionPolicy
  DIM excludedUser
  DIM excludedUserColl   
  Dim excludedUserType
  Dim excludedUserDate


  ' Retrieve the ExclusionPolicy object.
  SET exclusionPolicy = config_manager.Enterprise.ExclusionPolicy
  CheckError()

  ' Create an ExcludedUserAccount object.
  SET excludedUser = CreateObject( _
    "Microsoft.RightsManagementServices.Admin.ExcludedUserAccount")
  CheckError()

  ' Identify the excluded public key.
  excludedUser.PublicKey = "D3QgTm9y1ujYqiy4tocvmnyvnlp" _
        & "kthp5+TrtF94qJN/I38bxALpAj9ExB4Do6P+rHWvMR+0HztV7Yelo" _
        & "B3r2IlX2lQYe7mxZwnF2D5/7GUzPj5hKxCT/By55tX3Bzs4Eno7cX" _
        & "fTeJ6mnMDO+KyjNoObg9kPRCy2hmHhj2ftRvLk="
  CheckError()

  ' Retrieve the ExcludedUSerAccountCollection object.
  SET excludedUserColl = exclusionPolicy.UserAccounts
  CheckError()

  ' Enable the collection.
  excludedUserColl.Enabled = TRUE

  ' Add the new user account to the collection.
  excludedUserColl.Add( excludedUser )
  CheckError()

  ' Retrieve the user type.
  excludedUserType = excludedUser.Type
  CheckError()

  ' Retrieve the date on which the user account was excluded.
  excludedUserDate = excludedUser.Date
  CheckError()

END SUB

' *******************************************************************
' Error checking function.

FUNCTION CheckError()
  CheckError = Err.number
  IF Err.number <> 0 THEN
    CALL WScript.Echo( vbTab & "*****Error Number: " _
                       & Err.number _
                       & " Desc:" _
                       & Err.Description _
                       & "*****")
    WScript.StdErr.Write(Err.Description)
    WScript.Quit( Err.number )
  END IF
END FUNCTION
```



## Requirements



|                                     |                                                                                                                         |
|-------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | None supported<br/>                                                                                               |
| Minimum supported server<br/> | Windows Server�2008<br/>                                                                                          |
| Assembly<br/>                 | <dl> <dt>Microsoft.RightsManagementServices.Admin.dll</dt> </dl> |



## See also

<dl> <dt>

[**ExclusionPolicy**](exclusionpolicy-object.md)
</dt> </dl>

�

�



