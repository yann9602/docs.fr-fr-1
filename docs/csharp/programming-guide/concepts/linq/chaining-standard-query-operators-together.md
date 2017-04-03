---
title: "Chaînage d’opérateurs de requête standard (C#) | Microsoft Docs"
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
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8e9da047fcc224176d028f8caef8b57bc134dc21
ms.lasthandoff: 03/13/2017


---
# <a name="chaining-standard-query-operators-together-c"></a>Chaînage d’opérateurs de requête standard (C#)
Il s’agit de la dernière rubrique du [Didacticiel : chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
 Les opérateurs de requête standard peuvent également être chaînés ensemble. Par exemple, vous pouvez introduire l’opérateur <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName>, qui fonctionne également de manière différée. Aucun résultat intermédiaire n'est matérialisé par l'opérateur.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la méthode <xref:System.Linq.Enumerable.Where%2A> est appelée avant `ConvertCollectionToUpperCase`. La méthode <xref:System.Linq.Enumerable.Where%2A> fonctionne presque de la même façon que les méthodes différées utilisées dans les exemples précédents de ce didacticiel, à savoir `ConvertCollectionToUpperCase` et `AppendString`.  
  
 Il existe toutefois une différence : dans le cas présent, la méthode <xref:System.Linq.Enumerable.Where%2A> itère sa collection source, détermine que le premier élément ne passe pas le prédicat et obtient l’élément suivant qui, lui, passe. Elle génère ensuite le deuxième élément.  
  
 L'idée de base est néanmoins identique : les collections intermédiaires ne sont matérialisées que si elles doivent l'être.  
  
 Lorsque des expressions de requêtes sont utilisées, elles sont converties en appels aux opérateurs de requête standard et les mêmes principes sont applicables.  
  
 Tous les exemples de cette section qui interrogent des documents Office Open XML utilisent le même principe. L'exécution et l'évaluation différées sont deux concepts fondamentaux que vous devez comprendre pour utiliser LINQ (et LINQ to XML) de manière optimale.  
  
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
            where s.CompareTo("D") >= 0  
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
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : chaînage de requêtes (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
