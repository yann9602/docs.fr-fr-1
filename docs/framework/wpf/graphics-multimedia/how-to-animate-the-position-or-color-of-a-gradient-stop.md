---
title: "Comment : animer la position ou la couleur d'un point de dégradé"
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
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968d285d8a3345da9810f0ba4797bf8b2e33d36e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="e1c05-102">Comment : animer la position ou la couleur d'un point de dégradé</span><span class="sxs-lookup"><span data-stu-id="e1c05-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="e1c05-103">Cet exemple montre comment animer la <xref:System.Windows.Media.GradientStop.Color%2A> et <xref:System.Windows.Media.GradientStop.Offset%2A> de <xref:System.Windows.Media.GradientStop> objets.</span><span class="sxs-lookup"><span data-stu-id="e1c05-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1c05-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1c05-104">Example</span></span>  
 <span data-ttu-id="e1c05-105">L’exemple suivant anime trois points de dégradé dans un <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="e1c05-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="e1c05-106">L’exemple utilise trois animations, chacune d’elles réalise une animation d’un point de dégradé différent :</span><span class="sxs-lookup"><span data-stu-id="e1c05-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="e1c05-107">La première animation, un <xref:System.Windows.Media.Animation.DoubleAnimation>, anime le premier point de dégradé <xref:System.Windows.Media.GradientStop.Offset%2A> de 0.0 à 1.0, puis revient à 0.0.</span><span class="sxs-lookup"><span data-stu-id="e1c05-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="e1c05-108">Par conséquent, la première couleur du dégradé se décale à partir de la gauche vers le côté droit du rectangle et puis de nouveau sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="e1c05-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="e1c05-109">La deuxième animation, un <xref:System.Windows.Media.Animation.ColorAnimation>, anime le deuxième point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> de <xref:System.Windows.Media.Colors.Purple%2A> à <xref:System.Windows.Media.Colors.Yellow%2A> , puis revient à <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1c05-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="e1c05-110">Par conséquent, la couleur intermédiaire du dégradé passe de violet en jaune et en violet.</span><span class="sxs-lookup"><span data-stu-id="e1c05-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="e1c05-111">La troisième animation, un autre <xref:System.Windows.Media.Animation.ColorAnimation>, anime l’opacité de la troisième point de dégradé <xref:System.Windows.Media.GradientStop.Color%2A> par -1, puis à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e1c05-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="e1c05-112">Par conséquent, la troisième couleur dans le dégradé disparaît et devient alors opaque à nouveau.</span><span class="sxs-lookup"><span data-stu-id="e1c05-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="e1c05-113">Bien que cet exemple utilise un <xref:System.Windows.Media.LinearGradientBrush>, le processus est le même pour animer <xref:System.Windows.Media.GradientStop> d’objets contenus dans un <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="e1c05-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="e1c05-114">Pour obtenir des exemples supplémentaires, consultez le [pinceaux, exemple](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="e1c05-114">For additional examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c05-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c05-115">See Also</span></span>  
 <xref:System.Windows.Media.GradientStop>  
 [<span data-ttu-id="e1c05-116">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="e1c05-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e1c05-117">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="e1c05-117">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
