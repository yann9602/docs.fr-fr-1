---
title: "Comment&#160;: redimensionner des colonnes avec un GridSplitter | Microsoft Docs"
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
  - "colonnes de grille, redimensionner"
  - "GridSplitter (contrôle), redimensionner des colonnes de grille"
  - "redimensionner des colonnes de grille"
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: redimensionner des colonnes avec un GridSplitter
Cet exemple montre comment créer un <xref:System.Windows.Controls.GridSplitter> vertical pour redistribuer l'espace entre deux colonnes dans une <xref:System.Windows.Controls.Grid> sans modifier les dimensions de la <xref:System.Windows.Controls.Grid>.  
  
## Exemple  
 **Comment créer un GridSplitter qui chevauche le bord d'une colonne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui redimensionne les colonnes adjacentes dans une <xref:System.Windows.Controls.Grid>, affectez à la [propriété attachée](GTMT) <xref:System.Windows.Controls.Grid.Column%2A> l'une des colonnes que vous souhaitez redimensionner.  Si votre <xref:System.Windows.Controls.Grid> a plusieurs lignes, affectez à la propriété attachée <xref:System.Windows.Controls.Grid.RowSpan%2A> le nombre de lignes.  Puis, affectez à la propriété <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> la valeur <xref:System.Windows.HorizontalAlignment> ou <xref:System.Windows.HorizontalAlignment> \(l'alignement défini dépend des deux colonnes que vous souhaitez redimensionner\).  Enfin, affectez à la propriété <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> la valeur <xref:System.Windows.VerticalAlignment>.  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 Un <xref:System.Windows.Controls.GridSplitter> qui n'a pas sa propre colonne peut être masqué par d'autres contrôles dans la <xref:System.Windows.Controls.Grid>.  Pour plus d'informations sur la manière d'éviter ce problème, consultez [Vérifier qu'un GridSplitter est visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Comment créer un GridSplitter qui occupe une colonne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui occupe une colonne dans une <xref:System.Windows.Controls.Grid>, affectez à la [propriété attachée](GTMT) <xref:System.Windows.Controls.Grid.Column%2A> l'une des colonnes que vous souhaitez redimensionner.  Si votre grille a plusieurs lignes, affectez à la propriété attachée <xref:System.Windows.Controls.Grid.RowSpan%2A> le nombre de lignes.  Puis, affectez à <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> la valeur <xref:System.Windows.HorizontalAlignment>, affectez à la propriété <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> la valeur <xref:System.Windows.VerticalAlignment>, et affectez à la <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de la colonne qui contient le <xref:System.Windows.Controls.GridSplitter> la valeur <xref:System.Windows.GridLength.Auto%2A>.  
  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.GridSplitter> vertical qui occupe une colonne et redimensionne les colonnes de chaque côté.  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.GridSplitter>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)