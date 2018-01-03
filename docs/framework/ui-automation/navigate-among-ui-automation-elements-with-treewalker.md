---
title: "Naviguer entre les éléments UI Automation avec TreeWalker"
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
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
caps.latest.revision: "8"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 00a5d3b33b45fd521f36f1e4775ad864ee525293
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>Naviguer entre les éléments UI Automation avec TreeWalker
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient des exemples de code qui montre comment naviguer entre [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] éléments à l’aide de la <xref:System.Windows.Automation.TreeWalker> classe.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise <xref:System.Windows.Automation.TreeWalker.GetParent%2A> pour remonter la [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] arborescence jusqu'à ce qu’il trouve l’élément racine ou le bureau. L’élément ci-dessous, qui est la fenêtre parente de l’élément spécifié.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> et <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> pour créer un <xref:System.Windows.Forms.TreeView> qui affiche l’intégralité d’une sous-arborescence de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] les éléments qui se trouvent dans l’affichage de contrôle et sont activés.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention d’éléments UI Automation](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
