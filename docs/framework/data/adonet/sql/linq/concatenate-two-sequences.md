---
title: "Concaténer deux séquences"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8bcb20f5d057c3b54e49e2fac81e9799ac42b1f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="182a0-102">Concaténer deux séquences</span><span class="sxs-lookup"><span data-stu-id="182a0-102">Concatenate Two Sequences</span></span>
<span data-ttu-id="182a0-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Concat%2A> pour concaténer deux séquences.</span><span class="sxs-lookup"><span data-stu-id="182a0-103">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="182a0-104">L'opérateur <xref:System.Linq.Queryable.Concat%2A> est défini pour les multijeux ordonnés pour lesquels l'ordre du destinataire et de l'argument est identique.</span><span class="sxs-lookup"><span data-stu-id="182a0-104">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="182a0-105">Le classement dans SQL est la dernière étape avant la génération des résultats.</span><span class="sxs-lookup"><span data-stu-id="182a0-105">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="182a0-106">Par conséquent, l'opérateur <xref:System.Linq.Queryable.Concat%2A> est implémenté en utilisant `UNION ALL` et ne conserve pas l'ordre de ses arguments.</span><span class="sxs-lookup"><span data-stu-id="182a0-106">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="182a0-107">Pour vérifier que le classement est correct dans les résultats, assurez-vous de classer les résultats explicitement.</span><span class="sxs-lookup"><span data-stu-id="182a0-107">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="182a0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="182a0-108">Example</span></span>  
 <span data-ttu-id="182a0-109">Cet exemple utilise <xref:System.Linq.Queryable.Concat%2A> pour retourner une séquence de tous les numéros de téléphone et de télécopie de `Customer` et `Employee`.</span><span class="sxs-lookup"><span data-stu-id="182a0-109">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="182a0-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="182a0-110">Example</span></span>  
 <span data-ttu-id="182a0-111">Cet exemple utilise <xref:System.Linq.Queryable.Concat%2A> pour retourner une séquence de tous les mappages de nom et de numéro de téléphone de `Customer` et `Employee`.</span><span class="sxs-lookup"><span data-stu-id="182a0-111">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="182a0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="182a0-112">See Also</span></span>  
 [<span data-ttu-id="182a0-113">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="182a0-113">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="182a0-114">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="182a0-114">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
