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
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b0f0ed30ae5192ed8a8f069d591855857bd2fa49
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="f9e1e-102">Comment : utiliser la boucle ForEach pour supprimer les éléments d'un BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="f9e1e-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="f9e1e-103">Outre l’extraction d’éléments à partir d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide des méthodes <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, vous pouvez également utiliser une boucle [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) en Visual Basic) pour supprimer des éléments jusqu’à ce que l’ajout soit terminé et que la collection soit vide.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="f9e1e-104">Cela s’appelle une *énumération de mutation* ou *énumération de consommation* car, contrairement à une boucle `foreach` (`For Each`) typique, cet énumérateur modifie la collection source en supprimant ses éléments.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9e1e-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9e1e-105">Example</span></span>  
 <span data-ttu-id="f9e1e-106">L’exemple suivant indique comment supprimer tous les éléments d’un <xref:System.Collections.Concurrent.BlockingCollection%601> à l’aide d’une boucle `foreach` (`For Each`).</span><span class="sxs-lookup"><span data-stu-id="f9e1e-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 <span data-ttu-id="f9e1e-107">[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)] [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]</span><span class="sxs-lookup"><span data-stu-id="f9e1e-107">[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)] [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]</span></span>  
  
 <span data-ttu-id="f9e1e-108">Cet exemple utilise une boucle `foreach` avec la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> dans le thread consommateur, ce qui provoque la suppression de chaque élément de la collection pendant son énumération.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-108">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="f9e1e-109"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> limite le nombre maximal d’éléments présents dans la collection à tout moment.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-109"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="f9e1e-110">Cette façon d’énumérer la collection bloque le thread consommateur si aucun élément n’est disponible ou si la collection est vide.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-110">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="f9e1e-111">Dans cet exemple, le blocage n’est pas un problème, car le thread producteur ajoute des éléments plus vite qu’ils ne peuvent être consommés.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-111">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="f9e1e-112">Il n’y a aucune garantie que les éléments soient énumérés dans le même ordre que celui dans lequel ils ont été ajoutés par les threads producteurs.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-112">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="f9e1e-113">Pour énumérer la collection sans la modifier, utilisez seulement `foreach` (`For Each`) sans la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-113">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="f9e1e-114">Toutefois, il est important de comprendre que ce genre d’énumération représente un instantané de la collection à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-114">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="f9e1e-115">Si d’autres threads ajoutent ou suppriment des éléments simultanément pendant l’exécution de la boucle, la boucle peut ne pas représenter l’état réel de la collection.</span><span class="sxs-lookup"><span data-stu-id="f9e1e-115">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e1e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9e1e-116">See Also</span></span>  
 <span data-ttu-id="f9e1e-117"><xref:System.Collections.Concurrent?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f9e1e-117"><xref:System.Collections.Concurrent?displayProperty=fullName></span></span>   
 [<span data-ttu-id="f9e1e-118">Programmation parallèle</span><span class="sxs-lookup"><span data-stu-id="f9e1e-118">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)

