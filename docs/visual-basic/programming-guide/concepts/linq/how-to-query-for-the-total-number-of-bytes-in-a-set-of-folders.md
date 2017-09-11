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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bda25acd3065898eeb61dce83d46d7526e825add
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="6c99e-102">Comment : rechercher le nombre Total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c99e-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="6c99e-103">Cet exemple montre comment récupérer le nombre total d’octets utilisés par tous les fichiers dans un dossier spécifié et tous ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="6c99e-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c99e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c99e-104">Example</span></span>  
 <span data-ttu-id="6c99e-105">Le <xref:System.Linq.Enumerable.Sum%2A>méthode ajoute les valeurs de tous les éléments sélectionnés dans le `select` clause.</xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="6c99e-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="6c99e-106">Vous pouvez facilement modifier cette requête pour récupérer le fichier plus grand ou plus petit dans l’arborescence de répertoires spécifiée en appelant <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A>méthode au lieu de <xref:System.Linq.Enumerable.Sum%2A>.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Max%2A> ou</xref:System.Linq.Enumerable.Min%2A></span><span class="sxs-lookup"><span data-stu-id="6c99e-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="6c99e-107">Si vous n’avez compter le nombre d’octets dans une arborescence de répertoires spécifiée, procéder plus efficacement sans création d’une requête LINQ, ce qui induit une surcharge de la création de la collection de listes comme source de données.</span><span class="sxs-lookup"><span data-stu-id="6c99e-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="6c99e-108">L’utilité de l’approche LINQ augmente lorsque la requête devient plus complexe, ou lorsque vous devez exécuter plusieurs requêtes sur la même source de données.</span><span class="sxs-lookup"><span data-stu-id="6c99e-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="6c99e-109">La requête appelle une méthode distincte pour obtenir la longueur du fichier.</span><span class="sxs-lookup"><span data-stu-id="6c99e-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="6c99e-110">Il effectue cette opération pour utiliser l’exception potentielle qui sera levée si le fichier a été supprimé sur un autre thread après la <xref:System.IO.FileInfo>objet a été créé dans l’appel à `GetFiles`.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="6c99e-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="6c99e-111">Bien que le <xref:System.IO.FileInfo>objet a déjà été créé, l’exception peut se produire car un <xref:System.IO.FileInfo>objet tente d’actualiser son <xref:System.IO.FileInfo.Length%2A>propriété avec la longueur actuelle plus la première fois que la propriété est accessible.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="6c99e-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="6c99e-112">En plaçant cette opération dans un bloc try-catch à l’extérieur de la requête, le code suit la règle consistant à éviter les opérations dans les requêtes qui peuvent provoquer des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="6c99e-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="6c99e-113">En règle générale, précaution doit être prise lors de l’utilisation des exceptions afin de vous assurer qu’une application n’est pas conservée dans un état inconnu.</span><span class="sxs-lookup"><span data-stu-id="6c99e-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c99e-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6c99e-114">Compiling the Code</span></span>  
 <span data-ttu-id="6c99e-115">Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="6c99e-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c99e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c99e-116">See Also</span></span>  
 <span data-ttu-id="6c99e-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="6c99e-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="6c99e-118"> [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="6c99e-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
