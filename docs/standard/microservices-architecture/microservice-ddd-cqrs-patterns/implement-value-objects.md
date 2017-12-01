---
title: "Implémentation d’objets de valeur"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation d’objets de valeur"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a>Implémentation d’objets de valeur

Comme indiqué dans les sections précédentes sur les entités et les agrégats, l’identité est fondamentale pour les entités. Toutefois, il existe plusieurs objets et les éléments de données dans un système qui ne nécessitent pas une identité et l’identité de suivi, tels que les objets de valeur.

Autres entités permettre faire référence à un objet de valeur. Par exemple, dans une application qui génère un itinéraire qui explique comment obtenir à partir d’un point à un autre, cet itinéraire est un objet de valeur. Il serait un instantané des points sur un itinéraire spécifique, mais cet itinéraire suggéré n’aurait pas une identité, même si en interne, il peut faire référence à des entités telles que la ville, route, etc..

Figure 9-13 illustre l’objet de valeur d’adresse dans l’agrégat de la commande.

![](./media/image14.png)

**Figure 9-13**. Objet de valeur dans l’agrégat d’ordre d’adresses

Comme indiqué dans la Figure 9 à 13, une entité est généralement constituée de plusieurs attributs. Par exemple, ordre peut être modélisé en tant qu’entité avec une identité et composé en interne d’un ensemble d’attributs tels que OrderId, OrderDate, OrderItems, etc.. Mais l’adresse, ce qui est simplement une valeur complexe composé de pays, rue, ville, etc. doivent être modélisés et traité comme un objet de valeur.

## <a name="important-characteristics-of-value-objects"></a>Caractéristiques importantes des objets de valeur

Il existe deux principales caractéristiques des objets de valeur :

-   Ils auront pas d’identité.

-   Ils sont immuables.

La première caractéristique a été présentée précédemment. Immuabilité est une exigence importante. Une fois que l’objet est créé, les valeurs d’un objet de valeur doivent être immuables. Par conséquent, lorsque l’objet est construit, vous devez fournir les valeurs requises, mais vous ne devez pas autoriser les changer au cours de la durée de vie de l’objet.

Les objets de valeur permettent d’effectuer certaines astuces pour les performances, leur nature immuable. Cela est particulièrement vrai dans les systèmes où il peuvent y avoir des milliers de valeur des instances d’objet, qui ont les mêmes valeurs. Leur nature immuable leur permet de réutiliser ; ils peuvent être des objets interchangeables, étant donné que leurs valeurs sont identiques et qu’ils auront pas d’identité. Ce type d’optimisation peut parfois faire la différence entre les logiciels qui s’exécute lentement et avec de bonnes performances. Bien entendu, tous ces cas dépendent de l’environnement d’application et le contexte de déploiement.

## <a name="value-object-implementation-in-c"></a>Implémentation d’objet de valeur en C\#

En termes d’implémentation, vous pouvez avoir une classe de base de l’objet de valeur dont les méthodes d’utilitaire de base comme l’égalité en fonction de comparaison entre tous les attributs (depuis un objet de valeur ne doit pas être basé sur l’identité) et d’autres caractéristiques fondamentales. L’exemple suivant montre la valeur objet classe de base utilisée dans l’ordre de tri microservice d’eShopOnContainers.

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

Vous pouvez utiliser cette classe lors de l’implémentation de votre objet de valeur réelle, comme avec l’objet de valeur d’adresse indiqué dans l’exemple suivant :

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>Le masquage de la caractéristique d’identité lors de l’utilisation d’EF Core pour conserver des objets de valeur

Une limitation lorsque utilisant EF Core est dans son état actuel (1.1 de noyaux EF) ne peut pas utiliser [types complexes](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) tel que défini dans EF 6.x. Par conséquent, vous devez stocker votre objet de valeur comme une entité EF. Toutefois, vous pouvez masquer son ID afin de vous indiquer clairement que l’identité n’est pas importante dans le modèle faisant partie de l’objet de valeur. Vous masquez l’ID est à l’aide de l’ID en tant qu’une propriété de clichés instantanés. Étant donné que cette configuration pour masquer l’ID dans le modèle est configurée dans le niveau de l’infrastructure, il est transparent pour votre modèle de domaine et son implémentation de l’infrastructure peut changer à l’avenir.

Dans eShopOnContainers, l’ID masqué requis par l’infrastructure de base d’EF est implémenté de la manière suivante dans le niveau de DbContext, à l’aide des API Fluent du projet d’infrastructure.

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

Par conséquent, l’ID est masqué à partir du modèle de domaine point de vue et à l’avenir, l’infrastructure d’objet de valeur peut également être implémentée comme un type complexe ou d’une autre façon.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Martin Fowler. Modèle de ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Eric Evans. Conception domaine : Tackling Complexity in the Heart of Software.** (Livre et en savoir plus sur les objets de valeur) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Mise en œuvre de la conception pilotée par domaine.** (Livre et en savoir plus sur les objets de valeur) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Propriétés de clichés instantanés**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Les types complexes ou des objets de la valeur**. Discussion dans le référentiel GitHub de noyaux EF (onglet problèmes) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Classe d’objet de valeur de base dans eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/BLOB/Master/src/services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Classe d’adresse.** Classe d’objet valeur exemple eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/BLOB/Master/src/services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
[Précédente] (seedwork-domain-model-base-classes-interfaces.md) [suivant] (énumération-classes-over-enum-types.md)
