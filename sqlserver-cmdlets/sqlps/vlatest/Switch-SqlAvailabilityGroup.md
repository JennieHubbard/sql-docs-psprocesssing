---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 41D1496B-5767-4B2F-A0CD-734892A422B9
updated_at: 1/4/2017 6:38 PM
ms.date: 1/4/2017
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Switch-SqlAvailabilityGroup.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlps/vlatest/Switch-SqlAvailabilityGroup.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/4c48bd1c26220ff873e612527853aeeef98777da/sqlserver-cmdlets/sqlps/vlatest/Switch-SqlAvailabilityGroup.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: True
ms.service: sql-server
---

# Switch-SqlAvailabilityGroup

## SYNOPSIS
Starts a failover of an availability group to a secondary replica.

## SYNTAX

### ByPath (Default)
```
Switch-SqlAvailabilityGroup [-AllowDataLoss] [-Force] [[-Path] <String[]>] [-Script] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ByObject
```
Switch-SqlAvailabilityGroup [-AllowDataLoss] [-Force] [-InputObject] <AvailabilityGroup[]> [-Script] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
The **Switch-SqlAvailabilityGroup** cmdlet starts a failover of an availability group to a specified secondary replica.
Run this cmdlet on the target secondary replica.
After the failover, the secondary replica becomes the primary replica.

## EXAMPLES

### Example 1: Fail over an availability group
```
PS C:\> Switch-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MainAG"
```

This command performs a manual failover of the availability group MainAG to the server instance named SecondaryServer\InstanceName.
This command does not allow data loss.
Run this command on the server instance that hosts the secondary replica to which to fail over.

### Example 2: Force an availability group to fail over
```
PS C:\> Switch-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MainAG" -AllowDataLoss
```

This command performs a manual failover of the availability group MainAG to the server instance named SecondaryServer\InstanceName.
The command specifies the *AllowDataLoss* parameter.
Therefore, the failover has the potential of data loss, and the command prompts you for confirmation.
Specify the *Force* parameter to skip the confirmation.

### Example 3: Create a script to fail over an availability group
```
PS C:\>Switch-SqlAvailabilityGroup -Path "SQLSERVER:\Sql\SecondaryServer\InstanceName\AvailabilityGroups\MainAG" -Script
```

This command creates a Transact-SQL script that performs a manual failover of the availability group MainAG to the server instance named SecondaryServer\InstanceName.
The script does not allow data loss.
The command does not cause failover.

## PARAMETERS

### -AllowDataLoss
Indicates that this cmdlet starts a forced failover to the target secondary replica. 
Data loss is possible.
Unless you specify the *Force* or *Script* parameter, the cmdlet prompts you for confirmation.

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

### -Force
Forces the command to run without asking for user confirmation.
This cmdlet prompts you for confirmation only if you specify the *AllowDataLoss* parameter.

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
Specifies availability group that this cmdlet fails over.

```yaml
Type: AvailabilityGroup[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Path
Specifies the path of the availability group that this cmdlet fails over.
If you do not specify this parameter, this cmdlet uses current working location.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script
Indicates that this cmdlet returns a Transact-SQL script that performs the task that this cmdlet performs.

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
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityGroup
You can pass an availability group to this cmdlet.

## OUTPUTS

## NOTES

## RELATED LINKS

[Join-SqlAvailabilityGroup](xref:sqlps/vlatest/Join-SqlAvailabilityGroup.md)

[New-SqlAvailabilityGroup](xref:sqlps/vlatest/New-SqlAvailabilityGroup.md)

[Remove-SqlAvailabilityGroup](xref:sqlps/vlatest/Remove-SqlAvailabilityGroup.md)

[Set-SqlAvailabilityGroup](xref:sqlps/vlatest/Set-SqlAvailabilityGroup.md)

[Test-SqlAvailabilityGroup](xref:sqlps/vlatest/Test-SqlAvailabilityGroup.md)
