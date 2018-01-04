---
title: "Comment : obtenir le décalage d'un Visual"
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
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee18503bdd6100cbe7a62ac70d7ea0848fb124eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="5b8af-102">Comment : obtenir le décalage d'un Visual</span><span class="sxs-lookup"><span data-stu-id="5b8af-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="5b8af-103">Ces exemples montrent comment récupérer la valeur de décalage d’un objet visuel qui est relatif à son parent, ou de n’importe quel ancêtre ou descendant.</span><span class="sxs-lookup"><span data-stu-id="5b8af-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b8af-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="5b8af-104">Example</span></span>  
 <span data-ttu-id="5b8af-105">L’exemple de balise suivant montre un <xref:System.Windows.Controls.TextBlock> qui est défini avec <xref:System.Windows.FrameworkElement.Margin%2A> valeur 4.</span><span class="sxs-lookup"><span data-stu-id="5b8af-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="5b8af-106">L’exemple de code suivant montre comment utiliser le <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> méthode pour récupérer le décalage de la <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="5b8af-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="5b8af-107">Les valeurs de décalage sont contenues dans la liste retournée <xref:System.Windows.Vector> valeur.</span><span class="sxs-lookup"><span data-stu-id="5b8af-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="5b8af-108">L’offset prend en compte la <xref:System.Windows.FrameworkElement.Margin%2A> valeur.</span><span class="sxs-lookup"><span data-stu-id="5b8af-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="5b8af-109">Dans ce cas, <xref:System.Windows.Vector.X%2A> est 4, et <xref:System.Windows.Vector.Y%2A> est 4.</span><span class="sxs-lookup"><span data-stu-id="5b8af-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="5b8af-110">La valeur de décalage renvoyée est par rapport au parent de la <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="5b8af-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="5b8af-111">Si vous souhaitez retourner une valeur de décalage par rapport au parent de n’est pas un <xref:System.Windows.Media.Visual>, utilisez le <xref:System.Windows.Media.Visual.TransformToAncestor%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="5b8af-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="5b8af-112">Obtention de l’Offset relatif à un ancêtre</span><span class="sxs-lookup"><span data-stu-id="5b8af-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="5b8af-113">L’exemple de balise suivant montre un <xref:System.Windows.Controls.TextBlock> qui est imbriqué dans deux <xref:System.Windows.Controls.StackPanel> objets.</span><span class="sxs-lookup"><span data-stu-id="5b8af-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="5b8af-114">L’illustration suivante montre les résultats du balisage.</span><span class="sxs-lookup"><span data-stu-id="5b8af-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="5b8af-115">![Valeurs de décalage des objets](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="5b8af-115">![Offset values of objects](../../../../docs/framework/wpf/graphics-multimedia/media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="5b8af-116">TextBlock imbriqué dans deux StackPanels</span><span class="sxs-lookup"><span data-stu-id="5b8af-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="5b8af-117">L’exemple de code suivant montre comment utiliser le <xref:System.Windows.Media.Visual.TransformToAncestor%2A> méthode pour récupérer le décalage de la <xref:System.Windows.Controls.TextBlock> relatif au conteneur <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5b8af-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5b8af-118">Les valeurs de décalage sont contenues dans la liste retournée <xref:System.Windows.Media.GeneralTransform> valeur.</span><span class="sxs-lookup"><span data-stu-id="5b8af-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="5b8af-119">L’offset prend en compte la <xref:System.Windows.FrameworkElement.Margin%2A> valeurs pour tous les objets dans le conteneur <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5b8af-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5b8af-120">Dans ce cas, <xref:System.Windows.Vector.X%2A> 28 (16 + 8 + 4), et <xref:System.Windows.Vector.Y%2A> est 28.</span><span class="sxs-lookup"><span data-stu-id="5b8af-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="5b8af-121">La valeur de décalage renvoyée est relative à l’ancêtre de la <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="5b8af-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="5b8af-122">Si vous souhaitez retourner une valeur de décalage relative au descendant d’un <xref:System.Windows.Media.Visual>, utilisez le <xref:System.Windows.Media.Visual.TransformToDescendant%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="5b8af-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="5b8af-123">Obtention de l’Offset par rapport à un Descendant</span><span class="sxs-lookup"><span data-stu-id="5b8af-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="5b8af-124">L’exemple de balise suivant montre un <xref:System.Windows.Controls.TextBlock> qui est contenue dans un <xref:System.Windows.Controls.StackPanel> objet.</span><span class="sxs-lookup"><span data-stu-id="5b8af-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="5b8af-125">L’exemple de code suivant montre comment utiliser le <xref:System.Windows.Media.Visual.TransformToDescendant%2A> méthode pour récupérer le décalage de la <xref:System.Windows.Controls.StackPanel> par rapport à son enfant <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="5b8af-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="5b8af-126">Les valeurs de décalage sont contenues dans la liste retournée <xref:System.Windows.Media.GeneralTransform> valeur.</span><span class="sxs-lookup"><span data-stu-id="5b8af-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="5b8af-127">L’offset prend en compte la <xref:System.Windows.FrameworkElement.Margin%2A> valeurs pour tous les objets.</span><span class="sxs-lookup"><span data-stu-id="5b8af-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="5b8af-128">Dans ce cas, <xref:System.Windows.Vector.X%2A> -4, et <xref:System.Windows.Vector.Y%2A> est -4.</span><span class="sxs-lookup"><span data-stu-id="5b8af-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="5b8af-129">Les valeurs de décalage sont des valeurs négatives, étant donné que l’objet parent est décalé vers par rapport à son objet enfant.</span><span class="sxs-lookup"><span data-stu-id="5b8af-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8af-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b8af-130">See Also</span></span>  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="5b8af-131">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="5b8af-131">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
