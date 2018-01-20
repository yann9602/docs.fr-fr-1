---
title: "Rechercher un élément UI Automation basé sur une condition de propriété"
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
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: eda1d8baee9bb45dfb99c0368914a67b97cc10e7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Rechercher un élément UI Automation basé sur une condition de propriété
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient des exemples de code qui montre comment rechercher un élément dans le [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arborescence basée sur une ou plusieurs propriétés spécifiques.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un ensemble de conditions de propriété sont spécifiés qui identifient un élément particulier (ou des éléments) d’intérêt dans le <xref:System.Windows.Automation.AutomationElement> arborescence. Une recherche de tous les éléments correspondants est ensuite exécutée avec la <xref:System.Windows.Automation.AutomationElement.FindAll%2A> méthode qui incorpore une série de <xref:System.Windows.Automation.AndCondition> opérations booléennes pour limiter le nombre d’éléments correspondants.  
  
> [!NOTE]
>  Lors de la recherche à partir de la <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, vous devez tenter d’obtenir uniquement les enfants directs. Une recherche des descendants peut itérer au sein de centaines ou milliers d’éléments, ce qui peut provoquer un débordement de pile. Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Voir aussi  
 [InvokePattern et ExpandCollapsePattern Menu exemple d’élément](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [Obtention d’éléments UI Automation](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [Utiliser la propriété AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md)
