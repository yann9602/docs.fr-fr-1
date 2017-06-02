---
title: "Comment&#160;: d&#233;finir les propri&#233;t&#233;s Width d&#39;un &#233;l&#233;ment | Microsoft Docs"
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
  - "Panel (contrôle), propriétés de largeur d'éléments"
  - "propriétés de largeur"
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: d&#233;finir les propri&#233;t&#233;s Width d&#39;un &#233;l&#233;ment
## Exemple  
 Cet exemple montre visuellement les différences de rendu d'un comportement dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], parmi les quatre propriétés associées à la largeur.  
  
 La classe <xref:System.Windows.FrameworkElement> expose quatre propriétés qui décrivent les caractéristiques de largeur d'un élément.  Ces quatre propriétés peuvent entrer en conflit et, lorsque c'est le cas, la valeur prioritaire est déterminée comme suit : la valeur <xref:System.Windows.FrameworkElement.MinWidth%2A> est prioritaire sur la valeur <xref:System.Windows.FrameworkElement.MaxWidth%2A> qui, elle\-même, est prioritaire sur la valeur <xref:System.Windows.FrameworkElement.Width%2A>.  Une quatrième propriété, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, est en lecture seule et signale la largeur réelle, telle qu'elle est déterminée par les interactions avec le processus de disposition.  
  
 Les exemples [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivants dessinent un élément <xref:System.Windows.Shapes.Rectangle> \(`rect1`\) comme enfant de <xref:System.Windows.Controls.Canvas>.  Vous pouvez modifier les propriétés de largeur d'un <xref:System.Windows.Shapes.Rectangle> à l'aide d'une série d'éléments <xref:System.Windows.Controls.ListBox> qui représentent les valeurs de propriété de <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A> et <xref:System.Windows.FrameworkElement.Width%2A> De cette manière, la priorité de chaque propriété est affichée visuellement.  
  
 [!code-xml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 Les exemples de code\-behind suivants gèrent les événements déclenchés par l'événement <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>.  Chaque méthode personnalisée extrait l'entrée de la <xref:System.Windows.Controls.ListBox>, analyse la valeur en tant que <xref:System.Double> et applique la valeur à la propriété associée à la largeur spécifiée.  Les valeurs de largeur sont également converties en une chaîne et écrites dans différents éléments <xref:System.Windows.Controls.TextBlock> \(la définition de ces éléments n'est pas affichée dans le XAML sélectionné\).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Pour obtenir l'exemple complet, consultez [Comparaison des propriétés Width, exemple](http://go.microsoft.com/fwlink/?LinkID=160050)  
  
## Voir aussi  
 <xref:System.Windows.Controls.ListBox>   
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>   
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>   
 <xref:System.Windows.FrameworkElement.MinWidth%2A>   
 <xref:System.Windows.FrameworkElement.Width%2A>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Définir les propriétés Height d'un élément](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)   
 [Comparaison des propriétés Width, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160050)