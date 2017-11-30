---
title: "Comment : contrôler un storyboard après son démarrage"
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
helpviewer_keywords: Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b28cdf3b653925a5856c0bc9def5aebb9fdc6c14
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="d6588-102">Comment : contrôler un storyboard après son démarrage</span><span class="sxs-lookup"><span data-stu-id="d6588-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="d6588-103">Cet exemple montre comment utiliser le code pour contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="d6588-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="d6588-104">Pour contrôler un storyboard dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez <xref:System.Windows.Trigger> et <xref:System.Windows.TriggerAction> objets ; pour obtenir un exemple, consultez [utiliser les déclencheurs d’événements pour contrôler un Storyboard après démarrage](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="d6588-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="d6588-105">Pour démarrer une animation, vous utilisez ses <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> (méthode), qui distribue les animations de la table de montage séquentiel aux propriétés animées et démarre l’animation.</span><span class="sxs-lookup"><span data-stu-id="d6588-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="d6588-106">Pour rendre une table de montage séquentiel contrôlable, vous utilisez la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> (méthode) et spécifiez **true** comme second paramètre.</span><span class="sxs-lookup"><span data-stu-id="d6588-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="d6588-107">Vous pouvez ensuite utiliser les méthodes interactives de la table de montage séquentiel pour suspendre, reprendre, recherche, arrêter, accélérer ou ralentir l’animation ou avancer à sa période de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d6588-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="d6588-108">Voici une liste des méthodes interactives de la table de montage séquentiel :</span><span class="sxs-lookup"><span data-stu-id="d6588-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <span data-ttu-id="d6588-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Suspend le plan conceptuel.</span><span class="sxs-lookup"><span data-stu-id="d6588-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="d6588-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Reprend un storyboard suspendu.</span><span class="sxs-lookup"><span data-stu-id="d6588-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="d6588-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Définit la vitesse interactive de la table de montage séquentiel.</span><span class="sxs-lookup"><span data-stu-id="d6588-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
-   <span data-ttu-id="d6588-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Recherche la table de montage séquentiel l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6588-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
-   <span data-ttu-id="d6588-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Recherche la table de montage séquentiel à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="d6588-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="d6588-114">Contrairement à la <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> (méthode), cette opération est traitée avant le battement suivant.</span><span class="sxs-lookup"><span data-stu-id="d6588-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <span data-ttu-id="d6588-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Avance le plan conceptuel à sa période de remplissage, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d6588-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="d6588-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Arrête l’animation.</span><span class="sxs-lookup"><span data-stu-id="d6588-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="d6588-117">Dans l’exemple suivant, plusieurs méthodes de plan conceptuel sont utilisés pour contrôler de manière interactive un plan conceptuel.</span><span class="sxs-lookup"><span data-stu-id="d6588-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="d6588-118">**Remarque :** pour voir un exemple de contrôle d’un plan conceptuel à l’aide de déclencheurs avec [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [utiliser les déclencheurs d’événements pour contrôler un Storyboard après démarrage](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="d6588-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6588-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="d6588-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d6588-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6588-120">See Also</span></span>  
 [<span data-ttu-id="d6588-121">Utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage</span><span class="sxs-lookup"><span data-stu-id="d6588-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
