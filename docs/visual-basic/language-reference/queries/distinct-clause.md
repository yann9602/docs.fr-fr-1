---
title: Distinct, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="4ff8f-102">Distinct, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ff8f-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="4ff8f-103">Restreint les valeurs de la variable de portée actuelle pour éliminer les valeurs en double dans les clauses de requête suivantes.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ff8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ff8f-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="4ff8f-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="4ff8f-105">Remarks</span></span>  
 <span data-ttu-id="4ff8f-106">Vous pouvez utiliser la `Distinct` clause pour retourner une liste d’éléments uniques.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="4ff8f-107">Le `Distinct` clause indique que la requête d’ignorer les résultats de requête en double.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="4ff8f-108">Le `Distinct` clause s’applique aux valeurs doubles pour tous les champs spécifiés par un retour la `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="4ff8f-109">Si aucun `Select` clause est spécifiée, la `Distinct` clause est appliquée à la variable de portée pour la requête identifiée dans la `From` clause.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="4ff8f-110">Si la variable de portée n’est pas un type immuable, la requête n’ignore un résultat de requête si tous les membres du type correspond à un résultat de requête existant.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ff8f-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="4ff8f-111">Example</span></span>  
 <span data-ttu-id="4ff8f-112">L’expression de requête suivante joint une liste de clients et une liste des commandes client.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="4ff8f-113">Le `Distinct` clause est incluse pour retourner une liste de noms de clients uniques et les dates de commande.</span><span class="sxs-lookup"><span data-stu-id="4ff8f-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4ff8f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ff8f-114">See Also</span></span>  
 [<span data-ttu-id="4ff8f-115">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ff8f-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="4ff8f-116">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4ff8f-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="4ff8f-117">From (clause)</span><span class="sxs-lookup"><span data-stu-id="4ff8f-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="4ff8f-118">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="4ff8f-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="4ff8f-119">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="4ff8f-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
