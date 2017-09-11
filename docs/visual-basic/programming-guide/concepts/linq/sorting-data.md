---
title: "Tri des données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
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
ms.openlocfilehash: 1870d401ffdeeb2452ace1b74a8fb70e19c9b9ed
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="63882-102">Tri des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63882-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="63882-103">Une opération de tri classe les éléments d’une séquence en fonction d’un ou plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="63882-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="63882-104">Le premier critère de tri effectue un tri principal sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="63882-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="63882-105">En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.</span><span class="sxs-lookup"><span data-stu-id="63882-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="63882-106">L’illustration suivante montre les résultats d’une opération de tri par ordre alphabétique sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="63882-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="63882-107">![Opération de tri de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="63882-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="63882-108">Les méthodes d’opérateur de requête standard qui trient les données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="63882-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63882-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="63882-109">Methods</span></span>  
  
|<span data-ttu-id="63882-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="63882-110">Method Name</span></span>|<span data-ttu-id="63882-111">Description</span><span class="sxs-lookup"><span data-stu-id="63882-111">Description</span></span>|<span data-ttu-id="63882-112">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63882-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="63882-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="63882-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="63882-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="63882-114">OrderBy</span></span>|<span data-ttu-id="63882-115">Trie les valeurs dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="63882-115">Sorts values in ascending order.</span></span>|`Order By`|<span data-ttu-id="63882-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="63882-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="63882-118">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="63882-118">OrderByDescending</span></span>|<span data-ttu-id="63882-119">Trie les valeurs dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="63882-119">Sorts values in descending order.</span></span>|`Order By … Descending`|<span data-ttu-id="63882-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="63882-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="63882-122">ThenBy</span><span class="sxs-lookup"><span data-stu-id="63882-122">ThenBy</span></span>|<span data-ttu-id="63882-123">Effectue un tri secondaire dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="63882-123">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<span data-ttu-id="63882-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="63882-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="63882-126">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="63882-126">ThenByDescending</span></span>|<span data-ttu-id="63882-127">Effectue un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="63882-127">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<span data-ttu-id="63882-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="63882-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="63882-130">Reverse</span><span class="sxs-lookup"><span data-stu-id="63882-130">Reverse</span></span>|<span data-ttu-id="63882-131">Inverse l’ordre des éléments dans une collection.</span><span class="sxs-lookup"><span data-stu-id="63882-131">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="63882-132">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="63882-132">Not applicable.</span></span>|<span data-ttu-id="63882-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="63882-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="63882-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="63882-135">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="63882-135">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="63882-136">Exemples de tri principal</span><span class="sxs-lookup"><span data-stu-id="63882-136">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="63882-137">Tri principal croissant</span><span class="sxs-lookup"><span data-stu-id="63882-137">Primary Ascending Sort</span></span>  
 <span data-ttu-id="63882-138">L’exemple suivant montre comment utiliser le `Order By` clause dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="63882-138">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="63882-139">Tri principal décroissant</span><span class="sxs-lookup"><span data-stu-id="63882-139">Primary Descending Sort</span></span>  
 <span data-ttu-id="63882-140">L’exemple suivant montre comment utiliser le `Order By Descending` clause dans une requête LINQ pour trier les chaînes par leur première lettre dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="63882-140">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="63882-141">Exemples de tri secondaire</span><span class="sxs-lookup"><span data-stu-id="63882-141">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="63882-142">Tri secondaire croissant</span><span class="sxs-lookup"><span data-stu-id="63882-142">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="63882-143">L’exemple suivant montre comment utiliser le `Order By` clause dans une requête LINQ pour effectuer un tri principal et secondaire des chaînes d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="63882-143">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="63882-144">Les chaînes sont triées par longueur puis en fonction selon la première lettre de la chaîne, à la fois dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="63882-144">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="63882-145">Tri secondaire décroissant</span><span class="sxs-lookup"><span data-stu-id="63882-145">Secondary Descending Sort</span></span>  
 <span data-ttu-id="63882-146">L’exemple suivant montre comment utiliser le `Order By Descending` clause dans une requête LINQ pour effectuer un tri principal, par ordre croissant et un tri secondaire, dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="63882-146">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="63882-147">Les chaînes sont triées par longueur puis en fonction selon la première lettre de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="63882-147">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a><span data-ttu-id="63882-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63882-148">See Also</span></span>  
 <span data-ttu-id="63882-149"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="63882-149"><xref:System.Linq></span></span>   
<span data-ttu-id="63882-150"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="63882-150"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="63882-151"> [Clause Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="63882-151"> [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="63882-152"> [Comment : trier les résultats de la requête](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="63882-152"> [How to: Sort Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="63882-153"> [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="63882-153"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
