---
title: "Comment : simplifier des animations à l'aide de chronologies enfants"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d3b8f1ca1dbf7ba5452acffc62fdf0b655c9c12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a><span data-ttu-id="51d56-102">Comment : simplifier des animations à l'aide de chronologies enfants</span><span class="sxs-lookup"><span data-stu-id="51d56-102">How to: Simplify Animations by Using Child Timelines</span></span>
<span data-ttu-id="51d56-103">Cet exemple montre comment simplifier des animations à l’aide des enfants <xref:System.Windows.Media.Animation.ParallelTimeline> objets.</span><span class="sxs-lookup"><span data-stu-id="51d56-103">This example shows how to simplify animations by using child <xref:System.Windows.Media.Animation.ParallelTimeline> objects.</span></span> <span data-ttu-id="51d56-104">A <xref:System.Windows.Media.Animation.Storyboard> est un type de <xref:System.Windows.Media.Animation.Timeline> qui fournit des informations de ciblage pour les chronologies qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="51d56-104">A <xref:System.Windows.Media.Animation.Storyboard> is a type of <xref:System.Windows.Media.Animation.Timeline> that provides targeting information for the timelines it contains.</span></span> <span data-ttu-id="51d56-105">Utilisez un <xref:System.Windows.Media.Animation.Storyboard> pour fournir des informations, y compris les informations d’objet et la propriété de ciblage de chronologie.</span><span class="sxs-lookup"><span data-stu-id="51d56-105">Use a <xref:System.Windows.Media.Animation.Storyboard> to provide timeline targeting information, including object and property information.</span></span>  
  
 <span data-ttu-id="51d56-106">Pour commencer une animation, utilisez une ou plusieurs <xref:System.Windows.Media.Animation.ParallelTimeline> objets en tant qu’éléments enfants imbriqués d’un <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="51d56-106">To begin an animation, use one or more <xref:System.Windows.Media.Animation.ParallelTimeline> objects as nested child elements of a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="51d56-107">Ces <xref:System.Windows.Media.Animation.ParallelTimeline> objets peuvent contenir d’autres animations et par conséquent, mieux encapsuler les séquences temporelles dans des animations complexes.</span><span class="sxs-lookup"><span data-stu-id="51d56-107">These <xref:System.Windows.Media.Animation.ParallelTimeline> objects can contain other animations and therefore, can better encapsulate the timing sequences in complex animations.</span></span> <span data-ttu-id="51d56-108">Par exemple, si vous animez un <xref:System.Windows.Controls.TextBlock> et plusieurs formes dans le même <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez séparer les animations de la <xref:System.Windows.Controls.TextBlock> et les formes, en les mettant chacune dans un distinct <xref:System.Windows.Media.Animation.ParallelTimeline>.</span><span class="sxs-lookup"><span data-stu-id="51d56-108">For example, if you are animating a <xref:System.Windows.Controls.TextBlock> and several shapes in the same <xref:System.Windows.Media.Animation.Storyboard>, you can separate the animations for the <xref:System.Windows.Controls.TextBlock> and the shapes, putting each into a separate <xref:System.Windows.Media.Animation.ParallelTimeline>.</span></span> <span data-ttu-id="51d56-109">Étant donné que chaque <xref:System.Windows.Media.Animation.ParallelTimeline> possède son propre <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> et tous les éléments enfants de la <xref:System.Windows.Media.Animation.ParallelTimeline> commencer par rapport à cette <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, minutage est mieux encapsulé.</span><span class="sxs-lookup"><span data-stu-id="51d56-109">Because each <xref:System.Windows.Media.Animation.ParallelTimeline> has its own <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> and all child elements of the <xref:System.Windows.Media.Animation.ParallelTimeline> begin relative to this <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, timing is better encapsulated.</span></span>  
  
 <span data-ttu-id="51d56-110">L’exemple suivant anime deux parties de texte (<xref:System.Windows.Controls.TextBlock> objets) à partir d’au sein du même <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="51d56-110">The following example animates two pieces of text (<xref:System.Windows.Controls.TextBlock> objects) from within the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="51d56-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsule les animations de l’un de le <xref:System.Windows.Controls.TextBlock> objets.</span><span class="sxs-lookup"><span data-stu-id="51d56-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsulates the animations of one of the <xref:System.Windows.Controls.TextBlock> objects.</span></span>  
  
 <span data-ttu-id="51d56-112">**Remarque de performances :** bien que vous pouvez imbriquer des <xref:System.Windows.Media.Animation.Storyboard> chronologies à l’intérieur de l’autre, <xref:System.Windows.Media.Animation.ParallelTimeline>s sont plus adaptés à l’imbrication, car elles nécessitent moins de surcharge.</span><span class="sxs-lookup"><span data-stu-id="51d56-112">**Performance Note:** Although you can nest <xref:System.Windows.Media.Animation.Storyboard> timelines inside each other, <xref:System.Windows.Media.Animation.ParallelTimeline>s are more suitable for nesting because they require less overhead.</span></span> <span data-ttu-id="51d56-113">(Le <xref:System.Windows.Media.Animation.Storyboard> classe hérite de la <xref:System.Windows.Media.Animation.ParallelTimeline> classe.)</span><span class="sxs-lookup"><span data-stu-id="51d56-113">(The <xref:System.Windows.Media.Animation.Storyboard> class inherits from the <xref:System.Windows.Media.Animation.ParallelTimeline> class.)</span></span>  
  
## <a name="example"></a><span data-ttu-id="51d56-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="51d56-114">Example</span></span>  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="51d56-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51d56-115">See Also</span></span>  
 [<span data-ttu-id="51d56-116">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="51d56-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="51d56-117">Spécifier HandoffBehavior entre des animations de storyboard</span><span class="sxs-lookup"><span data-stu-id="51d56-117">Specify HandoffBehavior Between Storyboard Animations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
