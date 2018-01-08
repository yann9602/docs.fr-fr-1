---
title: "Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38a8c3556d78431672ebeab16a3fa65e2debc0e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées
Dans les applications Windows Forms qui ciblent des versions du .NET Framework à partir du [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], une implémentation personnalisée de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> peut en toute sécurité filtrer les messages quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée si l’implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> :  
  
-   Effectue l’une des actions suivantes ou les deux :  
  
    -   Ajout d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.  
  
    -   Suppression d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. .  
  
-   **Et** pompe des messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.  
  
## <a name="impact"></a>Impact  
 Cette modification affecte uniquement les applications Windows Forms qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions ultérieures.  
  
 Pour les applications Windows Forms qui ciblent des versions antérieures du .NET Framework, de telles implémentations lèvent dans certains cas une exception <xref:System.IndexOutOfRangeException> quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée.  
  
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
