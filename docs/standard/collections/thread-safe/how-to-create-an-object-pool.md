---
title: "Guide pratique : créer un pool d'objets à l'aide d'un ConcurrentBag"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3e26e5954c886d52debbf3e2d41260767b94dc74
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="8a000-102">Comment : créer un pool d'objets à l'aide d'un ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="8a000-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="8a000-103">L’exemple suivant montre comment utiliser un conteneur simultané pour implémenter un pool d’objets.</span><span class="sxs-lookup"><span data-stu-id="8a000-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="8a000-104">Les pools d’objet peuvent améliorer les performances de l’application dans les cas où vous avez besoin de plusieurs instances d’une classe et que la création ou la destruction de la classe est coûteuse.</span><span class="sxs-lookup"><span data-stu-id="8a000-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="8a000-105">Quand un programme client demande un nouvel objet, le pool d’objets tente d’abord d’en fournir un qui a été créé et retourné au pool.</span><span class="sxs-lookup"><span data-stu-id="8a000-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="8a000-106">Si aucun n’est disponible, et uniquement dans ce cas, un nouvel objet est créé.</span><span class="sxs-lookup"><span data-stu-id="8a000-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="8a000-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> est utilisé pour stocker les objets, car il prend en charge l’insertion et la suppression rapides, en particulier quand le même thread ajoute et supprime des éléments.</span><span class="sxs-lookup"><span data-stu-id="8a000-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="8a000-108">Cet exemple peut être augmenté davantage pour être généré autour d’un <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que la structure de données de conteneur implémente, comme le font <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="8a000-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a000-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a000-109">Example</span></span>  
 <span data-ttu-id="8a000-110">[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)] [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]</span><span class="sxs-lookup"><span data-stu-id="8a000-110">[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)] [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a000-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a000-111">See Also</span></span>  
 [<span data-ttu-id="8a000-112">Collections thread-safe</span><span class="sxs-lookup"><span data-stu-id="8a000-112">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

