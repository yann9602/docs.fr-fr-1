---
title: "Conversion des Types de données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
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
ms.openlocfilehash: 948779e1648291b00a68bfd83d57750d48a9a6d8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="converting-data-types-visual-basic"></a><span data-ttu-id="160e6-102">Conversion des Types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="160e6-102">Converting Data Types (Visual Basic)</span></span>
<span data-ttu-id="160e6-103">Méthodes de conversion modifient le type d’objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="160e6-103">Conversion methods change the type of input objects.</span></span>  
  
 <span data-ttu-id="160e6-104">Les opérations de conversion dans les requêtes LINQ sont utiles dans une variété d’applications.</span><span class="sxs-lookup"><span data-stu-id="160e6-104">Conversion operations in LINQ queries are useful in a variety of applications.</span></span> <span data-ttu-id="160e6-105">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="160e6-105">Following are some examples:</span></span>  
  
-   <span data-ttu-id="160e6-106">Le <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>méthode peut être utilisée pour masquer l’implémentation personnalisée d’un type d’opérateur de requête standard.</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-106">The <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> method can be used to hide a type's custom implementation of a standard query operator.</span></span>  
  
-   <span data-ttu-id="160e6-107">Le <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>méthode peut être utilisée pour activer des collections non paramétrées pour l’interrogation LINQ.</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-107">The <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> method can be used to enable non-parameterized collections for LINQ querying.</span></span>  
  
-   <span data-ttu-id="160e6-108">Le <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>méthodes peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu'à ce que la requête est énumérée.</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-108">The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, and <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> methods can be used to force immediate query execution instead of deferring it until the query is enumerated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="160e6-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="160e6-109">Methods</span></span>  
 <span data-ttu-id="160e6-110">Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de type de données.</span><span class="sxs-lookup"><span data-stu-id="160e6-110">The following table lists the standard query operator methods that perform data-type conversions.</span></span>  
  
 <span data-ttu-id="160e6-111">Les méthodes de conversion de cette table dont le nom commence par « As » modifient le type statique de la collection source, mais ne l’énumèrent pas.</span><span class="sxs-lookup"><span data-stu-id="160e6-111">The conversion methods in this table whose names start with "As" change the static type of the source collection but do not enumerate it.</span></span> <span data-ttu-id="160e6-112">Les méthodes qui commencent par « To » énumèrent la collection source et placer les éléments dans la collection correspondante type.</span><span class="sxs-lookup"><span data-stu-id="160e6-112">The methods whose names start with "To" enumerate the source collection and put the items into the corresponding collection type.</span></span>  
  
|<span data-ttu-id="160e6-113">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="160e6-113">Method Name</span></span>|<span data-ttu-id="160e6-114">Description</span><span class="sxs-lookup"><span data-stu-id="160e6-114">Description</span></span>|<span data-ttu-id="160e6-115">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="160e6-115">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="160e6-116">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="160e6-116">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="160e6-117">AsEnumerable</span><span class="sxs-lookup"><span data-stu-id="160e6-117">AsEnumerable</span></span>|<span data-ttu-id="160e6-118">Retourne l’entrée typée en tant que <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="160e6-118">Returns the input typed as <xref:System.Collections.Generic.IEnumerable%601>.</span></span>|<span data-ttu-id="160e6-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-119">Not applicable.</span></span>|<span data-ttu-id="160e6-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-120"><xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-121">AsQueryable</span><span class="sxs-lookup"><span data-stu-id="160e6-121">AsQueryable</span></span>|<span data-ttu-id="160e6-122">Convertit un (générique) <xref:System.Collections.IEnumerable> <xref:System.Linq.IQueryable>.</xref:System.Linq.IQueryable> (générique)</xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="160e6-122">Converts a (generic) <xref:System.Collections.IEnumerable> to a (generic) <xref:System.Linq.IQueryable>.</span></span>|<span data-ttu-id="160e6-123">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-123">Not applicable.</span></span>|<span data-ttu-id="160e6-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-124"><xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-125">Cast</span><span class="sxs-lookup"><span data-stu-id="160e6-125">Cast</span></span>|<span data-ttu-id="160e6-126">Convertit les éléments d’une collection en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="160e6-126">Casts the elements of a collection to a specified type.</span></span>|`From … As …`|<span data-ttu-id="160e6-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-127"><xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="160e6-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-128"><xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-129">OfType</span><span class="sxs-lookup"><span data-stu-id="160e6-129">OfType</span></span>|<span data-ttu-id="160e6-130">Filtre les valeurs, en fonction de leur capacité à être casté en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="160e6-130">Filters values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="160e6-131">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-131">Not applicable.</span></span>|<span data-ttu-id="160e6-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-132"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="160e6-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-133"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-134">ToArray</span><span class="sxs-lookup"><span data-stu-id="160e6-134">ToArray</span></span>|<span data-ttu-id="160e6-135">Convertit une collection vers un tableau.</span><span class="sxs-lookup"><span data-stu-id="160e6-135">Converts a collection to an array.</span></span> <span data-ttu-id="160e6-136">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="160e6-136">This method forces query execution.</span></span>|<span data-ttu-id="160e6-137">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-137">Not applicable.</span></span>|<span data-ttu-id="160e6-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-138"><xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-139">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="160e6-139">ToDictionary</span></span>|<span data-ttu-id="160e6-140">Met des éléments dans un <xref:System.Collections.Generic.Dictionary%602>basé sur une fonction de sélection de clé.</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="160e6-140">Puts elements into a <xref:System.Collections.Generic.Dictionary%602> based on a key selector function.</span></span> <span data-ttu-id="160e6-141">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="160e6-141">This method forces query execution.</span></span>|<span data-ttu-id="160e6-142">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-142">Not applicable.</span></span>|<span data-ttu-id="160e6-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-143"><xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-144">ToList</span><span class="sxs-lookup"><span data-stu-id="160e6-144">ToList</span></span>|<span data-ttu-id="160e6-145">Convertit une collection en un <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="160e6-145">Converts a collection to a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="160e6-146">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="160e6-146">This method forces query execution.</span></span>|<span data-ttu-id="160e6-147">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-147">Not applicable.</span></span>|<span data-ttu-id="160e6-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-148"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="160e6-149">ToLookup</span><span class="sxs-lookup"><span data-stu-id="160e6-149">ToLookup</span></span>|<span data-ttu-id="160e6-150">Met des éléments dans un <xref:System.Linq.Lookup%602>(un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélection de clé.</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="160e6-150">Puts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span> <span data-ttu-id="160e6-151">Cette méthode force l’exécution de la requête.</span><span class="sxs-lookup"><span data-stu-id="160e6-151">This method forces query execution.</span></span>|<span data-ttu-id="160e6-152">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="160e6-152">Not applicable.</span></span>|<span data-ttu-id="160e6-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="160e6-153"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="160e6-154">Exemple de syntaxe de requête Expression</span><span class="sxs-lookup"><span data-stu-id="160e6-154">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="160e6-155">Le code suivant exemple utilise le `From As` clause pour convertir un type en un sous-type avant d’accéder à un membre qui est uniquement disponible sur le sous-type.</span><span class="sxs-lookup"><span data-stu-id="160e6-155">The following code example uses the `From As` clause to cast a type to a subtype before accessing a member that is available only on the subtype.</span></span>  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="160e6-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="160e6-156">See Also</span></span>  
 <span data-ttu-id="160e6-157"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="160e6-157"><xref:System.Linq></span></span>   
<span data-ttu-id="160e6-158"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="160e6-158"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="160e6-159"> [La Clause FROM](../../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="160e6-159"> [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="160e6-160"> [Comment : interroger un ArrayList avec LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="160e6-160"> [How to: Query an ArrayList with LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)</span></span>
