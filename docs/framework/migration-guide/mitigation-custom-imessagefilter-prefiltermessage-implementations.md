---
title: "Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d85c827b414cc94410a921bfae9ce3e1764d22ea
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées
Dans les applications Windows Forms qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures, une implémentation <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> personnalisée peut filtrer en toute sécurité les messages lorsque la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée si l’implémentation <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> :  
  
-   Effectue l’une des actions suivantes ou les deux :  
  
    -   Ajoute un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.  
  
    -   Supprime un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. .  
  
-   **Et** pompe les messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>.  
  
## <a name="impact"></a>Impact  
 Cette modification affecte uniquement les applications Windows Forms qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures.  
  
 Pour les applications Windows Forms qui ciblent des versions antérieures du .NET Framework, ces implémentations peuvent, dans certains cas, lever une exception <xref:System.IndexOutOfRangeException> lorsque la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée.  
  
## <a name="mitigation"></a>Atténuation  
 Si cette modification n’est pas souhaitable, les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], ou une version ultérieure, peuvent ne pas y adhérer en ajoutant le paramètre de configuration suivant dans la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
  
```  
  
 De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], ou version ultérieure, peuvent adhérer à ce comportement en ajoutant le paramètre de configuration suivant dans la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
