---
title: "Guide pratique pour interroger des caractères dans une chaîne (LINQ) (C#)"
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
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e78ad4aa493a7f58c43e77772138900e2b20b18a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="786dd-102">Guide pratique pour interroger des caractères dans une chaîne (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="786dd-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="786dd-103">La classe <xref:System.String> implémente l’interface <xref:System.Collections.Generic.IEnumerable%601> générique. De ce fait, il est possible d’interroger n’importe quelle chaîne comme une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="786dd-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="786dd-104">Toutefois, ceci n’est pas une utilisation courante de LINQ.</span><span class="sxs-lookup"><span data-stu-id="786dd-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="786dd-105">Pour les opérations de critères spéciaux complexes, utilisez la classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="786dd-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="786dd-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="786dd-106">Example</span></span>  
 <span data-ttu-id="786dd-107">L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="786dd-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="786dd-108">Notez que la requête est « réutilisée » après sa première exécution.</span><span class="sxs-lookup"><span data-stu-id="786dd-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="786dd-109">Ceci est possible car la requête proprement dite ne stocke pas de résultats réels.</span><span class="sxs-lookup"><span data-stu-id="786dd-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="786dd-110">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="786dd-110">Compiling the Code</span></span>  
 <span data-ttu-id="786dd-111">Créez un projet qui cible le .NET Framework version 3.5 ou version ultérieure, avec une référence à System.Core.dll et des directives `using` pour les espaces de noms System.Linq et System.IO.</span><span class="sxs-lookup"><span data-stu-id="786dd-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786dd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="786dd-112">See Also</span></span>  
 <span data-ttu-id="786dd-113">[LINQ et chaînes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="786dd-113">[LINQ and Strings (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
 [<span data-ttu-id="786dd-114">Guide pratique pour combiner des requêtes LINQ avec des expressions régulières (C#)</span><span class="sxs-lookup"><span data-stu-id="786dd-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)

