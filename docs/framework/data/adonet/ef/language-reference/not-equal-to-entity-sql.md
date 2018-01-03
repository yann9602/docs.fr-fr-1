---
title: "!= (différent de) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 81643b9a4a1cd49e950010c0023b27108d34180c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="175f0-102">!= (différent de) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="175f0-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="175f0-103">Compare deux expressions pour déterminer si l'expression de gauche est différente de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="175f0-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="175f0-104">L'opérateur != (différent de) est d'un point de vue fonctionnel équivalent à l'opérateur <>.</span><span class="sxs-lookup"><span data-stu-id="175f0-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="175f0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="175f0-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="175f0-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="175f0-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="175f0-107">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="175f0-107">Any valid expression.</span></span> <span data-ttu-id="175f0-108">Les deux expressions doivent posséder des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="175f0-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="175f0-109">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="175f0-109">Result Types</span></span>  
 <span data-ttu-id="175f0-110">`true` si l'expression de gauche est différente de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="175f0-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="175f0-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="175f0-111">Example</span></span>  
 <span data-ttu-id="175f0-112">La requête Entity SQL ci-dessous utilise l'opérateur != pour comparer deux expressions afin de déterminer si l'expression de gauche est différente de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="175f0-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="175f0-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="175f0-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="175f0-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="175f0-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="175f0-115">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="175f0-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="175f0-116">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="175f0-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="175f0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="175f0-117">See Also</span></span>  
 [<span data-ttu-id="175f0-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="175f0-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
