---
title: KEY (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3be9c51e48e21d76c4425401000cbfdd55f5f538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="key-entity-sql"></a><span data-ttu-id="3d53a-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3d53a-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="3d53a-103">Extrait la clé d'une référence ou d'une expression d'entité.</span><span class="sxs-lookup"><span data-stu-id="3d53a-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d53a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d53a-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="3d53a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="3d53a-105">Remarks</span></span>  
 <span data-ttu-id="3d53a-106">Une clé d'entité contient les valeurs de clés dans l'ordre correct de l'entité ou de la référence d'entité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3d53a-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="3d53a-107">Plusieurs jeux d'entités pouvant être basés sur le même type d'entité, la même clé peut apparaître dans chaque jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="3d53a-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="3d53a-108">Pour obtenir une référence unique, utilisez `REF`.</span><span class="sxs-lookup"><span data-stu-id="3d53a-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="3d53a-109">Le type de retour de l'opérateur KEY est un type de ligne qui inclut un champ pour chaque clé de l'entité, dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="3d53a-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="3d53a-110">Dans l'exemple suivant, une référence à l'entité BadOrder est passée à l'opérateur Key, lequel retourne la partie clé de cette référence.</span><span class="sxs-lookup"><span data-stu-id="3d53a-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="3d53a-111">Dans le cas présent, un type d'enregistrement ayant exactement un champ correspondant à la propriété `Id` .</span><span class="sxs-lookup"><span data-stu-id="3d53a-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="3d53a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d53a-112">Example</span></span>  
 <span data-ttu-id="3d53a-113">La requête Entity SQL suivante utilise l'opérateur KEY pour extraire la partie clé d'une expression avec référence de type.</span><span class="sxs-lookup"><span data-stu-id="3d53a-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="3d53a-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="3d53a-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d53a-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3d53a-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3d53a-116">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d53a-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3d53a-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="3d53a-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="3d53a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d53a-118">See Also</span></span>  
 [<span data-ttu-id="3d53a-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3d53a-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="3d53a-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="3d53a-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="3d53a-121">REF</span><span class="sxs-lookup"><span data-stu-id="3d53a-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="3d53a-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="3d53a-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
