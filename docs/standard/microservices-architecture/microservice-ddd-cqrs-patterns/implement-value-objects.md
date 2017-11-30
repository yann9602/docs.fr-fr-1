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
# <a name="implementing-value-objects"></a><span data-ttu-id="5a8c4-104">Implémentation d’objets de valeur</span><span class="sxs-lookup"><span data-stu-id="5a8c4-104">Implementing value objects</span></span>

<span data-ttu-id="5a8c4-105">Comme indiqué dans les sections précédentes sur les entités et les agrégats, l’identité est fondamentale pour les entités.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="5a8c4-106">Toutefois, il existe plusieurs objets et les éléments de données dans un système qui ne nécessitent pas une identité et l’identité de suivi, tels que les objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="5a8c4-107">Autres entités permettre faire référence à un objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-107">A value object can reference other entities.</span></span> <span data-ttu-id="5a8c4-108">Par exemple, dans une application qui génère un itinéraire qui explique comment obtenir à partir d’un point à un autre, cet itinéraire est un objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="5a8c4-109">Il serait un instantané des points sur un itinéraire spécifique, mais cet itinéraire suggéré n’aurait pas une identité, même si en interne, il peut faire référence à des entités telles que la ville, route, etc..</span><span class="sxs-lookup"><span data-stu-id="5a8c4-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="5a8c4-110">Figure 9-13 illustre l’objet de valeur d’adresse dans l’agrégat de la commande.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="5a8c4-111">**Figure 9-13**.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-111">**Figure 9-13**.</span></span> <span data-ttu-id="5a8c4-112">Objet de valeur dans l’agrégat d’ordre d’adresses</span><span class="sxs-lookup"><span data-stu-id="5a8c4-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="5a8c4-113">Comme indiqué dans la Figure 9 à 13, une entité est généralement constituée de plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="5a8c4-114">Par exemple, ordre peut être modélisé en tant qu’entité avec une identité et composé en interne d’un ensemble d’attributs tels que OrderId, OrderDate, OrderItems, etc.. Mais l’adresse, ce qui est simplement une valeur complexe composé de pays, rue, ville, etc. doivent être modélisés et traité comme un objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-114">For example, Order can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="5a8c4-115">Caractéristiques importantes des objets de valeur</span><span class="sxs-lookup"><span data-stu-id="5a8c4-115">Important characteristics of value objects</span></span>

<span data-ttu-id="5a8c4-116">Il existe deux principales caractéristiques des objets de valeur :</span><span class="sxs-lookup"><span data-stu-id="5a8c4-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="5a8c4-117">Ils auront pas d’identité.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-117">They have no identity.</span></span>

-   <span data-ttu-id="5a8c4-118">Ils sont immuables.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-118">They are immutable.</span></span>

<span data-ttu-id="5a8c4-119">La première caractéristique a été présentée précédemment.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="5a8c4-120">Immuabilité est une exigence importante.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-120">Immutability is an important requirement.</span></span> <span data-ttu-id="5a8c4-121">Une fois que l’objet est créé, les valeurs d’un objet de valeur doivent être immuables.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="5a8c4-122">Par conséquent, lorsque l’objet est construit, vous devez fournir les valeurs requises, mais vous ne devez pas autoriser les changer au cours de la durée de vie de l’objet.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="5a8c4-123">Les objets de valeur permettent d’effectuer certaines astuces pour les performances, leur nature immuable.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="5a8c4-124">Cela est particulièrement vrai dans les systèmes où il peuvent y avoir des milliers de valeur des instances d’objet, qui ont les mêmes valeurs.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="5a8c4-125">Leur nature immuable leur permet de réutiliser ; ils peuvent être des objets interchangeables, étant donné que leurs valeurs sont identiques et qu’ils auront pas d’identité.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="5a8c4-126">Ce type d’optimisation peut parfois faire la différence entre les logiciels qui s’exécute lentement et avec de bonnes performances.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="5a8c4-127">Bien entendu, tous ces cas dépendent de l’environnement d’application et le contexte de déploiement.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="5a8c4-128">Implémentation d’objet de valeur en C\#</span><span class="sxs-lookup"><span data-stu-id="5a8c4-128">Value object implementation in C\#</span></span>

<span data-ttu-id="5a8c4-129">En termes d’implémentation, vous pouvez avoir une classe de base de l’objet de valeur dont les méthodes d’utilitaire de base comme l’égalité en fonction de comparaison entre tous les attributs (depuis un objet de valeur ne doit pas être basé sur l’identité) et d’autres caractéristiques fondamentales.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="5a8c4-130">L’exemple suivant montre la valeur objet classe de base utilisée dans l’ordre de tri microservice d’eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="5a8c4-131">Vous pouvez utiliser cette classe lors de l’implémentation de votre objet de valeur réelle, comme avec l’objet de valeur d’adresse indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5a8c4-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a><span data-ttu-id="5a8c4-132">Le masquage de la caractéristique d’identité lors de l’utilisation d’EF Core pour conserver des objets de valeur</span><span class="sxs-lookup"><span data-stu-id="5a8c4-132">Hiding the identity characteristic when using EF Core to persist value objects</span></span>

<span data-ttu-id="5a8c4-133">Une limitation lorsque utilisant EF Core est dans son état actuel (1.1 de noyaux EF) ne peut pas utiliser [types complexes](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) tel que défini dans EF 6.x.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-133">A limitation when using EF Core is that in its current version (EF Core 1.1) you cannot use [complex types](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) as defined in EF 6.x.</span></span> <span data-ttu-id="5a8c4-134">Par conséquent, vous devez stocker votre objet de valeur comme une entité EF.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-134">Therefore, you must store your value object as an EF entity.</span></span> <span data-ttu-id="5a8c4-135">Toutefois, vous pouvez masquer son ID afin de vous indiquer clairement que l’identité n’est pas importante dans le modèle faisant partie de l’objet de valeur.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-135">However, you can hide its ID so you make clear that the identity is not important in the model that the value object is part of.</span></span> <span data-ttu-id="5a8c4-136">Vous masquez l’ID est à l’aide de l’ID en tant qu’une propriété de clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-136">You hide the ID is by using the ID as a shadow property.</span></span> <span data-ttu-id="5a8c4-137">Étant donné que cette configuration pour masquer l’ID dans le modèle est configurée dans le niveau de l’infrastructure, il est transparent pour votre modèle de domaine et son implémentation de l’infrastructure peut changer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-137">Since that configuration for hiding the ID in the model is set up in the infrastructure level, it will be transparent for your domain model, and its infrastructure implementation could change in the future.</span></span>

<span data-ttu-id="5a8c4-138">Dans eShopOnContainers, l’ID masqué requis par l’infrastructure de base d’EF est implémenté de la manière suivante dans le niveau de DbContext, à l’aide des API Fluent du projet d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-138">In eShopOnContainers, the hidden ID needed by EF Core infrastructure is implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span>

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

<span data-ttu-id="5a8c4-139">Par conséquent, l’ID est masqué à partir du modèle de domaine point de vue et à l’avenir, l’infrastructure d’objet de valeur peut également être implémentée comme un type complexe ou d’une autre façon.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-139">Therefore, the ID is hidden from the domain model point of view, and in the future, the value object infrastructure could also be implemented as a complex type or another way.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5a8c4-140">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5a8c4-140">Additional resources</span></span>

-   <span data-ttu-id="5a8c4-141">**Martin Fowler. Modèle de ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="5a8c4-141">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="5a8c4-142">**Eric Evans. Conception domaine : Tackling Complexity in the Heart of Software.**</span><span class="sxs-lookup"><span data-stu-id="5a8c4-142">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="5a8c4-143">(Livre et en savoir plus sur les objets de valeur) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="5a8c4-143">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="5a8c4-144">**Vaughn Vernon. Mise en œuvre de la conception pilotée par domaine.**</span><span class="sxs-lookup"><span data-stu-id="5a8c4-144">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="5a8c4-145">(Livre et en savoir plus sur les objets de valeur) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="5a8c4-145">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="5a8c4-146">**Propriétés de clichés instantanés**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="5a8c4-146">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="5a8c4-147">**Les types complexes ou des objets de la valeur**.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-147">**Complex types and/or value objects**.</span></span> <span data-ttu-id="5a8c4-148">Discussion dans le référentiel GitHub de noyaux EF (onglet problèmes) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="5a8c4-148">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="5a8c4-149">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="5a8c4-149">**ValueObject.cs.**</span></span> <span data-ttu-id="5a8c4-150">Classe d’objet de valeur de base dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-150">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="5a8c4-151">*https://github.com/dotnet/eShopOnContainers/BLOB/Master/src/services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span><span class="sxs-lookup"><span data-stu-id="5a8c4-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="5a8c4-152">**Classe d’adresse.**</span><span class="sxs-lookup"><span data-stu-id="5a8c4-152">**Address class.**</span></span> <span data-ttu-id="5a8c4-153">Classe d’objet valeur exemple eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5a8c4-153">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="5a8c4-154">*https://github.com/dotnet/eShopOnContainers/BLOB/Master/src/services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span><span class="sxs-lookup"><span data-stu-id="5a8c4-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
<span data-ttu-id="5a8c4-155">[Précédente] (seedwork-domain-model-base-classes-interfaces.md) [suivant] (énumération-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="5a8c4-155">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
