---
title: "Comment : animer un objet sur un tracé (animation de point)"
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
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399d6b8028b8715f38335089a723707657df4a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="97fe3-102">Comment : animer un objet sur un tracé (animation de point)</span><span class="sxs-lookup"><span data-stu-id="97fe3-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="97fe3-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.Animation.PointAnimationUsingPath> objet à animer un <xref:System.Windows.Point> sur un tracé courbé.</span><span class="sxs-lookup"><span data-stu-id="97fe3-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97fe3-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="97fe3-104">Example</span></span>  
 <span data-ttu-id="97fe3-105">L’exemple suivant déplace un <xref:System.Windows.Media.EllipseGeometry> le long d’un chemin d’accès défini par un <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="97fe3-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="97fe3-106">La géométrie d’ellipse <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété, qui prend un <xref:System.Windows.Point> valeur, spécifie sa position ; pour déplacer la géométrie de l’ellipse, vous animer son <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="97fe3-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="97fe3-107">L’exemple utilise un <xref:System.Windows.Media.Animation.PointAnimationUsingPath> pour animer la <xref:System.Windows.Media.EllipseGeometry> l’objet <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="97fe3-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="97fe3-108">Pour obtenir un exemple complet, consultez [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="97fe3-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="97fe3-109">La version de code de l’exemple précédent utilisé un <xref:System.Windows.Media.Animation.Storyboard> pour animer la <xref:System.Windows.Media.EllipseGeometry>, bien qu’une animation a été appliquée.</span><span class="sxs-lookup"><span data-stu-id="97fe3-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="97fe3-110">A <xref:System.Windows.Media.Animation.Storyboard> est souvent le moyen le plus simple d’appliquer plusieurs animations, car ces animations peuvent être contrôlées par le même <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="97fe3-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="97fe3-111">Toutefois, un moyen plus simple pour appliquer une seule animation à une propriété lors de l’utilisation de code consiste à utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="97fe3-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="97fe3-112">Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="97fe3-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fe3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97fe3-113">See Also</span></span>  
 [<span data-ttu-id="97fe3-114">Animation de tracés, exemple</span><span class="sxs-lookup"><span data-stu-id="97fe3-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="97fe3-115">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="97fe3-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="97fe3-116">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="97fe3-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
