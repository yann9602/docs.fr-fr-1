---
title: "Atténuation : X509CertificateClaimSet.FindClaim, méthode | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c234d6ddeda50dfefff8c49a2e14d623cdd8d861
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Atténuation : X509CertificateClaimSet.FindClaims, méthode
À présent, pour les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> tente de faire correspondre l’argument `claimType` avec toutes les entrées DNS dans son champ SAN.  
  
## <a name="impact"></a>Impact  
 Cette modification affecte uniquement les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures.  
  
 Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> tente de faire correspondre l’argument `claimType` avec la dernière entrée DNS.  
  
## <a name="mitigation"></a>Atténuation  
 Si cette modification n’est pas souhaitable, les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures peuvent ne pas y adhérer en ajoutant le paramètre de configuration suivant dans la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
  
```  
  
 De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou ultérieur peuvent adhérer à ce comportement en ajoutant le paramètre de configuration suivant dans la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
