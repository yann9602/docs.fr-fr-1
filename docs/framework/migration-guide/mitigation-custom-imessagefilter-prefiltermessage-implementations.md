---
title: "Att&#233;nuation&#160;: impl&#233;mentations IMessageFilter.PreFilterMessage personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 2
---
# Att&#233;nuation&#160;: impl&#233;mentations IMessageFilter.PreFilterMessage personnalis&#233;es
Dans les applications Windows Forms qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], une implémentation personnalisée de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> peut en toute sécurité filtrer les messages quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée si l’implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> :  
  
-   Effectue l’une ou actions suivantes ou les deux :  
  
    -   Ajoute un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.  
  
    -   Supprime un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. .  
  
-   **Et** pompe des messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName>.  
  
## Impact  
 Cette modification affecte uniquement les applications Windows Forms qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Pour les applications Windows Forms qui ciblent les versions antérieures du .NET Framework, de telles implémentations lèvent dans certains cas une exception <xref:System.IndexOutOfRangeException> quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> est appelée.  
  
## Atténuation  
 Si cette modification n’est pas souhaitable, les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent la refuser en ajoutant le paramètre de configuration suivant à la section [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" /> </runtime>  
  
```  
  
 De plus, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s’exécutent sous le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] peuvent accepter ce comportement en ajoutant le paramètre de configuration suivant à la section [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" /> </runtime>  
  
```  
  
## Voir aussi  
 [Reciblage des modifications](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)