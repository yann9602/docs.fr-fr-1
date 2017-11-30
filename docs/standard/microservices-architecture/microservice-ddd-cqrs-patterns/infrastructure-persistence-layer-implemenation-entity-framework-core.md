---
title: "Implémentation de la couche de persistance d’infrastructure avec Entity Framework Core"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation de la couche de persistance d’infrastructure avec Entity Framework Core"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="a2558-104">Implémentation de la couche de persistance d’infrastructure avec Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a2558-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="a2558-105">Lorsque vous utilisez des bases de données relationnelles telles que SQL Server, Oracle ou PostgreSQL, une approche recommandée consiste à implémenter la couche de persistance basée sur Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="a2558-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="a2558-106">EF prend en charge LINQ et fournit des objets fortement typés pour votre modèle, ainsi que la persistance simplifié dans votre base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="a2558-107">Entity Framework a un long historique en tant que partie du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2558-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="a2558-108">Lorsque vous utilisez .NET Core, vous devez également utiliser Entity Framework Core, qui s’exécute sur Windows ou Linux de la même façon que .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2558-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="a2558-109">EF Core est une réécriture complète d’Entity Framework, mis en œuvre avec un beaucoup plus faible encombrement et importantes améliorations des performances.</span><span class="sxs-lookup"><span data-stu-id="a2558-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="a2558-110">Introduction à Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a2558-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="a2558-111">Entity Framework (EF) Core est léger et extensible, et version inter-plateformes des données Entity Framework populaires technologie d’accès.</span><span class="sxs-lookup"><span data-stu-id="a2558-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="a2558-112">Il a été introduit avec le .NET Core dans mid 2016.</span><span class="sxs-lookup"><span data-stu-id="a2558-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="a2558-113">Dans la mesure où une introduction à EF Core est déjà disponible dans la documentation de Microsoft, ici nous il suffit de fournir des liens vers ces informations.</span><span class="sxs-lookup"><span data-stu-id="a2558-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="a2558-114">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a2558-114">Additional resources</span></span>

-   <span data-ttu-id="a2558-115">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="a2558-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="a2558-116">**Mise en route avec ASP.NET Core et Entity Framework Core, à l’aide de Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="a2558-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="a2558-117">**Classe DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="a2558-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="a2558-118">**Comparer EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="a2558-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="a2558-119">Infrastructure dans Entity Framework Core à partir d’une perspective DDD</span><span class="sxs-lookup"><span data-stu-id="a2558-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="a2558-120">À partir d’un point de vue DDD, une fonctionnalité importante de EF est la possibilité d’utiliser les entités POCO domaine, également connues dans la terminologie EF POCO *code-first-entités*.</span><span class="sxs-lookup"><span data-stu-id="a2558-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="a2558-121">Si vous utilisez les entités POCO domaine, vos classes de modèle de domaine sont ignorant la persistance, suivant le [ignorant la persistance](http://deviq.com/persistence-ignorance/) et [Ignorance de l’Infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance) principes.</span><span class="sxs-lookup"><span data-stu-id="a2558-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="a2558-122">Par les modèles DDD, vous devez encapsuler comportement du domaine et les règles au sein de la classe d’entité, donc il peut contrôler les règles, les validations et les invariants lors de l’accès à toute collection.</span><span class="sxs-lookup"><span data-stu-id="a2558-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="a2558-123">Par conséquent, il n’est pas une bonne pratique DDD pour autoriser les accès public à des regroupements d’enfant entités ou des objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="a2558-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="a2558-124">Au lieu de cela, vous souhaitez exposer des méthodes qui contrôlent comment et quand vos champs et les collections de propriétés peuvent être mis à jour, et les actions de comportement doivent se produire lorsque cela se produit.</span><span class="sxs-lookup"><span data-stu-id="a2558-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="a2558-125">EF Core 1.1, pour satisfaire à ces exigences DDD, vous pouvez avoir des champs ordinaires dans vos entités au lieu des propriétés avec des accesseurs Set public et privé.</span><span class="sxs-lookup"><span data-stu-id="a2558-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="a2558-126">Si vous ne souhaitez pas un champ d’entité doit être accessible en externe, vous pouvez simplement créer le champ au lieu d’une propriété ou un attribut.</span><span class="sxs-lookup"><span data-stu-id="a2558-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="a2558-127">Il est inutile d’utiliser setters privées si vous préférez cette approche plus claire.</span><span class="sxs-lookup"><span data-stu-id="a2558-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="a2558-128">De la même façon, vous pouvez maintenant accéder en lecture seule aux collections à l’aide d’une propriété publique de type IEnumerable&lt;T&gt;, qui est soutenu par un membre de champ privé pour le regroupement (comme une liste&lt;&gt;) dans votre entité qui s’appuie sur EF pour la persistance.</span><span class="sxs-lookup"><span data-stu-id="a2558-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="a2558-129">Les versions précédentes d’Entity Framework requiert des propriétés de collection pour prendre en charge de ICollection&lt;T&gt;, ce qui signifiait que les développeurs à l’aide de la classe d’entité parent peut ajouter ou supprimer des éléments à partir de ses collections de propriétés.</span><span class="sxs-lookup"><span data-stu-id="a2558-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="a2558-130">Cette possibilité serait contre les modèles DDD recommandées.</span><span class="sxs-lookup"><span data-stu-id="a2558-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="a2558-131">Vous pouvez utiliser une collection privée lors de l’exposition d’un objet IEnumerable en lecture seule, comme indiqué dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="a2558-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
        decimal unitPrice, decimal discount,
        string pictureUrl, int units = 1)
    {
        // Validation logic...
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="a2558-132">Notez que la propriété OrderItems n’est accessible en lecture seule à l’aide de la liste&lt;&gt;. AsReadOnly().</span><span class="sxs-lookup"><span data-stu-id="a2558-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="a2558-133">Cette méthode crée un wrapper en lecture seule autour de la liste privée afin qu’il est protégé contre les mises à jour externes.</span><span class="sxs-lookup"><span data-stu-id="a2558-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="a2558-134">Il est beaucoup moins coûteuse que l’utilisation de la méthode ToList, car il n’a pas copier tous les éléments dans une nouvelle collection ; au lieu de cela, il effectue une seule opération d’allocation de segment de mémoire pour l’instance de wrapper.</span><span class="sxs-lookup"><span data-stu-id="a2558-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="a2558-135">EF Core offre un moyen pour mapper le modèle de domaine à la base de données physique sans duplication le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="a2558-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="a2558-136">Il est .NET POCO code pure, étant donné que l’action de mappage est implémentée dans la couche de persistance.</span><span class="sxs-lookup"><span data-stu-id="a2558-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="a2558-137">Dans cette action de mappage, vous devez configurer le mappage de champs à base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="a2558-138">Dans l’exemple suivant d’une méthode OnModelCreating, le code en surbrillance indique Core EF pour accéder à la propriété OrderItems via son champ.</span><span class="sxs-lookup"><span data-stu-id="a2558-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

<span data-ttu-id="a2558-139">Lorsque vous utilisez des champs au lieu des propriétés, l’entité OrderItem est conservée comme s’il avait une liste de&lt;OrderItem&gt; propriété.</span><span class="sxs-lookup"><span data-stu-id="a2558-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="a2558-140">Toutefois, il expose un seul accesseur (méthode AddOrderItem) pour ajouter de nouveaux éléments à la commande.</span><span class="sxs-lookup"><span data-stu-id="a2558-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="a2558-141">Par conséquent, comportement et les données sont liées entre elles et seront cohérentes dans n’importe quel code d’application qui utilise le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="a2558-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="a2558-142">Implémentation de référentiels personnalisés avec Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a2558-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="a2558-143">Au niveau de l’implémentation, un référentiel est simplement une classe avec le code de persistance de données coordonnée par une unité de travail (DBContext dans EF Core) lorsque vous effectuez des mises à jour, comme indiqué dans la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="a2558-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;

        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

<span data-ttu-id="a2558-144">Notez que l’interface IBuyerRepository proviennent de la couche de modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="a2558-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="a2558-145">Toutefois, l’implémentation de référentiel est effectuée à la persistance et la couche d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="a2558-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="a2558-146">Le DbContext EF est fourni par le biais du constructeur à l’Injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="a2558-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="a2558-147">Il est partagé entre plusieurs référentiels dans la même portée de demande HTTP, grâce à sa durée de vie par défaut (ServiceLifetime.Scoped) dans le conteneur inversion de contrôle (qui peut également être explicitement définie avec les services. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="a2558-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="a2558-148">Méthodes à implémenter dans un référentiel (mises à jour ou les transactions et requêtes)</span><span class="sxs-lookup"><span data-stu-id="a2558-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="a2558-149">Dans chaque classe de référentiel, vous devez placer les méthodes de persistance qui mettent à jour l’état des entités contenues par ses agrégat connexe.</span><span class="sxs-lookup"><span data-stu-id="a2558-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="a2558-150">N’oubliez pas d’il existe une relation un à un entre un agrégat et de son espace de stockage associé.</span><span class="sxs-lookup"><span data-stu-id="a2558-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="a2558-151">Prendre en compte qu’un objet d’entité racine d’agrégation peut incorporée entités enfants dans son graphique EF.</span><span class="sxs-lookup"><span data-stu-id="a2558-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="a2558-152">Par exemple, un acheteur peut avoir plusieurs modes de paiement en tant qu’entités enfants connexes.</span><span class="sxs-lookup"><span data-stu-id="a2558-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="a2558-153">Étant donné que l’approche pour le tri microservice dans eShopOnContainers repose également sur CQS/CQRS, la plupart des requêtes n’est pas implémentée dans des référentiels personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a2558-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="a2558-154">Les développeurs ont la possibilité de créer les requêtes et les jointures, qu'ils ont besoin pour la couche de présentation sans les restrictions imposées par les agrégats, les dépôts personnalisés par agrégat et DDD en général.</span><span class="sxs-lookup"><span data-stu-id="a2558-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="a2558-155">La plupart des référentiels personnalisés suggérées par ce guide ont plusieurs mises à jour ou les méthodes transactionnelles, mais uniquement les méthodes de requête nécessaires obtenir des données à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="a2558-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="a2558-156">Par exemple, le référentiel BuyerRepository implémente une méthode FindAsync, étant donné que l’application a besoin de savoir si un acheteur donné existe avant de créer un nouvel acheteur lié à la commande.</span><span class="sxs-lookup"><span data-stu-id="a2558-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="a2558-157">Toutefois, les méthodes de requête réel pour obtenir des données à envoyer aux applications client ou de la couche de présentation sont implémentés, comme indiqué dans les requêtes CQRS basées sur des requêtes flexibles à l’aide de Dapper.</span><span class="sxs-lookup"><span data-stu-id="a2558-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="a2558-158">À l’aide d’un référentiel personnalisé plutôt que directement à l’aide de DbContext EF</span><span class="sxs-lookup"><span data-stu-id="a2558-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="a2558-159">La classe Entity Framework DbContext est basée sur les modèles de l’unité de travail et le référentiel et peut servir directement à partir de votre code, par exemple à partir d’un contrôleur principal de ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="a2558-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="a2558-160">Qui est la façon vous pouvez créer le code le plus simple, comme dans le microservice catalogue CRUD dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a2558-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="a2558-161">Dans les cas où vous souhaitez le code le plus simple possible, vous pourriez utiliser directement la classe DbContext, comme de nombreux développeurs.</span><span class="sxs-lookup"><span data-stu-id="a2558-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="a2558-162">Toutefois, l’implémentation référentiels personnalisés fournit plusieurs avantages lors de l’implémentation des microservices ou des applications plus complexes.</span><span class="sxs-lookup"><span data-stu-id="a2558-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="a2558-163">Les modèles de référentiel et d’unité de travail sont prévues pour encapsuler la couche de persistance infrastructure afin qu’il est dissocié de l’application et les couches de modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="a2558-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="a2558-164">Implémentation de ces modèles peut faciliter l’utilisation de référentiels fictives simulation d’accès à la base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="a2558-165">Dans la Figure 9-18, vous pouvez voir les différences entre le ne pas à l’aide de référentiels (directement en utilisant le DbContext EF) et l’utilisation des référentiels qui facilitent la simuler les référentiels.</span><span class="sxs-lookup"><span data-stu-id="a2558-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="a2558-166">**Figure 9-18**.</span><span class="sxs-lookup"><span data-stu-id="a2558-166">**Figure 9-18**.</span></span> <span data-ttu-id="a2558-167">À l’aide de référentiels personnalisés par rapport à un DbContext brut</span><span class="sxs-lookup"><span data-stu-id="a2558-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="a2558-168">Il existe plusieurs alternatives lors de la simulation.</span><span class="sxs-lookup"><span data-stu-id="a2558-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="a2558-169">Vous pourriez simuler les référentiels simplement ou vous pouvez simuler toute unité de travail.</span><span class="sxs-lookup"><span data-stu-id="a2558-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="a2558-170">Généralement simulation simplement les référentiels est suffisant, et la complexité d’abstraction et de simuler une ensemble unité de travail n’est généralement pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a2558-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="a2558-171">Une version ultérieure, lorsque nous concentrer sur la couche application, vous verrez comment fonctionne l’Injection de dépendance dans ASP.NET Core et comment il est implémenté lors de l’utilisation de référentiels.</span><span class="sxs-lookup"><span data-stu-id="a2558-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="a2558-172">En bref, les dépôts personnalisés permettent de tester plus facilement le code avec des tests unitaires qui ne sont pas affectés par l’état de la couche données.</span><span class="sxs-lookup"><span data-stu-id="a2558-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="a2558-173">Si vous exécutez des tests qui également accéder à la base de données via Entity Framework, ils ne sont pas des tests unitaires, mais les tests d’intégration, qui sont beaucoup plus lents.</span><span class="sxs-lookup"><span data-stu-id="a2558-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="a2558-174">Si vous utilisiez DbContext directement, le seul choix que vous devriez serait pour exécuter des tests unitaires à l’aide d’une mémoire de SQL Server avec des données est prévisible pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="a2558-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="a2558-175">Vous ne serez pas en mesure de contrôler les objets fictifs et des données factices de la même manière au niveau du référentiel.</span><span class="sxs-lookup"><span data-stu-id="a2558-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="a2558-176">Bien entendu, vous pouvez toujours tester les contrôleurs MVC.</span><span class="sxs-lookup"><span data-stu-id="a2558-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="a2558-177">Durée de vie DbContext EF et IUnitOfWork instance dans votre conteneur inversion de contrôle</span><span class="sxs-lookup"><span data-stu-id="a2558-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="a2558-178">L’objet DbContext (exposée en tant qu’objet IUnitOfWork) peut doivent être partagés entre plusieurs référentiels au sein de la même étendue de la demande HTTP.</span><span class="sxs-lookup"><span data-stu-id="a2558-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="a2558-179">Par exemple, cela est vrai lorsque l’opération en cours d’exécution doit traiter avec plusieurs fonctions d’agrégation, ou simplement parce que vous utilisez plusieurs instances de référentiel.</span><span class="sxs-lookup"><span data-stu-id="a2558-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="a2558-180">Il est également important de mentionner que l’interface IUnitOfWork fait partie du domaine, pas un type EF.</span><span class="sxs-lookup"><span data-stu-id="a2558-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="a2558-181">Pour ce faire, l’instance de l’objet DbContext doit avoir sa durée de vie du service pour ServiceLifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="a2558-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="a2558-182">Il s’agit de la durée de vie par défaut lors de l’inscription d’un DbContext avec des services. AddDbContext dans votre conteneur inversion de contrôle à partir de la méthode ConfigureServices du fichier Startup.cs dans votre projet de l’API Web ASP.NET principale.</span><span class="sxs-lookup"><span data-stu-id="a2558-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="a2558-183">Le code suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="a2558-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
    .AddDbContext<OrderingContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
        Assembly.GetName().Name));
    },
    ServiceLifetime.Scoped // Note that Scoped is the default choice
    // in AddDbContext. It is shown here only for
    // pedagogic purposes.
    );
}
```

<span data-ttu-id="a2558-184">Le mode d’instanciation DbContext ne doit pas être configuré en tant que ServiceLifetime.Transient ou ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="a2558-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="a2558-185">La durée de vie instance référentiel dans votre conteneur inversion de contrôle</span><span class="sxs-lookup"><span data-stu-id="a2558-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="a2558-186">De la même façon, durée de vie du référentiel doit généralement être définie comme étant incluses dans l’étendue (InstancePerLifetimeScope dans Autofac).</span><span class="sxs-lookup"><span data-stu-id="a2558-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="a2558-187">Cela peut également être temporaire (InstancePerDependency dans Autofac), mais votre service sera plus efficace en ce qui concerne la mémoire lors de l’utilisation de la durée de vie étendue.</span><span class="sxs-lookup"><span data-stu-id="a2558-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="a2558-188">Notez que pour le référentiel à l’aide de la durée de vie singleton peut entraîner des problèmes graves lorsque votre DbContext est définie sur une étendue (InstancePerLifetimeScope) la durée de vie (les valeur par défaut des durées de vie d’un DBContext).</span><span class="sxs-lookup"><span data-stu-id="a2558-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="a2558-189">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a2558-189">Additional resources</span></span>

-   <span data-ttu-id="a2558-190">**Implémentation du référentiel et une unité de travail des modèles dans une Application ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="a2558-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="a2558-191">**Jonathan Allen. Stratégies d’implémentation pour le référentiel de modèle avec Entity Framework, Dapper et chaîner**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="a2558-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="a2558-192">**Cesar de la Torre. Comparaison des durées de vie du service ASP.NET Core IoC conteneur avec des étendues d’instance Autofac IoC conteneur**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="a2558-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="a2558-193">Mappage de table</span><span class="sxs-lookup"><span data-stu-id="a2558-193">Table mapping</span></span>

<span data-ttu-id="a2558-194">Mappage de table identifie les données de table pour être interrogées à partir d’et enregistrées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="a2558-195">Précédemment, vous avez vu comment les entités de domaine (par exemple, un domaine de produit ou de l’ordre) peuvent servir pour générer un schéma de base de données associée.</span><span class="sxs-lookup"><span data-stu-id="a2558-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="a2558-196">EF est fortement conçu autour du concept de *conventions*.</span><span class="sxs-lookup"><span data-stu-id="a2558-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="a2558-197">Conventions répondre aux questions telles que « Ce que le nom d’une table sera ? »</span><span class="sxs-lookup"><span data-stu-id="a2558-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="a2558-198">ou « quelle propriété est la clé primaire ? »</span><span class="sxs-lookup"><span data-stu-id="a2558-198">or “What property is the primary key?”</span></span> <span data-ttu-id="a2558-199">Conventions sont généralement basées sur des noms conventionnels, par exemple, il est généralement utilisé pour la clé primaire à une propriété qui se termine par le code.</span><span class="sxs-lookup"><span data-stu-id="a2558-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="a2558-200">Par convention, chaque entité est configurée pour mapper à une table avec le même nom que le DbSet&lt;TEntity&gt; propriété qui expose l’entité dans le contexte dérivée.</span><span class="sxs-lookup"><span data-stu-id="a2558-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="a2558-201">Si aucun DbSet&lt;TEntity&gt; valeur est fournie pour l’entité donnée, le nom de classe est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a2558-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="a2558-202">Annotations de données par rapport à l’API Fluent</span><span class="sxs-lookup"><span data-stu-id="a2558-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="a2558-203">Il existe de nombreuses conventions EF Core supplémentaires et la plupart d'entre elles peut être modifiée à l’aide des annotations de données ou des API Fluent, implémentée dans la méthode OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="a2558-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="a2558-204">Annotations de données doivent être utilisées sur les classes de modèle d’entité, qui est un moyen plus contraignant du point de vue DDD.</span><span class="sxs-lookup"><span data-stu-id="a2558-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="a2558-205">Il s’agit, car vous sont duplication votre modèle avec des annotations de données liées à la base de données de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="a2558-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="a2558-206">En revanche, les API Fluent est un moyen pratique pour modifier la plupart des conventions et des mappages dans la couche infrastructure de persistance de données, le modèle d’entité est donc propre et découplées à partir de l’infrastructure de persistance.</span><span class="sxs-lookup"><span data-stu-id="a2558-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="a2558-207">API Fluent et la méthode OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="a2558-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="a2558-208">Comme mentionné, afin de modifier les mappages et les conventions, vous pouvez utiliser la méthode OnModelCreating dans la classe DbContext.</span><span class="sxs-lookup"><span data-stu-id="a2558-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="a2558-209">L’exemple suivant montre comment procéder dans l’ordre de tri microservice dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a2558-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

<span data-ttu-id="a2558-210">Vous pouvez définir tous les mappages de l’API Fluent au sein de la même méthode OnModelCreating, mais il est recommandé que le code de la partition et avoir plusieurs submethods, une par une entité, comme indiqué dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="a2558-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="a2558-211">Pour les modèles particulièrement volumineux, il peut même être recommandé d’avoir des fichiers sources distincts (les classes static) pour la configuration de différents types d’entité.</span><span class="sxs-lookup"><span data-stu-id="a2558-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="a2558-212">Le code dans l’exemple est explicit.</span><span class="sxs-lookup"><span data-stu-id="a2558-212">The code in the example is explicit.</span></span> <span data-ttu-id="a2558-213">Toutefois, les conventions EF Core faire la plupart de ces automatiquement, le code réel, que vous devez écrire parvenir au même résultat serait beaucoup plus petit.</span><span class="sxs-lookup"><span data-stu-id="a2558-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="a2558-214">L’algorithme max/min dans EF Core</span><span class="sxs-lookup"><span data-stu-id="a2558-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="a2558-215">Un aspect intéressant de code dans l’exemple précédent est qu’il utilise le [max/min algorithme](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) en tant que la stratégie de génération de clés.</span><span class="sxs-lookup"><span data-stu-id="a2558-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="a2558-216">L’algorithme max/min est utile lorsque vous avez besoin de clés uniques.</span><span class="sxs-lookup"><span data-stu-id="a2558-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="a2558-217">Sous forme de résumé, l’algorithme Hi-Lo affecte les identificateurs uniques pour les lignes de la table pendant ne pas selon le stockage de la ligne dans la base de données immédiatement.</span><span class="sxs-lookup"><span data-stu-id="a2558-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="a2558-218">Cela vous permet de démarrer l’utilisation des identificateurs immédiatement, comme cela arrive avec régulière séquentielle de base de données ID.</span><span class="sxs-lookup"><span data-stu-id="a2558-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="a2558-219">L’algorithme max/min décrit un mécanisme pour générer des ID sécurisés sur le côté client plutôt que dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="a2558-220">*Safe* dans ce contexte signifie sans collisions.</span><span class="sxs-lookup"><span data-stu-id="a2558-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="a2558-221">Cet algorithme est intéressant pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2558-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="a2558-222">Il n’interrompt pas le modèle de l’unité de travail.</span><span class="sxs-lookup"><span data-stu-id="a2558-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="a2558-223">Il ne nécessite pas les boucles, les générateurs de séquence de façon faire dans les autres SGBD.</span><span class="sxs-lookup"><span data-stu-id="a2558-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="a2558-224">Il génère un identificateur contrôlable de visu, contrairement aux techniques qui utilisent des GUID.</span><span class="sxs-lookup"><span data-stu-id="a2558-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="a2558-225">Prend en charge de EF Core [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) avec la méthode ForSqlServerUseSequenceHiLo, comme indiqué dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="a2558-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="a2558-226">Mappage de champs au lieu des propriétés</span><span class="sxs-lookup"><span data-stu-id="a2558-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="a2558-227">Avec la fonctionnalité de EF Core 1.1 qui mappe les colonnes à des champs, il est possible de ne pas utiliser toutes les propriétés dans la classe d’entité et simplement pour mapper les colonnes d’une table aux champs.</span><span class="sxs-lookup"><span data-stu-id="a2558-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="a2558-228">Une utilisation courante pour qui serait des champs privés pour n’importe quel état interne qui ne doivent pas être accessible de l’extérieur de l’entité.</span><span class="sxs-lookup"><span data-stu-id="a2558-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="a2558-229">EF 1.1 prend en charge permet de mapper un champ sans une propriété associée à une colonne dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="a2558-230">Cela avec champs uniques ou également avec des collections, comme une liste&lt; &gt; champ.</span><span class="sxs-lookup"><span data-stu-id="a2558-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="a2558-231">Ce point a été indiqué précédemment, lorsque nous avons abordée modélisation les classes de modèle de domaine, mais ici, vous pouvez voir comment ce mappage est effectué avec la configuration PropertyAccessMode.Field mis en surbrillance dans le code précédent.</span><span class="sxs-lookup"><span data-stu-id="a2558-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="a2558-232">À l’aide d’occulter les propriétés dans les objets de valeur pour les identifiants masqués au niveau de l’infrastructure</span><span class="sxs-lookup"><span data-stu-id="a2558-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="a2558-233">Clichés instantanés dans EF Core les propriétés qui n’existent pas dans votre modèle de classe d’entité.</span><span class="sxs-lookup"><span data-stu-id="a2558-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="a2558-234">Les valeurs et les États de ces propriétés sont conservées uniquement dans le [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) classe au niveau de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="a2558-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="a2558-235">À partir d’un point de vue DDD, occulter les propriétés sont un moyen pratique d’implémenter des objets de valeur en masquant l’ID comme clé primaire propriété clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="a2558-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="a2558-236">Ceci est important, car un objet de valeur ne doit pas avoir identité (au moins, vous n’aurez pas l’ID de la couche de modèle de domaine lors de la mise en forme des objets de valeur).</span><span class="sxs-lookup"><span data-stu-id="a2558-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="a2558-237">Le point ici est que, à compter de la version actuelle du noyau de EF, EF Core n’a pas un moyen d’implémenter des objets de valeur en tant que [types complexes](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), que possible dans EF 6.x.</span><span class="sxs-lookup"><span data-stu-id="a2558-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="a2558-238">C’est pourquoi vous avez pas besoin d’implémenter un objet de valeur comme une entité avec un ID masqué (clé primaire), définie comme une propriété de clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="a2558-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="a2558-239">Comme vous pouvez le voir dans le [objet de valeur d’adresse](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) dans eShopOnContainers, dans le modèle d’adresse vous ne voyez pas un ID :</span><span class="sxs-lookup"><span data-stu-id="a2558-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

<span data-ttu-id="a2558-240">En pratique, nous devons fournir un ID afin que EF Core est en mesure de conserver ces données dans les tables de base de données.</span><span class="sxs-lookup"><span data-stu-id="a2558-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="a2558-241">Cela se fait dans la méthode ConfigureAddress de la [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) classe au niveau de l’infrastructure, afin de nous pollue pas pas le modèle de domaine avec le code d’infrastructure EF.</span><span class="sxs-lookup"><span data-stu-id="a2558-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a><span data-ttu-id="a2558-242">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a2558-242">Additional resources</span></span>

-   <span data-ttu-id="a2558-243">**Mappage de table**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="a2558-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="a2558-244">**Permet de générer des clés avec Entity Framework Core HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="a2558-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="a2558-245">**Sauvegarde des champs**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="a2558-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="a2558-246">**Steve Smith. Encapsulé de Collections dans Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="a2558-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="a2558-247">**Propriétés de clichés instantanés**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="a2558-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a2558-248">[Précédente] (infrastructure-persistance-layer-design.md) [suivant] (nosql-base de données-persistance-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="a2558-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
