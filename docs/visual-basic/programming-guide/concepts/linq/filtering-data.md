---
title: "Filtrage des données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fa2d3b6c5b81f137ab3a81f9b18707bb2da91f6e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="b64a5-102">Filtrage des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b64a5-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="b64a5-103">Le filtrage fait référence à l’opération de restriction du jeu de résultats à contenir uniquement les éléments qui satisfont une condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b64a5-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="b64a5-104">Il est également appelé.</span><span class="sxs-lookup"><span data-stu-id="b64a5-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="b64a5-105">L’illustration suivante montre les résultats du filtrage d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="b64a5-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="b64a5-106">Le prédicat de l’opération de filtrage Spécifie que le caractère doit être « A ».</span><span class="sxs-lookup"><span data-stu-id="b64a5-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="b64a5-107">![Opération de filtrage de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="b64a5-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="b64a5-108">Les méthodes d’opérateur de requête standard qui effectuent une sélection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="b64a5-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b64a5-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b64a5-109">Methods</span></span>  
  
|<span data-ttu-id="b64a5-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="b64a5-110">Method Name</span></span>|<span data-ttu-id="b64a5-111">Description</span><span class="sxs-lookup"><span data-stu-id="b64a5-111">Description</span></span>|<span data-ttu-id="b64a5-112">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b64a5-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b64a5-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="b64a5-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b64a5-114">OfType</span><span class="sxs-lookup"><span data-stu-id="b64a5-114">OfType</span></span>|<span data-ttu-id="b64a5-115">Sélectionne des valeurs, en fonction de leur capacité à être casté en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b64a5-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="b64a5-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="b64a5-116">Not applicable.</span></span>|<span data-ttu-id="b64a5-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b64a5-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="b64a5-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b64a5-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="b64a5-119">Où</span><span class="sxs-lookup"><span data-stu-id="b64a5-119">Where</span></span>|<span data-ttu-id="b64a5-120">Sélectionne les valeurs qui sont basées sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="b64a5-120">Selects values that are based on a predicate function.</span></span>|`Where`|<span data-ttu-id="b64a5-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b64a5-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="b64a5-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b64a5-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b64a5-123">Exemple de syntaxe de requête Expression</span><span class="sxs-lookup"><span data-stu-id="b64a5-123">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b64a5-124">L’exemple suivant utilise le `Where` à filtrer dans un tableau les chaînes qui ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="b64a5-124">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a><span data-ttu-id="b64a5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b64a5-125">See Also</span></span>  
 <span data-ttu-id="b64a5-126"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="b64a5-126"><xref:System.Linq></span></span>   
<span data-ttu-id="b64a5-127"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="b64a5-127"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="b64a5-128"> [Où Clause](../../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="b64a5-128"> [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="b64a5-129"> [Comment : filtrer les résultats de la requête](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="b64a5-129"> [How to: Filter Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="b64a5-130"> [Comment : interroger les métadonnées d’un Assembly avec réflexion (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="b64a5-130"> [How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
<span data-ttu-id="b64a5-131"> [Comment : interroger des fichiers possédant un attribut spécifié ou un nom (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="b64a5-131"> [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
<span data-ttu-id="b64a5-132"> [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b64a5-132"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
