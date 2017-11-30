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
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="173a9-102">Comment : créer un élément de grille</span><span class="sxs-lookup"><span data-stu-id="173a9-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="173a9-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="173a9-103">Example</span></span>  
 <span data-ttu-id="173a9-104">L’exemple suivant montre comment créer et utiliser une instance de <xref:System.Windows.Controls.Grid> à l’aide [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code.</span><span class="sxs-lookup"><span data-stu-id="173a9-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="173a9-105">Cet exemple utilise trois <xref:System.Windows.Controls.ColumnDefinition> objets et trois <xref:System.Windows.Controls.RowDefinition> objets pour créer une grille comportant neuf cellules, comme dans une feuille de calcul.</span><span class="sxs-lookup"><span data-stu-id="173a9-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="173a9-106">Chaque cellule contient un <xref:System.Windows.Controls.TextBlock> élément qui représente les données et la ligne supérieure contient un <xref:System.Windows.Controls.TextBlock> avec la <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriété appliquée.</span><span class="sxs-lookup"><span data-stu-id="173a9-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="173a9-107">Pour afficher les limites de chaque cellule, le <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriété est activée.</span><span class="sxs-lookup"><span data-stu-id="173a9-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="173a9-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="173a9-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="173a9-109">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="173a9-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
