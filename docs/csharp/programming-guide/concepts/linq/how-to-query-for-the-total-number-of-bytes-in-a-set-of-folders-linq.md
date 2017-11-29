---
title: "Guide pratique pour rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 342ab9e23b733051679483172a1da6027f6e6f3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="8b40a-102">Guide pratique pour rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b40a-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="8b40a-103">Cet exemple montre comment récupérer le nombre total d’octets utilisés par tous les fichiers d’un dossier spécifié, ainsi que par tous ses sous-dossiers.</span><span class="sxs-lookup"><span data-stu-id="8b40a-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b40a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b40a-104">Example</span></span>  
 <span data-ttu-id="8b40a-105">La méthode <xref:System.Linq.Enumerable.Sum%2A> ajoute les valeurs de tous les éléments sélectionnés dans la clause `select`.</span><span class="sxs-lookup"><span data-stu-id="8b40a-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="8b40a-106">Vous pouvez facilement modifier cette requête pour récupérer le fichier le plus grand ou le plus petit de l’arborescence du répertoire spécifié en appelant la méthode <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> plutôt que <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b40a-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="8b40a-107">Si vous devez seulement compter le nombre d’octets dans une arborescence de répertoires spécifiée, pour être plus efficace, ne créez pas de requête LINQ, car cela induit la surcharge liée à la création de la collection de listes comme source de données.</span><span class="sxs-lookup"><span data-stu-id="8b40a-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="8b40a-108">Plus la requête est complexe, plus l’approche LINQ devient utile. C’est également valable lorsque vous devez exécuter plusieurs requêtes sur une même source de données.</span><span class="sxs-lookup"><span data-stu-id="8b40a-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="8b40a-109">La requête appelle une méthode distincte pour obtenir la longueur du fichier.</span><span class="sxs-lookup"><span data-stu-id="8b40a-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="8b40a-110">Elle procède ainsi pour utiliser l’exception qui sera éventuellement levée si le fichier a été supprimé sur un autre thread après la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="8b40a-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="8b40a-111">Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> avec la longueur la plus récente lors du premier accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="8b40a-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="8b40a-112">En plaçant cette opération dans un bloc try-catch en dehors de la requête, le code respecte la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="8b40a-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="8b40a-113">En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.</span><span class="sxs-lookup"><span data-stu-id="8b40a-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b40a-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8b40a-114">Compiling the Code</span></span>  
 <span data-ttu-id="8b40a-115">Créez un projet qui cible le .NET Framework version 3.5 ou ultérieure, avec une référence à System.Core.dll et des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="8b40a-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b40a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b40a-116">See Also</span></span>  
 [<span data-ttu-id="8b40a-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="8b40a-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="8b40a-118">LINQ et répertoires de fichiers (C#)</span><span class="sxs-lookup"><span data-stu-id="8b40a-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
