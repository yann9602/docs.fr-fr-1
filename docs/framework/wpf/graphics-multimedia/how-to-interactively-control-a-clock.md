---
title: "Comment : contrôler une horloge de façon interactive"
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
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24a5154607bf535cbf995705332092bb86ca02e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="75795-102">Comment : contrôler une horloge de façon interactive</span><span class="sxs-lookup"><span data-stu-id="75795-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="75795-103">A <xref:System.Windows.Media.Animation.Clock> l’objet <xref:System.Windows.Media.Animation.ClockController> propriété permet interactivement Démarrer, suspendre, reprendre, rechercher, avancer l’horloge à sa période de remplissage et arrêter l’horloge.</span><span class="sxs-lookup"><span data-stu-id="75795-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="75795-104">Que l’horloge racine d’arborescence de minutage peut être contrôlée de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="75795-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75795-105">Il existe des autres méthodes de manière interactive les animations de contrôle qui ne nécessitent pas vous permet de travailler directement avec des horloges : vous pouvez également utiliser des plans conceptuels.</span><span class="sxs-lookup"><span data-stu-id="75795-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="75795-106">Storyboards sont pris en charge dans le balisage et le code.</span><span class="sxs-lookup"><span data-stu-id="75795-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="75795-107">Pour obtenir un exemple, consultez [animer une propriété à l’aide d’un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ou [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="75795-107">For an example, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span>  
  
 <span data-ttu-id="75795-108">Dans l’exemple suivant, plusieurs boutons sont utilisés pour contrôler de façon interactive une horloge d’animation.</span><span class="sxs-lookup"><span data-stu-id="75795-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75795-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="75795-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="75795-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75795-110">See Also</span></span>  
 [<span data-ttu-id="75795-111">Animer une propriété à l’aide d’une table de montage séquentiel</span><span class="sxs-lookup"><span data-stu-id="75795-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="75795-112">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="75795-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
