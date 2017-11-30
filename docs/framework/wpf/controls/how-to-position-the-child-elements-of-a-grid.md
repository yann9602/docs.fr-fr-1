---
title: "Comment : positionner les éléments enfants d'une grille"
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
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dbe0bcb5d3c46edcb97410e00832f1b9d6205b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="eb6b3-102">Comment : positionner les éléments enfants d'une grille</span><span class="sxs-lookup"><span data-stu-id="eb6b3-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="eb6b3-103">Cet exemple montre comment utiliser la méthode get et définir des méthodes qui sont définis dans <xref:System.Windows.Controls.Grid> pour positionner des éléments enfants.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb6b3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb6b3-104">Example</span></span>  
 <span data-ttu-id="eb6b3-105">L’exemple suivant définit un parent <xref:System.Windows.Controls.Grid> élément (`grid1`) qui a trois colonnes et trois lignes.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="eb6b3-106">Un enfant <xref:System.Windows.Shapes.Rectangle> élément (`rect1`) est ajouté à la <xref:System.Windows.Controls.Grid> position de colonne zéro, position de ligne zéro.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="eb6b3-107"><xref:System.Windows.Controls.Button>les éléments représentent des méthodes qui peuvent être appelées pour repositionner le <xref:System.Windows.Shapes.Rectangle> élément dans le <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="eb6b3-108">Lorsqu’un utilisateur clique sur un bouton, la méthode associée est activée.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="eb6b3-109">L’exemple de code-behind suivant gère les méthodes que le bouton <xref:System.Windows.Controls.Primitives.ButtonBase.Click> déclenchent des événements.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="eb6b3-110">L’exemple écrit ces appels de méthode <xref:System.Windows.Controls.TextBlock> éléments liée de l’utilisation des méthodes get pour sortir les nouvelles valeurs de propriété sous forme de chaînes.</span><span class="sxs-lookup"><span data-stu-id="eb6b3-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="eb6b3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb6b3-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="eb6b3-112">Vue d’ensemble de Panel</span><span class="sxs-lookup"><span data-stu-id="eb6b3-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
