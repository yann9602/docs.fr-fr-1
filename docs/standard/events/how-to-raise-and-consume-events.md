---
title: "Comment : déclencher et utiliser des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="2030b-102">Comment : déclencher et utiliser des événements</span><span class="sxs-lookup"><span data-stu-id="2030b-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="2030b-103">Les exemples de cette rubrique montrent comment utiliser des événements.</span><span class="sxs-lookup"><span data-stu-id="2030b-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="2030b-104">Ils incluent des exemples de la <xref:System.EventHandler> délégué, le <xref:System.EventHandler%601> délégué et un délégué personnalisé, pour illustrer des événements avec et sans les données.</span><span class="sxs-lookup"><span data-stu-id="2030b-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="2030b-105">Les exemples utilisent les concepts décrits dans le [événements](../../../docs/standard/events/index.md) l’article.</span><span class="sxs-lookup"><span data-stu-id="2030b-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2030b-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2030b-106">Example</span></span>  
 <span data-ttu-id="2030b-107">Le premier exemple montre comment déclencher et de consommer un événement n’ayant pas de données.</span><span class="sxs-lookup"><span data-stu-id="2030b-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="2030b-108">Il contient une classe nommée `Counter` qui possède un événement nommé `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="2030b-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="2030b-109">Cet événement est déclenché lorsqu’une valeur de compteur est égal à ou dépasse un seuil.</span><span class="sxs-lookup"><span data-stu-id="2030b-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="2030b-110">Le <xref:System.EventHandler> délégué est associé à l’événement, car aucune donnée d’événement n’est fournie.</span><span class="sxs-lookup"><span data-stu-id="2030b-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2030b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="2030b-111">Example</span></span>  
 <span data-ttu-id="2030b-112">L’exemple suivant montre comment déclencher et de consommer un événement qui fournit des données.</span><span class="sxs-lookup"><span data-stu-id="2030b-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="2030b-113">Le <xref:System.EventHandler%601> délégué est associé à l’événement, et une instance d’un objet de données d’événement personnalisé est fournie.</span><span class="sxs-lookup"><span data-stu-id="2030b-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="2030b-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="2030b-114">Example</span></span>  
 <span data-ttu-id="2030b-115">L’exemple suivant montre comment déclarer un délégué pour un événement.</span><span class="sxs-lookup"><span data-stu-id="2030b-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="2030b-116">Le délégué est appelé `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="2030b-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="2030b-117">Il s’agit d’obtenir une illustration.</span><span class="sxs-lookup"><span data-stu-id="2030b-117">This is just an illustration.</span></span> <span data-ttu-id="2030b-118">En règle générale, il est inutile de déclarer un délégué d’un événement, car vous pouvez utiliser soit le <xref:System.EventHandler> ou <xref:System.EventHandler%601> déléguer.</span><span class="sxs-lookup"><span data-stu-id="2030b-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="2030b-119">Vous devez déclarer un délégué uniquement dans les rares scénarios, par exemple, votre classe disponible pour le code hérité qui ne peut pas utiliser des classes génériques.</span><span class="sxs-lookup"><span data-stu-id="2030b-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="2030b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2030b-120">See Also</span></span>  
 [<span data-ttu-id="2030b-121">Événements</span><span class="sxs-lookup"><span data-stu-id="2030b-121">Events</span></span>](../../../docs/standard/events/index.md)
