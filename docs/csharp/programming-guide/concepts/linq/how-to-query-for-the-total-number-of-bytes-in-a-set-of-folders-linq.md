---
title: "Guide pratique pour rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7eabb1b04a708e0b6f443552cdb07540b4d970dc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a>Guide pratique pour rechercher le nombre total d’octets dans un ensemble de dossiers (LINQ) (C#)
Cet exemple montre comment récupérer le nombre total d’octets utilisés par tous les fichiers d’un dossier spécifié, ainsi que par tous ses sous-dossiers.  
  
## <a name="example"></a>Exemple  
 La méthode <xref:System.Linq.Enumerable.Sum%2A> ajoute les valeurs de tous les éléments sélectionnés dans la clause `select`. Vous pouvez facilement modifier cette requête pour récupérer le fichier le plus grand ou le plus petit de l’arborescence du répertoire spécifié en appelant la méthode <xref:System.Linq.Enumerable.Min%2A> ou <xref:System.Linq.Enumerable.Max%2A> plutôt que <xref:System.Linq.Enumerable.Sum%2A>.  
  
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
  
 Si vous devez seulement compter le nombre d’octets dans une arborescence de répertoires spécifiée, pour être plus efficace, ne créez pas de requête LINQ, car cela induit la surcharge liée à la création de la collection de listes comme source de données. Plus la requête est complexe, plus l’approche LINQ devient utile. C’est également valable lorsque vous devez exécuter plusieurs requêtes sur une même source de données.  
  
 La requête appelle une méthode distincte pour obtenir la longueur du fichier. Elle procède ainsi pour utiliser l’exception qui sera éventuellement levée si le fichier a été supprimé sur un autre thread après la création de l’objet <xref:System.IO.FileInfo> dans l’appel à `GetFiles`. Même si l’objet <xref:System.IO.FileInfo> a déjà été créé, l’exception peut être levée, car un objet <xref:System.IO.FileInfo> essaiera d’actualiser sa propriété <xref:System.IO.FileInfo.Length%2A> avec la longueur la plus récente lors du premier accès à la propriété. En plaçant cette opération dans un bloc try-catch en dehors de la requête, le code respecte la règle qui consiste à éviter les opérations dans les requêtes qui peuvent avoir des effets secondaires. En règle générale, il faut faire très attention lors de l’utilisation d’exceptions et s’assurer que l’application ne reste pas dans un état inconnu.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créez un projet qui cible le .NET Framework version 3.5 ou ultérieure, avec une référence à System.Core.dll et des directives `using` pour les espaces de noms System.Linq et System.IO.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ et répertoires de fichiers (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)

