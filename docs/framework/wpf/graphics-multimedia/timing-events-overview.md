---
title: "Vue d'ensemble des événements de minutage"
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
- timelines [WPF]
- timing events [WPF]
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f50923d9e314d2f677e26416cef59fdf380213e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="timing-events-overview"></a>Vue d'ensemble des événements de minutage
Cette rubrique décrit comment utiliser les cinq événements de minutage disponibles sur <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> objets.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez être en mesure de créer et d’utiliser des animations. Pour commencer l’animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Il existe plusieurs façons pour animer des propriétés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **À l’aide d’objets de table de montage séquentiel** (balisage et code) : vous pouvez utiliser <xref:System.Windows.Media.Animation.Storyboard> objets pour réorganiser et distribuer des animations à un ou plusieurs objets. Pour obtenir un exemple, consultez [animer une propriété à l’aide d’un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Utilisation d’animations locales** (code uniquement) : vous pouvez appliquer <xref:System.Windows.Media.Animation.AnimationTimeline> objets directement aux propriétés qu’ils animent. Si vous voulez voir un exemple, consultez l’article [Comment : animer une propriété sans utiliser de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **En utilisant des horloges** (code uniquement) : vous pouvez gérer la création d’horloge explicitement et distribuer vous-même les horloges d’animation.  Pour obtenir un exemple, consultez [animer une propriété à l’aide d’un AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Étant donné que vous pouvez les utiliser dans le balisage et le code, les exemples de cette vue d’ensemble utilisent <xref:System.Windows.Media.Animation.Storyboard> objets. Toutefois, les concepts décrits sont applicables aux autres méthodes d’animation des propriétés.  
  
### <a name="what-is-a-clock"></a>Qu’est-ce qu’une horloge ?  
 Une chronologie, par elle-même, ne fait rien d’autre que décrire un segment de temps. Il s’agit de la chronologie <xref:System.Windows.Media.Animation.Clock> objet qui effectue le travail réel : il conserve l’état d’exécution temporisation de la chronologie. Dans la plupart des cas, par exemple quand vous utilisez des tables de montage séquentiel, une horloge est créée automatiquement pour votre chronologie. Vous pouvez également créer un <xref:System.Windows.Media.Animation.Clock> explicitement en utilisant la <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> (méthode). Pour plus d’informations sur <xref:System.Windows.Media.Animation.Clock> , consultez la [Animation et vue d’ensemble du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Pourquoi utiliser des événements ?  
 À une exception près (seekAlignedToLastTick), toutes les opérations de minutage interactives sont asynchrones. Il n’existe aucun moyen de savoir exactement quand elles s’exécutent. Ceci peut être un problème lorsque vous avez d’autres codes qui dépendent de l’opération de minutage. Supposons que vous souhaitiez arrêter une chronologie qui animait un rectangle. Après l’arrêt de la chronologie, vous modifiez la couleur du rectangle.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 Dans l’exemple précédent, la deuxième ligne de code peut s’exécuter avant l’arrêt de la table de montage séquentiel. Cela est dû au fait que l’arrêt est une opération asynchrone. Si vous demandez à une chronologie ou à une horloge de s’arrêter, elle crée une « demande d’arrêt » qui n’est pas traitée avant le prochain battement du moteur de minutage.  
  
 Pour exécuter des commandes après la fin d’une chronologie, utilisez les événements de minutage. Dans l’exemple suivant, un gestionnaire d’événements est utilisé pour modifier la couleur d’un rectangle, après l’arrêt de la table de montage séquentiel.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Pour obtenir un exemple plus complet, consultez [changements d’état de réception Notification quand une horloge](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Événements publics  
 Le <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> les classes fournissent les cinq événements de minutage. Le tableau suivant répertorie ces événements et les conditions qui les déclenchent.  
  
|Événement|Opération interactive déclenchante|Autres déclencheurs|  
|-----------|--------------------------------------|--------------------|  
|**Completed**|Passer au remplissage|L’horloge s’arrête.|  
|**CurrentGlobalSpeedInvalidated**|Suspendre, reprendre, rechercher, définir le ratio vitesse, passer au remplissage, s’arrêter|L’horloge s’inverse, accélère, démarre ou s’arrête.|  
|**CurrentStateInvalidated**|Démarrer, passer au remplissage, s’arrêter|L’horloge démarre, s’arrête ou remplit.|  
|**CurrentTimeInvalidated**|Démarrer, rechercher, passer au remplissage, s’arrêter|L’horloge progresse.|  
|**RemoveRequested**|Remove||  
  
## <a name="ticking-and-event-consolidation"></a>Cycles et regroupement des événements  
 Lorsque vous animez des objets dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], c’est le moteur de synchronisation qui gère vos animations. Le moteur de minutage suit l’écoulement du temps et calcule l’état de chaque animation. Il effectue plusieurs calculs de ce type en une seconde. Ces calculs sont appelés « cycles ».  
  
 Étant donné que ces cycles sont fréquents, beaucoup de choses peuvent se passer entre chaque cycle. Par exemple, une chronologie peut s’arrêter, démarrer et s’arrêter à nouveau. Dans ce cas, son état actuel aura changé trois fois. En théorie, l’événement peut être déclenché plusieurs fois dans un seul cycle. Toutefois, le moteur de minutage regroupe les événements, afin que chacun ne puisse être déclenché qu’une fois par cycle.  
  
## <a name="registering-for-events"></a>Inscription pour des événements  
 Il existe deux façons d’inscrire des événements de minutage : vous pouvez les inscrire avec la chronologie ou avec l’horloge créée à partir de la chronologie. Il est assez simple d’inscrire un événement directement avec une horloge, mais il n’est possible de le faire qu’à partir du code. Vous pouvez inscrire des événements avec une chronologie, à partir d’une balise ou du code. La section suivante décrit comment inscrire les événements d’horloge avec une chronologie.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>Inscription des événements d’horloge avec une chronologie  
 Bien que d’une chronologie <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, et <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> événements s’affichent à associer à la chronologie, l’inscription pour ces événements associe réellement un gestionnaire d’événements avec le <xref:System.Windows.Media.Animation.Clock> créé pour la chronologie.  
  
 Lorsque vous inscrivez pour le <xref:System.Windows.Media.Animation.Timeline.Completed> événement sur une chronologie, par exemple, vous indiquez en fait le système pour vous inscrire à le <xref:System.Windows.Media.Animation.Clock.Completed> l’événement de chaque horloge créée pour la chronologie. Dans le code, vous devez vous inscrire à cet événement avant que le <xref:System.Windows.Media.Animation.Clock> est créé pour cette chronologie ; sinon, vous ne recevrez aucune notification. Cela se produit automatiquement dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; l’analyseur s’inscrit automatiquement pour l’événement avant le <xref:System.Windows.Media.Animation.Clock> est créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d’ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
