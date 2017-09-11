---
title: "Événements (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a913a615de8185bb358376def1e2a051bdaa951
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="events-c-programming-guide"></a><span data-ttu-id="5a326-102">Événements (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="5a326-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="5a326-103">Les événements permettent à une [classe](../../../csharp/language-reference/keywords/class.md) ou à un objet de notifier d’autres classes ou objets quand quelque chose de significatif se produit.</span><span class="sxs-lookup"><span data-stu-id="5a326-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="5a326-104">La classe qui envoie (ou *déclenche*) l’événement est appelée *publieur* et les classes qui reçoivent (ou *gèrent*) l’événement sont appelées *abonnés*.</span><span class="sxs-lookup"><span data-stu-id="5a326-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="5a326-105">Dans une application C# Windows Forms ou web classique, vous vous abonnez à des événements déclenchés par des contrôles, comme des boutons et des zones de liste.</span><span class="sxs-lookup"><span data-stu-id="5a326-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="5a326-106">Vous pouvez utiliser l’IDE [!INCLUDE[csprcs](~/includes/csprcs-md.md)] pour parcourir les événements publiés par un contrôle et sélectionner ceux que vous voulez gérer.</span><span class="sxs-lookup"><span data-stu-id="5a326-106">You can use the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="5a326-107">L’IDE ajoute automatiquement une méthode de gestionnaire d’événements vide et le code pour vous abonner à l’événement.</span><span class="sxs-lookup"><span data-stu-id="5a326-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="5a326-108">Pour plus d’informations, consultez [Guide pratique pour s’abonner et annuler l’abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="5a326-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="5a326-109">Vue d'ensemble des événements</span><span class="sxs-lookup"><span data-stu-id="5a326-109">Events Overview</span></span>  
 <span data-ttu-id="5a326-110">Les événements ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5a326-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="5a326-111">Le publieur détermine quand un événement est déclenché ; les abonnés déterminent l’action entreprise en réponse à l’événement.</span><span class="sxs-lookup"><span data-stu-id="5a326-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="5a326-112">Un événement peut avoir plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="5a326-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="5a326-113">Un abonné peut gérer plusieurs événements provenant de plusieurs publieurs.</span><span class="sxs-lookup"><span data-stu-id="5a326-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="5a326-114">Les événements qui n’ont aucun abonné ne sont jamais déclenchés.</span><span class="sxs-lookup"><span data-stu-id="5a326-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="5a326-115">Les événements sont généralement utilisés pour signaler des actions de l’utilisateur, comme les clics de bouton ou les sélections de menu dans les interfaces utilisateur graphiques.</span><span class="sxs-lookup"><span data-stu-id="5a326-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="5a326-116">Quand un événement a plusieurs abonnés, les gestionnaires d’événements sont appelées de façon synchrone quand un événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="5a326-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="5a326-117">Pour appeler des événements de façon asynchrone, consultez [Calling Synchronous Methods Asynchronously](https://msdn.microsoft.com/library/2e08f6yc).</span><span class="sxs-lookup"><span data-stu-id="5a326-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](https://msdn.microsoft.com/library/2e08f6yc).</span></span>  
  
-   <span data-ttu-id="5a326-118">Dans la bibliothèque de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] , les événements sont basés sur le délégué <xref:System.EventHandler> et la classe de base <xref:System.EventArgs> .</span><span class="sxs-lookup"><span data-stu-id="5a326-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a326-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="5a326-119">Related Sections</span></span>  
 <span data-ttu-id="5a326-120">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="5a326-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5a326-121">Guide pratique pour s’abonner et se désabonner d’événements</span><span class="sxs-lookup"><span data-stu-id="5a326-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="5a326-122">Comment : publier des événements conformes aux indications du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5a326-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="5a326-123">Comment : déclencher les événements de la classe de base dans les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="5a326-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="5a326-124">Guide pratique d’implémentation d’événements d’interface</span><span class="sxs-lookup"><span data-stu-id="5a326-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="5a326-125">Synchronisation des threads</span><span class="sxs-lookup"><span data-stu-id="5a326-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="5a326-126">Comment : utiliser un dictionnaire pour stocker des instances d’événements</span><span class="sxs-lookup"><span data-stu-id="5a326-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="5a326-127">Comment : implémenter des accesseurs d’événement personnalisés</span><span class="sxs-lookup"><span data-stu-id="5a326-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5a326-128">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5a326-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="5a326-129">Chapitres proposés</span><span class="sxs-lookup"><span data-stu-id="5a326-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="5a326-130">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) (Délégués, événements et expressions lambda) dans [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="5a326-130">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="5a326-131">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) dans [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span><span class="sxs-lookup"><span data-stu-id="5a326-131">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a326-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a326-132">See Also</span></span>  
 <span data-ttu-id="5a326-133"><xref:System.EventHandler></span><span class="sxs-lookup"><span data-stu-id="5a326-133"><xref:System.EventHandler></span></span>   
 <span data-ttu-id="5a326-134">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a326-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="5a326-135">[Délégués](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a326-135">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="5a326-136">[Création de gestionnaires d’événements dans Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx) </span><span class="sxs-lookup"><span data-stu-id="5a326-136">[Creating Event Handlers in Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx) </span></span>  
 [<span data-ttu-id="5a326-137">Programmation multithread avec le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="5a326-137">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](https://msdn.microsoft.com/library/hkasytyf)

