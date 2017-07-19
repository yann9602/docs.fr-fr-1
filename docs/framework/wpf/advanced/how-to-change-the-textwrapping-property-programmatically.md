---
title: "Comment&#160;: modifier la propri&#233;t&#233; TextWrapping par programmation | Microsoft Docs"
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
  - "documents, modifier la propriété TextWrapping par programmation"
  - "TextWrapping (propriété), modifier par programmation"
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: modifier la propri&#233;t&#233; TextWrapping par programmation
## Exemple  
 L'exemple de code suivant indique comment modifier par programmation la valeur de la propriété <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.  
  
 Trois éléments <xref:System.Windows.Controls.Button> sont placés dans un élément <xref:System.Windows.Controls.StackPanel> de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Chaque événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> d'un <xref:System.Windows.Controls.Button> correspond à un gestionnaire d'événements dans le code.  Les gestionnaires d'événements utilisent le même nom que la valeur <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> qu'ils appliqueront à `txt2` lors d'un clic sur le bouton.  En outre, le texte dans `txt1` \(un <xref:System.Windows.Controls.TextBlock> non affiché dans le code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]\) est mis à jour pour répercuter la modification dans la propriété.  
  
 [!code-xml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>   
 <xref:System.Windows.TextWrapping>