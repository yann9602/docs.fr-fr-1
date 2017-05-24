---
title: "Guide pratique pour interroger des caractères dans une chaîne (LINQ) (C#) | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 86c763d8f31a7021605d82ecab0664a290934e07
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Guide pratique pour interroger des caractères dans une chaîne (LINQ) (C#)
Étant donné que la classe <xref:System.String> implémente l’interface générique <xref:System.Collections.Generic.IEnumerable%601>, toute chaîne peut être interrogée en tant que séquence de caractères. Toutefois, ceci n’est pas une utilisation courante de LINQ. Pour les opérations de critères spéciaux complexes, utilisez la classe <xref:System.Text.RegularExpressions.Regex>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient. Notez que la requête est « réutilisée » après sa première exécution. Ceci est possible car la requête proprement dite ne stocke pas de résultats réels.  
  
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
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créez un projet qui cible le .NET Framework version 3.5 ou version ultérieure, avec une référence à System.Core.dll et des directives `using` pour les espaces de noms System.Linq et System.IO.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ et chaînes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)   
 [Guide pratique pour combiner des requêtes LINQ avec des expressions régulières (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
