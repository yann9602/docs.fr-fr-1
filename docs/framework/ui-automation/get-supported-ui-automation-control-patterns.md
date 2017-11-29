---
title: "Obtenir des modèles de contrôle UI Automation pris en charge"
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
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a>Obtenir des modèles de contrôle UI Automation pris en charge
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment récupérer des objets de modèle de contrôle à partir de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] éléments.  
  
### <a name="obtain-all-control-patterns"></a>Obtenir tous les modèles de contrôle  
  
1.  Obtenir le <xref:System.Windows.Automation.AutomationElement> les modèles dont le contrôle vous intéressent.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pour obtenir tous les modèles de contrôle de l’élément.  
  
> [!CAUTION]
>  Il est fortement recommandé qu’un client n’utilise pas <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Performances peuvent être gravement affectées, car cette méthode appelle <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> en interne pour chaque modèle de contrôle existant. Si possible, un client doit appeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pour les modèles les plus intéressants.  
  
### <a name="obtain-a-specific-control-pattern"></a>Obtenir un modèle de contrôle spécifique  
  
1.  Obtenir le <xref:System.Windows.Automation.AutomationElement> les modèles dont le contrôle vous intéressent.  
  
2.  Appelez <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> pour rechercher un modèle spécifique. Ces méthodes sont similaires, mais si le modèle est introuvable, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> lève une exception, et <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> retourne `false`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant récupère une <xref:System.Windows.Automation.AutomationElement> pour un élément de liste et obtient un <xref:System.Windows.Automation.SelectionItemPattern> à partir de cet élément.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles de contrôle UI Automation pour les Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
