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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 95c5197b2cb66745201ceac89b78fe67b95ecb75
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="f91d2-102">Comment : interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f91d2-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="f91d2-103">Cet exemple montre cinq requêtes liées à la taille du fichier en octets :</span><span class="sxs-lookup"><span data-stu-id="f91d2-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="f91d2-104">Comment récupérer la taille en octets du plus grand fichier.</span><span class="sxs-lookup"><span data-stu-id="f91d2-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="f91d2-105">Comment récupérer la taille en octets du fichier plus petit.</span><span class="sxs-lookup"><span data-stu-id="f91d2-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="f91d2-106">Comment récupérer le <xref:System.IO.FileInfo>fichier maximale ou minimale d’objets à partir d’un ou plusieurs dossiers dans un dossier racine spécifié.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="f91d2-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="f91d2-107">Comment récupérer une séquence, telles que les 10 fichiers les plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="f91d2-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="f91d2-108">Comment classer des fichiers par groupes selon leur taille en octets, en ignorant les fichiers qui sont inférieurs à une taille spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f91d2-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f91d2-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="f91d2-109">Example</span></span>  
 <span data-ttu-id="f91d2-110">L’exemple suivant contient cinq requêtes distinctes qui montrent comment interroger et regrouper des fichiers selon leur taille en octets.</span><span class="sxs-lookup"><span data-stu-id="f91d2-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="f91d2-111">Vous pouvez facilement modifier ces exemples pour baser la requête sur une autre propriété de la <xref:System.IO.FileInfo>objet.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="f91d2-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
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
  
 <span data-ttu-id="f91d2-112">Pour retourner un ou plusieurs Terminer <xref:System.IO.FileInfo>d’objets, la requête doit tout d’abord examiner chacun d’eux dans les données source, puis les trier par la valeur de leur propriété Length.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="f91d2-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="f91d2-113">Elle peut ensuite retourner l’unique ou la séquence avec les longueurs de plus grandes.</span><span class="sxs-lookup"><span data-stu-id="f91d2-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="f91d2-114">Utilisez <xref:System.Linq.Enumerable.First%2A>pour renvoyer le premier élément dans une liste.</xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="f91d2-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="f91d2-115">Utilisez <xref:System.Linq.Enumerable.Take%2A>pour renvoyer les n premiers éléments.</xref:System.Linq.Enumerable.Take%2A></span><span class="sxs-lookup"><span data-stu-id="f91d2-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="f91d2-116">Spécifier un ordre de tri décroissant pour placer les plus petits éléments au début de la liste.</span><span class="sxs-lookup"><span data-stu-id="f91d2-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="f91d2-117">La requête appelle une méthode distincte pour obtenir la taille du fichier en octets afin de consommer l’exception qui sera levée dans le cas où un fichier a été supprimé sur un autre thread dans la période de temps depuis la <xref:System.IO.FileInfo>objet a été créé dans l’appel à `GetFiles`.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="f91d2-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="f91d2-118">Même la <xref:System.IO.FileInfo>objet a déjà été créé, l’exception peut se produire car un <xref:System.IO.FileInfo>objet essaiera d’actualiser son <xref:System.IO.FileInfo.Length%2A>propriété à l’aide de la taille la plus actuelle en octets de la première fois que la propriété est accessible.</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="f91d2-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="f91d2-119">En plaçant cette opération dans un bloc try-catch à l’extérieur de la requête, vous respectez la règle consistant à éviter les opérations dans les requêtes qui peuvent provoquer des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="f91d2-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="f91d2-120">En règle générale, précaution doit être prise lors de l’utilisation des exceptions, pour vous assurer qu’une application n’est pas conservée dans un état inconnu.</span><span class="sxs-lookup"><span data-stu-id="f91d2-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f91d2-121">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f91d2-121">Compiling the Code</span></span>  
 <span data-ttu-id="f91d2-122">Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="f91d2-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91d2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f91d2-123">See Also</span></span>  
 <span data-ttu-id="f91d2-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="f91d2-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="f91d2-125"> [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="f91d2-125"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
