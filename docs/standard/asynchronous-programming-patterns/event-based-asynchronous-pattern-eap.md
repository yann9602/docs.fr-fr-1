---
title: "Modèle asynchrone basé sur les événements (EAP)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b5f242b9586c4ea3b045daf8f10b84127b81085
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="49e32-102">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="49e32-102">Event-based Asynchronous Pattern (EAP)</span></span>
<span data-ttu-id="49e32-103">Il existe plusieurs façons d’exposer des fonctionnalités asynchrones à du code client.</span><span class="sxs-lookup"><span data-stu-id="49e32-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="49e32-104">Le modèle asynchrone basé sur les événements recommande une méthode pour obtenir des classes un comportement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="49e32-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49e32-105">À partir du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la bibliothèque parallèle de tâches fournit un nouveau modèle de programmation asynchrone et parallèle.</span><span class="sxs-lookup"><span data-stu-id="49e32-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="49e32-106">Pour plus d’informations, consultez la page [Programmation parallèle](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="49e32-106">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49e32-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="49e32-107">In This Section</span></span>  
 [<span data-ttu-id="49e32-108">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="49e32-108">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="49e32-109">Explique comment le modèle asynchrone basé sur les événements permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.</span><span class="sxs-lookup"><span data-stu-id="49e32-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="49e32-110">Implémentation du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="49e32-110">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="49e32-111">Décrit la façon standardisée de placer dans un package une classe qui possède des fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="49e32-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="49e32-112">Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="49e32-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="49e32-113">Décrit les exigences liées à l’exposition de fonctionnalités asynchrones conformément au modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="49e32-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="49e32-114">Choix du moment auquel implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="49e32-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="49e32-115">Explique dans quelles situations vous devez implémenter le modèle asynchrone basé sur les événements plutôt que le modèle <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="49e32-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="49e32-116">Procédure pas à pas : implémenter un composant qui prend en charge le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="49e32-116">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="49e32-117">Illustre la création d’un composant qui implémente le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="49e32-117">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="49e32-118">Il est implémenté à l'aide de classes d'assistance à partir de l'espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>, ce qui garantit le bon fonctionnement du composant avec n'importe quel modèle d'application.</span><span class="sxs-lookup"><span data-stu-id="49e32-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="49e32-119">Guide pratique : utiliser des composants qui prennent en charge le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="49e32-119">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="49e32-120">Explique comment créer un composant qui prend en charge le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="49e32-120">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="49e32-121">Référence</span><span class="sxs-lookup"><span data-stu-id="49e32-121">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="49e32-122">Décrit la classe <xref:System.ComponentModel.AsyncOperation> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="49e32-122">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="49e32-123">Décrit la classe <xref:System.ComponentModel.AsyncOperationManager> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="49e32-123">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="49e32-124">Décrit le composant <xref:System.ComponentModel.BackgroundWorker> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="49e32-124">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49e32-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="49e32-125">Related Sections</span></span>  
 [<span data-ttu-id="49e32-126">La bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="49e32-126">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="49e32-127">Décrit un modèle de programmation pour les opérations asynchrones et parallèles.</span><span class="sxs-lookup"><span data-stu-id="49e32-127">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="49e32-128">Thread</span><span class="sxs-lookup"><span data-stu-id="49e32-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="49e32-129">Décrit les fonctionnalités de multithreading du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49e32-129">Describes multithreading features in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="49e32-130">Thread</span><span class="sxs-lookup"><span data-stu-id="49e32-130">Threading</span></span>](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 <span data-ttu-id="49e32-131">Décrit les fonctionnalités de multithreading des langages C# et Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="49e32-131">Describes multithreading features in the C# and Visual Basic languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e32-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49e32-132">See Also</span></span>  
 [<span data-ttu-id="49e32-133">Bonnes pratiques de threading géré</span><span class="sxs-lookup"><span data-stu-id="49e32-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="49e32-134">Événements</span><span class="sxs-lookup"><span data-stu-id="49e32-134">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="49e32-135">Multithreading dans les composants</span><span class="sxs-lookup"><span data-stu-id="49e32-135">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="49e32-136">Modèles de conception de la programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="49e32-136">Asynchronous Programming Design Patterns</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
