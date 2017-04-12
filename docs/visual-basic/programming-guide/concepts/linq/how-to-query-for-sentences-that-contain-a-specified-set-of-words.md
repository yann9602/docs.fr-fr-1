---
title: "Comment : rechercher des phrases qui contiennent un jeu spécifié de mots (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
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
ms.openlocfilehash: 31561d586c9c05f502002efdfc455acb55159fed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>Comment : rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (Visual Basic)
Cet exemple montre comment rechercher des phrases dans un fichier texte contenant des correspondances pour chaque ensemble de mots spécifié. Bien que le tableau des termes de recherche est codé en dur dans cet exemple, il pourrait également être rempli dynamiquement lors de l’exécution. Dans cet exemple, la requête retourne les phrases qui contiennent les mots « Avant », « données » et « intégré ».  
  
## <a name="example"></a>Exemple  
  
```vb  
Class FindSentences  
  
    Shared Sub Main()  
        Dim text As String = "Historically, the world of data and the world of objects " &   
        "have not been well integrated. Programmers work in C# or Visual Basic " &   
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &   
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &   
        "are tables, columns, rows, nodes, and separate languages for dealing with " &   
        "them. Data types often require translation between the two worlds; there are " &   
        "different standard functions. Because the object world has no notion of query, a " &   
        "query can only be represented as a string without compile-time type checking or " &   
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &   
        "objects in memory is often tedious and error-prone."  
  
        ' Split the text block into an array of sentences.  
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})  
  
        ' Define the search terms. This list could also be dynamically populated at runtime  
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}  
  
        ' Find sentences that contain all the terms in the wordsToMatch array  
        ' Note that the number of terms to match is not specified at compile time  
        Dim sentenceQuery = From sentence In sentences   
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                   StringSplitOptions.RemoveEmptyEntries)   
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()   
                            Select sentence  
  
        ' Execute the query  
        For Each str As String In sentenceQuery  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Class  
' Output:  
' Historically, the world of data and the world of objects have not been well integrated  
```  
  
 La requête fonctionne en fractionnant d’abord le texte en phrases, puis en fractionnant les phrases en un tableau de chaînes qui contient chaque mot. Pour chacun de ces tableaux, la <xref:System.Linq.Enumerable.Distinct%2A>méthode supprime tous les doublons, puis la requête effectue une <xref:System.Linq.Enumerable.Intersect%2A>opération sur le tableau de mots et le `wordsToMatch` tableau.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Distinct%2A> Si le nombre de l’intersection est identique à celui de le `wordsToMatch` tableau de tous les mots ont été trouvés dans les mots et la phrase d’origine est retournée.  
  
 Dans l’appel à <xref:System.String.Split%2A>, les signes de ponctuation sont utilisés comme séparateurs pour les supprimer de la chaîne.</xref:System.String.Split%2A> Si vous n’avez pas, par exemple, vous pourriez avoir une chaîne « Toujours », qui ne renverrait pas « Toujours » dans le `wordsToMatch` tableau. Vous devrez peut-être utiliser des séparateurs supplémentaires, selon les types de signes de ponctuation trouvés dans le texte source.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
