---
title: "Comment : ajouter la gestion de classe d'un événement routé"
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
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f0315bbd1d1a5ab2ae08d8bc1810e240cb6a5a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="50d54-102">Comment : ajouter la gestion de classe d'un événement routé</span><span class="sxs-lookup"><span data-stu-id="50d54-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="50d54-103">Les événements routés peuvent être gérés par les gestionnaires de classe ou les gestionnaires d’instance sur un nœud donné de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="50d54-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="50d54-104">Gestionnaires de classe sont appelés tout d’abord et peuvent être utilisés par les implémentations de classe pour supprimer des événements à partir de la gestion de l’instance ou d’introduire d’autres comportements spécifiques des événements sur les événements qui sont détenus par les classes de base.</span><span class="sxs-lookup"><span data-stu-id="50d54-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="50d54-105">Cet exemple illustre deux techniques étroitement liées pour l’implémentation des gestionnaires de classe.</span><span class="sxs-lookup"><span data-stu-id="50d54-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d54-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="50d54-106">Example</span></span>  
 <span data-ttu-id="50d54-107">Cet exemple utilise une classe personnalisée basée sur le <xref:System.Windows.Controls.Canvas> Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="50d54-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="50d54-108">Le principe de base de l’application est que la classe personnalisée introduit des comportements sur ses éléments enfants, y compris l’interception des que clics de n’importe quel bouton gauche de la souris et leur marquage comme gérés, avant de la classe d’élément enfant ou d’instances sur ce dernier sera appelé.</span><span class="sxs-lookup"><span data-stu-id="50d54-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="50d54-109">Le <xref:System.Windows.UIElement> classe expose une méthode virtuelle qui permet la gestion de classe sur le <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> événement, en substituant simplement l’événement.</span><span class="sxs-lookup"><span data-stu-id="50d54-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="50d54-110">Il s’agit de la façon la plus simple pour implémenter la gestion de classe si cette méthode virtuelle est disponible quelque part dans la hiérarchie de votre classe.</span><span class="sxs-lookup"><span data-stu-id="50d54-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="50d54-111">Le code suivant illustre la <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> mise en œuvre dans le « MyEditContainer » qui est dérivé de <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="50d54-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="50d54-112">L’implémentation marque l’événement comme géré dans les arguments, puis ajoute du code pour permettre à l’élément source à une modification visible de base.</span><span class="sxs-lookup"><span data-stu-id="50d54-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="50d54-113">Si aucun élément virtuel n’est disponible sur les classes de base ou pour cette méthode particulière, la gestion de classe peut être ajoutée directement à l’aide d’une méthode utilitaire de la <xref:System.Windows.EventManager> (classe), <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="50d54-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="50d54-114">Cette méthode doit uniquement être appelée au sein de l’initialisation statique des classes qui ajoutent la gestion de classe.</span><span class="sxs-lookup"><span data-stu-id="50d54-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="50d54-115">Cet exemple ajoute un autre gestionnaire pour <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , et dans ce cas la classe inscrite correspond à la classe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="50d54-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="50d54-116">En revanche, lorsque vous utilisez les méthodes virtuelles, la classe inscrite correspond réellement le <xref:System.Windows.UIElement> classe de base.</span><span class="sxs-lookup"><span data-stu-id="50d54-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="50d54-117">Dans les cas où des classes de base et les sous-classes inscrivent la gestion de classe, les gestionnaires de sous-classes sont appelées au préalable.</span><span class="sxs-lookup"><span data-stu-id="50d54-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="50d54-118">Le comportement de l’application serait que ce gestionnaire affiche tout d’abord sa boîte de message et ensuite le changement dans le Gestionnaire de la méthode virtuelle sont affiché.</span><span class="sxs-lookup"><span data-stu-id="50d54-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="50d54-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50d54-119">See Also</span></span>  
 <xref:System.Windows.EventManager>  
 [<span data-ttu-id="50d54-120">Marquage des événements routés comme gérés et gestion de classe</span><span class="sxs-lookup"><span data-stu-id="50d54-120">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="50d54-121">Gérer un événement routé</span><span class="sxs-lookup"><span data-stu-id="50d54-121">Handle a Routed Event</span></span>](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [<span data-ttu-id="50d54-122">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="50d54-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
