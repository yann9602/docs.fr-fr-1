---
title: "Comment : animer un EllipseGeometry"
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
- animation [WPF], EllipseGeometry objects [WPF]
- EllipseGeometry objects [WPF], animating
- graphics [WPF], animation
ms.assetid: 767b9b6e-9cb7-482e-b6c2-fee7750c3995
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc9eea56d9070d33820f8e2ef1bd8eba3ec04303
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-ellipsegeometry"></a><span data-ttu-id="32de8-102">Comment : animer un EllipseGeometry</span><span class="sxs-lookup"><span data-stu-id="32de8-102">How to: Animate an EllipseGeometry</span></span>
<span data-ttu-id="32de8-103">Cet exemple montre comment animer un <xref:System.Windows.Media.Geometry> dans un <xref:System.Windows.Shapes.Path> élément.</span><span class="sxs-lookup"><span data-stu-id="32de8-103">This example shows how to animate a <xref:System.Windows.Media.Geometry> within a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="32de8-104">Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.PointAnimation> est utilisée pour animer la <xref:System.Windows.Media.EllipseGeometry.Center%2A> d’un <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="32de8-104">In the following example, a <xref:System.Windows.Media.Animation.PointAnimation> is used to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> of an <xref:System.Windows.Media.EllipseGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32de8-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="32de8-105">Example</span></span>  
 [!code-xaml[animatepath_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip_XAML/CS/EllipseGeometryExample.xaml#1)]  
  
 [!code-csharp[animatepath_snip#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip/CSharp/EllipseGeometryExample.cs#101)]  
  
 [!code-vb[animatepath_snip#201](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animatepath_snip/VisualBasic/EllipseGeometryExample.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="32de8-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32de8-106">See Also</span></span>  
 [<span data-ttu-id="32de8-107">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="32de8-107">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="32de8-108">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="32de8-108">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
