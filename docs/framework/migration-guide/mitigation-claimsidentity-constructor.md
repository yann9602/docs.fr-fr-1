---
title: "Atténuation : Constructeur ClaimsIdentity | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84016664708b9b7fc61a9535e5f7910417caa6f1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-claimsidentity-constructor"></a>Atténuation : Constructeur ClaimsIdentity
À compter de [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la façon dont le constructeur <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> définit la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> est modifiée. Si l’argument <xref:System.Security.Principal.IIdentity> est un objet <xref:System.Security.Claims.ClaimsIdentity> et que la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> de cet objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas `null`, la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> est jointe à l’aide de la méthode <xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName>. Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> est jointe en tant que référence existante.  
  
## <a name="impact"></a>Impact  
 À compter de [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> du nouvel objet <xref:System.Security.Claims.ClaimsIdentity> n’est pas égale à la propriété <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> de l’argument <xref:System.Security.Principal.IIdentity> du constructeur. Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, il n’y a pas de différence.  
  
## <a name="mitigation"></a>Atténuation  
 Si ce comportement n’est pas souhaitable, vous pouvez restaurer le comportement précédent en réglant `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` dans votre fichier de configuration d’application sur `true`. Pour cela, vous ajoutez le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier web.config :  
  
```  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

