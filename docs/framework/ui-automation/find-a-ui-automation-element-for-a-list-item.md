---
title: "Find a UI Automation Element for a List Item | Microsoft Docs"
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
  - "list items, finding elements for"
  - "elements, finding for list items"
  - "UI Automation, finding elements for List items"
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
caps.latest.revision: 5
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 5
---
# Find a UI Automation Element for a List Item
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui veulent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.  Pour obtenir les informations les plus récentes sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment récupérer un <xref:System.Windows.Automation.AutomationElement> pour un élément dans une liste lorsque l'index de l'élément est connu.  
  
## Exemple  
 L'exemple suivant présente deux manières de récupérer un élément spécifié dans une liste : une à l'aide de <xref:System.Windows.Automation.TreeWalker> et l'autre à l'aide de <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 La première technique est plus rapide pour les contrôles [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], mais la deuxième est plus rapide pour les contrôles [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)].  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## Voir aussi  
 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)