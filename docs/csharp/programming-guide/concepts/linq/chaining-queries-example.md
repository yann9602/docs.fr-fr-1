---
title: "Exemple de chaînage de requêtes (C#) | Microsoft Docs"
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
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5426fbf710917b537d44e25966a8bc51d78f298e
ms.lasthandoff: 03/13/2017


---
# <a name="chaining-queries-example-c"></a>Exemple de chaînage de requêtes (C#)
Cet exemple est basé sur l’exemple précédent et illustre ce qui se produit quand vous chaînez deux requêtes qui utilisent toutes deux l’exécution et l’évaluation différées.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, une autre méthode d'extension est introduite : `AppendString`. Elle ajoute une chaîne spécifiée à chaque chaîne de la collection source, puis génère les nouvelles chaînes.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
  
```  
  
 Dans cet exemple, vous pouvez constater que chaque méthode d'extension opère l'une après l'autre pour chaque élément de la collection source.  
  
 Il doit être clair, au vu de cet exemple, que bien que nous ayons chaîné des requêtes qui produisent des collections, aucune collection intermédiaire n'est matérialisée. Au lieu de cela, chaque élément est passé d'une méthode différée à la suivante. L'encombrement mémoire est par conséquent beaucoup plus faible par rapport à une approche qui consisterait à prendre d'abord un tableau de chaînes, à créer un deuxième tableau de chaînes converties en majuscules, puis à créer un troisième tableau de chaînes où des points d'exclamations sont ajoutés à chaque chaîne.  
  
 La rubrique suivante de ce didacticiel illustre la matérialisation intermédiaire :  
  
-   [Matérialisation intermédiaire (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
