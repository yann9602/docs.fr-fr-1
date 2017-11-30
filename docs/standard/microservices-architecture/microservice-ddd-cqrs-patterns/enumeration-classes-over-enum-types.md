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
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="0ea44-104">À l’aide des classes d’énumération au lieu de types enum</span><span class="sxs-lookup"><span data-stu-id="0ea44-104">Using Enumeration classes instead of enum types</span></span>

<span data-ttu-id="0ea44-105">[Énumérations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* en abrégé) sont un wrapper mince langage autour d’un type intégral.</span><span class="sxs-lookup"><span data-stu-id="0ea44-105">[Enumerations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="0ea44-106">Vous pouvez décider de limiter leur utilisation aux lorsque vous stockez une valeur d’un ensemble fermé de valeurs.</span><span class="sxs-lookup"><span data-stu-id="0ea44-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="0ea44-107">La classification basée sur le sexe (par exemple, homme, femme, inconnu) ou taille (S, M, L, XL) sont de bons exemples.</span><span class="sxs-lookup"><span data-stu-id="0ea44-107">Classification based on gender (for example, male, female, unknown), or sizes (S, M, L, XL) are good examples.</span></span> <span data-ttu-id="0ea44-108">L’utilisation des enums pour le flux de contrôle ou abstractions plus fiables peut être un [code odeur](http://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="0ea44-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="0ea44-109">Ce type d’utilisation peut aboutir à code fragile avec de nombreuses instructions de flux de contrôle la vérification des valeurs de l’enum.</span><span class="sxs-lookup"><span data-stu-id="0ea44-109">This type of usage will lead to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="0ea44-110">Au lieu de cela, vous pouvez créer des classes qui permettent de toutes les fonctionnalités complètes d’un langage orienté objet d’énumération.</span><span class="sxs-lookup"><span data-stu-id="0ea44-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span> <span data-ttu-id="0ea44-111">Toutefois, il ne s’agit pas d’un problème critique et dans de nombreux cas, par souci de simplicité, vous pouvez toujours utiliser les énumérations régulières si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="0ea44-111">However, this is not a critical issue and in many cases, for simplicity, you can still use regular enums if that is your preference.</span></span>

## <a name="implementing-enumeration-classes"></a><span data-ttu-id="0ea44-112">Implémentation des classes d’énumération</span><span class="sxs-lookup"><span data-stu-id="0ea44-112">Implementing Enumeration classes</span></span>

<span data-ttu-id="0ea44-113">La commande microservice dans eShopOnContainers fournit un exemple d’implémentation de classe de base d’énumération, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0ea44-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="0ea44-114">Vous pouvez utiliser cette classe en tant que type dans n’importe quel objet d’entité ou une valeur que pour la classe d’énumération de CardType suivante.</span><span class="sxs-lookup"><span data-stu-id="0ea44-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="0ea44-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="0ea44-115">Additional resources</span></span>

-   <span data-ttu-id="0ea44-116">**L’enum est néfastes, mettre à jour**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="0ea44-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="0ea44-117">**Michel Hardman. Comment les Enums réparties maladie — Et comment résoudre il**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="0ea44-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="0ea44-118">**Jimmy Bogard. Classes d’énumération**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="0ea44-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="0ea44-119">**Steve Smith. Alternatives d’enum dans C#**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="0ea44-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="0ea44-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="0ea44-120">**Enumeration.cs.**</span></span> <span data-ttu-id="0ea44-121">Classe d’énumération dans eShopOnContainers de base [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="0ea44-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="0ea44-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="0ea44-122">**CardType.cs**.</span></span> <span data-ttu-id="0ea44-123">Exemple de classe d’énumération dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0ea44-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="0ea44-124">*https://github.com/dotnet/eShopOnContainers/BLOB/Master/src/services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span><span class="sxs-lookup"><span data-stu-id="0ea44-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="0ea44-125">[Précédente] (mettre en œuvre-valeur-objects.md) [suivant] (domaine-modèle-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="0ea44-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
