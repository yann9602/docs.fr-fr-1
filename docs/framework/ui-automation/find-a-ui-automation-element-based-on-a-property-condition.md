---
title: "Find a UI Automation Element Based on a Property Condition | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elements, finding by property conditions"
  - "UI Automation, finding elements by property conditions"
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: 19
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 19
---
# Find a UI Automation Element Based on a Property Condition
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui veulent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.  Pour obtenir les informations les plus récentes sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment localiser un élément dans l'arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sur la base d'une ou plusieurs propriétés spécifiques.  
  
## Exemple  
 Dans l'exemple suivant, un jeu de conditions de propriétés est spécifié ; il identifie un ou plusieurs éléments spécifiques intéressants dans l'arborescence <xref:System.Windows.Automation.AutomationElement>.  Une recherche de tous les éléments correspondants est ensuite exécutée avec la méthode <xref:System.Windows.Automation.AutomationElement.FindAll%2A> qui incorpore une série d'opérations booléennes <xref:System.Windows.Automation.AndCondition> pour limiter le nombre d'éléments correspondants.  
  
> [!NOTE]
>  Lorsque vous effectuez une recherche à partir de <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, vous devez essayer d'obtenir uniquement les enfants directs.  Une recherche des descendants peut itérer au sein de centaines ou de milliers d'éléments, ce qui peut provoquer un dépassement de capacité de la pile.  Si vous tentez d'obtenir un élément spécifique à un niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d'application ou d'un conteneur à un niveau inférieur.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## Voir aussi  
 [InvokePattern and ExpandCollapsePattern Menu Item Sample](http://msdn.microsoft.com/fr-fr/b7fa141c-e2d1-4da2-a27f-81a7d1172210)   
 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)   
 [Use the AutomationID Property](../../../docs/framework/ui-automation/use-the-automationid-property.md)