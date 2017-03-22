---
title: "Comment : rechercher le nombre Total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 668a8a4d89f7b81c3aef9b4e1a46ad749c4a8341
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>Comment : rechercher le nombre Total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)
Cet exemple montre comment récupérer le nombre total d’octets utilisés par tous les fichiers dans un dossier spécifié et tous ses sous-dossiers.  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Linq.Enumerable.Sum%2A>méthode ajoute les valeurs de tous les éléments sélectionnés dans le `select` clause.</xref:System.Linq.Enumerable.Sum%2A> Vous pouvez facilement modifier cette requête pour récupérer le fichier plus grand ou plus petit dans l’arborescence de répertoires spécifiée en appelant <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A>méthode au lieu de <xref:System.Linq.Enumerable.Sum%2A>.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Max%2A> ou</xref:System.Linq.Enumerable.Min%2A>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Si vous n’avez compter le nombre d’octets dans une arborescence de répertoires spécifiée, procéder plus efficacement sans création d’une requête LINQ, ce qui induit une surcharge de la création de la collection de listes comme source de données. L’utilité de l’approche LINQ augmente lorsque la requête devient plus complexe, ou lorsque vous devez exécuter plusieurs requêtes sur la même source de données.  
  
 La requête appelle une méthode distincte pour obtenir la longueur du fichier. Il effectue cette opération pour utiliser l’exception potentielle qui sera levée si le fichier a été supprimé sur un autre thread après la <xref:System.IO.FileInfo>objet a été créé dans l’appel à `GetFiles`.</xref:System.IO.FileInfo> Bien que le <xref:System.IO.FileInfo>objet a déjà été créé, l’exception peut se produire car un <xref:System.IO.FileInfo>objet tente d’actualiser son <xref:System.IO.FileInfo.Length%2A>propriété avec la longueur actuelle plus la première fois que la propriété est accessible.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> En plaçant cette opération dans un bloc try-catch à l’extérieur de la requête, le code suit la règle consistant à éviter les opérations dans les requêtes qui peuvent provoquer des effets secondaires. En règle générale, précaution doit être prise lors de l’utilisation des exceptions afin de vous assurer qu’une application n’est pas conservée dans un état inconnu.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
