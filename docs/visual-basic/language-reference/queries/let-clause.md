---
title: Let, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="1d66f-102">Let, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d66f-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="1d66f-103">Calcule une valeur et l’assigne à une variable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="1d66f-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d66f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d66f-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="1d66f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="1d66f-105">Parts</span></span>  
  
|<span data-ttu-id="1d66f-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1d66f-106">Term</span></span>|<span data-ttu-id="1d66f-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1d66f-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="1d66f-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1d66f-108">Required.</span></span> <span data-ttu-id="1d66f-109">Un alias qui peut être utilisé pour référencer les résultats de l’expression fournie.</span><span class="sxs-lookup"><span data-stu-id="1d66f-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="1d66f-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1d66f-110">Required.</span></span> <span data-ttu-id="1d66f-111">Une expression qui sera évaluée et assignée à la variable spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1d66f-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d66f-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d66f-112">Remarks</span></span>  
 <span data-ttu-id="1d66f-113">Le `Let` clause vous permet de calculer des valeurs pour chaque résultat de la requête et y fait référence à l’aide d’un alias.</span><span class="sxs-lookup"><span data-stu-id="1d66f-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="1d66f-114">L’alias peut être utilisé dans d’autres clauses, telles que le `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="1d66f-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="1d66f-115">Le `Let` clause vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et substituer l’alias chaque fois que la clause d’expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1d66f-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="1d66f-116">Vous pouvez inclure un nombre quelconque de `variable` et `expression` les affectations dans la `Let` clause.</span><span class="sxs-lookup"><span data-stu-id="1d66f-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="1d66f-117">Séparez chaque assignation par une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="1d66f-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d66f-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d66f-118">Example</span></span>  
 <span data-ttu-id="1d66f-119">Le code suivant exemple utilise le `Let` clause pour calculer une remise de 10 pour cent sur les produits.</span><span class="sxs-lookup"><span data-stu-id="1d66f-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d66f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d66f-120">See Also</span></span>  
 [<span data-ttu-id="1d66f-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d66f-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1d66f-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="1d66f-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1d66f-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="1d66f-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="1d66f-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="1d66f-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1d66f-125">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="1d66f-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
