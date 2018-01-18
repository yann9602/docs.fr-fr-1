---
title: "Comment : éliminer des éléments en double d'une séquence"
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
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3f3196b07c84ac5c63d883eef35d29b450c3b285
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a><span data-ttu-id="1f65e-102">Comment : éliminer des éléments en double d'une séquence</span><span class="sxs-lookup"><span data-stu-id="1f65e-102">Eliminate Duplicate Elements from a Sequence</span></span>
<span data-ttu-id="1f65e-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Distinct%2A> pour éliminer des éléments en double d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="1f65e-103">Use the <xref:System.Linq.Queryable.Distinct%2A> operator to eliminate duplicate elements from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f65e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f65e-104">Example</span></span>  
 <span data-ttu-id="1f65e-105">L'exemple suivant utilise <xref:System.Linq.Queryable.Distinct%2A> pour sélectionner une séquence des villes uniques qui comportent des clients.</span><span class="sxs-lookup"><span data-stu-id="1f65e-105">The following example uses <xref:System.Linq.Queryable.Distinct%2A> to select a sequence of the unique cities that have customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a><span data-ttu-id="1f65e-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f65e-106">See Also</span></span>  
 [<span data-ttu-id="1f65e-107">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="1f65e-107">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
