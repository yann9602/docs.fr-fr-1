---
title: "Comment : spécifier le FillBehavior pour une chronologie ayant atteint la fin de sa période active"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2c1d65ec9fad94fed02bee1f018ae1aa00a8591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="2f1e4-102">Comment : spécifier le FillBehavior pour une chronologie ayant atteint la fin de sa période active</span><span class="sxs-lookup"><span data-stu-id="2f1e4-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="2f1e4-103">Cet exemple montre comment spécifier le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pour inactifs <xref:System.Windows.Media.Animation.Timeline> d’une propriété animée.</span><span class="sxs-lookup"><span data-stu-id="2f1e4-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f1e4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f1e4-104">Example</span></span>  
 <span data-ttu-id="2f1e4-105">Le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété d’un <xref:System.Windows.Media.Animation.Timeline> détermine ce qui se passe à la valeur d’une propriété animée lorsqu’il n’est pas en cours d’animation, autrement dit, lorsque la <xref:System.Windows.Media.Animation.Timeline> est inactif, mais son parent <xref:System.Windows.Media.Animation.Timeline> est active ou d’une période d’attente.</span><span class="sxs-lookup"><span data-stu-id="2f1e4-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="2f1e4-106">Par exemple, une propriété animée reste à sa fin valeur une fois l’animation se termine ou qu’il le fait revenir à la valeur qu’elle avait avant le démarrage de l’animation ?</span><span class="sxs-lookup"><span data-stu-id="2f1e4-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="2f1e4-107">L’exemple suivant utilise un <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer la <xref:System.Windows.FrameworkElement.Width%2A> de deux rectangles.</span><span class="sxs-lookup"><span data-stu-id="2f1e4-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="2f1e4-108">Chaque rectangle utilise un autre <xref:System.Windows.Media.Animation.Timeline> objet.</span><span class="sxs-lookup"><span data-stu-id="2f1e4-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="2f1e4-109">Un <xref:System.Windows.Media.Animation.Timeline> a un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> qui a la valeur <xref:System.Windows.Media.Animation.FillBehavior.Stop>, ce qui entraîne la largeur du rectangle à revenir à son non animée valeur lorsque le <xref:System.Windows.Media.Animation.Timeline> se termine.</span><span class="sxs-lookup"><span data-stu-id="2f1e4-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="2f1e4-110">L’autre <xref:System.Windows.Media.Animation.Timeline> a un <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> de <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, ce qui entraîne la largeur reste à sa fin valeur lorsque le <xref:System.Windows.Media.Animation.Timeline> se termine.</span><span class="sxs-lookup"><span data-stu-id="2f1e4-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="2f1e4-111">Pour obtenir un exemple complet, consultez [Galerie d’exemples d’Animation](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="2f1e4-111">For the complete sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1e4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f1e4-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [<span data-ttu-id="2f1e4-113">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="2f1e4-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="2f1e4-114">Animation et minutage</span><span class="sxs-lookup"><span data-stu-id="2f1e4-114">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="2f1e4-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="2f1e4-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
