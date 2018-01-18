---
title: IN (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d32e5012b4acbf0ecd6830f549de5dccf79bb38b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="in-entity-sql"></a><span data-ttu-id="51fe4-102">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="51fe4-102">IN (Entity SQL)</span></span>
<span data-ttu-id="51fe4-103">Détermine si une valeur correspond à une valeur incluse dans une collection.</span><span class="sxs-lookup"><span data-stu-id="51fe4-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fe4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51fe4-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="51fe4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="51fe4-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="51fe4-106">Toute expression valide qui retourne la valeur dont rechercher une correspondance.</span><span class="sxs-lookup"><span data-stu-id="51fe4-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="51fe4-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="51fe4-107">[ NOT ]</span></span>  
 <span data-ttu-id="51fe4-108">Spécifie que la valeur du résultat `Boolean` de IN est inversée.</span><span class="sxs-lookup"><span data-stu-id="51fe4-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="51fe4-109">Toute expression valide qui retourne la collection dans laquelle rechercher une correspondance.</span><span class="sxs-lookup"><span data-stu-id="51fe4-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="51fe4-110">Toutes les expressions doivent être du même type que le `value` ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="51fe4-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51fe4-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="51fe4-111">Return Value</span></span>  
 <span data-ttu-id="51fe4-112">`true` si la valeur est trouvée dans la collection ; null si la valeur ou la collection est Null ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="51fe4-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="51fe4-113">L'utilisation de NOT IN inverse les résultats de IN.</span><span class="sxs-lookup"><span data-stu-id="51fe4-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51fe4-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="51fe4-114">Example</span></span>  
 <span data-ttu-id="51fe4-115">La requête Entity SQL ci-dessous utilise l’opérateur IN pour déterminer si une valeur correspond à une valeur contenue dans une collection.</span><span class="sxs-lookup"><span data-stu-id="51fe4-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="51fe4-116">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="51fe4-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="51fe4-117">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="51fe4-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="51fe4-118">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="51fe4-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="51fe4-119">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="51fe4-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="51fe4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51fe4-120">See Also</span></span>  
 [<span data-ttu-id="51fe4-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="51fe4-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
