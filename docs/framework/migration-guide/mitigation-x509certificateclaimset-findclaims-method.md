---
title: "Att&#233;nuation&#160;: X509CertificiateClaimSet.FindClaim (m&#233;thode) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 3
---
# Att&#233;nuation&#160;: X509CertificiateClaimSet.FindClaim (m&#233;thode)
En commençant par les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> tente de trouver une correspondance à l’argument `claimType` parmi toutes les entrées DNS de son champ SAN.  
  
## Impact  
 Cette modification affecte uniquement les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> tente de faire correspondre l’argument `claimType` uniquement avec la dernière entrée DNS.  
  
## Atténuation  
 Si cette modification n’est pas souhaitable, les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent la refuser en ajoutant le paramètre de configuration suivant dans la section [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" /> </runtime>  
  
```  
  
 De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sous [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent accepter ce comportement en ajoutant le paramètre de configuration suivant dans la section [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" /> </runtime>  
  
```  
  
## Voir aussi  
 [Reciblage des modifications](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)