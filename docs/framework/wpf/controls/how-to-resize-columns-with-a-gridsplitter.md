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
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="d95c1-102">Comment : redimensionner des colonnes avec un GridSplitter</span><span class="sxs-lookup"><span data-stu-id="d95c1-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="d95c1-103">Cet exemple montre comment créer un vertical <xref:System.Windows.Controls.GridSplitter> afin de redistribuer l’espace entre deux colonnes dans un <xref:System.Windows.Controls.Grid> sans modifier les dimensions de la <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="d95c1-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d95c1-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d95c1-104">Example</span></span>  
 <span data-ttu-id="d95c1-105">**Comment créer un GridSplitter qui chevauche le bord d’une colonne**</span><span class="sxs-lookup"><span data-stu-id="d95c1-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="d95c1-106">Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui redimensionne les colonnes adjacentes dans une <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Column%2A> propriété attachée à une des colonnes que vous voulez redimensionner.</span><span class="sxs-lookup"><span data-stu-id="d95c1-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="d95c1-107">Si votre <xref:System.Windows.Controls.Grid> a plusieurs lignes, définissez le <xref:System.Windows.Controls.Grid.RowSpan%2A> propriété attachée au nombre de lignes.</span><span class="sxs-lookup"><span data-stu-id="d95c1-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="d95c1-108">Définissez ensuite la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Left> ou <xref:System.Windows.HorizontalAlignment.Right> (l’alignement défini dépend des deux colonnes que vous souhaitez redimensionner).</span><span class="sxs-lookup"><span data-stu-id="d95c1-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="d95c1-109">Enfin, définissez la <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété <xref:System.Windows.VerticalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="d95c1-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="d95c1-110">A <xref:System.Windows.Controls.GridSplitter> qui n’a pas sa propre colonne peut être masqué par d’autres contrôles dans le <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="d95c1-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="d95c1-111">Pour plus d’informations sur la manière d’éviter ce problème, consultez la page [Vérifier qu’un GridSplitter est visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="d95c1-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="d95c1-112">**Comment créer un GridSplitter qui occupe une colonne**</span><span class="sxs-lookup"><span data-stu-id="d95c1-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="d95c1-113">Pour spécifier un <xref:System.Windows.Controls.GridSplitter> qui occupe une colonne dans un <xref:System.Windows.Controls.Grid>, définissez le <xref:System.Windows.Controls.Grid.Column%2A> propriété attachée à une des colonnes que vous voulez redimensionner.</span><span class="sxs-lookup"><span data-stu-id="d95c1-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="d95c1-114">Si votre grille a plusieurs lignes, définissez le <xref:System.Windows.Controls.Grid.RowSpan%2A> propriété attachée au nombre de lignes.</span><span class="sxs-lookup"><span data-stu-id="d95c1-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="d95c1-115">Puis définissez la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> à <xref:System.Windows.HorizontalAlignment.Center>, définissez le <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriété <xref:System.Windows.VerticalAlignment.Stretch>et définissez la <xref:System.Windows.Controls.ColumnDefinition.Width%2A> de la colonne qui contient le <xref:System.Windows.Controls.GridSplitter> à <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="d95c1-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="d95c1-116">L’exemple suivant montre comment définir une verticale <xref:System.Windows.Controls.GridSplitter> qui occupe une colonne et redimensionne les colonnes de chaque côté de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="d95c1-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="d95c1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d95c1-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="d95c1-118">Guides pratiques</span><span class="sxs-lookup"><span data-stu-id="d95c1-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
