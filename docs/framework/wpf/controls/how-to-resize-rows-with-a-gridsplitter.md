---
title: "Comment&#160;: redimensionner des lignes avec un GridSplitter | Microsoft Docs"
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
  - "lignes de grille, redimensionner"
  - "GridSplitter (contrôle), redimensionner des lignes de grille"
  - "redimensionner des lignes de grille"
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: redimensionner des lignes avec un GridSplitter
Cet exemple montre comment utiliser un <xref:System.Windows.Controls.GridSplitter> horizontal pour redistribuer l'espace entre deux lignes dans une <xref:System.Windows.Controls.Grid> sans modifier les dimensions de la <xref:System.Windows.Controls.Grid>.  
  
## Exemple  
 **Comment créer un GridSplitter qui chevauche le bord d'une ligne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui redimensionne les lignes adjacentes dans une <xref:System.Windows.Controls.Grid>, affectez à la [propriété attachée](GTMT) <xref:System.Windows.Controls.Grid.Row%2A> l'une des lignes que vous souhaitez redimensionner.  Si votre <xref:System.Windows.Controls.Grid> a plusieurs colonnes, définissez la propriété attachée <xref:System.Windows.Controls.Grid.ColumnSpan%2A> pour spécifier le nombre de colonnes.  Puis, affectez à <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> la valeur <xref:System.Windows.VerticalAlignment> ou <xref:System.Windows.VerticalAlignment> \(l'alignement défini dépend des deux lignes que vous souhaitez redimensionner\).  Enfin, affectez à la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> la valeur <xref:System.Windows.HorizontalAlignment>.  
  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.GridSplitter> horizontal qui redimensionne des lignes adjacentes.  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 Un <xref:System.Windows.Controls.GridSplitter> qui n'occupe pas sa propre ligne peut être masqué par d'autres contrôles dans la <xref:System.Windows.Controls.Grid>.  Pour plus d'informations sur la manière d'éviter ce problème, consultez [Vérifier qu'un GridSplitter est visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Comment créer un GridSplitter qui occupe une ligne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui occupe une ligne dans une <xref:System.Windows.Controls.Grid>, affectez à la [propriété attachée](GTMT) <xref:System.Windows.Controls.Grid.Row%2A> l'une des lignes que vous souhaitez redimensionner.  Si votre <xref:System.Windows.Controls.Grid> a plusieurs colonnes, affectez à la propriété attachée <xref:System.Windows.Controls.Grid.ColumnSpan%2A> le nombre de colonnes.  Puis, affectez à <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> la valeur <xref:System.Windows.VerticalAlignment>, affectez à la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> la valeur <xref:System.Windows.HorizontalAlignment>, et affectez à la <xref:System.Windows.Controls.RowDefinition.Height%2A> de la ligne qui contient le <xref:System.Windows.Controls.GridSplitter> la valeur <xref:System.Windows.GridLength.Auto%2A>.  
  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.GridSplitter> horizontal qui occupe une ligne et redimensionne les lignes de chaque côté.  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.GridSplitter>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)