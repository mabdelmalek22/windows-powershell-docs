---
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: SmbShare.cdxml-help.xml
Module Name: SmbShare
ms.date: 12/20/2016
online version: https://docs.microsoft.com/powershell/module/smbshare/unblock-smbshareaccess?view=windowsserver2022-ps&wt.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-SmbShareAccess
---

# Unblock-SmbShareAccess

## SYNOPSIS
Removes all of the deny ACEs for the trustee from the security descriptor of the SMB share.

## SYNTAX

### Query
```
Unblock-SmbShareAccess [-Name] <String[]> [[-ScopeName] <String[]>] [-SmbInstance <SmbInstance>]
 [-AccountName <String[]>] [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObject (cdxml)
```
Unblock-SmbShareAccess -InputObject <CimInstance[]> [-AccountName <String[]>] [-Force]
 [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Unblock-SmbShareAccess** cmdlet removes all of the deny access control entries (ACEs) for the trustee from the security descriptor of the Server Message Block (SMB) share.

## EXAMPLES

### Example 1: Remove the deny ACEs for a trustee
```
PS C:\>Unblock-SmbShareAccess -Name "VMFiles" -AccountName "Guest Users"
Confirm 
Are you sure you want to perform this action? 
Performing operation 'Modify' on Target 'Contoso-SO,VMFiles'. 
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y 

Name                    ScopeName               AccountName             AccessControlType       AccessRight 
----                    ---------               -----------             -----------------       ----------- 
VMFiles                 Contoso-SO              Contoso\Guest           Deny                    Full 
VMFiles                 Contoso-SO              Contoso\Administrator   Allow                   Full 
VMFiles                 Contoso-SO              Contoso\Contoso-HV1$    Allow                   Full
```

This command removes all of the deny ACEs for the trustee from the security descriptor of the SMB share.

### Example 2: Remove the deny ACEs for a trustee without confirmation
```
PS C:\>Unblock-SmbShareAccess -Name "VMFiles" -AccountName "Contoso\Guest" -Force
Name                    ScopeName               AccountName             AccessControlType       AccessRight 
----                    ---------               -----------             -----------------       ----------- 
VMFiles                 Contoso-SO              Contoso\Administrator   Allow                   Full 
VMFiles                 Contoso-SO              Contoso\Contoso-HV1$    Allow                   Full
```

This command removes all of the deny ACEs for the trustee from the security descriptor of the SMB share without user confirmation.

## PARAMETERS

### -AccountName
Specifies an array of the names of the trustees whose deny ACEs are removed from the security descriptor of the SMB share.
Specify a comma-separated list to unblock multiple trustees.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
Runs the cmdlet as a background job. Use this parameter to run commands that take a long time to complete.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession
Runs the cmdlet in a remote session or on a remote computer.
Enter a computer name or a session object, such as the output of a [New-CimSession](https://go.microsoft.com/fwlink/p/?LinkId=227967) or [Get-CimSession](https://go.microsoft.com/fwlink/p/?LinkId=227966) cmdlet.
The default is the current session on the local computer.

```yaml
Type: CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Forces the command to run without asking for user confirmation.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies the input object that is used in a pipeline command.

```yaml
Type: CimInstance[]
Parameter Sets: InputObject (cdxml)
Aliases: 

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies the name of the SMB share.

```yaml
Type: String[]
Parameter Sets: Query
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ScopeName
Specifies an array of names of the scopes of the shares.

```yaml
Type: String[]
Parameter Sets: Query
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SmbInstance
Specifies the input to this cmdlet.
You can use this parameter, or you can pipe the input to this cmdlet.

```yaml
Type: SmbInstance
Parameter Sets: Query
Aliases: 
Accepted values: Default, CSV, SBL, SR

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ThrottleLimit
Specifies the maximum number of concurrent operations that can be established to run the cmdlet.
If this parameter is omitted or a value of `0` is entered, then Windows PowerShell® calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.
The throttle limit applies only to the current cmdlet, not to the session or to the computer.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### Microsoft.Management.Infrastructure.CimInstance#root/Microsoft/Windows/SMB/MSFT_SmbShareAccessControlEntry
The `Microsoft.Management.Infrastructure.CimInstance` object is a wrapper class that displays Windows Management Instrumentation (WMI) objects.
The path after the pound sign (`#`) provides the namespace and class name for the underlying WMI object.
This cmdlet returns a **MSFT_SmbShareAccessControlEntry** object.

## NOTES

## RELATED LINKS

[Block-SmbShareAccess](./Block-SmbShareAccess.md)

[Get-SmbShareAccess](./Get-SmbShareAccess.md)

[Grant-SmbShareAccess](./Grant-SmbShareAccess.md)

[Revoke-SmbShareAccess](./Revoke-SmbShareAccess.md)

