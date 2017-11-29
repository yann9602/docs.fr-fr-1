---
title: "Comment : animer la position d'un objet à l'aide de PointAnimation"
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
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6590c79ac6b6f104d9944a32da4c99318d334eec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="4bcf5-102">Comment : animer la position d'un objet à l'aide de PointAnimation</span><span class="sxs-lookup"><span data-stu-id="4bcf5-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="4bcf5-103">Cet exemple montre comment utiliser le <xref:System.Windows.Media.Animation.PointAnimation> classe pour animer un objet sur un <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="4bcf5-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bcf5-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4bcf5-104">Example</span></span>  
 <span data-ttu-id="4bcf5-105">L’exemple suivant déplace une ellipse le long d’un <xref:System.Windows.Shapes.Path> à partir d’un point sur l’écran à l’autre.</span><span class="sxs-lookup"><span data-stu-id="4bcf5-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="4bcf5-106">L’exemple anime la position d’un <xref:System.Windows.Media.EllipseGeometry> à l’aide de <xref:System.Windows.Media.Animation.PointAnimation> pour animer la <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4bcf5-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4bcf5-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bcf5-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="4bcf5-108">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="4bcf5-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="4bcf5-109">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="4bcf5-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="4bcf5-110">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="4bcf5-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="4bcf5-111">Animation et minutage</span><span class="sxs-lookup"><span data-stu-id="4bcf5-111">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="4bcf5-112">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="4bcf5-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
