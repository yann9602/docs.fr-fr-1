---
title: "Guide pratique : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection"
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
helpviewer_keywords: thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7683e295bd1d898e112a754b06993dabf4483871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="82d4f-102">Comment : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="82d4f-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="82d4f-103">Outre l’extraction d’éléments à partir d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide des méthodes <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, vous pouvez également utiliser une boucle [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) en Visual Basic) pour supprimer des éléments jusqu’à ce que l’ajout soit terminé et que la collection soit vide.</span><span class="sxs-lookup"><span data-stu-id="82d4f-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="82d4f-104">Cela s’appelle une *énumération de mutation* ou *énumération de consommation* car, contrairement à une boucle `foreach` (`For Each`) typique, cet énumérateur modifie la collection source en supprimant ses éléments.</span><span class="sxs-lookup"><span data-stu-id="82d4f-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82d4f-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="82d4f-105">Example</span></span>  
 <span data-ttu-id="82d4f-106">L’exemple suivant indique comment supprimer tous les éléments d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide d’une boucle `foreach` (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="82d4f-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="82d4f-107">Cet exemple utilise une boucle `foreach` avec la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> dans le thread consommateur, ce qui provoque la suppression de chaque élément de la collection pendant son énumération.</span><span class="sxs-lookup"><span data-stu-id="82d4f-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="82d4f-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limite le nombre maximal d’éléments présents dans la collection à tout moment.</span><span class="sxs-lookup"><span data-stu-id="82d4f-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="82d4f-109">Cette façon d’énumérer la collection bloque le thread consommateur si aucun élément n’est disponible ou si la collection est vide.</span><span class="sxs-lookup"><span data-stu-id="82d4f-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="82d4f-110">Dans cet exemple, le blocage n’est pas un problème, car le thread producteur ajoute des éléments plus vite qu’ils ne peuvent être consommés.</span><span class="sxs-lookup"><span data-stu-id="82d4f-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="82d4f-111">Il n’y a aucune garantie que les éléments soient énumérés dans le même ordre que celui dans lequel ils ont été ajoutés par les threads producteurs.</span><span class="sxs-lookup"><span data-stu-id="82d4f-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="82d4f-112">Pour énumérer la collection sans la modifier, utilisez seulement `foreach` (`For Each`) sans la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="82d4f-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="82d4f-113">Toutefois, il est important de comprendre que ce genre d’énumération représente un instantané de la collection à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="82d4f-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="82d4f-114">Si d’autres threads ajoutent ou suppriment des éléments simultanément pendant l’exécution de la boucle, la boucle peut ne pas représenter l’état réel de la collection.</span><span class="sxs-lookup"><span data-stu-id="82d4f-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d4f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d4f-115">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="82d4f-116">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="82d4f-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)
