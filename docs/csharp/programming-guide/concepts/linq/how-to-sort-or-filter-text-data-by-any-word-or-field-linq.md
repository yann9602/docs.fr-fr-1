---
title: "Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ccc48745918081663317e746953be6e0f09cdd8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="1f6b3-102">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1f6b3-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>
<span data-ttu-id="1f6b3-103">L’exemple suivant montre comment trier les lignes d’un texte structuré, telles que des valeurs séparées par des virgules, à l’aide d’un champ de la ligne.</span><span class="sxs-lookup"><span data-stu-id="1f6b3-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="1f6b3-104">Le champ peut être spécifié de manière dynamique lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1f6b3-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="1f6b3-105">Supposons que les champs du fichier scores.csv correspondent au numéro d’identification d’un étudiant, suivi d’une série de quatre notes d’examen.</span><span class="sxs-lookup"><span data-stu-id="1f6b3-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="1f6b3-106">Pour créer un fichier contenant des données</span><span class="sxs-lookup"><span data-stu-id="1f6b3-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="1f6b3-107">Copiez les données du fichier scores.csv disponible dans la rubrique [Guide pratique pour joindre du contenu issu de fichiers non similaires (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md), puis enregistrez-les dans le dossier de votre solution.</span><span class="sxs-lookup"><span data-stu-id="1f6b3-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f6b3-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f6b3-108">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="1f6b3-109">Cet exemple montre également comment retourner une variable de requête à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="1f6b3-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f6b3-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="1f6b3-110">Compiling the Code</span></span>  
 <span data-ttu-id="1f6b3-111">Créez un projet qui cible le .NET Framework version 3.5 ou version ultérieure, avec une référence à System.Core.dll et des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="1f6b3-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6b3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f6b3-112">See Also</span></span>  
 [<span data-ttu-id="1f6b3-113">LINQ et chaînes (C#)</span><span class="sxs-lookup"><span data-stu-id="1f6b3-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
