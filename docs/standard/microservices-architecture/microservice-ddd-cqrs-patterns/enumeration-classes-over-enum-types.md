---
title: "À l’aide des classes d’énumération au lieu de types enum"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | À l’aide des classes d’énumération au lieu de types enum"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1745198720fd12a9d26aab2d2afb2c5dd6b6b49d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>À l’aide des classes d’énumération au lieu de types enum

[Énumérations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* en abrégé) sont un wrapper mince langage autour d’un type intégral. Vous pouvez décider de limiter leur utilisation aux lorsque vous stockez une valeur d’un ensemble fermé de valeurs. La classification basée sur le sexe (par exemple, homme, femme, inconnu) ou taille (S, M, L, XL) sont de bons exemples. L’utilisation des enums pour le flux de contrôle ou abstractions plus fiables peut être un [code odeur](http://deviq.com/code-smells/). Ce type d’utilisation peut aboutir à code fragile avec de nombreuses instructions de flux de contrôle la vérification des valeurs de l’enum.

Au lieu de cela, vous pouvez créer des classes qui permettent de toutes les fonctionnalités complètes d’un langage orienté objet d’énumération. Toutefois, il ne s’agit pas d’un problème critique et dans de nombreux cas, par souci de simplicité, vous pouvez toujours utiliser les énumérations régulières si tel est votre choix.

## <a name="implementing-enumeration-classes"></a>Implémentation des classes d’énumération

La commande microservice dans eShopOnContainers fournit un exemple d’implémentation de classe de base d’énumération, comme illustré dans l’exemple suivant :

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

Vous pouvez utiliser cette classe en tant que type dans n’importe quel objet d’entité ou une valeur que pour la classe d’énumération de CardType suivante.

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }


    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a>Ressources supplémentaires

-   **L’enum est néfastes, mettre à jour**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Michel Hardman. Comment les Enums réparties maladie — Et comment résoudre il**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard. Classes d’énumération**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith. Alternatives d’enum dans C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs.** Classe d’énumération dans eShopOnContainers de base [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**. Exemple de classe d’énumération dans eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/BLOB/Master/src/services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[Précédente] (mettre en œuvre-valeur-objects.md) [suivant] (domaine-modèle-layer-validations.md)
