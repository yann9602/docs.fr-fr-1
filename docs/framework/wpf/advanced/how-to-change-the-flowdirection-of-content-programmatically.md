---
title: "Comment&#160;: modifier la propri&#233;t&#233; FlowDirection d&#39;un contenu par programmation | Microsoft Docs"
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
  - "documents, modifier la propriété FlowDirection par programme"
  - "FlowDirection (propriété), modifier par programmation"
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: modifier la propri&#233;t&#233; FlowDirection d&#39;un contenu par programmation
Cet exemple indique comment modifier par programme la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> d'un <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## Exemple  
 Deux éléments <xref:System.Windows.Controls.Button> sont créés, chacun représentant l'une des valeurs possibles de <xref:System.Windows.FlowDirection>.  Lorsque vous cliquez sur un bouton, la valeur de propriété associée est appliquée au contenu d'un <xref:System.Windows.Controls.FlowDocumentReader> nommé `tf1`.  La valeur de propriété est également écrite dans un <xref:System.Windows.Controls.TextBlock> nommé `txt1`.  
  
 [!code-xml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## Exemple  
 Les événements associés aux clics de bouton définis au\-dessus sont gérés dans un fichier code\-behind [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)].  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]