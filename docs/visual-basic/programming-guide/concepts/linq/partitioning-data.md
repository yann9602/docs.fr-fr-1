---
title: "Partitionnement des données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
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
ms.openlocfilehash: 9d0df2bc473f48fba4bbb094317166407f7c7ec2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="d3786-102">Partitionnement des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3786-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="d3786-103">Partitionnement dans LINQ fait référence à l’opération de division d’une séquence d’entrée en deux sections, sans réorganiser les éléments, puis retourner une des sections.</span><span class="sxs-lookup"><span data-stu-id="d3786-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="d3786-104">L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="d3786-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="d3786-105">La première opération retourne les trois premiers éléments de la séquence.</span><span class="sxs-lookup"><span data-stu-id="d3786-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="d3786-106">La deuxième opération ignore les trois premiers éléments et retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="d3786-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="d3786-107">La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments.</span><span class="sxs-lookup"><span data-stu-id="d3786-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="d3786-108">![LINQ, opérations de partitionnement](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="d3786-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="d3786-109">Les méthodes d’opérateur de requête standard qui partitionnent les séquences sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="d3786-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="d3786-110">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="d3786-110">Operators</span></span>  
  
|<span data-ttu-id="d3786-111">Nom d'opérateur</span><span class="sxs-lookup"><span data-stu-id="d3786-111">Operator Name</span></span>|<span data-ttu-id="d3786-112">Description</span><span class="sxs-lookup"><span data-stu-id="d3786-112">Description</span></span>|<span data-ttu-id="d3786-113">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3786-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="d3786-114">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="d3786-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="d3786-115">Ignorer</span><span class="sxs-lookup"><span data-stu-id="d3786-115">Skip</span></span>|<span data-ttu-id="d3786-116">Ignore les éléments jusqu'à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="d3786-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<span data-ttu-id="d3786-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="d3786-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="d3786-119">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="d3786-119">SkipWhile</span></span>|<span data-ttu-id="d3786-120">Ignore les éléments basés sur une fonction de prédicat jusqu'à ce qu’un élément ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="d3786-120">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<span data-ttu-id="d3786-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="d3786-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="d3786-123">Take</span><span class="sxs-lookup"><span data-stu-id="d3786-123">Take</span></span>|<span data-ttu-id="d3786-124">Prend les éléments jusqu'à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="d3786-124">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<span data-ttu-id="d3786-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="d3786-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="d3786-127">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="d3786-127">TakeWhile</span></span>|<span data-ttu-id="d3786-128">Prend les éléments basés sur une fonction de prédicat jusqu'à ce qu’un élément ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="d3786-128">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<span data-ttu-id="d3786-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="d3786-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d3786-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d3786-131">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="d3786-131">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="d3786-132">Ignorer</span><span class="sxs-lookup"><span data-stu-id="d3786-132">Skip</span></span>  
 <span data-ttu-id="d3786-133">Le code suivant exemple utilise le `Skip` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour ignorer les quatre premières chaînes d’un tableau de chaînes avant de retourner les chaînes restantes dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="d3786-133">The following code example uses the `Skip` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 <span data-ttu-id="d3786-134">[!code-vb[CsLINQPartitioning n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3786-134">[!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span></span>  
  
### <a name="skipwhile"></a><span data-ttu-id="d3786-135">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="d3786-135">SkipWhile</span></span>  
 <span data-ttu-id="d3786-136">Le code suivant exemple utilise le `Skip While` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour ignorer les chaînes dans un tableau dont la première lettre de la chaîne est « a ».</span><span class="sxs-lookup"><span data-stu-id="d3786-136">The following code example uses the `Skip While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="d3786-137">Les chaînes restantes dans le tableau sont retournés.</span><span class="sxs-lookup"><span data-stu-id="d3786-137">The remaining strings in the array are returned.</span></span>  
  
 <span data-ttu-id="d3786-138">[!code-vb[CsLINQPartitioning n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3786-138">[!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span></span>  
  
### <a name="take"></a><span data-ttu-id="d3786-139">Take</span><span class="sxs-lookup"><span data-stu-id="d3786-139">Take</span></span>  
 <span data-ttu-id="d3786-140">Le code suivant exemple utilise le `Take` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour retourner les deux premières chaînes dans un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="d3786-140">The following code example uses the `Take` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return the first two strings in an array of strings.</span></span>  
  
 <span data-ttu-id="d3786-141">[!code-vb[CsLINQPartitioning n °&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3786-141">[!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span></span>  
  
### <a name="takewhile"></a><span data-ttu-id="d3786-142">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="d3786-142">TakeWhile</span></span>  
 <span data-ttu-id="d3786-143">Le code suivant exemple utilise le `Take While` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour renvoyer des chaînes à partir d’un tableau dont la longueur de la chaîne est inférieur ou égal à cinq.</span><span class="sxs-lookup"><span data-stu-id="d3786-143">The following code example uses the `Take While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return strings from an array while the length of the string is five or less.</span></span>  
  
 <span data-ttu-id="d3786-144">[!code-vb[CsLINQPartitioning n °&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d3786-144">[!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3786-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3786-145">See Also</span></span>  
 <span data-ttu-id="d3786-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="d3786-146"><xref:System.Linq></span></span>   
<span data-ttu-id="d3786-147"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d3786-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="d3786-148"> [Skip (Clause)](../../../../visual-basic/language-reference/queries/skip-clause.md) </span><span class="sxs-lookup"><span data-stu-id="d3786-148"> [Skip Clause](../../../../visual-basic/language-reference/queries/skip-clause.md) </span></span>  
<span data-ttu-id="d3786-149"> [Skip While, Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="d3786-149"> [Skip While Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span></span>  
<span data-ttu-id="d3786-150"> [Take, Clause](../../../../visual-basic/language-reference/queries/take-clause.md) </span><span class="sxs-lookup"><span data-stu-id="d3786-150"> [Take Clause](../../../../visual-basic/language-reference/queries/take-clause.md) </span></span>  
<span data-ttu-id="d3786-151"> [Take While (clause)](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span><span class="sxs-lookup"><span data-stu-id="d3786-151"> [Take While Clause](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span></span>
