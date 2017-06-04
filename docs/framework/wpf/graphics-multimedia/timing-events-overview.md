---
title: "Vue d&#39;ensemble des &#233;v&#233;nements de minutage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Clock (classe)"
  - "classes, l’horloge"
  - "chronologies"
  - "événements de minutage"
ms.assetid: 597e3280-0867-4359-a97b-5b2f4149e350
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Vue d&#39;ensemble des &#233;v&#233;nements de minutage
Cette rubrique explique comment utiliser les cinq événements de minutage disponibles sur <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> objets.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez comprendre comment créer et utiliser des animations. Pour commencer avec une animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Il existe plusieurs méthodes pour animer des propriétés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
-   **À l’aide d’objets de table de montage séquentiel** (balise et code) : vous pouvez utiliser <xref:System.Windows.Media.Animation.Storyboard> objets pour réorganiser et distribuer des animations à un ou plusieurs objets. Pour obtenir un exemple, consultez [animer une propriété à l’aide d’un Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
-   **Utilisation d’animations locales** (code uniquement) : vous pouvez appliquer <xref:System.Windows.Media.Animation.AnimationTimeline> objets directement aux propriétés qu’ils animent. Pour obtenir un exemple, consultez [animer une propriété sans utiliser de Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
-   **Utilisation d’horloges** (code uniquement) : permet de gérer la création d’horloge explicitement et distribuer vous-même les horloges d’animation.  Pour obtenir un exemple, consultez [animer une propriété à l’aide d’un AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).  
  
 Étant donné que vous pouvez les utiliser dans le balisage et le code, les exemples de cette vue d’ensemble utilisent <xref:System.Windows.Media.Animation.Storyboard> objets. Toutefois, les concepts décrits sont applicables aux autres méthodes d’animation des propriétés.  
  
### <a name="what-is-a-clock"></a>Quel est l’horloge ?  
 Une chronologie, par elle-même, ne fait rien de décrire un segment de temps. Il s’agit de la chronologie <xref:System.Windows.Media.Animation.Clock> objet qui fait le vrai travail : il maintient l’état d’exécution de temporisation de la chronologie. Dans la plupart des cas, par exemple quand à l’aide de tables de montage séquentiel, une horloge est créée automatiquement pour votre scénario. Vous pouvez également créer un <xref:System.Windows.Media.Animation.Clock> explicitement en utilisant la <xref:System.Windows.Media.Animation.Timeline.CreateClock%2A> (méthode). Pour plus d’informations sur <xref:System.Windows.Media.Animation.Clock> , voir la [Animation and Timing System Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="why-use-events"></a>Pourquoi utiliser des événements ?  
 À une exception près (appel aligné sur le dernier battement), toutes les opérations d’horloge interactives sont asynchrones. Il n’existe aucun moyen de savoir exactement quand elles s’exécutent. Qui peut être un problème lorsque vous disposez de tout autre code qui dépend de l’opération d’horloge. Supposons que vous souhaitiez arrêter une chronologie qui animait un rectangle. Après l’arrêt de la chronologie, vous modifiez la couleur du rectangle.  
  
 [!code-csharp[events_procedural#NeedForEventsFragment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#needforeventsfragment)]
 [!code-vb[events_procedural#NeedForEventsFragment](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#needforeventsfragment)]  
  
 Dans l’exemple précédent, la deuxième ligne de code peut s’exécuter avant l’arrêt de la table de montage séquentiel. C’est parce que l’arrêt est une opération asynchrone. Indique une chronologie ou une horloge à arrêter crée une « demande d’arrêt » de tri qui n’est pas traitée avant le prochain battement du moteur de minutage.  
  
 Pour exécuter des commandes à l’issue de l’exécution d’une chronologie, utilisez les événements de minutage. Dans l’exemple suivant, un gestionnaire d’événements est utilisé pour modifier la couleur d’un rectangle, une fois la table de montage séquentiel s’arrête.  
  
 [!code-csharp[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#registerforstoryboardcurrentstateinvalidatedevent)]
 [!code-vb[events_procedural#RegisterForStoryboardCurrentStateInvalidatedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#registerforstoryboardcurrentstateinvalidatedevent)]  
[!code-csharp[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/events_procedural/CSharp/EventExample.cs#storyboardcurrentstateinvalidatedevent2)]
[!code-vb[events_procedural#StoryboardCurrentStateInvalidatedEvent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/events_procedural/VisualBasic/EventExample.vb#storyboardcurrentstateinvalidatedevent2)]  
  
 Pour obtenir un exemple plus complet, consultez la page [changements d’état de réception Notification lorsqu’un l’horloge](../../../../docs/framework/wpf/graphics-multimedia/how-to-receive-notification-when-clock-state-changes.md).  
  
## <a name="public-events"></a>Événements publics  
 Le <xref:System.Windows.Media.Animation.Timeline> et <xref:System.Windows.Media.Animation.Clock> classes fournissent les cinq événements de minutage. Le tableau suivant répertorie ces événements et les conditions qui les déclenchent.  
  
|Événement|Opération interactive de déclenchement|Autres déclencheurs|  
|-----------|--------------------------------------|--------------------|  
|**Terminé**|Ignorer pour remplir|L’horloge se termine.|  
|**CurrentGlobalSpeedInvalidated**|Suspendre, reprendre, rechercher, définir ratio vitesse, ignorer pour remplir, arrêter|L’horloge inverse, accélère, démarre ou s’arrête.|  
|**CurrentStateInvalidated**|Démarrer, ignorer pour remplir, arrêter|L’horloge démarre, s’arrête ou remplit.|  
|**CurrentTimeInvalidated**|Démarrer, appeler, ignorer pour remplir, arrêter|L’horloge progresse.|  
|**RemoveRequested**|Remove||  
  
## <a name="ticking-and-event-consolidation"></a>Égrener les secondes et la consolidation des événements  
 Lorsque vous animez des objets dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], c’est le moteur de minutage qui gère vos animations. Le moteur de minutage suit la progression du temps et calcule l’état de chaque animation. Il passe nombreux ce type d’évaluation en une seconde. Ces passes d’évaluation sont appelées « cycles ».  
  
 Alors que les battements se produisent fréquemment, il est possible que beaucoup de choses se passent entre les graduations. Par exemple, une chronologie peut être arrêtée, démarrée et arrêtée, auquel cas son état actuel sera modifié trois fois. En théorie, l’événement peut être déclenché plusieurs fois dans un seul battement ; Toutefois, le moteur de minutage consolide les événements, afin que chaque événement peut être déclenché au plus une fois par cycle.  
  
## <a name="registering-for-events"></a>L’inscription aux événements  
 Il existe deux façons de s’inscrire aux événements de minutage : vous pouvez enregistrer la chronologie ou avec l’horloge créée à partir de la chronologie. S’inscrire pour un événement directement avec une horloge est assez simple, bien qu’il n’est possible à partir du code. Vous pouvez enregistrer des événements avec une chronologie de balise ou du code. La section suivante décrit comment s’inscrire aux événements de minutage avec une chronologie.  
  
<a name="registeringforclockeventswithatimeline"></a>   
## <a name="registering-for-clock-events-with-a-timeline"></a>L’inscription aux événements d’horloge avec une chronologie  
 Bien que d’une chronologie <xref:System.Windows.Media.Animation.Timeline.Completed>, <xref:System.Windows.Media.Animation.Timeline.CurrentGlobalSpeedInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated>, <xref:System.Windows.Media.Animation.Timeline.CurrentTimeInvalidated>, et <xref:System.Windows.Media.Animation.Timeline.RemoveRequested> événements semblent être associé à la chronologie, l’inscription pour ces événements associe réellement un gestionnaire d’événements avec le <xref:System.Windows.Media.Animation.Clock> créé pour la chronologie.  
  
 Lorsque vous inscrivez pour le <xref:System.Windows.Media.Animation.Timeline.Completed> événement sur une chronologie, par exemple, vous indiquez en fait le système pour s’inscrire à la <xref:System.Windows.Media.Animation.Clock.Completed> événements de chaque horloge créée pour la chronologie. Dans le code, vous devez vous inscrire à cet événement avant que le <xref:System.Windows.Media.Animation.Clock> est créé pour cette chronologie ; sinon, vous ne recevrez aucune notification. Cela se produit automatiquement dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; l’analyseur s’inscrit automatiquement pour l’événement avant le <xref:System.Windows.Media.Animation.Clock> est créé.  
  
## <a name="see-also"></a>Voir aussi  
 [Animation et le minutage de vue d’ensemble du système](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [Présentation de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d’ensemble des comportements de minutage](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)