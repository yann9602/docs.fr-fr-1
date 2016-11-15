---
title: Comparaisons et tris dans les collections
description: Comparaisons et tris dans les collections
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c7b7c005-628d-427a-91ad-af0c3958c00e
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: de1fe3bb9b9a75561b4f28ec4609491d6f3c39f5

---

# <a name="comparisons-and-sorts-within-collections"></a>Comparaisons et tris dans les collections

Les classes [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) effectuent des comparaisons dans quasiment tous les processus impliqués dans la gestion des collections, que ce soit pendant la recherche d’un élément à supprimer ou le renvoi d’une valeur d’une paire clé-valeur.

Les collections utilisent généralement un comparateur d’égalité et/ou un comparateur de classement. Deux constructions sont utilisées pour les comparaisons. 

## <a name="checking-for-equality"></a>Vérification de l'égalité

Les méthodes telles que `Contains`, `IndexOf`, `LastIndexOf` et `Remove` utilisent un comparateur d'égalité pour les éléments de collection. Si la collection est générique, les éléments font l’objet d’une comparaison d’égalité, selon les consignes suivantes :

*   Si le type T implémente l’interface générique [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1), le comparateur d’égalité est la méthode `Equals` de cette interface.

*   Si le type T n'implémente pas `IEquatable<T>`, `Object.Equals` est utilisé.

De plus, certaines surcharges de constructeur pour les collections de dictionnaires acceptent une implémentation [IEqualityComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEqualityComparer-1), qui est utilisée pour comparer l’égalité de clés.

## <a name="determining-sort-order"></a>Détermination de l'ordre de tri

Les méthodes telles que `BinarySearch` et `Sort` utilisent un comparateur de classement pour les éléments de collection. Les comparaisons peuvent être effectuées entre les éléments d’une collection, ou entre un élément et une valeur spécifiée. Pour comparer des objets, il existe le concept d’un comparateur par défaut et d’un comparateur explicite. 

Le comparateur par défaut s’appuie sur au moins l’un des objets comparés pour implémenter l’interface `IComparable`. Il est recommandé d’implémenter `IComparable` sur toutes les classes utilisées comme valeurs dans une collection de listes ou comme clés dans une collection de dictionnaires. Pour une collection générique, la comparaison d’égalité est déterminée selon ce qui suit :

*   Si le type T implémente l’interface générique [System.IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1), le comparateur par défaut est la méthode `CompareTo(T)` de cette interface.

*   Si le type T implémente l’interface générique [System.IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable), le comparateur par défaut est la méthode `CompareTo`(Object) de cette interface.

*   Si le type T n'implémente aucune interface, il n'existe aucun comparateur par défaut. Un comparateur ou un délégué de comparaison doit donc être fourni explicitement.

Pour fournir des comparaisons explicites, certaines méthodes acceptent une implémentation `IComparer` comme paramètre. Par exemple, la méthode `List<T>.Sort` accepte une implémentation [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1). 

## <a name="equality-and-sort-example"></a>Exemple d'égalité et de tri

Le code suivant illustre une implémentation d’[IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1) et d’[IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1) sur un objet métier simple. De plus, quand l’objet est stocké dans une liste et trié, vous voyez que l’appel de la méthode `Sort()` se traduit par l’utilisation du comparateur par défaut pour le type de partie et par l’implémentation de la méthode `Sort(Comparison<T>)` à l’aide d’une méthode anonyme.

C#

```csharp
using System;
using System.Collections.Generic;
// Simple business object. A PartId is used to identify the type of part 
// but the part name can change. 
public class Part : IEquatable<Part> , IComparable<Part>
{
    public string PartName { get; set; }

    public int PartId { get; set; }

    public override string ToString()
    {
        return "ID: " + PartId + "   Name: " + PartName;
    }
    public override bool Equals(object obj)
    {
        if (obj == null) return false;
        Part objAsPart = obj as Part;
        if (objAsPart == null) return false;
        else return Equals(objAsPart);
    }
    public int SortByNameAscending(string name1, string name2)
    {

        return name1.CompareTo(name2);
    }

    // Default comparer for Part type.
    public int CompareTo(Part comparePart)
    {
          // A null value means that this object is greater.
        if (comparePart == null)
            return 1;

        else
            return this.PartId.CompareTo(comparePart.PartId);
    }
    public override int GetHashCode()
    {
        return PartId;
    }
    public bool Equals(Part other)
    {
        if (other == null) return false;
        return (this.PartId.Equals(other.PartId));
    }
    // Should also override == and != operators.

}
public class Example
{
    public static void Main()
    {
        // Create a list of parts.
        List<Part> parts = new List<Part>();

        // Add parts to the list.
        parts.Add(new Part() { PartName = "regular seat", PartId = 1434 });
        parts.Add(new Part() { PartName= "crank arm", PartId = 1234 });
        parts.Add(new Part() { PartName = "shift lever", PartId = 1634 }); ;
        // Name intentionally left null.
        parts.Add(new Part() {  PartId = 1334 });
        parts.Add(new Part() { PartName = "banana seat", PartId = 1444 });
        parts.Add(new Part() { PartName = "cassette", PartId = 1534 });


        // Write out the parts in the list. This will call the overridden 
        // ToString method in the Part class.
        Console.WriteLine("\nBefore sort:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }


        // Call Sort on the list. This will use the 
        // default comparer, which is the Compare method 
        // implemented on Part.
        parts.Sort();


        Console.WriteLine("\nAfter sort by part number:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        // This shows calling the Sort(Comparison(T) overload using 
        // an anonymous method for the Comparison delegate. 
        // This method treats null as the lesser of two values.
        parts.Sort(delegate(Part x, Part y)
        {
            if (x.PartName == null && y.PartName == null) return 0;
            else if (x.PartName == null) return -1;
            else if (y.PartName == null) return 1;
            else return x.PartName.CompareTo(y.PartName);
        });

        Console.WriteLine("\nAfter sort by name:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        /*

            Before sort:
        ID: 1434   Name: regular seat
        ID: 1234   Name: crank arm
        ID: 1634   Name: shift lever
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette

        After sort by part number:
        ID: 1234   Name: crank arm
        ID: 1334   Name:
        ID: 1434   Name: regular seat
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1634   Name: shift lever

        After sort by name:
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1234   Name: crank arm
        ID: 1434   Name: regular seat
        ID: 1634   Name: shift lever

         */

    }
}
```

## <a name="see-also"></a>Voir aussi

[IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer)

[IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1)

[IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1)

[IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable)

[IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1)



<!--HONumber=Nov16_HO1-->


