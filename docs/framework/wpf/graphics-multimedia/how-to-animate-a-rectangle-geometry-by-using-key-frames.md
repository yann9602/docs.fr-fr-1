---
title: "Comment : animer une géométrie rectangle à l'aide d'images clés"
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
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6c23f894b6fa93a3889356416bd95f61fff8beb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a><span data-ttu-id="78838-102">Comment : animer une géométrie rectangle à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="78838-102">How to: Animate a Rectangle Geometry by Using Key Frames</span></span>
<span data-ttu-id="78838-103">Cet exemple montre comment animer la <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriété d’un <xref:System.Windows.Media.RectangleGeometry> à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="78838-103">This example shows how to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78838-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="78838-104">Example</span></span>  
 <span data-ttu-id="78838-105">L’exemple suivant utilise le <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> classe pour animer la <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriété d’un <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="78838-105">The following example uses the <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.RectangleGeometry.Rect%2A> property of a <xref:System.Windows.Media.RectangleGeometry>.</span></span> <span data-ttu-id="78838-106">Cette animation utilise trois images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="78838-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="78838-107">Pendant les deux premières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.LinearRectKeyFrame> classe pour animer une modification graduelle de la position, la largeur et la hauteur d’un rectangle.</span><span class="sxs-lookup"><span data-stu-id="78838-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearRectKeyFrame> class to animate a gradual change in the position, width, and height of a rectangle.</span></span> <span data-ttu-id="78838-108">Images clés linéaires comme <xref:System.Windows.Media.Animation.LinearRectKeyFrame> créer une transition linéaire fluide entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="78838-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearRectKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="78838-109">À la fin de la prochaine demi-seconde, utilise une instance de la <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> classe pour diminuer soudainement la hauteur du rectangle.</span><span class="sxs-lookup"><span data-stu-id="78838-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> class to suddenly decrease the height of the rectangle.</span></span> <span data-ttu-id="78838-110">Les images clés discrètes telles que <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> créer des changements soudains entre les valeurs, autrement dit, la diminution de la hauteur se produit rapidement et n’est pas subtile.</span><span class="sxs-lookup"><span data-stu-id="78838-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> create sudden changes between values, that is, the decrease in height occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="78838-111">Pendant les deux dernières secondes, utilise une instance de la <xref:System.Windows.Media.Animation.SplineRectKeyFrame> classe pour modifier le rectangle à sa taille et la position d’origine.</span><span class="sxs-lookup"><span data-stu-id="78838-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame> class to change the rectangle back to its original size and position.</span></span> <span data-ttu-id="78838-112">Les images clés spline comme <xref:System.Windows.Media.Animation.SplineRectKeyFrame> créer une transition entre des valeurs en fonction des valeurs de la <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="78838-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineRectKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="78838-113">Dans cet exemple, le changement commence lentement, puis accélère de façon exponentielle jusqu’à la fin du segment temporel.</span><span class="sxs-lookup"><span data-stu-id="78838-113">In this example, the change begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="78838-114">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="78838-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78838-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78838-115">See Also</span></span>  
 <xref:System.Windows.Media.RectangleGeometry>  
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>  
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>  
 [<span data-ttu-id="78838-116">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="78838-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="78838-117">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="78838-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
