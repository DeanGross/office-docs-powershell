---
title: "Remove-SPSiteSubscriptionSettings"
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 3c9856f7-3b48-4d43-aef7-e927e70e7618

description: "Removes the settings service data for a specified site subscription, or finds and removes orphaned data."
---

# Remove-SPSiteSubscriptionSettings

Removes the settings service data for a specified site subscription, or finds and removes orphaned data.
  
```
Remove-SPSiteSubscriptionSettings [-Identity] <SPServiceApplicationPipeBind> -SiteSubscriptions <Guid[]> [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]
```

## Detailed Description

This cmdlet contains more than one parameter set. You may only use parameters from one parameter set, and you may not combine parameters from different parameter sets. For more information about how to use parameter sets, see [Cmdlet Parameter Sets](https://go.microsoft.com/fwlink/?LinkID=187810).
  
The **Remove-SPSiteSubscriptionSettings** cmdlet deletes site subscription stored data for the specified site subscription. If the **FindAllOrphans** parameter is specified, this cmdlet locates any data in the service application that does not exist in the list of local site subscriptions or the alternate list of subscriptions. 
  
The set of site subscriptions can be specified directly, or discovered by comparing data in the service application to the set of existing site subscriptions which finds the data set that corresponds to nonexistent site subscriptions.
  
> [!IMPORTANT]
> If this cmdlet is run on a federated service application without specifying the complete list of site subscription IDs for the **AlternativeSiteSubscriptions** parameter, data loss can result. 
  
For permissions and the most current information about Windows PowerShell for SharePoint Products, see the online documentation at [Windows PowerShell for SharePoint Server 2016 reference](https://go.microsoft.com/fwlink/p/?LinkId=671715).
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Identity** <br/> |Required  <br/> |Microsoft.SharePoint.PowerShell.SPServiceApplicationPipeBind  <br/> |Specifies the site subscription settings service application that contains the service data to delete.  <br/> The type must be a valid GUID, in the form 12345678-90ab-cdef-1234-567890bcdefgh; a valid name of a subscription settings service application (for example, SubscriptionSettingsApp1); or an instance of a valid **SPSubscriptionSettingsServiceApplication** object.  <br/> |
|**FindAllOrphans** <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> |Specifies that orphaned settings stores in the service application are deleted.  <br/> |
|**SiteSubscriptions** <br/> |Required  <br/> |System.Guid[]  <br/> |Specifies the site subscriptions with the settings service data to delete.  <br/> The type must be an array of valid GUIDs.  <br/> |
|**AlternativeSiteSubscriptions** <br/> |Optional  <br/> |System.Guid[]  <br/> |Specifies the complete collection or comma-separated list of site subscriptions that should exist in the settings service application. Any data not matching the items in this list will be removed.  <br/> This parameter is important when the **FindAllOrphans** parameter is used. The value specified for **AlternativeSiteSubscriptions** parameter is stating that any site subscriptions not on the local farm will be deleted, unless an alternate list of site subscriptions is given.  <br/> The type must be an array of valid GUIDs.  <br/> |
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> |Manages objects for the purpose of proper disposal. Use of objects, such as **SPWeb** or **SPSite**, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the **SPAssignment** object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When **SPWeb**, **SPSite**, or **SPSiteAdministration** objects are used, the objects are automatically disposed of if an assignment collection or the **Global** parameter is not used.  <br/> > [!NOTE]> When the **Global** parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the **Stop-SPAssignment** command, an out-of-memory scenario can occur.           |
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Automatically bypasses the secondary warning provided by the cmdlet prior to the operation.  <br/> |
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Displays a message that describes the effect of the command instead of executing the command. For more information, type the following command: **get-help about_commonparameters** <br/> |
   
## AutoGenParams

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Identity** <br/> |Required  <br/> |Microsoft.SharePoint.PowerShell.SPServiceApplicationPipeBind  <br/> ||
|**FindAllOrphans** <br/> |Required  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**SiteSubscriptions** <br/> |Required  <br/> |System.Guid[]  <br/> ||
|**AlternativeSiteSubscriptions** <br/> |Optional  <br/> |System.Guid[]  <br/> ||
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> ||
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Force** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   
## Errors

|**Error**|**Description**|
|:-----|:-----|
|||
   
## Exceptions

|**Exceptions**|**Description**|
|:-----|:-----|
|||
   
## Example

------------EXAMPLE 1--------------
  
```
Remove-SPSiteSubscriptionSettings -FindAllOrphans -Whatif
```

This example finds all orphans and displays them on the screen. Remove the  `WhatIf` parameter to remove these extra settings. 
  
------------EXAMPLE 2--------------
  
```
Remove-SPSubscriptionSettingsServiceApplication -FindAllOrphans -AlternativeSiteSubscriptions $SubscriptionList
```

Use this example if the service application is consumed by a remote farm and you want the clean orphaned site subscription settings data (an array of all site subscriptions whose data must remain in the service application is assigned to the  `$SubscriptionList` variable. 
  
## See also

#### 

[Import-SPSiteSubscriptionSettings](import-spsitesubscriptionsettings.md)
  
[Export-SPSiteSubscriptionSettings](export-spsitesubscriptionsettings.md)
