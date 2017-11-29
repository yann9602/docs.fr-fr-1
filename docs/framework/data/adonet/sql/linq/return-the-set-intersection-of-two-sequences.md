---
title: "Retourner l'intersection définie de deux séquences"
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
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ff65c310323f7505f00dc4a768869cac8226d25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="01ce4-102">Retourner l'intersection définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="01ce4-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="01ce4-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Intersect%2A> pour retourner l'intersection définie de deux séquences.</span><span class="sxs-lookup"><span data-stu-id="01ce4-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ce4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="01ce4-104">Example</span></span>  
 <span data-ttu-id="01ce4-105">Cet exemple utilise <xref:System.Linq.Queryable.Intersect%2A> pour retourner une séquence de tous les pays dans lesquels les `Customers` et les `Employees` habitent.</span><span class="sxs-lookup"><span data-stu-id="01ce4-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="01ce4-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opération <xref:System.Linq.Queryable.Intersect%2A> est correctement définie sur les jeux uniquement.</span><span class="sxs-lookup"><span data-stu-id="01ce4-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="01ce4-107">La sémantique pour les multijeux n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="01ce4-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ce4-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01ce4-108">See Also</span></span>  
 [<span data-ttu-id="01ce4-109">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="01ce4-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="01ce4-110">Traduction d’opérateur de requête standard</span><span class="sxs-lookup"><span data-stu-id="01ce4-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
