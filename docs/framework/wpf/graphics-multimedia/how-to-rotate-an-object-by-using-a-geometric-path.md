---
title: "Comment : faire pivoter un objet à l'aide d'un tracé géométrique"
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
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 078d1054f9b6a4c2f6172f00aa8c4ad9077e6db2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="3b7d9-102">Comment : faire pivoter un objet à l'aide d'un tracé géométrique</span><span class="sxs-lookup"><span data-stu-id="3b7d9-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="3b7d9-103">Cet exemple montre comment pivoter un objet le long d’un tracé géométrique définie par un <xref:System.Windows.Media.PathGeometry> objet.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7d9-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b7d9-104">Example</span></span>  
 <span data-ttu-id="3b7d9-105">L’exemple suivant utilise trois <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objets pour déplacer un rectangle sur un tracé géométrique.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="3b7d9-106">La première <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anime un <xref:System.Windows.Media.RotateTransform> qui est appliqué au rectangle.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="3b7d9-107">L’animation génère des valeurs d’angle.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-107">The animation generates angle values.</span></span> <span data-ttu-id="3b7d9-108">Le rectangle tourne (pivote) ainsi sur les contours du tracé.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="3b7d9-109">Les deux objets animent la <xref:System.Windows.Media.TranslateTransform.X%2A> et <xref:System.Windows.Media.TranslateTransform.Y%2A> valeurs d’un <xref:System.Windows.Media.TranslateTransform> qui est appliqué au rectangle.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="3b7d9-110">Le rectangle se déplace alors horizontalement et verticalement sur le tracé.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="3b7d9-111">Une autre façon de faire pivoter un objet à l’aide d’un tracé géométrique consiste à utiliser un <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> et définissez son <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="3b7d9-112">Pour plus d’informations et obtenir un exemple, consultez [faire pivoter un objet à l’aide d’un tracé géométrique (Animation de matrice)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="3b7d9-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="3b7d9-113">Pour obtenir un exemple complet, consultez [exemple d’Animation de chemin d’accès](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="3b7d9-113">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7d9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b7d9-114">See Also</span></span>  
 [<span data-ttu-id="3b7d9-115">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="3b7d9-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="3b7d9-116">Animation de tracés, exemple</span><span class="sxs-lookup"><span data-stu-id="3b7d9-116">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="3b7d9-117">Guides pratiques relatifs aux animations de tracés</span><span class="sxs-lookup"><span data-stu-id="3b7d9-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
