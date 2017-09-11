---
title: "Guide pratique : utiliser des tableaux de collections de blocage dans un pipeline"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8dda929df8e3de907c228bbef85749cba5cabc25
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="de471-102">Comment : utiliser des tableaux de collections de blocage dans un pipeline</span><span class="sxs-lookup"><span data-stu-id="de471-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="de471-103">L’exemple suivant montre comment utiliser des tableaux d’objets <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> avec des méthodes statiques telles que <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> pour implémenter le transfert de données rapide et flexible entre des composants.</span><span class="sxs-lookup"><span data-stu-id="de471-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de471-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="de471-104">Example</span></span>  
 <span data-ttu-id="de471-105">L’exemple suivant montre une implémentation de pipeline de base dans laquelle chaque objet prend simultanément des données dans la collection d’entrée, les transforme et les passe à la collection de sortie.</span><span class="sxs-lookup"><span data-stu-id="de471-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 <span data-ttu-id="de471-106">[!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)] [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]</span><span class="sxs-lookup"><span data-stu-id="de471-106">[!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)] [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de471-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de471-107">See Also</span></span>  
 <span data-ttu-id="de471-108"><xref:System.Collections.Concurrent?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="de471-108"><xref:System.Collections.Concurrent?displayProperty=fullName></span></span>   
 [<span data-ttu-id="de471-109">Collections thread-safe</span><span class="sxs-lookup"><span data-stu-id="de471-109">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

