---
title: "Find and Highlight Text Using UI Automation | Microsoft Docs"
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
  - "text, highlighting"
  - "finding text"
  - "text, finding"
  - "UI automation, highlighting text"
  - "UI automation, finding text"
  - "highlighting text"
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
caps.latest.revision: 15
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 15
---
# Find and Highlight Text Using UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui veulent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.  Pour obtenir les informations les plus récentes sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment rechercher de manière séquentielle et mettre en surbrillance chaque occurrence d'une chaîne dans le contenu d'un contrôle de texte à l'aide d'[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].  
  
## Exemple  
 L'exemple suivant obtient un objet <xref:System.Windows.Automation.TextPattern> d'un contrôle de texte.  Un objet <xref:System.Windows.Automation.Text.TextPatternRange>, représentant le contenu textuel du document entier, est ensuite créé à l'aide de la propriété <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> de ce <xref:System.Windows.Automation.TextPattern>.  Deux objets <xref:System.Windows.Automation.Text.TextPatternRange> supplémentaires sont ensuite créés pour les fonctionnalités de recherche séquentielle et de surbrillance.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## Voir aussi  
 [Find and Highlight Text Using UI Automation](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)