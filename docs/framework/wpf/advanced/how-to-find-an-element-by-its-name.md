---
title: "Comment&#160;: rechercher un &#233;l&#233;ment par son nom | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éléments, rechercher par nom"
  - "FindName (méthode)"
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: rechercher un &#233;l&#233;ment par son nom
Cet exemple décrit comment utiliser la méthode <xref:System.Windows.FrameworkElement.FindName%2A> pour rechercher un élément par sa valeur <xref:System.Windows.FrameworkElement.Name%2A>.  
  
## Exemple  
 Dans cet exemple, la méthode permettant de rechercher un élément particulier par son nom est écrite en tant que gestionnaire d'événements d'un bouton.  `stackPanel` est le <xref:System.Windows.FrameworkElement.Name%2A> du <xref:System.Windows.FrameworkElement> racine recherché, et la méthode d'exemple indique ensuite visuellement l'élément trouvé en le castant en tant que <xref:System.Windows.Controls.TextBlock> et en modifiant l'une des propriétés [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.TextBlock> visibles.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]