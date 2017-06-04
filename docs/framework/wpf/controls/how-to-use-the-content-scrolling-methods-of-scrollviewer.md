---
title: "Comment&#160;: utiliser les m&#233;thodes de d&#233;filement du contenu de ScrollViewer | Microsoft Docs"
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
  - "IScrollInfo (interface)"
  - "méthodes de défilement"
  - "ScrollViewer (contrôle), méthodes de défilement"
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: utiliser les m&#233;thodes de d&#233;filement du contenu de ScrollViewer
Cet exemple montre comment utiliser les méthodes de défilement de l'élément <xref:System.Windows.Controls.ScrollViewer>.  Ces méthodes fournissent un défilement incrémentiel du contenu, par ligne ou par page, dans un <xref:System.Windows.Controls.ScrollViewer>.  
  
## Exemple  
 L'exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> nommé `sv1` qui héberge un élément <xref:System.Windows.Controls.TextBlock> enfant.  Étant donné que le <xref:System.Windows.Controls.TextBlock> est plus grand que le <xref:System.Windows.Controls.ScrollViewer> parent, les barres de défilement s'affichent pour permettre le défilement.  Les éléments <xref:System.Windows.Controls.Button> qui représentent les différentes méthodes de défilement sont ancrés sur la gauche dans un <xref:System.Windows.Controls.StackPanel> distinct.  Chaque <xref:System.Windows.Controls.Button> du fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] appelle une méthode personnalisée associée qui contrôle le comportement de défilement dans <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 L'exemple suivant utilise les méthodes <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> et <xref:System.Windows.Controls.ScrollViewer.LineDown%2A>.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.StackPanel>