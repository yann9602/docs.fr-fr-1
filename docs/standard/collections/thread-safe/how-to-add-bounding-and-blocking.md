---
title: "Guide pratique : ajouter des fonctionnalités de délimitation et de blocage à une collection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aeba49c31238c62a12dba96d3dc47c3cc8ef1bcb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="6e727-102">Comment : ajouter des fonctionnalités de liaison et de blocage à une collection</span><span class="sxs-lookup"><span data-stu-id="6e727-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="6e727-103">Cet exemple indique comment ajouter des fonctionnalités de délimitation et de blocage à une classe de collection personnalisée en implémentant l’interface <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> dans la classe, puis en utilisant une instance de classe comme mécanisme de stockage interne pour un <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e727-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e727-104">Pour plus d’informations sur la délimitation et le blocage, consultez [Vue d’ensemble de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6e727-104">For more information about bounding and blocking, see [BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e727-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e727-105">Example</span></span>  
 <span data-ttu-id="6e727-106">La classe de collection personnalisée est une file d’attente de priorité de base dans laquelle les niveaux de priorité sont représentés sous la forme d’un tableau d’objets <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e727-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="6e727-107">Aucun classement supplémentaire n’est effectué au sein de chaque file d’attente.</span><span class="sxs-lookup"><span data-stu-id="6e727-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="6e727-108">Dans le code client, trois tâches sont démarrées.</span><span class="sxs-lookup"><span data-stu-id="6e727-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="6e727-109">La première tâche demande juste aux touches du clavier de permettre l’annulation à tout moment pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6e727-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="6e727-110">La deuxième tâche est le thread producteur. Elle ajoute de nouveaux éléments à la collection de blocage et donne à chaque élément une priorité basée sur une valeur aléatoire.</span><span class="sxs-lookup"><span data-stu-id="6e727-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="6e727-111">La troisième tâche supprime des éléments de la collection à mesure qu’ils deviennent disponibles.</span><span class="sxs-lookup"><span data-stu-id="6e727-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="6e727-112">Vous pouvez ajuster le comportement de l’application en rendant un thread plus rapide qu’un autre.</span><span class="sxs-lookup"><span data-stu-id="6e727-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="6e727-113">Si le thread producteur s’exécute plus rapidement, vous remarquerez les fonctionnalités de délimitation quand la collection de blocage empêche l’ajout d’éléments si elle contient déjà le nombre d’éléments spécifié dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="6e727-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="6e727-114">Si le thread consommateur s’exécute plus rapidement, vous remarquerez les fonctionnalités de blocage quand le consommateur attend l’ajout d’un nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="6e727-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="6e727-115">Par défaut, le stockage pour <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> est <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e727-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e727-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e727-116">See Also</span></span>  
 [<span data-ttu-id="6e727-117">Collections thread-safe</span><span class="sxs-lookup"><span data-stu-id="6e727-117">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
