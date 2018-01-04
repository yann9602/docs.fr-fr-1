---
title: "Comment : définir une durée pour une animation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e8d15a1b8432b3dae5bee73396bdec9fc9d50f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="458b3-102">Comment : définir une durée pour une animation</span><span class="sxs-lookup"><span data-stu-id="458b3-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="458b3-103">A <xref:System.Windows.Media.Animation.Timeline> représente un segment de temps et de la longueur de ce segment sont déterminées par la chronologie <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="458b3-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="458b3-104">Lorsqu’un <xref:System.Windows.Media.Animation.Timeline> atteint la fin de sa durée, il s’arrête.</span><span class="sxs-lookup"><span data-stu-id="458b3-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="458b3-105">Si le <xref:System.Windows.Media.Animation.Timeline> a des chronologies enfants, ils cessent de jouer également.</span><span class="sxs-lookup"><span data-stu-id="458b3-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="458b3-106">Dans le cas d’une animation, la <xref:System.Windows.Duration> spécifie la durée nécessaire à l’animation transition à partir de sa valeur initiale à sa valeur de fin.</span><span class="sxs-lookup"><span data-stu-id="458b3-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="458b3-107">Vous pouvez spécifier un <xref:System.Windows.Duration> avec une durée finie spécifique ou les valeurs spéciales <xref:System.Windows.Duration.Automatic%2A> ou <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="458b3-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="458b3-108">Durée d’une animation doit toujours être une valeur d’heure, car une animation doit toujours avoir une longueur finie spécifique, dans le cas contraire, l’animation ne serait pas capable d’effectuer la transition entre ses valeurs cibles.</span><span class="sxs-lookup"><span data-stu-id="458b3-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="458b3-109">Les chronologies de conteneur (<xref:System.Windows.Media.Animation.TimelineGroup> objets), tel que <xref:System.Windows.Media.Animation.Storyboard> et <xref:System.Windows.Media.Animation.ParallelTimeline>, ont une durée par défaut de <xref:System.Windows.Duration.Automatic%2A>, ce qui signifie qu’elles se terminent automatiquement lorsque leur dernier enfant s’arrête.</span><span class="sxs-lookup"><span data-stu-id="458b3-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="458b3-110">Dans la couleur d’exemple, la largeur, la hauteur et remplissage suivante d’un <xref:System.Windows.Shapes.Rectangle> est animée.</span><span class="sxs-lookup"><span data-stu-id="458b3-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="458b3-111">Les durées sont définies sur des chronologies d’animation et de conteneur entraîne des effets d’animation, y compris le contrôle de la vitesse perçue d’une animation et la substitution de la durée des chronologies enfants avec la durée d’une chronologie de conteneur.</span><span class="sxs-lookup"><span data-stu-id="458b3-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="458b3-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="458b3-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="458b3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="458b3-113">See Also</span></span>  
 <xref:System.Windows.Duration>  
 [<span data-ttu-id="458b3-114">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="458b3-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
