---
title: "Regroupement de données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
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
ms.openlocfilehash: ce4e8f924f91eed451d3b1a02cd0bcff75589537
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="131b2-102">Regroupement de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="131b2-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="131b2-103">Le regroupement consiste à placer des données dans des groupes afin que les éléments de chaque groupe partagent un attribut commun.</span><span class="sxs-lookup"><span data-stu-id="131b2-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="131b2-104">L’illustration suivante montre les résultats du regroupement d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="131b2-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="131b2-105">La clé pour chaque groupe est le caractère.</span><span class="sxs-lookup"><span data-stu-id="131b2-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="131b2-106">![Opérations de regroupement LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="131b2-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="131b2-107">Les méthodes d’opérateur de requête standard qui regroupent des éléments de données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="131b2-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="131b2-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="131b2-108">Methods</span></span>  
  
|<span data-ttu-id="131b2-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="131b2-109">Method Name</span></span>|<span data-ttu-id="131b2-110">Description</span><span class="sxs-lookup"><span data-stu-id="131b2-110">Description</span></span>|<span data-ttu-id="131b2-111">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="131b2-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="131b2-112">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="131b2-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="131b2-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="131b2-113">GroupBy</span></span>|<span data-ttu-id="131b2-114">Regroupe les éléments qui partagent un attribut commun.</span><span class="sxs-lookup"><span data-stu-id="131b2-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="131b2-115">Chaque groupe est représenté par un <xref:System.Linq.IGrouping%602>objet.</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="131b2-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<span data-ttu-id="131b2-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="131b2-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="131b2-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="131b2-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="131b2-118">ToLookup</span><span class="sxs-lookup"><span data-stu-id="131b2-118">ToLookup</span></span>|<span data-ttu-id="131b2-119">Insère des éléments dans un <xref:System.Linq.Lookup%602>(un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélection de clé.</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="131b2-119">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="131b2-120">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="131b2-120">Not applicable.</span></span>|<span data-ttu-id="131b2-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="131b2-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="131b2-122">Exemple de syntaxe de requête Expression</span><span class="sxs-lookup"><span data-stu-id="131b2-122">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="131b2-123">Le code suivant exemple utilise le `Group By` clause pour regrouper des entiers dans une liste selon qu’ils sont pairs ou impairs.</span><span class="sxs-lookup"><span data-stu-id="131b2-123">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="131b2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="131b2-124">See Also</span></span>  
 <span data-ttu-id="131b2-125"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="131b2-125"><xref:System.Linq></span></span>   
<span data-ttu-id="131b2-126"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="131b2-126"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="131b2-127"> [GROUP BY, Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="131b2-127"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span></span>  
<span data-ttu-id="131b2-128"> [Comment : regrouper des fichiers par Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="131b2-128"> [How to: Group Files by Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
<span data-ttu-id="131b2-129"> [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="131b2-129"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
