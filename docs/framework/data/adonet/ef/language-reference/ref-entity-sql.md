---
title: REF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 226a14daa706f6cf0481b752fa03dc95db3eff81
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="ref-entity-sql"></a><span data-ttu-id="8f7e3-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8f7e3-102">REF (Entity SQL)</span></span>
<span data-ttu-id="8f7e3-103">Retourne une référence à une instance d'entité.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f7e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f7e3-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="8f7e3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8f7e3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8f7e3-106">Toute expression valide qui produit une instance d'un type d'entité.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f7e3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8f7e3-107">Return Value</span></span>  
 <span data-ttu-id="8f7e3-108">Référence à l'instance d'entité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f7e3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8f7e3-109">Remarks</span></span>  
 <span data-ttu-id="8f7e3-110">Une référence d'entité se compose de la clé d'entité et d'un nom de jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="8f7e3-111">Des jeux d'entités différents pouvant être basés sur le même type d'entité, une clé d'entité particulière peut apparaître dans plusieurs jeux d'entités.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="8f7e3-112">Toutefois, une référence d'entité est toujours unique.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="8f7e3-113">Si l'expression d'entrée représente une entité rendue persistante, une référence à cette entité est retournée.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="8f7e3-114">Si l'expression d'entrée n'est pas une entité rendue persistante, une référence Null à cette entité est retournée.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="8f7e3-115">Si l'opérateur d'extraction de propriété (.) est utilisé pour accéder à une propriété d'une entité, la référence est automatiquement supprimée.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f7e3-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f7e3-116">Example</span></span>  
 <span data-ttu-id="8f7e3-117">La requête Entity SQL suivante utilise l'opérateur REF pour retourner la référence d'un argument d'entité d'entrée.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="8f7e3-118">La même requête supprime la référence car nous utilisons une opération d'extraction de propriété (.) pour accéder à une propriété de l'entité Product.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="8f7e3-119">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="8f7e3-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8f7e3-120">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f7e3-120">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8f7e3-121">Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8f7e3-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="8f7e3-122">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="8f7e3-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="8f7e3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f7e3-123">See Also</span></span>  
 [<span data-ttu-id="8f7e3-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="8f7e3-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="8f7e3-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="8f7e3-125">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="8f7e3-126">KEY</span><span class="sxs-lookup"><span data-stu-id="8f7e3-126">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="8f7e3-127">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8f7e3-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="8f7e3-128">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="8f7e3-128">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
