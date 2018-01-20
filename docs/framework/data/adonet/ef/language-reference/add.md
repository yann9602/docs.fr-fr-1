---
title: + (Ajouter)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6014b2b37d3574af8462ec178f943340af6d7146
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="-add"></a><span data-ttu-id="3b5bb-102">+ (Ajouter)</span><span class="sxs-lookup"><span data-stu-id="3b5bb-102">+ (Add)</span></span>
<span data-ttu-id="3b5bb-103">Additionne deux nombres.</span><span class="sxs-lookup"><span data-stu-id="3b5bb-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b5bb-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b5bb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3b5bb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3b5bb-106">Toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="3b5bb-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3b5bb-107">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="3b5bb-107">Result Types</span></span>  
 <span data-ttu-id="3b5bb-108">Type de données qui résulte de la promotion de type implicite de deux arguments.</span><span class="sxs-lookup"><span data-stu-id="3b5bb-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="3b5bb-109">Pour plus d’informations sur la promotion de type implicite, consultez [système de Type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3b5bb-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b5bb-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3b5bb-110">Remarks</span></span>  
 <span data-ttu-id="3b5bb-111">Pour les types EDM.String, l'addition est une concaténation.</span><span class="sxs-lookup"><span data-stu-id="3b5bb-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b5bb-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b5bb-112">Example</span></span>  
 <span data-ttu-id="3b5bb-113">La requête Entity SQL ci-dessous utilise l'opérateur arithmétique + pour additionner deux nombres.</span><span class="sxs-lookup"><span data-stu-id="3b5bb-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="3b5bb-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="3b5bb-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3b5bb-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3b5bb-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3b5bb-116">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3b5bb-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3b5bb-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="3b5bb-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="3b5bb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b5bb-118">See Also</span></span>  
 [<span data-ttu-id="3b5bb-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3b5bb-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="3b5bb-120">Types de modèle conceptuel (CSDL)</span><span class="sxs-lookup"><span data-stu-id="3b5bb-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
