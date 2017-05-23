---
title: "Comment : interroger un ArrayList avec LINQ (Visual Basic) | Documents Microsoft"
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
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f48b06c23b1e28fccb953638954a8d9afefe574e
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>Comment : interroger un ArrayList avec LINQ (Visual Basic)
Lorsque vous utilisez LINQ pour requête non générique <xref:System.Collections.IEnumerable>collections telles que <xref:System.Collections.ArrayList>, vous devez déclarer explicitement le type de la variable de portée pour répercuter le type spécifique des objets dans la collection.</xref:System.Collections.ArrayList> </xref:System.Collections.IEnumerable> Par exemple, si vous avez un <xref:System.Collections.ArrayList>de `Student` objets, votre [à partir de la Clause](../../../../visual-basic/language-reference/queries/from-clause.md) doit ressembler à ceci :</xref:System.Collections.ArrayList>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 En spécifiant le type de la variable de portée, vous effectuez un cast de chaque élément de la <xref:System.Collections.ArrayList>à un `Student`.</xref:System.Collections.ArrayList>  
  
 L’utilisation d’une variable de portée explicitement typée dans une expression de requête équivaut à appeler le <xref:System.Linq.Enumerable.Cast%2A>méthode.</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A>lève une exception si le cast spécifié ne peut pas être effectué.</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A>et <xref:System.Linq.Enumerable.OfType%2A>sont les deux méthodes d’opérateur de requête Standard qui opèrent sur non générique <xref:System.Collections.IEnumerable>types.</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable.OfType%2A></xref:System.Linq.Enumerable.Cast%2A> Dans Visual Basic, vous devez appeler explicitement la <xref:System.Linq.Enumerable.Cast%2A>méthode sur la source de données pour garantir un type de variable de plage spécifique.</xref:System.Linq.Enumerable.Cast%2A> Pour plus d’informations, consultez[relations des types dans des opérations de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une requête simple sur un <xref:System.Collections.ArrayList>.</xref:System.Collections.ArrayList> Notez que cet exemple utilise des initialiseurs d’objets lorsque le code appelle la <xref:System.Collections.ArrayList.Add%2A>(méthode), mais cela n’est pas une obligation.</xref:System.Collections.ArrayList.Add%2A>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

