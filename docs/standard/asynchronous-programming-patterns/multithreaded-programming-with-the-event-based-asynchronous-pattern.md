---
title: "Programmation multithread avec le modèle asynchrone basé sur les événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a26f6750f68609b40e6917fc5b257e43d95c3c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c65ff-102">Programmation multithread avec le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="c65ff-103">Il existe plusieurs façons d’exposer des fonctionnalités asynchrones à du code client.</span><span class="sxs-lookup"><span data-stu-id="c65ff-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="c65ff-104">Le modèle asynchrone basé sur les événements prescrit la méthode recommandée pour que les classes présentent un comportement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c65ff-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c65ff-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c65ff-105">In This Section</span></span>  
 [<span data-ttu-id="c65ff-106">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="c65ff-107">Explique comment le modèle asynchrone basé sur les événements permet de profiter des avantages des applications multithread tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.</span><span class="sxs-lookup"><span data-stu-id="c65ff-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="c65ff-108">Implémentation du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="c65ff-109">Décrit la façon standardisée de placer dans un package une classe qui possède des fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c65ff-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="c65ff-110">Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="c65ff-111">Décrit les exigences liées à l’exposition de fonctionnalités asynchrones conformément au modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="c65ff-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="c65ff-112">Choix du moment auquel implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="c65ff-113">Explique dans quelles situations vous devez implémenter le modèle asynchrone basé sur les événements plutôt que le modèle <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="c65ff-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="c65ff-114">Procédure pas à pas : implémenter un composant qui prend en charge le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="c65ff-115">Illustre la création d’un composant qui implémente le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="c65ff-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="c65ff-116">Il est implémenté à l'aide de classes d'assistance à partir de l'espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>, ce qui garantit le bon fonctionnement du composant avec n'importe quel modèle d'application.</span><span class="sxs-lookup"><span data-stu-id="c65ff-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="c65ff-117">Guide pratique : utiliser des composants qui prennent en charge le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="c65ff-118">Explique comment créer un composant qui prend en charge le modèle asynchrone basé sur les événements.</span><span class="sxs-lookup"><span data-stu-id="c65ff-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c65ff-119">Référence</span><span class="sxs-lookup"><span data-stu-id="c65ff-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="c65ff-120">Décrit la classe <xref:System.ComponentModel.AsyncOperation> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="c65ff-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="c65ff-121">Décrit la classe <xref:System.ComponentModel.AsyncOperationManager> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="c65ff-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="c65ff-122">Décrit le composant <xref:System.ComponentModel.BackgroundWorker> et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="c65ff-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65ff-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c65ff-123">See Also</span></span>  
 [<span data-ttu-id="c65ff-124">Bonnes pratiques de threading géré</span><span class="sxs-lookup"><span data-stu-id="c65ff-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="c65ff-125">Événements</span><span class="sxs-lookup"><span data-stu-id="c65ff-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="c65ff-126">Multithreading dans les composants</span><span class="sxs-lookup"><span data-stu-id="c65ff-126">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="c65ff-127">Modèle asynchrone basé sur les événements (EAP)</span><span class="sxs-lookup"><span data-stu-id="c65ff-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
