---
title: ISOF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3e3f58608f6ef872f0000bc2d887cfd548589e17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isof-entity-sql"></a><span data-ttu-id="c4464-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c4464-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="c4464-103">Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous-types.</span><span class="sxs-lookup"><span data-stu-id="c4464-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4464-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4464-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4464-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c4464-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c4464-106">Toute expression de requête valide pour en déterminer le type.</span><span class="sxs-lookup"><span data-stu-id="c4464-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="c4464-107">NOT</span><span class="sxs-lookup"><span data-stu-id="c4464-107">NOT</span></span>  
 <span data-ttu-id="c4464-108">Inverse le résultat EDM.Boolean de l'opérateur IS OF.</span><span class="sxs-lookup"><span data-stu-id="c4464-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="c4464-109">ONLY</span><span class="sxs-lookup"><span data-stu-id="c4464-109">ONLY</span></span>  
 <span data-ttu-id="c4464-110">Indique que l'opérateur IS OF ne retourne `true` que si `expression` appartient au type `type` et non à l'un de ses sous-types.</span><span class="sxs-lookup"><span data-stu-id="c4464-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="c4464-111">Type sur lequel tester `expression`.</span><span class="sxs-lookup"><span data-stu-id="c4464-111">The type to test `expression` against.</span></span> <span data-ttu-id="c4464-112">Le type doit être qualifié par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4464-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4464-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c4464-113">Return Value</span></span>  
 <span data-ttu-id="c4464-114">`true` si `expression` est de type T, qui est soit un type de base, soit un type dérivé de `type` ; null si `expression` a la valeur null au moment de l'exécution ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="c4464-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4464-115">Notes</span><span class="sxs-lookup"><span data-stu-id="c4464-115">Remarks</span></span>  
 <span data-ttu-id="c4464-116">Les expressions `expression IS NOT OF (type)` et `expression IS NOT OF (ONLY type)` syntaxe est équivalente à `NOT (expression IS OF (type))` et `NOT (expression IS OF (ONLY type))`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="c4464-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="c4464-117">Le tableau suivant indique le comportement de l'opérateur `IS OF` sur certains modèles courants et d'autres plus singuliers.</span><span class="sxs-lookup"><span data-stu-id="c4464-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="c4464-118">Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :</span><span class="sxs-lookup"><span data-stu-id="c4464-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="c4464-119">Modèle</span><span class="sxs-lookup"><span data-stu-id="c4464-119">Pattern</span></span>|<span data-ttu-id="c4464-120">Comportement</span><span class="sxs-lookup"><span data-stu-id="c4464-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="c4464-121">null IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="c4464-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="c4464-122">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-122">Throws</span></span>|  
|<span data-ttu-id="c4464-123">null IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c4464-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="c4464-124">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-124">Throws</span></span>|  
|<span data-ttu-id="c4464-125">null IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="c4464-125">null IS OF (RowType)</span></span>|<span data-ttu-id="c4464-126">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-126">Throws</span></span>|  
|<span data-ttu-id="c4464-127">TREAT (null AS EntityType) IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="c4464-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="c4464-128">Retourne DBNull</span><span class="sxs-lookup"><span data-stu-id="c4464-128">Returns DBNull</span></span>|  
|<span data-ttu-id="c4464-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c4464-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="c4464-130">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-130">Throws</span></span>|  
|<span data-ttu-id="c4464-131">TREAT (null AS RowType) IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="c4464-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="c4464-132">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-132">Throws</span></span>|  
|<span data-ttu-id="c4464-133">EntityType IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="c4464-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="c4464-134">Retourne true/false</span><span class="sxs-lookup"><span data-stu-id="c4464-134">Returns true/false</span></span>|  
|<span data-ttu-id="c4464-135">ComplexType IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c4464-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="c4464-136">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-136">Throws</span></span>|  
|<span data-ttu-id="c4464-137">RowType IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="c4464-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="c4464-138">Exception</span><span class="sxs-lookup"><span data-stu-id="c4464-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4464-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4464-139">Example</span></span>  
 <span data-ttu-id="c4464-140">Les éléments suivants [!INCLUDE[esql](../../../../../../includes/esql-md.md)] requête utilise l’opérateur IS OF pour déterminer le type d’une expression de requête, puis utilise l’opérateur TREAT pour convertir un objet du type Course en collection d’objets du type OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="c4464-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="c4464-141">Cette requête est basée sur le modèle [School](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="c4464-141">The query is based on the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="c4464-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4464-142">See Also</span></span>  
 [<span data-ttu-id="c4464-143">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c4464-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
