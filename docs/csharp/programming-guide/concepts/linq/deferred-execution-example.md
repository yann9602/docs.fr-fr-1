---
title: "Exemple d’exécution différée (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b902c58f801a6e157a971335895670e8a8bf2181
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="deferred-execution-example-c"></a>Exemple d’exécution différée (C#)
Cette rubrique montre comment l'exécution et l'évaluation différées affectent l'exécution de vos requêtes LINQ to XML.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'ordre d'exécution lors de l'utilisation d'une méthode d'extension qui utilise l'exécution différée. L'exemple déclare un tableau de trois chaînes. Il itère ensuite au sein de la collection retournée par `ConvertCollectionToUpperCase`.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Notez que lors de l'itération de la collection retournée par `ConvertCollectionToUpperCase`, chaque élément est récupéré du tableau de chaînes source et converti en majuscules avant que l'élément suivant ne soit récupéré du tableau de chaînes source.  
  
 Vous pouvez constater que l'intégralité du tableau de chaînes n'est pas convertie en majuscules avant que chaque élément de la collection retournée n'ait été traité dans la boucle `foreach` dans `Main`.  
  
 La rubrique suivante de ce didacticiel illustre le chaînage de requêtes.  
  
-   [Exemple de chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
