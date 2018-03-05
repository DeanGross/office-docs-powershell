---
title: "New-SPTrustedServiceTokenIssuer"
ms.author: laurawi
author: LauraWi
manager: laurawi
ms.date: 12/7/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cea600ae-0b64-4c2b-8943-c7c21884fffe

description: "Creates a trust with a SharePoint farm."
---

# New-SPTrustedServiceTokenIssuer

Creates a trust with a SharePoint farm.
  
```
New-SPTrustedServiceTokenIssuer [-Name] <String> -Certificate <X509Certificate2> [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-WhatIf [<SwitchParameter>]]
```

## Detailed Description

This cmdlet contains more than one parameter set. You may only use parameters from one parameter set, and you may not combine parameters from different parameter sets. For more information about how to use parameter sets, see [Cmdlet Parameter Sets](https://go.microsoft.com/fwlink/?LinkID=187810).
  
The **New-SPTrustedServiceTokenIssuer** cmdlet creates a trust with a SharePoint farm. If a certificate file is used, it must have only one X509 certificate without private keys, otherwise an exception is raised. 
  
For permissions and the most current information about Windows PowerShell for SharePoint Products, see the online documentation at [Windows PowerShell for SharePoint Server 2016 reference](https://go.microsoft.com/fwlink/p/?LinkId=671715).
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Name** <br/> |Required  <br/> |System.String  <br/> |Specifies the name of the trust.  <br/> The type must be a valid name of a trusted service issuer; for example, WFEFarmTrust1.  <br/> |
|**Certificate** <br/> |Required  <br/> |System.Security.Cryptography.X509Certificates.X509Certificate2  <br/> |The type must be a name of a valid X.509 certificate; for example, Certificate1.  <br/> Specifies the X.509 certificate object from trusted authentication provider farm.  <br/> |
|**MetadataEndPoint** <br/> |Required  <br/> |System.Uri  <br/> |Specifies the URI for the metadata endpoint of the trusted provider.  <br/> |
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> |Manages objects for the purpose of proper disposal. Use of objects, such as **SPWeb** or **SPSite**, can use large amounts of memory and use of these objects in Windows PowerShell scripts requires proper memory management. Using the **SPAssignment** object, you can assign objects to a variable and dispose of the objects after they are needed to free up memory. When **SPWeb**, **SPSite**, or **SPSiteAdministration** objects are used, the objects are automatically disposed of if an assignment collection or the **Global** parameter is not used.  <br/> > [!NOTE]> When the **Global** parameter is used, all objects are contained in the global store. If objects are not immediately used, or disposed of by using the **Stop-SPAssignment** command, an out-of-memory scenario can occur.           |
|**Description** <br/> |Optional  <br/> |System.String  <br/> |Specifies a description for the trust.  <br/> The type must be a valid string; for example, WFE Farm Trust1.  <br/> |
   
## AutoGenParams

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|**Name** <br/> |Required  <br/> |System.String  <br/> ||
|**Certificate** <br/> |Required  <br/> |System.Security.Cryptography.X509Certificates.X509Certificate2  <br/> ||
|**MetadataEndPoint** <br/> |Required  <br/> |System.Uri  <br/> ||
|**AssignmentCollection** <br/> |Optional  <br/> |Microsoft.SharePoint.PowerShell.SPAssignmentCollection  <br/> ||
|**Confirm** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
|**Description** <br/> |Optional  <br/> |System.String  <br/> ||
|**WhatIf** <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> ||
   
## Example

------------------EXAMPLE 1------------------
  
```
$cert = Get-PfxCertificate C:\LiveIDSigningCert.pfx
```

```
New-SPTrustedServiceTokenIssuer -Name "WFEFarm1" -Description "WFE Farm 1" -Certificate $cert
```

This example shows how to create a new SharePoint Farm trust using the trust certificate from a file.
  
## See also

#### 

[Get-SPTrustedServiceTokenIssuer](get-sptrustedservicetokenissuer.md)
  
[Set-SPTrustedServiceTokenIssuer](set-sptrustedservicetokenissuer.md)
  
[Remove-SPTrustedServiceTokenIssuer](remove-sptrustedservicetokenissuer.md)
