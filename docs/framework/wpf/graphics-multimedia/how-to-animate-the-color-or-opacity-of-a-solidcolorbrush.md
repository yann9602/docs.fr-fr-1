---
title: "Comment : animer la couleur ou l'opacité d'un SolidColorBrush"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 03052cdf68a5a8564d5a24c91521749c10afa6cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="f3155-102">Comment : animer la couleur ou l'opacité d'un SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="f3155-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="f3155-103">Cet exemple montre comment animer la <xref:System.Windows.Media.SolidColorBrush.Color%2A> et <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="f3155-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3155-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3155-104">Example</span></span>  
 <span data-ttu-id="f3155-105">L’exemple suivant utilise trois animations pour animer les <xref:System.Windows.Media.SolidColorBrush.Color%2A> et <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="f3155-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
-   <span data-ttu-id="f3155-106">La première animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, modifie la couleur du pinceau à <xref:System.Windows.Media.Colors.Gray%2A> lorsque la souris entre dans le rectangle.</span><span class="sxs-lookup"><span data-stu-id="f3155-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
-   <span data-ttu-id="f3155-107">L’animation suivante, une autre <xref:System.Windows.Media.Animation.ColorAnimation>, modifie la couleur du pinceau à <xref:System.Windows.Media.Colors.Orange%2A> lorsque la souris quitte le rectangle.</span><span class="sxs-lookup"><span data-stu-id="f3155-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
-   <span data-ttu-id="f3155-108">La dernière animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, modifie l’opacité du pinceau à 0.0 lorsque le bouton gauche de la souris est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="f3155-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="f3155-109">Pour obtenir un exemple plus complet qui montre comment animer les différents types de pinceaux, consultez le [pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="f3155-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="f3155-110">Pour plus d’informations sur l’animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3155-110">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="f3155-111">Par souci de cohérence avec d’autres exemples d’animation, les versions de code de cet exemple montre comment utilisent un <xref:System.Windows.Media.Animation.Storyboard> objet pour appliquer leurs animations.</span><span class="sxs-lookup"><span data-stu-id="f3155-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="f3155-112">Toutefois, lorsque vous appliquez une animation unique dans le code, il est plus simple d’utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> méthode au lieu d’utiliser un <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="f3155-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="f3155-113">Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="f3155-113">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3155-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3155-114">See Also</span></span>  
 [<span data-ttu-id="f3155-115">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="f3155-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="f3155-116">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="f3155-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="f3155-117">Pinceaux, exemple</span><span class="sxs-lookup"><span data-stu-id="f3155-117">Brushes Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159973)
