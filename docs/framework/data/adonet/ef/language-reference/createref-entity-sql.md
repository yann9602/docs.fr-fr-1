---
title: CREATEREF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9fe960d5b19f5119f2337ec410738a2df31f20c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="createref-entity-sql"></a><span data-ttu-id="8ad4e-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8ad4e-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="8ad4e-103">Crée les références à une entité dans un jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ad4e-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ad4e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8ad4e-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="8ad4e-106">Identificateur de jeu d'entités ; ne correspond pas à un littéral de chaîne.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="8ad4e-107">Expression typée ligne correspondant aux propriétés de clés du type d'entité.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ad4e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="8ad4e-108">Remarks</span></span>  
 <span data-ttu-id="8ad4e-109">La structure de`row_typed_expression` doit être équivalente au type de clé de l'entité.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="8ad4e-110">Autrement dit, les champs qu'elle contient doivent être identiques en nombre et en types à ceux des clés de l'entité, et ils doivent être disposés dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="8ad4e-111">Dans l'exemple ci-dessous, Orders et BadOrders sont des jeux d'entités de type Order, et Id est supposé être l'unique propriété de clé de type Order.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="8ad4e-112">Cet exemple montre comment produire une référence à une entité de BadOrders.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="8ad4e-113">Notez que la référence peut être non résolue.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="8ad4e-114">Autrement dit, la référence peut ne pas identifier réellement une entité spécifique.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="8ad4e-115">Dans ce cas, une opération `DEREF` sur cette référence retourne une valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="8ad4e-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ad4e-116">Example</span></span>  
 <span data-ttu-id="8ad4e-117">La requête Entity SQL ci-dessous utilise l'opérateur CREATEREF pour créer des références à une entité contenue dans un jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="8ad4e-118">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="8ad4e-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8ad4e-119">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8ad4e-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8ad4e-120">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8ad4e-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8ad4e-121">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="8ad4e-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="8ad4e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad4e-122">See Also</span></span>  
 [<span data-ttu-id="8ad4e-123">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8ad4e-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="8ad4e-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="8ad4e-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="8ad4e-125">CLÉ</span><span class="sxs-lookup"><span data-stu-id="8ad4e-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="8ad4e-126">REF</span><span class="sxs-lookup"><span data-stu-id="8ad4e-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
