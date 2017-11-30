---
title: "Comment : redimensionner des lignes avec un GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resizing grid rows [WPF]
- grid rows [WPF], resizing
- GridSplitter control [WPF], resizing grid rows
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6621cc0048270b97c42ff4c4e646b0ddd9ca3477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a>Comment : redimensionner des lignes avec un GridSplitter
Cet exemple montre comment utiliser une horizontale <xref:System.Windows.Controls.GridSplitter> pour redistribuer l’espace entre les deux lignes dans un <xref:System.Windows.Controls.Grid> sans modifier les dimensions de la <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Exemple  
 **Comment créer un GridSplitter qui chevauche le bord d’une ligne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui redimensionne les lignes adjacentes dans une <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Row%2A> propriété attachée à une des lignes que vous voulez redimensionner. Si votre <xref:System.Windows.Controls.Grid> a plusieurs colonnes, définissez la <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriété attachée pour spécifier le nombre de colonnes. Définissez ensuite la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> à <xref:System.Windows.VerticalAlignment.Top> ou <xref:System.Windows.VerticalAlignment.Bottom> (l’alignement défini dépend des deux lignes que vous souhaitez redimensionner). Enfin, définissez la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Stretch>.  
  
 L’exemple suivant montre comment définir une horizontale <xref:System.Windows.Controls.GridSplitter> qui redimensionne les lignes adjacentes.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 A <xref:System.Windows.Controls.GridSplitter> qui n’occupe pas sa propre ligne peut être masqué par d’autres contrôles dans le <xref:System.Windows.Controls.Grid>. Pour plus d’informations sur la manière d’éviter ce problème, consultez la page [Vérifier qu’un GridSplitter est visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).  
  
 **Comment créer un GridSplitter qui occupe une ligne**  
  
 Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui occupe une ligne dans un <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Row%2A> propriété attachée à une des lignes que vous voulez redimensionner. Si votre <xref:System.Windows.Controls.Grid> a plusieurs colonnes, définissez la <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriété attachée au nombre de colonnes. Puis définissez la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> à <xref:System.Windows.VerticalAlignment.Center>, définissez le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Stretch>et définissez la <xref:System.Windows.Controls.RowDefinition.Height%2A> de la ligne qui contient le <xref:System.Windows.Controls.GridSplitter> à <xref:System.Windows.GridLength.Auto%2A>.  
  
 L’exemple suivant montre comment définir une horizontale <xref:System.Windows.Controls.GridSplitter> qui occupe une ligne et redimensionne les lignes de chaque côté de celui-ci.  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.GridSplitter>  
 [Guides pratiques](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
