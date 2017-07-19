---
title: "Comment&#160;: d&#233;finir les propri&#233;t&#233;s Height d&#39;un &#233;l&#233;ment | Microsoft Docs"
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
  - "propriétés de hauteur"
  - "Panel (contrôle), propriétés de hauteur d'éléments"
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;finir les propri&#233;t&#233;s Height d&#39;un &#233;l&#233;ment
## Exemple  
 Cet exemple montre visuellement les différences de rendu d'un comportement dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], parmi les quatre propriétés associées à la hauteur.  
  
 La classe <xref:System.Windows.FrameworkElement> expose quatre propriétés qui décrivent les caractéristiques de hauteur d'un élément.  Ces quatre propriétés peuvent entrer en conflit et, lorsque c'est le cas, la valeur prioritaire est déterminée comme suit : la valeur <xref:System.Windows.FrameworkElement.MinHeight%2A> est prioritaire sur la valeur <xref:System.Windows.FrameworkElement.MaxHeight%2A> qui, elle\-même, est prioritaire sur la valeur <xref:System.Windows.FrameworkElement.Height%2A>.  Une quatrième propriété, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, est en lecture seule et signale la hauteur réelle, telle qu'elle est déterminée par les interactions avec le processus de disposition.  
  
 Les exemples [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivants dessinent un élément <xref:System.Windows.Shapes.Rectangle> \(`rect1`\) comme enfant de <xref:System.Windows.Controls.Canvas>.  Vous pouvez modifier les propriétés de hauteur d'un <xref:System.Windows.Shapes.Rectangle> à l'aide d'une série d'éléments <xref:System.Windows.Controls.ListBox> qui représentent les valeurs de propriété <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> et <xref:System.Windows.FrameworkElement.Height%2A> De cette manière, la priorité de chaque propriété est affichée visuellement.  
  
 [!code-xml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Les exemples de code\-behind suivants gèrent les événements déclenchés par l'événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>.  Chaque gestionnaire extrait l'entrée de <xref:System.Windows.Controls.ListBox>, analyse la valeur en tant que <xref:System.Double> et applique la valeur à la propriété associée à la hauteur spécifiée.  Les valeurs de hauteur sont également converties en une chaîne et écrites dans différents éléments <xref:System.Windows.Controls.TextBlock> \(la définition de ces éléments n'est pas affichée dans le XAML sélectionné\).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Pour obtenir l'exemple complet, consultez [Propriétés Height, exemple](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>   
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>   
 <xref:System.Windows.FrameworkElement.MinHeight%2A>   
 <xref:System.Windows.FrameworkElement.Height%2A>   
 [Définir les propriétés Width d'un élément](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Propriétés Height, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=159993)