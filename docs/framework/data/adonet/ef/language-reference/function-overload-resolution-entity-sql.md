---
title: "Résolution de surcharge des fonctions (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cafbdd1a06ce506516fa985e9af147f55b4ea3d4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="d2f9b-102">Résolution de surcharge des fonctions (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d2f9b-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="d2f9b-103">Cette rubrique décrit comment résoudre les fonctions [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2f9b-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="d2f9b-104">Plusieurs fonctions peuvent être définies avec le même nom à condition que ces fonctions aient des signatures uniques.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="d2f9b-105">Lorsque cela est le cas, les critères suivants doivent être appliqués pour déterminer quelle fonction est référencée par une expression donnée.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="d2f9b-106">Ces critères sont appliqués dans l'ordre donné.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="d2f9b-107">Le premier critère qui s'applique uniquement à une fonction unique est la fonction résolue.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="d2f9b-108">**Le paramètre**.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-108">**Parameter number**.</span></span> <span data-ttu-id="d2f9b-109">La fonction a le même nombre de paramètres spécifiés dans l'expression.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="d2f9b-110">**Correspondance exacte sur le type**.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-110">**Exact match on type**.</span></span> <span data-ttu-id="d2f9b-111">Chaque type d’argument de la fonction correspond exactement au type de paramètre ou correspond au littéral Null.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="d2f9b-112">**Concordance sur le sous-type**.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-112">**Match on subtype**.</span></span> <span data-ttu-id="d2f9b-113">Chaque type d’argument de la fonction correspond exactement au type de paramètre ou en est un sous-type, ou l’argument correspond au littéral Null.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="d2f9b-114">Au cas où plusieurs fonctions diffèrent uniquement par le nombre de conversions de sous-types requis, la fonction avec le moins de conversions de sous-types est la fonction résolue.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="d2f9b-115">**Concordance sur le sous-type ou le type de promotion**.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="d2f9b-116">Chaque type d’argument de la fonction correspond exactement au type de paramètre, en est un sous-type ou peut être converti dans le type de paramètre, ou l’argument correspond au littéral Null.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="d2f9b-117">Encore une fois, au cas où plusieurs fonctions diffèrent uniquement par le nombre de promotions et de conversions de sous-types, la fonction avec le moins de promotions et de conversions de sous-types est la fonction résolue.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="d2f9b-118">Si aucun de ces critères ne permet la sélection d'une fonction unique, l'expression d'appel de la fonction est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="d2f9b-119">Même si une fonction unique peut être extraite à l'aide de ces règles, les arguments peuvent ne pas correspondre encore aux paramètres.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="d2f9b-120">Dans ce cas, une erreur est générée.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="d2f9b-121">Pour les fonctions définies par l'utilisateur, la définition pour une fonction de requête inline est prioritaire même lorsqu'une fonction définie par modèle existe avec une signature qui est une meilleure correspondance pour la fonction définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2f9b-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f9b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2f9b-122">See Also</span></span>  
 [<span data-ttu-id="d2f9b-123">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d2f9b-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d2f9b-124">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d2f9b-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="d2f9b-125">Fonctions</span><span class="sxs-lookup"><span data-stu-id="d2f9b-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
