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
ms.workload: dotnet
ms.openlocfilehash: 2d4cf06a86a1da7bb34074623f8f19f4bda7a724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-rows-with-a-gridsplitter"></a><span data-ttu-id="b61f8-102">Comment : redimensionner des lignes avec un GridSplitter</span><span class="sxs-lookup"><span data-stu-id="b61f8-102">How to: Resize Rows with a GridSplitter</span></span>
<span data-ttu-id="b61f8-103">Cet exemple montre comment utiliser une horizontale <xref:System.Windows.Controls.GridSplitter> pour redistribuer l’espace entre les deux lignes dans un <xref:System.Windows.Controls.Grid> sans modifier les dimensions de la <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="b61f8-103">This example shows how to use a horizontal <xref:System.Windows.Controls.GridSplitter> to redistribute the space between two rows in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b61f8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b61f8-104">Example</span></span>  
 <span data-ttu-id="b61f8-105">**Comment créer un GridSplitter qui chevauche le bord d’une ligne**</span><span class="sxs-lookup"><span data-stu-id="b61f8-105">**How to create a GridSplitter that overlays the edge of a row**</span></span>  
  
 <span data-ttu-id="b61f8-106">Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui redimensionne les lignes adjacentes dans une <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Row%2A> propriété attachée à une des lignes que vous voulez redimensionner.</span><span class="sxs-lookup"><span data-stu-id="b61f8-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="b61f8-107">Si votre <xref:System.Windows.Controls.Grid> a plusieurs colonnes, définissez la <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriété attachée pour spécifier le nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="b61f8-107">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to specify the number of columns.</span></span> <span data-ttu-id="b61f8-108">Définissez ensuite la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> à <xref:System.Windows.VerticalAlignment.Top> ou <xref:System.Windows.VerticalAlignment.Bottom> (l’alignement défini dépend des deux lignes que vous souhaitez redimensionner).</span><span class="sxs-lookup"><span data-stu-id="b61f8-108">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Top> or <xref:System.Windows.VerticalAlignment.Bottom> (which alignment you set depends on which two rows you want to resize).</span></span> <span data-ttu-id="b61f8-109">Enfin, définissez la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="b61f8-109">Finally, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>.</span></span>  
  
 <span data-ttu-id="b61f8-110">L’exemple suivant montre comment définir une horizontale <xref:System.Windows.Controls.GridSplitter> qui redimensionne les lignes adjacentes.</span><span class="sxs-lookup"><span data-stu-id="b61f8-110">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that resizes adjacent rows.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 <span data-ttu-id="b61f8-111">A <xref:System.Windows.Controls.GridSplitter> qui n’occupe pas sa propre ligne peut être masqué par d’autres contrôles dans le <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="b61f8-111">A <xref:System.Windows.Controls.GridSplitter> that does not occupy its own row may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="b61f8-112">Pour plus d’informations sur la manière d’éviter ce problème, consultez la page [Vérifier qu’un GridSplitter est visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="b61f8-112">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="b61f8-113">**Comment créer un GridSplitter qui occupe une ligne**</span><span class="sxs-lookup"><span data-stu-id="b61f8-113">**How to create a GridSplitter that occupies a row**</span></span>  
  
 <span data-ttu-id="b61f8-114">Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui occupe une ligne dans un <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Row%2A> propriété attachée à une des lignes que vous voulez redimensionner.</span><span class="sxs-lookup"><span data-stu-id="b61f8-114">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a row in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Row%2A> attached property to one of the rows that you want to resize.</span></span> <span data-ttu-id="b61f8-115">Si votre <xref:System.Windows.Controls.Grid> a plusieurs colonnes, définissez la <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriété attachée au nombre de colonnes.</span><span class="sxs-lookup"><span data-stu-id="b61f8-115">If your <xref:System.Windows.Controls.Grid> has more than one column, set the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> attached property to the number of columns.</span></span> <span data-ttu-id="b61f8-116">Puis définissez la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> à <xref:System.Windows.VerticalAlignment.Center>, définissez le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Stretch>et définissez la <xref:System.Windows.Controls.RowDefinition.Height%2A> de la ligne qui contient le <xref:System.Windows.Controls.GridSplitter> à <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="b61f8-116">Then set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> to <xref:System.Windows.VerticalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Stretch>, and set the <xref:System.Windows.Controls.RowDefinition.Height%2A> of the row that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="b61f8-117">L’exemple suivant montre comment définir une horizontale <xref:System.Windows.Controls.GridSplitter> qui occupe une ligne et redimensionne les lignes de chaque côté de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="b61f8-117">The following example shows how to define a horizontal <xref:System.Windows.Controls.GridSplitter> that occupies a row and resizes the rows on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="b61f8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b61f8-118">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="b61f8-119">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="b61f8-119">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
