---
title: "Comment : appliquer une transformation à un élément lorsqu'un événement se produit"
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
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e58e49ecc852b87d03d4112208354e608248984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="842f6-102">Comment : appliquer une transformation à un élément lorsqu'un événement se produit</span><span class="sxs-lookup"><span data-stu-id="842f6-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="842f6-103">Cet exemple montre comment appliquer un <xref:System.Windows.Media.ScaleTransform> lorsqu’un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="842f6-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="842f6-104">Le concept illustré ici est le même que celui que vous utilisez pour l’application d’autres types de transformations.</span><span class="sxs-lookup"><span data-stu-id="842f6-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="842f6-105">Pour plus d’informations sur les types de transformations disponibles, consultez le <xref:System.Windows.Media.Transform> classe ou [transforme une vue d’ensemble](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="842f6-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="842f6-106">Vous pouvez appliquer une transformation à un élément de deux façons :</span><span class="sxs-lookup"><span data-stu-id="842f6-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="842f6-107">Si vous le faites *pas* voulez que la transformation affecte la disposition, utilisez le <xref:System.Windows.UIElement.RenderTransform%2A> propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="842f6-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="842f6-108">Si vous ne souhaitez pas que la transformation affecte la disposition, utilisez le <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="842f6-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="842f6-109">L’exemple suivant applique un <xref:System.Windows.Media.ScaleTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="842f6-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="842f6-110">Lorsque la souris se déplace sur le bouton, le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés de la <xref:System.Windows.Media.ScaleTransform> sont définies sur `2`, ce qui entraîne le bouton plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="842f6-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="842f6-111">Lorsque la souris se déplace hors du bouton, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> sont définies sur `1`, ce qui entraîne le bouton revenir à sa taille d’origine.</span><span class="sxs-lookup"><span data-stu-id="842f6-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="842f6-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="842f6-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="842f6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="842f6-113">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="842f6-114">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="842f6-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="842f6-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="842f6-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="842f6-116">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="842f6-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
