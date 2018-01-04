---
title: "Comment : créer et utiliser un objet GridLengthConverter"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300916ec102682e1d886d43fbe70eeaf088d6454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>Comment : créer et utiliser un objet GridLengthConverter
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer et utiliser une instance de <xref:System.Windows.GridLengthConverter>. L’exemple définit une méthode personnalisée appelée `changeCol`, qui passe le <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.GridLengthConverter> qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d’un <xref:System.Windows.Controls.ListBoxItem> à une instance de <xref:System.Windows.GridLength>. La valeur convertie est ensuite retournée comme la valeur de la <xref:System.Windows.Controls.ColumnDefinition.Width%2A> propriété de la <xref:System.Windows.Controls.ColumnDefinition> élément.  
  
 L’exemple définit également une deuxième méthode personnalisée, appelée `changeColVal`. Cette méthode personnalisée convertit le <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> d’un <xref:System.Windows.Controls.Slider> à un <xref:System.String> puis passe cette valeur à la <xref:System.Windows.Controls.ColumnDefinition> en tant que le <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de l’élément.  
  
 Notez que distinct [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier définit le contenu d’un <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
