---
title: "Comment : créer un élément de grille"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30fdd89a46e5d2027e9c525b0ca8cfcfb1d11ed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-grid-element"></a>Comment : créer un élément de grille
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer et utiliser une instance de <xref:System.Windows.Controls.Grid> à l’aide [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code. Cet exemple utilise trois <xref:System.Windows.Controls.ColumnDefinition> objets et trois <xref:System.Windows.Controls.RowDefinition> objets pour créer une grille comportant neuf cellules, comme dans une feuille de calcul. Chaque cellule contient un <xref:System.Windows.Controls.TextBlock> élément qui représente les données et la ligne supérieure contient un <xref:System.Windows.Controls.TextBlock> avec la <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriété appliquée. Pour afficher les limites de chaque cellule, le <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriété est activée.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Grid>  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)
