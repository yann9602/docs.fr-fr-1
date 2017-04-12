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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8876e65e752e0b18404ec32aecdcad7805533840
ms.lasthandoff: 03/13/2017

---
# <a name="projection-operations-visual-basic"></a>Opérations de projection (Visual Basic)
La projection désigne l’opération de transformation d’un objet dans un nouveau formulaire qui se compose souvent uniquement des propriétés qui seront utilisées ensuite. À l'aide de la projection, vous pouvez créer un nouveau type qui est généré à partir de chaque objet. Vous pouvez projeter une propriété et effectuer une fonction mathématique sur celle-ci. Vous pouvez également projeter l’objet d’origine sans le modifier.  
  
 Les méthodes d’opérateur de requête standard qui effectuent la projection sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Sélectionner|Valeurs de projets qui sont basées sur une fonction de transformation.|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName>|  
|SelectMany|Projettent des séquences de valeurs qui sont basées sur une fonction de transformation, puis les aplatit en une seule séquence.|Utilisez plusieurs `From` clauses|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="select"></a>Sélectionner  
 L’exemple suivant utilise le `Select` clause pour projeter la première lettre de chaque chaîne dans une liste de chaînes.  
  
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
  
### <a name="selectmany"></a>SelectMany  
 L’exemple suivant utilise plusieurs `From` clauses pour projeter chaque mot à partir de chaque chaîne dans une liste de chaînes.  
  
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
  
## <a name="select-versus-selectmany"></a>Sélectionnez et SelectMany  
 Le travail des deux `Select()` et `SelectMany()` est de produire une valeur de résultat (ou valeurs) à partir des valeurs de la source. `Select()`génère une valeur de résultat pour chaque valeur source. Le résultat total est donc une collection qui a le même nombre d’éléments que la collection source. En revanche, `SelectMany()` génère un résultat global unique qui contient des sous-collections concaténées à partir de chaque valeur source. La fonction de transformation qui est passée comme argument de `SelectMany()` doit retourner une séquence énumérable de valeurs pour chaque valeur source. Ces séquences énumérables sont alors concaténées par `SelectMany()` pour créer une grande séquence.  
  
 Les deux illustrations suivantes montrent la différence conceptuelle entre les actions de ces deux méthodes. Dans chaque cas, supposons que la fonction de sélecteur (transformation) sélectionne le tableau de fleurs à partir de chaque valeur source.  
  
 Cette illustration montre comment `Select()` renvoie une collection qui a le même nombre d’éléments que la collection source.  
  
 ![Illustration conceptuelle de l’action Select()](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Cette illustration montre comment `SelectMany()` concatène la séquence intermédiaire de tableaux en une valeur de résultat final contient chaque valeur de chaque tableau intermédiaire.  
  
 ![Graphique montrant l’action de SelectMany(). ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>Exemple de code  
 L’exemple suivant compare le comportement de `Select()` et `SelectMany()`. Le code crée un « bouquet » de fleurs en prenant les deux premiers éléments de chaque liste de noms de fleur de la collection source. Dans cet exemple, la « valeur unique » que la fonction de transformation <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>utilise lui-même est une collection de valeurs.</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> Cela nécessite la supplémentaire `For Each` boucle énumère chaque chaîne dans chaque sous-séquence.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Clause SELECT](../../../../visual-basic/language-reference/queries/select-clause.md)   
 [Comment : combiner des données avec des jointures](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)   
 [Comment : remplir des Collections d’objets issues de plusieurs Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)   
 [Comment : retourner un résultat de requête LINQ comme un Type spécifique](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)   
 [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
