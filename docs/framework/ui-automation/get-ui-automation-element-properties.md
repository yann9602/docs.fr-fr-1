---
title: "Obtenir les propriétés d'éléments UI Automation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2b9e1f24a6384cd052dd7b15c7afb3facac05c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-ui-automation-element-properties"></a>Obtenir les propriétés d'éléments UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment récupérer les propriétés d’un [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] élément.  
  
### <a name="get-a-current-property-value"></a>Obtenir une valeur de propriété en cours  
  
1.  Obtenir le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, ou de récupérer le <xref:System.Windows.Automation.AutomationElement.Current%2A> structure de propriété et d’obtenir la valeur d’un de ses membres.  
  
### <a name="get-a-cached-property-value"></a>Obtenir une valeur de propriété mises en cache  
  
1.  Obtenir le <xref:System.Windows.Automation.AutomationElement> dont vous souhaitez obtenir la propriété. La propriété doit avoir été spécifiée dans le <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, ou de récupérer le <xref:System.Windows.Automation.AutomationElement.Cached%2A> structure de propriété et d’obtenir la valeur d’un de ses membres.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les différentes façons de récupérer les propriétés actuelles d’un <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>Voir aussi  
 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [Utiliser la mise en cache dans UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Mise en cache dans les Clients UI Automation](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
