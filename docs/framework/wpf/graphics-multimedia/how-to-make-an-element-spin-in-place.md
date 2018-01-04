---
title: "Comment : mettre un élément en rotation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae76d33a30853107cbecf0749230aefce77a866d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="a5983-102">Comment : mettre un élément en rotation</span><span class="sxs-lookup"><span data-stu-id="a5983-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="a5983-103">Cet exemple montre comment mettre un élément en rotation à l’aide un <xref:System.Windows.Media.RotateTransform> et un <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="a5983-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="a5983-104">L’exemple suivant applique la <xref:System.Windows.Media.RotateTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="a5983-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="a5983-105">L’exemple utilise un <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer la <xref:System.Windows.Media.RotateTransform.Angle%2A> de la <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="a5983-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="a5983-106">Pour rendre l’élément à mettre en place, l’exemple définit le <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriété de l’élément sur le point (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="a5983-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5983-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5983-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="a5983-108">Pour l’exemple complet, qui inclut plusieurs exemples de transformation, consultez [Transformations 2D, exemple](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="a5983-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5983-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5983-109">See Also</span></span>  
 [<span data-ttu-id="a5983-110">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="a5983-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a5983-111">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="a5983-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
