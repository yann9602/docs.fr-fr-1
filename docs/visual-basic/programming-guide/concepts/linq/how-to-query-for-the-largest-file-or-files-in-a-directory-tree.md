---
title: "Comment : interroger le plus grand nombre ou les fichiers dans une arborescence de répertoires (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
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
ms.openlocfilehash: 055cbdd5a5903417ab382d390e1215f0319c0b5a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>Comment : interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (Visual Basic)
Cet exemple montre cinq requêtes liées à la taille du fichier en octets :  
  
-   Comment récupérer la taille en octets du plus grand fichier.  
  
-   Comment récupérer la taille en octets du fichier plus petit.  
  
-   Comment récupérer le <xref:System.IO.FileInfo>fichier maximale ou minimale d’objets à partir d’un ou plusieurs dossiers dans un dossier racine spécifié.</xref:System.IO.FileInfo>  
  
-   Comment récupérer une séquence, telles que les 10 fichiers les plus volumineux.  
  
-   Comment classer des fichiers par groupes selon leur taille en octets, en ignorant les fichiers qui sont inférieurs à une taille spécifiée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient cinq requêtes distinctes qui montrent comment interroger et regrouper des fichiers selon leur taille en octets. Vous pouvez facilement modifier ces exemples pour baser la requête sur une autre propriété de la <xref:System.IO.FileInfo>objet.</xref:System.IO.FileInfo>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 Pour retourner un ou plusieurs Terminer <xref:System.IO.FileInfo>d’objets, la requête doit tout d’abord examiner chacun d’eux dans les données source, puis les trier par la valeur de leur propriété Length.</xref:System.IO.FileInfo> Elle peut ensuite retourner l’unique ou la séquence avec les longueurs de plus grandes. Utilisez <xref:System.Linq.Enumerable.First%2A>pour renvoyer le premier élément dans une liste.</xref:System.Linq.Enumerable.First%2A> Utilisez <xref:System.Linq.Enumerable.Take%2A>pour renvoyer les n premiers éléments.</xref:System.Linq.Enumerable.Take%2A> Spécifier un ordre de tri décroissant pour placer les plus petits éléments au début de la liste.  
  
 La requête appelle une méthode distincte pour obtenir la taille du fichier en octets afin de consommer l’exception qui sera levée dans le cas où un fichier a été supprimé sur un autre thread dans la période de temps depuis la <xref:System.IO.FileInfo>objet a été créé dans l’appel à `GetFiles`.</xref:System.IO.FileInfo> Même la <xref:System.IO.FileInfo>objet a déjà été créé, l’exception peut se produire car un <xref:System.IO.FileInfo>objet essaiera d’actualiser son <xref:System.IO.FileInfo.Length%2A>propriété à l’aide de la taille la plus actuelle en octets de la première fois que la propriété est accessible.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> En plaçant cette opération dans un bloc try-catch à l’extérieur de la requête, vous respectez la règle consistant à éviter les opérations dans les requêtes qui peuvent provoquer des effets secondaires. En règle générale, précaution doit être prise lors de l’utilisation des exceptions, pour vous assurer qu’une application n’est pas conservée dans un état inconnu.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
