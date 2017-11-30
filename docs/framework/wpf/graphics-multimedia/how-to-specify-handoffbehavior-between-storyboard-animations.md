---
title: "Comment : spécifier HandoffBehavior entre des animations de storyboard"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 323ea563aec7bc7ad0abec2372e3af977c7e38eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="ba2c6-102">Comment : spécifier HandoffBehavior entre des animations de storyboard</span><span class="sxs-lookup"><span data-stu-id="ba2c6-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="ba2c6-103">Cet exemple montre comment spécifier le comportement de transfert entre des animations storyboard.</span><span class="sxs-lookup"><span data-stu-id="ba2c6-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="ba2c6-104">Le <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> propriété du <xref:System.Windows.Media.Animation.BeginStoryboard> spécifie comment les nouvelles animations interagissent avec les animations existantes qui sont déjà appliquées à une propriété.</span><span class="sxs-lookup"><span data-stu-id="ba2c6-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba2c6-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba2c6-105">Example</span></span>  
 <span data-ttu-id="ba2c6-106">L’exemple suivant crée deux boutons qui agrandissent lorsque le curseur de la souris se déplace au-dessus d’eux et diminuent lorsque le curseur se déplace.</span><span class="sxs-lookup"><span data-stu-id="ba2c6-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="ba2c6-107">Si vous placez la souris sur un bouton, puis supprimez rapidement le curseur, la deuxième animation est appliquée avant que la première est terminée.</span><span class="sxs-lookup"><span data-stu-id="ba2c6-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="ba2c6-108">C’est lorsque deux animations se chevauchent ainsi que vous pouvez voir la différence entre la <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> les valeurs de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> et <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="ba2c6-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="ba2c6-109">La valeur <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combine les animations qui se chevauche, ce qui provoque une transition plus lisse entre les animations alors que la valeur <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> provoque la nouvelle animation remplacement immédiat de l’animation qui se chevauchent plus haut.</span><span class="sxs-lookup"><span data-stu-id="ba2c6-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ba2c6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba2c6-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="ba2c6-111">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="ba2c6-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ba2c6-112">Animation et minutage</span><span class="sxs-lookup"><span data-stu-id="ba2c6-112">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="ba2c6-113">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="ba2c6-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
