---
title: "Opérations de quantificateur (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4e0c982508640ef1ecb47d477d3e9330198474ca
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="78ba4-102">Opérations de quantificateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78ba4-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="78ba4-103">Opérations de quantificateur retournent un <xref:System.Boolean>valeur qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="78ba4-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="78ba4-104">L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences source différentes.</span><span class="sxs-lookup"><span data-stu-id="78ba4-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="78ba4-105">La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="78ba4-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="78ba4-106">La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="78ba4-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="78ba4-107">![Opérations de quantificateur LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="78ba4-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="78ba4-108">Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="78ba4-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78ba4-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="78ba4-109">Methods</span></span>  
  
|<span data-ttu-id="78ba4-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="78ba4-110">Method Name</span></span>|<span data-ttu-id="78ba4-111">Description</span><span class="sxs-lookup"><span data-stu-id="78ba4-111">Description</span></span>|<span data-ttu-id="78ba4-112">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78ba4-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="78ba4-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="78ba4-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="78ba4-114">Tout</span><span class="sxs-lookup"><span data-stu-id="78ba4-114">All</span></span>|<span data-ttu-id="78ba4-115">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="78ba4-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<span data-ttu-id="78ba4-116"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78ba4-116"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="78ba4-117"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78ba4-117"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="78ba4-118">Any</span><span class="sxs-lookup"><span data-stu-id="78ba4-118">Any</span></span>|<span data-ttu-id="78ba4-119">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="78ba4-119">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<span data-ttu-id="78ba4-120"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78ba4-120"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="78ba4-121"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78ba4-121"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="78ba4-122">Contient</span><span class="sxs-lookup"><span data-stu-id="78ba4-122">Contains</span></span>|<span data-ttu-id="78ba4-123">Détermine si une séquence contient un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="78ba4-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="78ba4-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="78ba4-124">Not applicable.</span></span>|<span data-ttu-id="78ba4-125"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78ba4-125"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="78ba4-126"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="78ba4-126"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="78ba4-127">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="78ba4-127">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="78ba4-128">Ces exemples utilisent la `Aggregate` clause dans Visual Basic en tant que partie de la condition de filtrage dans une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="78ba4-128">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="78ba4-129">L’exemple suivant utilise le `Aggregate` clause et la <xref:System.Linq.Enumerable.All%2A>méthode d’extension pour retourner à partir d’une collection de ces personnes dont les animaux domestiques ont tous dépassés un âge spécifié.</xref:System.Linq.Enumerable.All%2A></span><span class="sxs-lookup"><span data-stu-id="78ba4-129">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 <span data-ttu-id="78ba4-130">[!code-vb[CsLINQAnyAll n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="78ba4-130">[!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="78ba4-131">L’exemple suivant utilise le `Aggregate` clause et la <xref:System.Linq.Enumerable.Any%2A>méthode d’extension à retourner à partir d’une collection les personnes qui ont au moins un animal domestique qui a dépassé un âge spécifié.</xref:System.Linq.Enumerable.Any%2A></span><span class="sxs-lookup"><span data-stu-id="78ba4-131">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 <span data-ttu-id="78ba4-132">[!code-vb[CsLINQAnyAll n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="78ba4-132">[!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ba4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78ba4-133">See Also</span></span>  
 <span data-ttu-id="78ba4-134"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="78ba4-134"><xref:System.Linq></span></span>   
<span data-ttu-id="78ba4-135"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="78ba4-135"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="78ba4-136"> [Aggregate (Clause)](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="78ba4-136"> [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="78ba4-137"> [Comment : rechercher des phrases qui contiennent un jeu spécifié de mots (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)</span><span class="sxs-lookup"><span data-stu-id="78ba4-137"> [How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)</span></span>
