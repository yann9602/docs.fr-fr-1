---
title: "Opérations de projection (Visual Basic) | Documents Microsoft"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
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
ms.openlocfilehash: aac5cf69e6c3f4041a4302e8d606ca8dfddbc8a2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="a5e8d-102">Opérations de projection (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5e8d-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="a5e8d-103">La projection désigne l’opération de transformation d’un objet dans un nouveau formulaire qui se compose souvent uniquement des propriétés qui seront utilisées ensuite.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="a5e8d-104">À l'aide de la projection, vous pouvez créer un nouveau type qui est généré à partir de chaque objet.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="a5e8d-105">Vous pouvez projeter une propriété et effectuer une fonction mathématique sur celle-ci.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="a5e8d-106">Vous pouvez également projeter l’objet d’origine sans le modifier.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="a5e8d-107">Les méthodes d’opérateur de requête standard qui effectuent la projection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5e8d-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a5e8d-108">Methods</span></span>  
  
|<span data-ttu-id="a5e8d-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="a5e8d-109">Method Name</span></span>|<span data-ttu-id="a5e8d-110">Description</span><span class="sxs-lookup"><span data-stu-id="a5e8d-110">Description</span></span>|<span data-ttu-id="a5e8d-111">Syntaxe d’Expression de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5e8d-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a5e8d-112">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="a5e8d-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="a5e8d-113">Sélectionner</span><span class="sxs-lookup"><span data-stu-id="a5e8d-113">Select</span></span>|<span data-ttu-id="a5e8d-114">Valeurs de projets qui sont basées sur une fonction de transformation.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-114">Projects values that are based on a transform function.</span></span>|`Select`|<span data-ttu-id="a5e8d-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a5e8d-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="a5e8d-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a5e8d-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="a5e8d-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="a5e8d-117">SelectMany</span></span>|<span data-ttu-id="a5e8d-118">Projettent des séquences de valeurs qui sont basées sur une fonction de transformation, puis les aplatit en une seule séquence.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="a5e8d-119">Utilisez plusieurs `From` clauses</span><span class="sxs-lookup"><span data-stu-id="a5e8d-119">Use multiple `From` clauses</span></span>|<span data-ttu-id="a5e8d-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a5e8d-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="a5e8d-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a5e8d-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a5e8d-122">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="a5e8d-122">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="a5e8d-123">Sélectionner</span><span class="sxs-lookup"><span data-stu-id="a5e8d-123">Select</span></span>  
 <span data-ttu-id="a5e8d-124">L’exemple suivant utilise le `Select` clause pour projeter la première lettre de chaque chaîne dans une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-124">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a><span data-ttu-id="a5e8d-125">SelectMany</span><span class="sxs-lookup"><span data-stu-id="a5e8d-125">SelectMany</span></span>  
 <span data-ttu-id="a5e8d-126">L’exemple suivant utilise plusieurs `From` clauses pour projeter chaque mot à partir de chaque chaîne dans une liste de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-126">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="a5e8d-127">Sélectionnez et SelectMany</span><span class="sxs-lookup"><span data-stu-id="a5e8d-127">Select versus SelectMany</span></span>  
 <span data-ttu-id="a5e8d-128">Le travail des deux `Select()` et `SelectMany()` est de produire une valeur de résultat (ou valeurs) à partir des valeurs de la source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-128">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="a5e8d-129">`Select()`génère une valeur de résultat pour chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-129">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="a5e8d-130">Le résultat total est donc une collection qui a le même nombre d’éléments que la collection source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-130">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="a5e8d-131">En revanche, `SelectMany()` génère un résultat global unique qui contient des sous-collections concaténées à partir de chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-131">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="a5e8d-132">La fonction de transformation qui est passée comme argument de `SelectMany()` doit retourner une séquence énumérable de valeurs pour chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-132">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="a5e8d-133">Ces séquences énumérables sont alors concaténées par `SelectMany()` pour créer une grande séquence.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-133">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="a5e8d-134">Les deux illustrations suivantes montrent la différence conceptuelle entre les actions de ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-134">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="a5e8d-135">Dans chaque cas, supposons que la fonction de sélecteur (transformation) sélectionne le tableau de fleurs à partir de chaque valeur source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-135">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="a5e8d-136">Cette illustration montre comment `Select()` renvoie une collection qui a le même nombre d’éléments que la collection source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-136">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="a5e8d-137">![Illustration conceptuelle de l’action Select()](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="a5e8d-137">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="a5e8d-138">Cette illustration montre comment `SelectMany()` concatène la séquence intermédiaire de tableaux en une valeur de résultat final contient chaque valeur de chaque tableau intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-138">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="a5e8d-139">![Graphique montrant l’action de SelectMany(). ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="a5e8d-139">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="a5e8d-140">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="a5e8d-140">Code Example</span></span>  
 <span data-ttu-id="a5e8d-141">L’exemple suivant compare le comportement de `Select()` et `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-141">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="a5e8d-142">Le code crée un « bouquet » de fleurs en prenant les deux premiers éléments de chaque liste de noms de fleur de la collection source.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-142">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="a5e8d-143">Dans cet exemple, la « valeur unique » que la fonction de transformation <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>utilise lui-même est une collection de valeurs.</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29></span><span class="sxs-lookup"><span data-stu-id="a5e8d-143">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="a5e8d-144">Cela nécessite la supplémentaire `For Each` boucle énumère chaque chaîne dans chaque sous-séquence.</span><span class="sxs-lookup"><span data-stu-id="a5e8d-144">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5e8d-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5e8d-145">See Also</span></span>  
 <span data-ttu-id="a5e8d-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="a5e8d-146"><xref:System.Linq></span></span>   
<span data-ttu-id="a5e8d-147"> [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="a5e8d-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="a5e8d-148"> [Clause SELECT](../../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="a5e8d-148"> [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="a5e8d-149"> [Comment : combiner des données avec des jointures](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span><span class="sxs-lookup"><span data-stu-id="a5e8d-149"> [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span></span>  
<span data-ttu-id="a5e8d-150"> [Comment : remplir des Collections d’objets issues de plusieurs Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span><span class="sxs-lookup"><span data-stu-id="a5e8d-150"> [How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span></span>  
<span data-ttu-id="a5e8d-151"> [Comment : retourner un résultat de requête LINQ comme un Type spécifique](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span><span class="sxs-lookup"><span data-stu-id="a5e8d-151"> [How to: Return a LINQ Query Result as a Specific Type](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span></span>  
<span data-ttu-id="a5e8d-152"> [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="a5e8d-152"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
