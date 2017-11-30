---
title: "Implémentation d’un modèle de domaine microservice avec le .NET Core"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation d’un modèle de domaine microservice avec le .NET Core"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="598ff-104">Implémentation d’un modèle de domaine microservice avec le .NET Core</span><span class="sxs-lookup"><span data-stu-id="598ff-104">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="598ff-105">Dans la section précédente, les principes fondamentaux et les modèles de conception d’un modèle de domaine ont été expliqués.</span><span class="sxs-lookup"><span data-stu-id="598ff-105">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="598ff-106">Il est temps d’Explorer des méthodes possibles pour implémenter le modèle de domaine à l’aide de .NET Core (C brut\# code) et EF Core.</span><span class="sxs-lookup"><span data-stu-id="598ff-106">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="598ff-107">Notez que votre modèle de domaine sera composé simplement de votre code.</span><span class="sxs-lookup"><span data-stu-id="598ff-107">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="598ff-108">Il a seulement les spécifications de modèle de base de EF, mais pas réels dépendances sur EF.</span><span class="sxs-lookup"><span data-stu-id="598ff-108">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="598ff-109">Vous devez pas dépendances dures ou des références à EF Core ou n’importe quel autre ORM dans votre modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="598ff-109">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="598ff-110">Structure de modèle de domaine dans une bibliothèque .NET Standard personnalisée</span><span class="sxs-lookup"><span data-stu-id="598ff-110">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="598ff-111">L’organisation du dossier utilisée pour l’application de référence eShopOnContainers montre le modèle DDD pour l’application.</span><span class="sxs-lookup"><span data-stu-id="598ff-111">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="598ff-112">Vous constaterez peut-être qu’une organisation de l’autre dossier plus clairement les choix de conception pour votre application.</span><span class="sxs-lookup"><span data-stu-id="598ff-112">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="598ff-113">Comme vous pouvez le voir dans la Figure 9 et 10, dans le modèle de domaine tri il existe deux agrégats, l’agrégat de commande et l’agrégation de l’acheteur.</span><span class="sxs-lookup"><span data-stu-id="598ff-113">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="598ff-114">Chaque agrégat est un groupe d’entités de domaine et les objets de valeur, bien que vous pourriez avoir un agrégat composé ainsi d’une entité de domaine unique (la racine d’agrégat ou une entité racine).</span><span class="sxs-lookup"><span data-stu-id="598ff-114">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="598ff-115">**Figure 9-10**.</span><span class="sxs-lookup"><span data-stu-id="598ff-115">**Figure 9-10**.</span></span> <span data-ttu-id="598ff-116">Structure de modèle de domaine pour le tri microservice dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="598ff-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="598ff-117">En outre, la couche de modèle de domaine inclut les contrats de référentiel (interfaces) sont les exigences de l’infrastructure de votre modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="598ff-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="598ff-118">En d’autres termes, ces interfaces express les référentiels de la couche d’infrastructure doit implémenter et comment.</span><span class="sxs-lookup"><span data-stu-id="598ff-118">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="598ff-119">Il est essentiel que l’implémentation des dépôts placées en dehors de la couche de modèle de domaine, dans la bibliothèque de couche d’infrastructure, afin de la couche de modèle de domaine n'est pas « contamination » par l’API ou les classes de technologies d’infrastructure, telles que Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="598ff-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="598ff-120">Vous pouvez également voir un [SeedWork](https://martinfowler.com/bliki/Seedwork.html) dossier qui contient les classes de base personnalisées que vous pouvez utiliser comme base pour vos entités de domaine et la valeur des objets, donc vous n’avez pas de code redondant dans la classe d’objet de chaque domaine.</span><span class="sxs-lookup"><span data-stu-id="598ff-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="598ff-121">Structuration des agrégats dans une bibliothèque .NET Standard personnalisée</span><span class="sxs-lookup"><span data-stu-id="598ff-121">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="598ff-122">Un agrégat fait référence à un cluster d’objets domaine regroupés pour faire correspondre la cohérence transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="598ff-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="598ff-123">Ces objets peuvent être des instances des entités (y compris la racine d’agrégat ou une entité racine) ainsi que tous les objets de valeur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="598ff-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="598ff-124">La cohérence transactionnelle signifie qu’un agrégat est garanti être cohérentes et à jour à la fin d’une action d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="598ff-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="598ff-125">Par exemple, l’agrégat de la commande à partir de l’eShopOnContainers classement du modèle de domaine microservice est composé comme indiqué dans la Figure 9-11.</span><span class="sxs-lookup"><span data-stu-id="598ff-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="598ff-126">**Figure 9-11**.</span><span class="sxs-lookup"><span data-stu-id="598ff-126">**Figure 9-11**.</span></span> <span data-ttu-id="598ff-127">L’ordre d’agrégation dans une solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="598ff-127">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="598ff-128">Si vous ouvrez les fichiers dans un dossier d’agrégation, vous pouvez voir comment il est marqué comme une classe de base personnalisée ou une interface, comme les objets entité ou une valeur, tel qu’implémenté dans le [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) dossier.</span><span class="sxs-lookup"><span data-stu-id="598ff-128">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="598ff-129">Implémentation des entités de domaine en tant que classes POCO</span><span class="sxs-lookup"><span data-stu-id="598ff-129">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="598ff-130">Vous implémentez un modèle de domaine dans .NET en créant des classes POCO qui implémentent les entités de votre domaine.</span><span class="sxs-lookup"><span data-stu-id="598ff-130">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="598ff-131">Dans l’exemple suivant, la classe de commande est définie comme une entité et également en tant que racine d’une agrégat.</span><span class="sxs-lookup"><span data-stu-id="598ff-131">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="598ff-132">Étant donné que la classe Order dérive de la classe de base d’entité, il peut réutiliser le code courantes lié aux entités.</span><span class="sxs-lookup"><span data-stu-id="598ff-132">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="598ff-133">N’oubliez pas que ces classes de base et les interfaces sont définies par vous dans le projet de modèle de domaine, il s’agit de votre code, le code d’infrastructure pas à partir d’un ORM comme EF.</span><span class="sxs-lookup"><span data-stu-id="598ff-133">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="598ff-134">Il est important de noter qu’il s’agit d’une entité de domaine implémentée comme une classe POCO.</span><span class="sxs-lookup"><span data-stu-id="598ff-134">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="598ff-135">Il n’a pas de dépendance directe avec Entity Framework Core ou toute autre infrastructure de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="598ff-135">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="598ff-136">Cette implémentation est qu’elle doit être simplement C\# code implémentant un modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="598ff-136">This implementation is as it should be, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="598ff-137">En outre, la classe est décorée avec une interface nommée IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="598ff-137">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="598ff-138">Cette interface est une interface vide, parfois appelée un *interface de marqueurs*, qui est utilisé uniquement pour indiquer que cette classe d’entité est également une racine d’agrégat.</span><span class="sxs-lookup"><span data-stu-id="598ff-138">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="598ff-139">Une interface de marqueur est parfois considérée comme un anti-modèle ; Toutefois, il est également un moyen adéquat pour marquer une classe, en particulier lorsque cette interface peut évoluer.</span><span class="sxs-lookup"><span data-stu-id="598ff-139">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="598ff-140">Un attribut peut être le choix pour le marqueur, mais il est plus rapide afficher la classe de base (entité) en regard de l’interface IAggregate au lieu de mettre un marqueur d’attribut d’agrégation au-dessus de la classe.</span><span class="sxs-lookup"><span data-stu-id="598ff-140">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="598ff-141">Il est un metter des préférences, dans tous les cas.</span><span class="sxs-lookup"><span data-stu-id="598ff-141">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="598ff-142">Avoir un moyen de racine d’agrégation que la plupart du code liées à la cohérence et d’entités de l’agrégat règles d’entreprise doivent être implémentées en tant que méthodes dans la classe de racine d’agrégation Order (par exemple, AddOrderItem lors de l’ajout d’un objet OrderItem à l’agrégat) .</span><span class="sxs-lookup"><span data-stu-id="598ff-142">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="598ff-143">Vous ne devez pas créer ou mettre à jour les objets OrderItems indépendamment ou directement. la classe AggregateRoot doit conserver la cohérence de toutes les opérations de mise à jour par rapport à ses entités enfants et de contrôle.</span><span class="sxs-lookup"><span data-stu-id="598ff-143">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

<span data-ttu-id="598ff-144">Par exemple, vous devez *pas* effectuer les opérations suivantes à partir de toute classe de couche commande Gestionnaire méthode ou d’une application :</span><span class="sxs-lookup"><span data-stu-id="598ff-144">For example, you should *not* do the following from any command handler method or application layer class:</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="598ff-145">Dans ce cas, la méthode Add est purement une opération pour ajouter des données, avec un accès direct à la collection OrderItems.</span><span class="sxs-lookup"><span data-stu-id="598ff-145">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="598ff-146">Par conséquent, la plupart de la logique de domaine, les règles ou les validations liées pour que l’opération avec les entités enfants est répartie sur la couche d’application (gestionnaires de commandes et contrôleurs de l’API Web).</span><span class="sxs-lookup"><span data-stu-id="598ff-146">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="598ff-147">Si vous accédez autour de la racine d’agrégation, la racine d’agrégation ne peut pas garantir son invariants, sa validité ou sa cohérence.</span><span class="sxs-lookup"><span data-stu-id="598ff-147">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="598ff-148">Vous aurez éventuellement spaghetti code ou script transactionnel.</span><span class="sxs-lookup"><span data-stu-id="598ff-148">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="598ff-149">Pour suivre les modèles DDD, les entités ne doivent pas avoir de méthodes setter public dans n’importe quelle propriété d’entité.</span><span class="sxs-lookup"><span data-stu-id="598ff-149">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="598ff-150">Modifications apportées à une entité doivent être pilotées par les méthodes explicites avec un langage omniprésent explicite sur la modification, qu'elles exécutent dans l’entité.</span><span class="sxs-lookup"><span data-stu-id="598ff-150">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="598ff-151">En outre, les collections dans l’entité (par exemple, les éléments de la commande) doivent être des propriétés en lecture seule (la méthode AsReadOnly abordées plus loin).</span><span class="sxs-lookup"><span data-stu-id="598ff-151">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="598ff-152">Vous devez pouvoir mettre à jour uniquement à partir de dans les méthodes de classe racine d’agrégation ou les méthodes d’entité enfant.</span><span class="sxs-lookup"><span data-stu-id="598ff-152">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="598ff-153">Comme vous pouvez le voir dans le code de la racine d’agrégation de commande, toutes les méthodes setter doit être privés ou au moins en lecture seule en externe, afin que toute opération sur les données de l’entité ou de ses entités enfants doit être effectuée via les méthodes dans la classe d’entité.</span><span class="sxs-lookup"><span data-stu-id="598ff-153">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="598ff-154">Cela maintient la cohérence d’une manière contrôlée et orienté objet au lieu d’implémenter le code de script transactionnel.</span><span class="sxs-lookup"><span data-stu-id="598ff-154">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="598ff-155">L’extrait de code suivant montre la façon correcte de la tâche d’ajout d’un objet OrderItem à l’agrégat de l’ordre de code.</span><span class="sxs-lookup"><span data-stu-id="598ff-155">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="598ff-156">Dans cet extrait de code, la plupart des validations ou logique relatives à la création d’un objet OrderItem seront sous le contrôle de la racine d’agrégation ordre, dans la méthode AddOrderItem, en particulier les validations et logique liées à d’autres éléments dans l’agrégat.</span><span class="sxs-lookup"><span data-stu-id="598ff-156">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="598ff-157">Par exemple, vous pouvez obtenir le même élément de produit comme résultat de plusieurs appels à AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="598ff-157">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="598ff-158">Dans cette méthode, vous pourriez examiner les éléments de produit et consolider les mêmes éléments de produit dans un seul objet OrderItem avec plusieurs unités.</span><span class="sxs-lookup"><span data-stu-id="598ff-158">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="598ff-159">En outre, si des montants de remises différents, mais l’ID de produit est le même, vous devez probablement appliquer la remise la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="598ff-159">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="598ff-160">Ce principe s’applique à toute autre logique de domaine pour l’objet OrderItem.</span><span class="sxs-lookup"><span data-stu-id="598ff-160">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="598ff-161">En outre, la nouvelle opération OrderItem(params) sera également être contrôlée et effectuée par la méthode AddOrderItem à partir de la racine d’agrégation de commande.</span><span class="sxs-lookup"><span data-stu-id="598ff-161">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="598ff-162">Par conséquent, la plupart de la logique ou les validations liées pour que l’opération (en particulier tout ce qui a un impact sur la cohérence entre les autres entités enfants) seront dans un endroit unique au sein de la racine d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="598ff-162">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="598ff-163">C’est l’objectif ultime du modèle racine d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="598ff-163">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="598ff-164">Lorsque vous utilisez Entity Framework 1.1, une entité DDD peut mieux exprimée, car une des nouvelles fonctionnalités d’Entity Framework Core 1.1 est qu’il permet [mapper à des champs](https://docs.microsoft.com/ef/core/modeling/backing-field) en plus des propriétés.</span><span class="sxs-lookup"><span data-stu-id="598ff-164">When you use Entity Framework 1.1, a DDD entity can be better expressed because one of the new features of Entity Framework Core 1.1 is that it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="598ff-165">Cela est utile lorsque vous protégez des collections d’entités enfants ou des objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="598ff-165">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="598ff-166">Avec cette amélioration, vous pouvez utiliser des champs privés simples au lieu des propriétés, et vous pouvez implémenter une mise à jour à la collection de champs dans les méthodes publiques et fournir un accès en lecture seule via la méthode AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="598ff-166">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="598ff-167">Dans DDD à mettre à jour l’entité uniquement par le biais de méthodes dans l’entité (ou le constructeur) afin de contrôler n’importe quel nom invariant et la cohérence des données, par conséquent, les propriétés sont définies uniquement avec un accesseur get.</span><span class="sxs-lookup"><span data-stu-id="598ff-167">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="598ff-168">Les propriétés sont soutenues par les champs privés.</span><span class="sxs-lookup"><span data-stu-id="598ff-168">The properties are backed by private fields.</span></span> <span data-ttu-id="598ff-169">Les membres privés uniquement accessibles à partir de la classe.</span><span class="sxs-lookup"><span data-stu-id="598ff-169">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="598ff-170">Toutefois, les exceptions là un : EF Core doit définir ces champs ainsi.</span><span class="sxs-lookup"><span data-stu-id="598ff-170">However, there one exception: EF Core needs to set these fields as well.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="598ff-171">Accesseurs get de mappage de propriétés avec uniquement pour les champs de la table de base de données</span><span class="sxs-lookup"><span data-stu-id="598ff-171">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="598ff-172">Mappage de propriétés pour les colonnes de table de base de données n’est pas une responsabilité de domaine, mais la partie de la couche d’infrastructure et de persistance.</span><span class="sxs-lookup"><span data-stu-id="598ff-172">Mapping properties to the database table columns is not a domain responsibility, but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="598ff-173">Nous signaler ce ici simplement afin de connaître les nouvelles fonctionnalités dans la version 1.1 de EF liées à la façon dont vous pouvez modéliser des entités.</span><span class="sxs-lookup"><span data-stu-id="598ff-173">We mention this here just so you are aware of the new capabilities in EF 1.1 related to how you can model entities.</span></span> <span data-ttu-id="598ff-174">Plus d’informations sur cette rubrique sont expliquées dans la section de l’infrastructure et de persistance.</span><span class="sxs-lookup"><span data-stu-id="598ff-174">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="598ff-175">Lorsque vous utilisez EF 1.0, vous devez mapper les propriétés qui sont définies uniquement avec des accesseurs Get aux champs dans la table de base de données réelles dans le DbContext.</span><span class="sxs-lookup"><span data-stu-id="598ff-175">When you use EF 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="598ff-176">Cela est fait avec la méthode HasField de la classe PropertyBuilder.</span><span class="sxs-lookup"><span data-stu-id="598ff-176">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="598ff-177">Mappage de champs sans propriétés</span><span class="sxs-lookup"><span data-stu-id="598ff-177">Mapping fields without properties</span></span>

<span data-ttu-id="598ff-178">Avec la nouvelle fonctionnalité dans la version 1.1 de noyaux EF pour mapper des colonnes aux champs, il est également possible de ne pas utiliser les propriétés.</span><span class="sxs-lookup"><span data-stu-id="598ff-178">With the new feature in EF Core 1.1 to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="598ff-179">Au lieu de cela, vous pouvez uniquement mapper des colonnes d’une table aux champs.</span><span class="sxs-lookup"><span data-stu-id="598ff-179">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="598ff-180">Un cas d’usage courants pour ce est champs privés pour un état interne qui ne doivent pas être accessible de l’extérieur de l’entité.</span><span class="sxs-lookup"><span data-stu-id="598ff-180">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="598ff-181">Par exemple, dans l’exemple de code précédent, le \_someOrderInternalState champ n’a aucune propriété connexe pour une méthode setter ou getter.</span><span class="sxs-lookup"><span data-stu-id="598ff-181">For example, in the preceding code example, the \_someOrderInternalState field has no related property for either a setter or getter.</span></span> <span data-ttu-id="598ff-182">Ce champ est également calculé au sein de la logique métier de la commande et utilisé dans les méthodes de la commande, mais il doit être rendue persistante dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="598ff-182">That field will also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="598ff-183">Par conséquent, dans la version 1.1 de EF est permet de mapper un champ sans une propriété associée à une colonne dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="598ff-183">So, in EF 1.1 there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="598ff-184">Cela est également indiqué dans le [couche d’Infrastructure](#the-infrastructure-layer) section de ce guide.</span><span class="sxs-lookup"><span data-stu-id="598ff-184">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="598ff-185">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="598ff-185">Additional resources</span></span>

-   <span data-ttu-id="598ff-186">**Vaughn Vernon. Modélisation des agrégats avec DDD et Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="598ff-186">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="598ff-187">Notez que cela est *pas* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="598ff-187">Note that this is *not* Entity Framework Core.</span></span>
    [<span data-ttu-id="598ff-188">*https://vaughnvernon.co/?p=879*</span><span class="sxs-lookup"><span data-stu-id="598ff-188">*https://vaughnvernon.co/?p=879*</span></span>](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="598ff-189">**Julie Lerman. Codage de conception domaine : conseils pour les développeurs d’axée sur les données**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="598ff-189">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="598ff-190">**UDI Dahan. Comment créer entièrement encapsulé les modèles de domaine**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="598ff-190">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="598ff-191">[Précédente] (microservice-domaine-model.md) [suivant] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="598ff-191">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>
