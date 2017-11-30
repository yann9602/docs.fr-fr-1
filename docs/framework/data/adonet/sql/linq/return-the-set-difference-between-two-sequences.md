---
title: "Comment : retourner la différence définie entre deux séquences"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a3dae34f2b5904312fa3fcd994a01b2e024f1970
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="78179-102">Comment : retourner la différence définie entre deux séquences</span><span class="sxs-lookup"><span data-stu-id="78179-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="78179-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Except%2A> pour retourner la différence définie entre deux séquences.</span><span class="sxs-lookup"><span data-stu-id="78179-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78179-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="78179-104">Example</span></span>  
 <span data-ttu-id="78179-105">Cet exemple utilise <xref:System.Linq.Queryable.Except%2A> pour retourner une séquence de tous les pays dans lesquels résident des `Customers` mais dans lesquels aucun des `Employees` ne réside.</span><span class="sxs-lookup"><span data-stu-id="78179-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="78179-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opération <xref:System.Linq.Queryable.Except%2A> est correctement définie sur les jeux uniquement.</span><span class="sxs-lookup"><span data-stu-id="78179-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="78179-107">La sémantique pour les multijeux n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="78179-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78179-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78179-108">See Also</span></span>  
 [<span data-ttu-id="78179-109">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="78179-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="78179-110">Traduction d’opérateur de requête standard</span><span class="sxs-lookup"><span data-stu-id="78179-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
