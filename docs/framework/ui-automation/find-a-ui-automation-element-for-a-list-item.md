---
title: "Rechercher un élément UI Automation pour un élément de liste"
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
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
caps.latest.revision: "5"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 16016f5e5b0ab9633f9f8e4ac662838dd7936b18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Rechercher un élément UI Automation pour un élément de liste
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment récupérer un <xref:System.Windows.Automation.AutomationElement> d’un élément dans une liste lorsque l’index de l’élément est connu.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux façons de récupérer un élément spécifié à partir d’une liste, à l’aide de <xref:System.Windows.Automation.TreeWalker> et l’autre à l’aide <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.  
  
 La première technique a tendance à être plus rapides pour [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] contrôles, mais la deuxième est plus rapide pour [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] contrôles.  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention d’éléments UI Automation](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
