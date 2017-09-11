---
title: GROUP BY, Clause (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement
- Group By clause
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a27e2f15e61456b2e7ac0ede81c66cdb4e8fd612
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="ea1d7-102">Group By, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea1d7-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="ea1d7-103">Regroupe les éléments d'un résultat de requête.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-103">Groups the elements of a query result.</span></span> <span data-ttu-id="ea1d7-104">Peut aussi être utilisée pour appliquer des fonctions d’agrégation à chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="ea1d7-105">L’opération de regroupement est basée sur une ou plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea1d7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea1d7-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="ea1d7-107">Composants</span><span class="sxs-lookup"><span data-stu-id="ea1d7-107">Parts</span></span>  
  
-   <span data-ttu-id="ea1d7-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="ea1d7-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="ea1d7-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-109">Optional.</span></span> <span data-ttu-id="ea1d7-110">Un ou plusieurs champs de la ou des variables de requête qui identifient explicitement les champs à inclure dans le résultat groupé.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="ea1d7-111">Si aucun champ n’est spécifié, tous les champs de la ou des variables de requête sont inclus dans le résultat groupé.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="ea1d7-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-112">Required.</span></span> <span data-ttu-id="ea1d7-113">Expression qui identifie la clé à utiliser pour déterminer les groupes d’éléments.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="ea1d7-114">Vous pouvez spécifier plusieurs clés pour spécifier une clé composite.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="ea1d7-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-115">Optional.</span></span> <span data-ttu-id="ea1d7-116">Une ou plusieurs clés supplémentaires combinées à `keyExp1` pour créer une clé composite.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="ea1d7-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-117">Required.</span></span> <span data-ttu-id="ea1d7-118">Une ou plusieurs expressions qui identifient la façon dont les groupes sont agrégés.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="ea1d7-119">Pour identifier un nom de membre pour les résultats groupés, utilisez le mot clé `Group` , qui peut prendre l’une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ea1d7-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="ea1d7-120">ou</span><span class="sxs-lookup"><span data-stu-id="ea1d7-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="ea1d7-121">Vous pouvez aussi inclure des fonctions d’agrégation à appliquer au groupe.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea1d7-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="ea1d7-122">Remarks</span></span>  
 <span data-ttu-id="ea1d7-123">Vous pouvez utiliser la clause `Group By` pour décomposer les résultats d’une requête en groupes.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="ea1d7-124">Le regroupement est basé sur une clé ou une clé composite constituée de plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="ea1d7-125">Les éléments associés à des valeurs de clé correspondantes sont inclus dans le même groupe.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="ea1d7-126">Utilisez le paramètre `aggregateList` de la clause `Into` et le mot clé `Group` pour identifier le nom de membre servant à référencer le groupe.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="ea1d7-127">Vous pouvez aussi inclure des fonctions d’agrégation dans la clause `Into` pour calculer les valeurs des éléments groupés.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="ea1d7-128">Pour une liste des fonctions d’agrégation standard, consultez [Clause Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ea1d7-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea1d7-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea1d7-129">Example</span></span>  
 <span data-ttu-id="ea1d7-130">L’exemple de code suivant regroupe une liste de clients en fonction de leur situation (pays) et indique le nombre de clients dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="ea1d7-131">Les résultats sont triés par nom de pays.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-131">The results are ordered by country name.</span></span> <span data-ttu-id="ea1d7-132">Les résultats groupés sont organisés par nom de ville.</span><span class="sxs-lookup"><span data-stu-id="ea1d7-132">The grouped results are ordered by city name.</span></span>  
  
 <span data-ttu-id="ea1d7-133">[!code-vb[VbSimpleQuerySamples&#11;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ea1d7-133">[!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea1d7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea1d7-134">See Also</span></span>  
 <span data-ttu-id="ea1d7-135">[Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="ea1d7-135">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="ea1d7-136"> [Requêtes](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="ea1d7-136"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="ea1d7-137"> [Clause SELECT](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ea1d7-137"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="ea1d7-138"> [La Clause FROM](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ea1d7-138"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="ea1d7-139"> [Clause Order By](../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ea1d7-139"> [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="ea1d7-140"> [Aggregate (Clause)](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ea1d7-140"> [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="ea1d7-141"> [Group Join (clause)](../../../visual-basic/language-reference/queries/group-join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="ea1d7-141"> [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)</span></span>
