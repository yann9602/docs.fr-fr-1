---
title: "Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 541da47893217e2915a6b001d1141eaadfa9e9e8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a>Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)
L’exemple suivant montre comment trier les lignes de texte structuré, telles que les valeurs séparées par des virgules, par n’importe quel champ de la ligne. Le champ peut être spécifié de manière dynamique lors de l’exécution. Supposons que les champs de scores.csv représentent le numéro d’identification d’un étudiant, suivi d’une série de quatre examens.  
  
### <a name="to-create-a-file-that-contains-data"></a>Pour créer un fichier qui contient des données  
  
1.  Copier les données de scores.csv de la rubrique [Comment : joindre contenu à partir de différents fichiers (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) et l’enregistrer dans votre dossier de solution.  
  
## <a name="example"></a>Exemple  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 Cet exemple montre également comment retourner une variable de requête d’une fonction.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
