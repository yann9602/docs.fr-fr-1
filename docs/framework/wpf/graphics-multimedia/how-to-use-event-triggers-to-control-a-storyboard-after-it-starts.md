---
title: "Comment : utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80871d9daeec257351134e9f7a72a10b697e842a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="ef302-102">Comment : utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage</span><span class="sxs-lookup"><span data-stu-id="ef302-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="ef302-103">Cet exemple montre comment contrôler une <xref:System.Windows.Media.Animation.Storyboard> après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="ef302-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="ef302-104">Pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez <xref:System.Windows.Media.Animation.BeginStoryboard>, qui distribue les animations aux objets et propriétés animées et démarre ensuite le plan conceptuel.</span><span class="sxs-lookup"><span data-stu-id="ef302-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="ef302-105">Si vous attribuez à <xref:System.Windows.Media.Animation.BeginStoryboard> un nom en spécifiant son <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> propriété, vous rendiez une table de montage séquentiel contrôlable.</span><span class="sxs-lookup"><span data-stu-id="ef302-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="ef302-106">Vous pouvez ensuite contrôler interactivement la table de montage séquentiel après son démarrage.</span><span class="sxs-lookup"><span data-stu-id="ef302-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="ef302-107">Utilisez les actions suivantes de la table de montage séquentiel avec <xref:System.Windows.EventTrigger> objets pour contrôler un storyboard.</span><span class="sxs-lookup"><span data-stu-id="ef302-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="ef302-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Suspend le plan conceptuel.</span><span class="sxs-lookup"><span data-stu-id="ef302-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="ef302-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend un storyboard suspendu.</span><span class="sxs-lookup"><span data-stu-id="ef302-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="ef302-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Modifie la vitesse d’animation.</span><span class="sxs-lookup"><span data-stu-id="ef302-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="ef302-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avance un plan conceptuel à la fin de sa période de remplissage, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ef302-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="ef302-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Arrête l’animation.</span><span class="sxs-lookup"><span data-stu-id="ef302-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="ef302-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime le plan conceptuel, la libération de ressources.</span><span class="sxs-lookup"><span data-stu-id="ef302-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef302-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ef302-114">Example</span></span>  
 <span data-ttu-id="ef302-115">L’exemple suivant utilise des actions de storyboard contrôlable pour contrôler de manière interactive un plan conceptuel.</span><span class="sxs-lookup"><span data-stu-id="ef302-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="ef302-116">**Remarque :** pour voir un exemple de contrôle d’un plan conceptuel à l’aide de code, consultez [contrôler un Storyboard après qu’il démarre à l’aide de ses méthodes interactives](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="ef302-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="ef302-117">Pour obtenir des exemples supplémentaires, consultez le [Galerie d’exemples d’Animation](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="ef302-117">For additional examples, see the [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef302-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef302-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="ef302-119">Contrôler un storyboard après son démarrage à l'aide de ses méthodes interactives</span><span class="sxs-lookup"><span data-stu-id="ef302-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="ef302-120">Vue d’ensemble de l’animation</span><span class="sxs-lookup"><span data-stu-id="ef302-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ef302-121">Vue d'ensemble des plans conceptuels</span><span class="sxs-lookup"><span data-stu-id="ef302-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
