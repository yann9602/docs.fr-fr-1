---
title: "Comment : définir les propriétés Height d'un élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ae66e60375cfbc45a4f1e8834b6420bc5c0b70a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>Comment : définir les propriétés Height d'un élément
## <a name="example"></a>Exemple  
 Cet exemple montre visuellement les différences de comportement entre les quatre propriétés associées à la hauteur dans rendu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 La <xref:System.Windows.FrameworkElement> classe expose quatre propriétés qui décrivent les caractéristiques de la hauteur d’un élément. Ces quatre propriétés peuvent entrer en conflit, et dans ce cas, la valeur est prioritaire est déterminée comme suit : le <xref:System.Windows.FrameworkElement.MinHeight%2A> valeur est prioritaire sur la <xref:System.Windows.FrameworkElement.MaxHeight%2A> valeur, qui à son tour est prioritaire sur la <xref:System.Windows.FrameworkElement.Height%2A> valeur. Une quatrième propriété, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, est en lecture seule et signale la hauteur réelle, telle que déterminée par les interactions avec le processus de mise en page.  
  
 Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemples dessinent un <xref:System.Windows.Shapes.Rectangle> élément (`rect1`) en tant qu’enfant de <xref:System.Windows.Controls.Canvas>. Vous pouvez modifier les propriétés de hauteur d’un <xref:System.Windows.Shapes.Rectangle> à l’aide d’une série de <xref:System.Windows.Controls.ListBox> éléments qui représentent les valeurs de propriété <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, et <xref:System.Windows.FrameworkElement.Height%2A>. De cette manière, la priorité de chaque propriété est affichée visuellement.  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 Les exemples de code-behind suivants gèrent les événements qui le <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> déclenche des événements. Chaque gestionnaire extrait l’entrée de la <xref:System.Windows.Controls.ListBox>, analyse la valeur en tant qu’un <xref:System.Double>et applique la valeur à la propriété associées à la hauteur spécifiée. Les valeurs de hauteur sont également converties en une chaîne et écrites dans différents <xref:System.Windows.Controls.TextBlock> éléments (définition de ces éléments n’est pas affichée dans le XAML sélectionné).  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 Pour obtenir un exemple complet, consultez [propriétés Height, exemple](http://go.microsoft.com/fwlink/?LinkID=159993).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [Définir les propriétés Width d’un élément](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Propriétés Height, exemple](http://go.microsoft.com/fwlink/?LinkID=159993)
