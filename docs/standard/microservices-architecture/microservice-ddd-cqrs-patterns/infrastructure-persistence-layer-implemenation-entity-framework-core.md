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
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implémentation de la couche de persistance d’infrastructure avec Entity Framework Core

Lorsque vous utilisez des bases de données relationnelles telles que SQL Server, Oracle ou PostgreSQL, une approche recommandée consiste à implémenter la couche de persistance basée sur Entity Framework (EF). EF prend en charge LINQ et fournit des objets fortement typés pour votre modèle, ainsi que la persistance simplifié dans votre base de données.

Entity Framework a un long historique en tant que partie du .NET Framework. Lorsque vous utilisez .NET Core, vous devez également utiliser Entity Framework Core, qui s’exécute sur Windows ou Linux de la même façon que .NET Core. EF Core est une réécriture complète d’Entity Framework, mis en œuvre avec un beaucoup plus faible encombrement et importantes améliorations des performances.

## <a name="introduction-to-entity-framework-core"></a>Introduction à Entity Framework Core

Entity Framework (EF) Core est léger et extensible, et version inter-plateformes des données Entity Framework populaires technologie d’accès. Il a été introduit avec le .NET Core dans mid 2016.

Dans la mesure où une introduction à EF Core est déjà disponible dans la documentation de Microsoft, ici nous il suffit de fournir des liens vers ces informations.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **Mise en route avec ASP.NET Core et Entity Framework Core, à l’aide de Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **Classe DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **Comparer EF Core & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastructure dans Entity Framework Core à partir d’une perspective DDD

À partir d’un point de vue DDD, une fonctionnalité importante de EF est la possibilité d’utiliser les entités POCO domaine, également connues dans la terminologie EF POCO *code-first-entités*. Si vous utilisez les entités POCO domaine, vos classes de modèle de domaine sont ignorant la persistance, suivant le [ignorant la persistance](http://deviq.com/persistence-ignorance/) et [Ignorance de l’Infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance) principes.

Par les modèles DDD, vous devez encapsuler comportement du domaine et les règles au sein de la classe d’entité, donc il peut contrôler les règles, les validations et les invariants lors de l’accès à toute collection. Par conséquent, il n’est pas une bonne pratique DDD pour autoriser les accès public à des regroupements d’enfant entités ou des objets de valeur. Au lieu de cela, vous souhaitez exposer des méthodes qui contrôlent comment et quand vos champs et les collections de propriétés peuvent être mis à jour, et les actions de comportement doivent se produire lorsque cela se produit.

EF Core 1.1, pour satisfaire à ces exigences DDD, vous pouvez avoir des champs ordinaires dans vos entités au lieu des propriétés avec des accesseurs Set public et privé. Si vous ne souhaitez pas un champ d’entité doit être accessible en externe, vous pouvez simplement créer le champ au lieu d’une propriété ou un attribut. Il est inutile d’utiliser setters privées si vous préférez cette approche plus claire.

De la même façon, vous pouvez maintenant accéder en lecture seule aux collections à l’aide d’une propriété publique de type IEnumerable&lt;T&gt;, qui est soutenu par un membre de champ privé pour le regroupement (comme une liste&lt;&gt;) dans votre entité qui s’appuie sur EF pour la persistance. Les versions précédentes d’Entity Framework requiert des propriétés de collection pour prendre en charge de ICollection&lt;T&gt;, ce qui signifiait que les développeurs à l’aide de la classe d’entité parent peut ajouter ou supprimer des éléments à partir de ses collections de propriétés. Cette possibilité serait contre les modèles DDD recommandées.

Vous pouvez utiliser une collection privée lors de l’exposition d’un objet IEnumerable en lecture seule, comme indiqué dans l’exemple de code suivant :

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

Notez que la propriété OrderItems n’est accessible en lecture seule à l’aide de la liste&lt;&gt;. AsReadOnly(). Cette méthode crée un wrapper en lecture seule autour de la liste privée afin qu’il est protégé contre les mises à jour externes. Il est beaucoup moins coûteuse que l’utilisation de la méthode ToList, car il n’a pas copier tous les éléments dans une nouvelle collection ; au lieu de cela, il effectue une seule opération d’allocation de segment de mémoire pour l’instance de wrapper.

EF Core offre un moyen pour mapper le modèle de domaine à la base de données physique sans duplication le modèle de domaine. Il est .NET POCO code pure, étant donné que l’action de mappage est implémentée dans la couche de persistance. Dans cette action de mappage, vous devez configurer le mappage de champs à base de données. Dans l’exemple suivant d’une méthode OnModelCreating, le code en surbrillance indique Core EF pour accéder à la propriété OrderItems via son champ.

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

Lorsque vous utilisez des champs au lieu des propriétés, l’entité OrderItem est conservée comme s’il avait une liste de&lt;OrderItem&gt; propriété. Toutefois, il expose un seul accesseur (méthode AddOrderItem) pour ajouter de nouveaux éléments à la commande. Par conséquent, comportement et les données sont liées entre elles et seront cohérentes dans n’importe quel code d’application qui utilise le modèle de domaine.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Implémentation de référentiels personnalisés avec Entity Framework Core

Au niveau de l’implémentation, un référentiel est simplement une classe avec le code de persistance de données coordonnée par une unité de travail (DBContext dans EF Core) lorsque vous effectuez des mises à jour, comme indiqué dans la classe suivante :

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

Notez que l’interface IBuyerRepository proviennent de la couche de modèle de domaine. Toutefois, l’implémentation de référentiel est effectuée à la persistance et la couche d’infrastructure.

Le DbContext EF est fourni par le biais du constructeur à l’Injection de dépendances. Il est partagé entre plusieurs référentiels dans la même portée de demande HTTP, grâce à sa durée de vie par défaut (ServiceLifetime.Scoped) dans le conteneur inversion de contrôle (qui peut également être explicitement définie avec les services. AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Méthodes à implémenter dans un référentiel (mises à jour ou les transactions et requêtes)

Dans chaque classe de référentiel, vous devez placer les méthodes de persistance qui mettent à jour l’état des entités contenues par ses agrégat connexe. N’oubliez pas d’il existe une relation un à un entre un agrégat et de son espace de stockage associé. Prendre en compte qu’un objet d’entité racine d’agrégation peut incorporée entités enfants dans son graphique EF. Par exemple, un acheteur peut avoir plusieurs modes de paiement en tant qu’entités enfants connexes.

Étant donné que l’approche pour le tri microservice dans eShopOnContainers repose également sur CQS/CQRS, la plupart des requêtes n’est pas implémentée dans des référentiels personnalisés. Les développeurs ont la possibilité de créer les requêtes et les jointures, qu'ils ont besoin pour la couche de présentation sans les restrictions imposées par les agrégats, les dépôts personnalisés par agrégat et DDD en général. La plupart des référentiels personnalisés suggérées par ce guide ont plusieurs mises à jour ou les méthodes transactionnelles, mais uniquement les méthodes de requête nécessaires obtenir des données à mettre à jour. Par exemple, le référentiel BuyerRepository implémente une méthode FindAsync, étant donné que l’application a besoin de savoir si un acheteur donné existe avant de créer un nouvel acheteur lié à la commande.

Toutefois, les méthodes de requête réel pour obtenir des données à envoyer aux applications client ou de la couche de présentation sont implémentés, comme indiqué dans les requêtes CQRS basées sur des requêtes flexibles à l’aide de Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>À l’aide d’un référentiel personnalisé plutôt que directement à l’aide de DbContext EF

La classe Entity Framework DbContext est basée sur les modèles de l’unité de travail et le référentiel et peut servir directement à partir de votre code, par exemple à partir d’un contrôleur principal de ASP.NET MVC. Qui est la façon vous pouvez créer le code le plus simple, comme dans le microservice catalogue CRUD dans eShopOnContainers. Dans les cas où vous souhaitez le code le plus simple possible, vous pourriez utiliser directement la classe DbContext, comme de nombreux développeurs.

Toutefois, l’implémentation référentiels personnalisés fournit plusieurs avantages lors de l’implémentation des microservices ou des applications plus complexes. Les modèles de référentiel et d’unité de travail sont prévues pour encapsuler la couche de persistance infrastructure afin qu’il est dissocié de l’application et les couches de modèle de domaine. Implémentation de ces modèles peut faciliter l’utilisation de référentiels fictives simulation d’accès à la base de données.

Dans la Figure 9-18, vous pouvez voir les différences entre le ne pas à l’aide de référentiels (directement en utilisant le DbContext EF) et l’utilisation des référentiels qui facilitent la simuler les référentiels.

![](./media/image19.png)

**Figure 9-18**. À l’aide de référentiels personnalisés par rapport à un DbContext brut

Il existe plusieurs alternatives lors de la simulation. Vous pourriez simuler les référentiels simplement ou vous pouvez simuler toute unité de travail. Généralement simulation simplement les référentiels est suffisant, et la complexité d’abstraction et de simuler une ensemble unité de travail n’est généralement pas nécessaire.

Une version ultérieure, lorsque nous concentrer sur la couche application, vous verrez comment fonctionne l’Injection de dépendance dans ASP.NET Core et comment il est implémenté lors de l’utilisation de référentiels.

En bref, les dépôts personnalisés permettent de tester plus facilement le code avec des tests unitaires qui ne sont pas affectés par l’état de la couche données. Si vous exécutez des tests qui également accéder à la base de données via Entity Framework, ils ne sont pas des tests unitaires, mais les tests d’intégration, qui sont beaucoup plus lents.

Si vous utilisiez DbContext directement, le seul choix que vous devriez serait pour exécuter des tests unitaires à l’aide d’une mémoire de SQL Server avec des données est prévisible pour les tests unitaires. Vous ne serez pas en mesure de contrôler les objets fictifs et des données factices de la même manière au niveau du référentiel. Bien entendu, vous pouvez toujours tester les contrôleurs MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Durée de vie DbContext EF et IUnitOfWork instance dans votre conteneur inversion de contrôle

L’objet DbContext (exposée en tant qu’objet IUnitOfWork) peut doivent être partagés entre plusieurs référentiels au sein de la même étendue de la demande HTTP. Par exemple, cela est vrai lorsque l’opération en cours d’exécution doit traiter avec plusieurs fonctions d’agrégation, ou simplement parce que vous utilisez plusieurs instances de référentiel. Il est également important de mentionner que l’interface IUnitOfWork fait partie du domaine, pas un type EF.

Pour ce faire, l’instance de l’objet DbContext doit avoir sa durée de vie du service pour ServiceLifetime.Scoped. Il s’agit de la durée de vie par défaut lors de l’inscription d’un DbContext avec des services. AddDbContext dans votre conteneur inversion de contrôle à partir de la méthode ConfigureServices du fichier Startup.cs dans votre projet de l’API Web ASP.NET principale. Le code suivant illustre ce comportement :

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

Le mode d’instanciation DbContext ne doit pas être configuré en tant que ServiceLifetime.Transient ou ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>La durée de vie instance référentiel dans votre conteneur inversion de contrôle

De la même façon, durée de vie du référentiel doit généralement être définie comme étant incluses dans l’étendue (InstancePerLifetimeScope dans Autofac). Cela peut également être temporaire (InstancePerDependency dans Autofac), mais votre service sera plus efficace en ce qui concerne la mémoire lors de l’utilisation de la durée de vie étendue.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Notez que pour le référentiel à l’aide de la durée de vie singleton peut entraîner des problèmes graves lorsque votre DbContext est définie sur une étendue (InstancePerLifetimeScope) la durée de vie (les valeur par défaut des durées de vie d’un DBContext).

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Implémentation du référentiel et une unité de travail des modèles dans une Application ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Stratégies d’implémentation pour le référentiel de modèle avec Entity Framework, Dapper et chaîner**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesar de la Torre. Comparaison des durées de vie du service ASP.NET Core IoC conteneur avec des étendues d’instance Autofac IoC conteneur**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mappage de table

Mappage de table identifie les données de table pour être interrogées à partir d’et enregistrées dans la base de données. Précédemment, vous avez vu comment les entités de domaine (par exemple, un domaine de produit ou de l’ordre) peuvent servir pour générer un schéma de base de données associée. EF est fortement conçu autour du concept de *conventions*. Conventions répondre aux questions telles que « Ce que le nom d’une table sera ? » ou « quelle propriété est la clé primaire ? » Conventions sont généralement basées sur des noms conventionnels, par exemple, il est généralement utilisé pour la clé primaire à une propriété qui se termine par le code.

Par convention, chaque entité est configurée pour mapper à une table avec le même nom que le DbSet&lt;TEntity&gt; propriété qui expose l’entité dans le contexte dérivée. Si aucun DbSet&lt;TEntity&gt; valeur est fournie pour l’entité donnée, le nom de classe est utilisé.

### <a name="data-annotations-versus-fluent-api"></a>Annotations de données par rapport à l’API Fluent

Il existe de nombreuses conventions EF Core supplémentaires et la plupart d'entre elles peut être modifiée à l’aide des annotations de données ou des API Fluent, implémentée dans la méthode OnModelCreating.

Annotations de données doivent être utilisées sur les classes de modèle d’entité, qui est un moyen plus contraignant du point de vue DDD. Il s’agit, car vous sont duplication votre modèle avec des annotations de données liées à la base de données de l’infrastructure. En revanche, les API Fluent est un moyen pratique pour modifier la plupart des conventions et des mappages dans la couche infrastructure de persistance de données, le modèle d’entité est donc propre et découplées à partir de l’infrastructure de persistance.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>API Fluent et la méthode OnModelCreating

Comme mentionné, afin de modifier les mappages et les conventions, vous pouvez utiliser la méthode OnModelCreating dans la classe DbContext. L’exemple suivant montre comment procéder dans l’ordre de tri microservice dans eShopOnContainers.

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

Vous pouvez définir tous les mappages de l’API Fluent au sein de la même méthode OnModelCreating, mais il est recommandé que le code de la partition et avoir plusieurs submethods, une par une entité, comme indiqué dans l’exemple. Pour les modèles particulièrement volumineux, il peut même être recommandé d’avoir des fichiers sources distincts (les classes static) pour la configuration de différents types d’entité.

Le code dans l’exemple est explicit. Toutefois, les conventions EF Core faire la plupart de ces automatiquement, le code réel, que vous devez écrire parvenir au même résultat serait beaucoup plus petit.

### <a name="the-hilo-algorithm-in-ef-core"></a>L’algorithme max/min dans EF Core

Un aspect intéressant de code dans l’exemple précédent est qu’il utilise le [max/min algorithme](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) en tant que la stratégie de génération de clés.

L’algorithme max/min est utile lorsque vous avez besoin de clés uniques. Sous forme de résumé, l’algorithme Hi-Lo affecte les identificateurs uniques pour les lignes de la table pendant ne pas selon le stockage de la ligne dans la base de données immédiatement. Cela vous permet de démarrer l’utilisation des identificateurs immédiatement, comme cela arrive avec régulière séquentielle de base de données ID.

L’algorithme max/min décrit un mécanisme pour générer des ID sécurisés sur le côté client plutôt que dans la base de données. *Safe* dans ce contexte signifie sans collisions. Cet algorithme est intéressant pour les raisons suivantes :

-   Il n’interrompt pas le modèle de l’unité de travail.

-   Il ne nécessite pas les boucles, les générateurs de séquence de façon faire dans les autres SGBD.

-   Il génère un identificateur contrôlable de visu, contrairement aux techniques qui utilisent des GUID.

Prend en charge de EF Core [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) avec la méthode ForSqlServerUseSequenceHiLo, comme indiqué dans l’exemple précédent.

### <a name="mapping-fields-instead-of-properties"></a>Mappage de champs au lieu des propriétés

Avec la fonctionnalité de EF Core 1.1 qui mappe les colonnes à des champs, il est possible de ne pas utiliser toutes les propriétés dans la classe d’entité et simplement pour mapper les colonnes d’une table aux champs. Une utilisation courante pour qui serait des champs privés pour n’importe quel état interne qui ne doivent pas être accessible de l’extérieur de l’entité.

EF 1.1 prend en charge permet de mapper un champ sans une propriété associée à une colonne dans la base de données. Cela avec champs uniques ou également avec des collections, comme une liste&lt; &gt; champ. Ce point a été indiqué précédemment, lorsque nous avons abordée modélisation les classes de modèle de domaine, mais ici, vous pouvez voir comment ce mappage est effectué avec la configuration PropertyAccessMode.Field mis en surbrillance dans le code précédent.

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>À l’aide d’occulter les propriétés dans les objets de valeur pour les identifiants masqués au niveau de l’infrastructure

Clichés instantanés dans EF Core les propriétés qui n’existent pas dans votre modèle de classe d’entité. Les valeurs et les États de ces propriétés sont conservées uniquement dans le [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) classe au niveau de l’infrastructure.

À partir d’un point de vue DDD, occulter les propriétés sont un moyen pratique d’implémenter des objets de valeur en masquant l’ID comme clé primaire propriété clichés instantanés. Ceci est important, car un objet de valeur ne doit pas avoir identité (au moins, vous n’aurez pas l’ID de la couche de modèle de domaine lors de la mise en forme des objets de valeur). Le point ici est que, à compter de la version actuelle du noyau de EF, EF Core n’a pas un moyen d’implémenter des objets de valeur en tant que [types complexes](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), que possible dans EF 6.x. C’est pourquoi vous avez pas besoin d’implémenter un objet de valeur comme une entité avec un ID masqué (clé primaire), définie comme une propriété de clichés instantanés.

Comme vous pouvez le voir dans le [objet de valeur d’adresse](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) dans eShopOnContainers, dans le modèle d’adresse vous ne voyez pas un ID :

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

En pratique, nous devons fournir un ID afin que EF Core est en mesure de conserver ces données dans les tables de base de données. Cela se fait dans la méthode ConfigureAddress de la [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) classe au niveau de l’infrastructure, afin de nous pollue pas pas le modèle de domaine avec le code d’infrastructure EF.

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

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Mappage de table**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Permet de générer des clés avec Entity Framework Core HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Sauvegarde des champs**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Encapsulé de Collections dans Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Propriétés de clichés instantanés**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[Précédente] (infrastructure-persistance-layer-design.md) [suivant] (nosql-base de données-persistance-infrastructure.md)
