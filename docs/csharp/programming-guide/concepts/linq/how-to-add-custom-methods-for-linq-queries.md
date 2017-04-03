---
title: "Guide pratique pour ajouter des méthodes personnalisées aux requêtes LINQ (C#) | Microsoft Docs"
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
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7843620518dd7965724f0108a8fa008c95bd4793
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Guide pratique pour ajouter des méthodes personnalisées aux requêtes LINQ (C#)
Vous pouvez étendre l’ensemble des méthodes utilisables pour les requêtes LINQ en ajoutant des méthodes d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>. Par exemple, en plus des opérations standard d’obtention de valeur moyenne et maximale, vous pouvez créer une méthode d’agrégation personnalisée pour calculer une valeur unique à partir d’une séquence de valeurs. Vous pouvez également créer une méthode qui fonctionne comme un filtre personnalisé ou une transformation de données pour une séquence de valeurs, et qui retourne une nouvelle séquence. Des exemples de ces méthodes sont <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Lorsque vous étendez l’interface <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez appliquer vos méthodes personnalisées à n’importe quelle collection énumérable. Pour plus d’informations, consultez [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Utilisation d’une méthode d’agrégation  
 Une méthode d’agrégation calcule une valeur à partir d’un ensemble de valeurs. LINQ fournit plusieurs méthodes d’agrégation, notamment <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Max%2A>. Vous pouvez créer votre propre méthode d’agrégation en ajoutant une méthode d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>.  
  
 L’exemple de code suivant montre comment créer une méthode d’extension appelée `Median` pour calculer une valeur médiane pour une séquence de nombres de type `double`.  
  
```cs  
public static class LINQExtension  
{  
    public static double Median(this IEnumerable<double> source)  
    {  
        if (source.Count() == 0)  
        {  
            throw new InvalidOperationException("Cannot compute median for an empty set.");  
        }  
  
        var sortedList = from number in source  
                         orderby number  
                         select number;  
  
        int itemIndex = (int)sortedList.Count() / 2;  
  
        if (sortedList.Count() % 2 == 0)  
        {  
            // Even number of items.  
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;  
        }  
        else  
        {  
            // Odd number of items.  
            return sortedList.ElementAt(itemIndex);  
        }  
    }  
}  
```  
  
 Vous pouvez appeler cette méthode d’extension pour n’importe quelle collection énumérable, de la même façon que vous appelez les autres méthodes d’agrégation à partir de l’interface <xref:System.Collections.Generic.IEnumerable%601>.  
  
 L’exemple de code suivant montre comment utiliser la méthode `Median` pour un tableau de type `double`.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Surcharge d’une méthode d’agrégation pour accepter différents types  
 Vous pouvez surcharger votre méthode d’agrégation pour qu’elle accepte des séquences de différents types. L’approche standard consiste à créer une surcharge pour chaque type. Une autre approche consiste à créer une surcharge qui accepte un type générique et le convertit en un autre type à l’aide d’un délégué. Vous pouvez également combiner ces deux approches.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Pour créer une surcharge pour chaque type  
 Vous pouvez créer une surcharge pour chacun des types que vous voulez prendre en charge. L’exemple de code suivant montre une surcharge de la méthode `Median` pour le type `integer`.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Vous pouvez maintenant appeler les surcharges `Median` pour les types `integer` et `double`, comme indiqué dans le code suivant :  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### <a name="to-create-a-generic-overload"></a>Pour créer une surcharge générique  
 Vous pouvez également créer une surcharge qui accepte une séquence d’objets génériques. Cette surcharge prend un délégué comme paramètre et l’utilise pour convertir une séquence d’objets de type générique en un autre type d’objets.  
  
 Le code suivant montre une surcharge de la méthode `Median` qui prend le délégué <xref:System.Func%602> comme paramètre. Ce délégué prend un objet de type générique T et retourne un objet de type `double`.  
  
```cs  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Vous pouvez maintenant appeler la méthode `Median` pour une séquence d’objets de tout type. Si le type n’a pas sa propre surcharge de méthode, vous devez passer un paramètre délégué. En C#, vous pouvez utiliser une expression lambda à cet effet. En outre, en Visual Basic uniquement, si vous utilisez la clause `Aggregate` ou `Group By` au lieu de l’appel de méthode, vous pouvez passer n’importe quelle valeur ou expression qui se trouve dans la portée de cette clause.  
  
 L’exemple de code suivant montre comment appeler la méthode `Median` pour un tableau d’entiers et un tableau de chaînes. Pour les chaînes, c’est la valeur médiane des longueurs de chaînes du tableau qui est calculée. L’exemple montre comment passer le paramètre de délégué <xref:System.Func%602> à la méthode `Median` pour chaque cas.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## <a name="adding-a-method-that-returns-a-collection"></a>Ajout d’une méthode qui retourne une collection  
 Vous pouvez étendre l’interface <xref:System.Collections.Generic.IEnumerable%601> avec une méthode de requête personnalisée qui retourne une séquence de valeurs. Dans ce cas, la méthode doit retourner une collection de type <xref:System.Collections.Generic.IEnumerable%601>. Ces méthodes peuvent être utilisées pour appliquer des filtres ou des transformations de données à une séquence de valeurs.  
  
 L’exemple suivant montre comment créer une méthode d’extension nommée `AlternateElements` qui retourne un élément sur deux d’une collection, en commençant par le premier élément.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Vous pouvez appeler cette méthode d’extension pour n’importe quelle collection énumérable, de la même façon que vous appelez les autres méthodes à partir de l’interface <xref:System.Collections.Generic.IEnumerable%601>, comme le montre l’exemple suivant :  
  
```cs  
string[] strings = { "a", "b", "c", "d", "e" };  
  
var query = strings.AlternateElements();  
  
foreach (var element in query)  
{  
    Console.WriteLine(element);  
}  
/*  
 This code produces the following output:  
  
 a  
 c  
 e  
*/  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
