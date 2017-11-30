---
title: "Comment : redimensionner des colonnes avec un GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c8299a3f4885618601c8087a61c21dc5d989813
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a>Comment : redimensionner des colonnes avec un GridSplitter
Cet exemple montre comment créer un vertical <xref:System.Windows.Controls.GridSplitter> afin de redistribuer l’espace entre deux colonnes dans un <xref:System.Windows.Controls.Grid> sans modifier les dimensions de la <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemple  
 **Comment créer un GridSplitter qui chevauche le bord d’une colonne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui redimensionne les colonnes adjacentes dans une <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Column%2A> propriété attachée à une des colonnes que vous voulez redimensionner. Si votre <xref:System.Windows.Controls.Grid> a plusieurs lignes, définissez le <xref:System.Windows.Controls.Grid.RowSpan%2A> propriété attachée au nombre de lignes. Définissez ensuite la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Left> ou <xref:System.Windows.HorizontalAlignment.Right> (l’alignement défini dépend des deux colonnes que vous souhaitez redimensionner). Enfin, définissez la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété <xref:System.Windows.VerticalAlignment.Stretch>.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> qui n’a pas sa propre colonne peut être masqué par d’autres contrôles dans le <xref:System.Windows.Controls.Grid>. Pour plus d’informations sur la manière d’éviter ce problème, consultez la page [Vérifier qu’un GridSplitter est visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Comment créer un GridSplitter qui occupe une colonne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui occupe une colonne dans un <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Column%2A> propriété attachée à une des colonnes que vous voulez redimensionner. Si votre grille a plusieurs lignes, définissez le <xref:System.Windows.Controls.Grid.RowSpan%2A> propriété attachée au nombre de lignes. Puis définissez la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> à <xref:System.Windows.HorizontalAlignment.Center>, définissez le <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété <xref:System.Windows.VerticalAlignment.Stretch>et définissez la <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de la colonne qui contient le <xref:System.Windows.Controls.GridSplitter> à <xref:System.Windows.GridLength.Auto%2A>.  
  
 L’exemple suivant montre comment définir une verticale <xref:System.Windows.Controls.GridSplitter> qui occupe une colonne et redimensionne les colonnes de chaque côté de celui-ci.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.GridSplitter>  
 [Guides pratiques](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
