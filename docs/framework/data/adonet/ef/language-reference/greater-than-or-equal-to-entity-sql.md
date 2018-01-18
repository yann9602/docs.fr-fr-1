---
title: "&gt;= (Supérieur ou égal à) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b176e1efdc17b58083234d0437033bd43775f604
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="be9bb-102">&gt;= (Supérieur ou égal à) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="be9bb-102">&gt;= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="be9bb-103">Compare deux expressions pour déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="be9bb-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be9bb-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="be9bb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="be9bb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="be9bb-106">Toute expression valide.</span><span class="sxs-lookup"><span data-stu-id="be9bb-106">Any valid expression.</span></span> <span data-ttu-id="be9bb-107">Les deux expressions doivent posséder des types de données implicitement convertibles.</span><span class="sxs-lookup"><span data-stu-id="be9bb-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="be9bb-108">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="be9bb-108">Result Types</span></span>  
 <span data-ttu-id="be9bb-109">`true` si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="be9bb-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be9bb-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="be9bb-110">Example</span></span>  
 <span data-ttu-id="be9bb-111">La requête Entity SQL ci-dessous utilise l'opérateur de comparaison >= pour comparer deux expressions afin de déterminer si la valeur de l'expression de gauche est supérieure ou égale à celle de l'expression de droite.</span><span class="sxs-lookup"><span data-stu-id="be9bb-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="be9bb-112">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="be9bb-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="be9bb-113">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="be9bb-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="be9bb-114">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="be9bb-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="be9bb-115">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="be9bb-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="be9bb-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be9bb-116">See Also</span></span>  
 [<span data-ttu-id="be9bb-117">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="be9bb-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
