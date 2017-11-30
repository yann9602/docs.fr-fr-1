---
title: "Création d’un simple microservice CRUD piloté par les données"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Création d’un simple microservice CRUD piloté par les données"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="f71bf-104">Création d’un simple microservice CRUD piloté par les données</span><span class="sxs-lookup"><span data-stu-id="f71bf-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="f71bf-105">Cette section décrit comment créer un simple microservice effectue créer, lire, mettre à jour et les opérations de suppression (CRUD) sur une source de données.</span><span class="sxs-lookup"><span data-stu-id="f71bf-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="f71bf-106">Conception d’un microservice CRUD simple</span><span class="sxs-lookup"><span data-stu-id="f71bf-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="f71bf-107">Du point de vue de la conception, ce type de microservice en conteneur est très simple.</span><span class="sxs-lookup"><span data-stu-id="f71bf-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="f71bf-108">Peut-être résoudre le problème est simple, ou l’implémentation est peut-être une preuve de concept uniquement.</span><span class="sxs-lookup"><span data-stu-id="f71bf-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="f71bf-109">**Figure 8-4**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-109">**Figure 8-4**.</span></span> <span data-ttu-id="f71bf-110">Conception interne pour simple CRUD microservices</span><span class="sxs-lookup"><span data-stu-id="f71bf-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="f71bf-111">Un exemple de ce type de service de lecteur de données simple est le catalogue microservice à partir de l’exemple d’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f71bf-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="f71bf-112">Ce type de service implémente toutes ses fonctionnalités dans un seul projet de l’API Web ASP.NET principale qui inclut des classes pour son modèle de données, sa logique d’entreprise et son code d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="f71bf-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="f71bf-113">Il stocke ses données associées dans une base de données en cours d’exécution dans SQL Server (comme un autre conteneur à des fins de développement/test), mais vous peut également être n’importe quel hôte de SQL Server standard, comme illustré dans la Figure 8-5.</span><span class="sxs-lookup"><span data-stu-id="f71bf-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="f71bf-114">**Figure 8-5**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-114">**Figure 8-5**.</span></span> <span data-ttu-id="f71bf-115">Conception de microservice de données-driven/CRUD simple</span><span class="sxs-lookup"><span data-stu-id="f71bf-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="f71bf-116">Lorsque vous développez ce type de service, vous devez uniquement [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) et une API d’accès aux données ou les ORM, par exemple [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="f71bf-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="f71bf-117">Vous pouvez également générer [Swagger](http://swagger.io/) automatiquement par le biais de métadonnées [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) pour fournir une description des fonctions proposées par votre service, comme expliqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="f71bf-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="f71bf-118">Notez qu’un serveur de base de données tel que SQL Server dans un conteneur Docker est idéal pour les environnements de développement, car vous pouvez avoir toutes les dépendances de votre en cours d’exécution et en cours d’exécution sans avoir à configurer une base de données dans le nuage ou sur site.</span><span class="sxs-lookup"><span data-stu-id="f71bf-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="f71bf-119">Cela est très utile lors de l’intégration en cours d’exécution de tests.</span><span class="sxs-lookup"><span data-stu-id="f71bf-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="f71bf-120">Toutefois, pour les environnements de production, un serveur de base de données en cours d’exécution dans un conteneur est déconseillé, car vous n’obtiendrez généralement pas de haute disponibilité avec cette approche.</span><span class="sxs-lookup"><span data-stu-id="f71bf-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="f71bf-121">Pour un environnement de production dans Azure, il est recommandé d’utiliser de base de données SQL Azure ou une autre technologie de base de données qui peut fournir une haute disponibilité et une haute évolutivité.</span><span class="sxs-lookup"><span data-stu-id="f71bf-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="f71bf-122">Par exemple, une approche NoSQL, vous pouvez choisir de DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="f71bf-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="f71bf-123">Enfin, en modifiant les fichiers de métadonnées Dockerfile et docker-compose.yml, vous pouvez configurer création de l’image de ce conteneur, quelle image de base sera utiliser et concevoir des paramètres tels que les noms internes et externes et les ports TCP.</span><span class="sxs-lookup"><span data-stu-id="f71bf-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="f71bf-124">Implémentation d’un microservice CRUD simple avec ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f71bf-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="f71bf-125">Pour implémenter un microservice CRUD simple à l’aide de .NET Core et Visual Studio, commencez par créer un projet de l’API Web ASP.NET principale simple (en cours d’exécution sur .NET Core afin qu’il puisse s’exécuter sur un hôte Linux Docker), comme indiqué dans la Figure 8-6.</span><span class="sxs-lookup"><span data-stu-id="f71bf-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="f71bf-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="f71bf-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="f71bf-127">**Figure 8-6**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-127">**Figure 8-6**.</span></span> <span data-ttu-id="f71bf-128">Création d’un projet de l’API Web ASP.NET principale dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f71bf-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="f71bf-129">Après avoir créé le projet, vous pouvez implémenter vos contrôleurs MVC comme vous le feriez dans n’importe quel autre projet d’API Web, à l’aide de l’API Entity Framework ou autres API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="f71bf-130">Dans le projet eShopOnContainers.Catalog.API, vous pouvez voir que les dépendances principales pour ce microservice sont simplement ASP.NET Core lui-même, Entity Framework et Swashbuckle, comme indiqué dans la Figure 8-7.</span><span class="sxs-lookup"><span data-stu-id="f71bf-130">In the eShopOnContainers.Catalog.API project, you can see that the main dependencies for that microservice are just ASP.NET Core itself, Entity Framework, and Swashbuckle, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="f71bf-131">**Figure 8-7**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-131">**Figure 8-7**.</span></span> <span data-ttu-id="f71bf-132">Dépendances dans un microservice CRUD Web API simple</span><span class="sxs-lookup"><span data-stu-id="f71bf-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="f71bf-133">Implémentation de services d’API Web de CRUD avec Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="f71bf-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="f71bf-134">Entity Framework (EF) Core est léger et extensible, et version inter-plateformes des données Entity Framework populaires technologie d’accès.</span><span class="sxs-lookup"><span data-stu-id="f71bf-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="f71bf-135">EF Core est un mappeur objet / relationnel (ORM) qui permet aux développeurs .NET travailler avec une base de données à l’aide d’objets .NET.</span><span class="sxs-lookup"><span data-stu-id="f71bf-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="f71bf-136">Le catalogue microservice utilise EF et le fournisseur SQL Server, car sa base de données est en cours d’exécution dans un conteneur avec SQL Server pour une image Docker de Linux.</span><span class="sxs-lookup"><span data-stu-id="f71bf-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="f71bf-137">Toutefois, la base de données peut être déployé dans n’importe quel serveur SQL, tels que Windows local ou de la base de données SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="f71bf-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="f71bf-138">La seule chose que vous devez modifier est la chaîne de connexion dans l’API Web ASP.NET microservice.</span><span class="sxs-lookup"><span data-stu-id="f71bf-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="add-entity-framework-core-to-your-dependencies"></a><span data-ttu-id="f71bf-139">Ajouter d’Entity Framework Core à vos dépendances</span><span class="sxs-lookup"><span data-stu-id="f71bf-139">Add Entity Framework Core to your dependencies</span></span>

<span data-ttu-id="f71bf-140">Vous pouvez installer le package NuGet pour le fournisseur de base de données que vous souhaitez utiliser, dans ce cas, SQL Server, à partir de l’IDE de Visual Studio ou avec la console de NuGet.</span><span class="sxs-lookup"><span data-stu-id="f71bf-140">You can install the NuGet package for the database provider you want to use, in this case SQL Server, from within the Visual Studio IDE or with the NuGet console.</span></span> <span data-ttu-id="f71bf-141">Utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="f71bf-141">Use the following command:</span></span>

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a><span data-ttu-id="f71bf-142">Le modèle de données</span><span class="sxs-lookup"><span data-stu-id="f71bf-142">The data model</span></span>

<span data-ttu-id="f71bf-143">Avec EF de base, l’accès aux données est effectuée à l’aide d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="f71bf-143">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="f71bf-144">Un modèle est composé de classes d’entité et un contexte dérivé qui représente une session avec la base de données, ce qui vous permet d’interroger et d’enregistrer des données.</span><span class="sxs-lookup"><span data-stu-id="f71bf-144">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="f71bf-145">Vous pouvez générer un modèle à partir d’une base de données existante, manuellement un modèle pour correspondre à votre base de données de code ou utiliser les migrations EF pour créer une base de données à partir de votre modèle (et évolue au même rythme que votre modèle change au fil du temps).</span><span class="sxs-lookup"><span data-stu-id="f71bf-145">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="f71bf-146">Pour le catalogue microservice, nous utilisons la dernière approche.</span><span class="sxs-lookup"><span data-stu-id="f71bf-146">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="f71bf-147">Vous pouvez voir un exemple de la classe d’entité CatalogItem dans l’exemple de code suivant, qui est un simple objet CLR simple ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) classe d’entité.</span><span class="sxs-lookup"><span data-stu-id="f71bf-147">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

<span data-ttu-id="f71bf-148">Vous devez également un DbContext qui représente une session avec la base de données.</span><span class="sxs-lookup"><span data-stu-id="f71bf-148">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="f71bf-149">Pour le catalogue microservice, la classe CatalogContext dérive de la classe de base DbContext, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f71bf-149">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }

    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

<span data-ttu-id="f71bf-150">Vous pouvez avoir code supplémentaire dans l’implémentation de DbContext.</span><span class="sxs-lookup"><span data-stu-id="f71bf-150">You can have additional code in the DbContext implementation.</span></span> <span data-ttu-id="f71bf-151">Par exemple, dans l’exemple d’application, nous avons une méthode OnModelCreating dans la classe CatalogContext qui remplit automatiquement la première fois, qu'il essaie d’accéder à la base de données à l’exemple de données.</span><span class="sxs-lookup"><span data-stu-id="f71bf-151">For example, in the sample application, we have an OnModelCreating method in the CatalogContext class that automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="f71bf-152">Cette méthode est utile pour les données de démonstration.</span><span class="sxs-lookup"><span data-stu-id="f71bf-152">This method is useful for demo data.</span></span> <span data-ttu-id="f71bf-153">Vous pouvez également utiliser la méthode OnModelCreating pour personnaliser les mappages d’entité objet/base de données avec nombreux autres [points d’extensibilité EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="f71bf-153">You can also use the OnModelCreating method to customize object/database entity mappings with many other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

<span data-ttu-id="f71bf-154">Vous pouvez afficher plus de détails sur OnModelCreating dans le [mise en œuvre de la couche de persistance de l’infrastructure avec Entity Framework Core](#implementing_infrastructure_persistence) section plus loin dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="f71bf-154">You can see further details about OnModelCreating in the [Implementing the infrastructure-persistence layer with Entity Framework Core](#implementing_infrastructure_persistence) section later in this book.</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="f71bf-155">Interrogation des données à partir des contrôleurs de l’API Web</span><span class="sxs-lookup"><span data-stu-id="f71bf-155">Querying data from Web API controllers</span></span>

<span data-ttu-id="f71bf-156">Instances de vos classes d’entité sont généralement récupérées à partir de la base de données à l’aide de Language Integrated Query (LINQ), comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f71bf-156">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10,
    [FromQuery]int pageIndex = 0)
    {
        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();
        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();
        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);
        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);
        return Ok(model);
    } 

    //...
}
```

##### <a name="saving-data"></a><span data-ttu-id="f71bf-157">L’enregistrement de données</span><span class="sxs-lookup"><span data-stu-id="f71bf-157">Saving data</span></span>

<span data-ttu-id="f71bf-158">Données sont créées, supprimées et modifiées dans la base de données à l’aide d’instances de vos classes d’entité.</span><span class="sxs-lookup"><span data-stu-id="f71bf-158">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="f71bf-159">Vous pouvez ajouter le code exemple suivant codée en dur (données fictives dans ce cas) à vos contrôleurs de l’API Web.</span><span class="sxs-lookup"><span data-stu-id="f71bf-159">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="f71bf-160">Injection de dépendances dans les contrôleurs ASP.NET Core et API Web</span><span class="sxs-lookup"><span data-stu-id="f71bf-160">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="f71bf-161">Dans ASP.NET Core, vous pouvez utiliser l’Injection de dépendance (DI) prêtes à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="f71bf-161">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="f71bf-162">Il est inutile configurer un conteneur Inversion de contrôle (IoC) tiers, même si votre conteneur inversion de contrôle par défaut peut s’intégrer à l’infrastructure ASP.NET Core si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="f71bf-162">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="f71bf-163">Dans ce cas, cela signifie que vous pouvez injecter directement le requis DBContext EF ou autres référentiels via le constructeur du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="f71bf-163">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="f71bf-164">Dans l’exemple ci-dessus de la classe CatalogController, nous allons injecter un objet de type de CatalogContext ainsi que les autres objets par le biais du constructeur CatalogController.</span><span class="sxs-lookup"><span data-stu-id="f71bf-164">In the example above of the CatalogController class, we are injecting an object of CatalogContext type plus other objects through the CatalogController constructor.</span></span>

<span data-ttu-id="f71bf-165">Une configuration importante de dans le projet d’API Web est l’inscription de la classe DbContext dans le conteneur d’inversion de contrôle du service.</span><span class="sxs-lookup"><span data-stu-id="f71bf-165">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="f71bf-166">En général, cela dans la classe de démarrage en appelant les services. Méthode AddDbContext à l’intérieur de la méthode ConfigureServices, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f71bf-166">You typically do so in the Startup class by calling the services.AddDbContext method inside the ConfigureServices method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
               typeof(Startup).
               GetTypeInfo().
               Assembly.
               GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...

}
```

### <a name="additional-resources"></a><span data-ttu-id="f71bf-167">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f71bf-167">Additional resources</span></span>

-   <span data-ttu-id="f71bf-168">**Interrogation des données**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="f71bf-168">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="f71bf-169">**L’enregistrement de données**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="f71bf-169">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="f71bf-170">Les variables de chaîne et l’environnement de connexion base de données utilisées par les conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="f71bf-170">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="f71bf-171">Vous pouvez utiliser les paramètres ASP.NET Core et ajouter une propriété ConnectionString à votre fichier settings.json comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f71bf-171">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```csharp
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

<span data-ttu-id="f71bf-172">Le fichier settings.json peut avoir des valeurs par défaut pour la propriété ConnectionString ou pour toute autre propriété.</span><span class="sxs-lookup"><span data-stu-id="f71bf-172">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="f71bf-173">Toutefois, ces propriétés seront être remplacées par les valeurs des variables d’environnement que vous spécifiez dans le fichier compose.override.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="f71bf-173">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file.</span></span>

<span data-ttu-id="f71bf-174">À partir de vos fichiers docker-compose.yml ou compose.override.yml de docker, vous pouvez initialiser les variables d’environnement afin que Docker sera configurez-les en tant que variables d’environnement du système d’exploitation, comme indiqué dans le fichier docker-compose.override.yml suivant (la connexion chaîne et les autres lignes encapsulent dans cet exemple, mais il ne serait pas encapsuler dans votre propre fichier).</span><span class="sxs-lookup"><span data-stu-id="f71bf-174">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

<span data-ttu-id="f71bf-175">Les fichiers compose.yml de docker au niveau de la solution pas ne sont plus flexibles que les fichiers de configuration au niveau du projet ou microservice, mais également plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="f71bf-175">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure.</span></span> <span data-ttu-id="f71bf-176">Considérez que les images Docker que vous générez par microservice ne contiennent pas le compose.yml de docker de fichiers, uniquement les fichiers binaires et les fichiers de configuration pour chaque microservice, y compris le fichier Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="f71bf-176">Consider that the Docker images that you build per microservice do not contain the docker-compose.yml files, only binary files and configuration files for each microservice, including the Dockerfile.</span></span> <span data-ttu-id="f71bf-177">Mais le fichier docker-compose.yml n’est pas déployé avec votre application ; Il est utilisé uniquement au moment du déploiement.</span><span class="sxs-lookup"><span data-stu-id="f71bf-177">But the docker-compose.yml file is not deployed along with your application; it is used only at deployment time.</span></span> <span data-ttu-id="f71bf-178">Par conséquent, il est plus sécurisé que le placement de ces valeurs dans les fichiers de configuration .NET standards qui sont déployés avec votre code de placer des valeurs de variables d’environnement dans les fichiers de docker-compose.yml (même sans chiffrer les valeurs).</span><span class="sxs-lookup"><span data-stu-id="f71bf-178">Therefore, placing environment variables values in those docker-compose.yml files (even without encrypting the values) is more secure than placing those values in regular .NET configuration files that are deployed with your code.</span></span>

<span data-ttu-id="f71bf-179">Enfin, vous pouvez obtenir cette valeur à partir de votre code à l’aide de Configuration\[« ConnectionString »\], comme illustré dans la méthode ConfigureServices dans un exemple de code précédent.</span><span class="sxs-lookup"><span data-stu-id="f71bf-179">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="f71bf-180">Toutefois, pour les environnements de production, vous pouvez à d’autres moyens de l’Explorateur sur la façon de stocker des secrets, comme les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="f71bf-180">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="f71bf-181">Généralement qui seront gérés par votre orchestrator choisi, comme vous le feriez avec [Docker Swarm de gestion de clés secrètes](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="f71bf-181">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="f71bf-182">Implémenter le contrôle de version dans les API Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f71bf-182">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="f71bf-183">En fonction de besoins de l’entreprise, des regroupements de ressources peuvent être ajoutés, les relations entre les ressources peuvent changer et la structure des données de ressources peut être modifiée.</span><span class="sxs-lookup"><span data-stu-id="f71bf-183">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="f71bf-184">Une API Web pour gérer les nouvelles exigences en matière de mise à jour est un processus relativement simple, mais vous devez prendre en compte les effets de ces modifications sur l’utilisation de l’API Web des applications clientes.</span><span class="sxs-lookup"><span data-stu-id="f71bf-184">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="f71bf-185">Bien que le développeur de conception et implémentation d’une API Web dispose d’un contrôle total sur cette API, le développeur n’a pas le même degré de contrôle sur les applications clientes qui peuvent être générées par des organisations tierce partie d’exploitation à distance.</span><span class="sxs-lookup"><span data-stu-id="f71bf-185">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="f71bf-186">Le contrôle de version permet à une API Web indiquer les fonctionnalités et les ressources qu’il expose.</span><span class="sxs-lookup"><span data-stu-id="f71bf-186">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="f71bf-187">Une application cliente peut ensuite soumettre les demandes vers une version spécifique d’une fonctionnalité ou d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="f71bf-187">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="f71bf-188">Il existe plusieurs approches pour implémenter le contrôle de version :</span><span class="sxs-lookup"><span data-stu-id="f71bf-188">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="f71bf-189">Contrôle de version URI</span><span class="sxs-lookup"><span data-stu-id="f71bf-189">URI versioning</span></span>

-   <span data-ttu-id="f71bf-190">Version de chaîne de requête</span><span class="sxs-lookup"><span data-stu-id="f71bf-190">Query string versioning</span></span>

-   <span data-ttu-id="f71bf-191">Contrôle de version en-tête</span><span class="sxs-lookup"><span data-stu-id="f71bf-191">Header versioning</span></span>

<span data-ttu-id="f71bf-192">Chaîne de requête et le contrôle de version URI sont le plus simple à implémenter.</span><span class="sxs-lookup"><span data-stu-id="f71bf-192">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="f71bf-193">Le contrôle de version en-tête est une bonne approche.</span><span class="sxs-lookup"><span data-stu-id="f71bf-193">Header versioning is a good approach.</span></span> <span data-ttu-id="f71bf-194">Toutefois, le contrôle de version en-tête pas aussi explicite et simple que le contrôle de version URI.</span><span class="sxs-lookup"><span data-stu-id="f71bf-194">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="f71bf-195">Étant donné que le contrôle de version URL est la plus simple et la plus explicite, l’exemple d’application eShopOnContainers utilise le contrôle de version URI.</span><span class="sxs-lookup"><span data-stu-id="f71bf-195">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="f71bf-196">Avec le contrôle de version URI, comme dans l’exemple d’application eShopOnContainers, chaque fois que vous modifiez l’API Web ou que vous modifiez le schéma de ressources, vous ajoutez un numéro de version à l’URI pour chaque ressource.</span><span class="sxs-lookup"><span data-stu-id="f71bf-196">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="f71bf-197">URI existants doit continuer à fonctionner comme avant, retournant des ressources qui sont conformes au schéma qui correspond à la version demandée.</span><span class="sxs-lookup"><span data-stu-id="f71bf-197">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="f71bf-198">Comme indiqué dans l’exemple de code suivant, la version peut être définie à l’aide de l’attribut d’itinéraire dans l’API Web, ce qui rend la version explicite dans l’URI (v1 dans ce cas).</span><span class="sxs-lookup"><span data-stu-id="f71bf-198">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="f71bf-199">Ce mécanisme de contrôle de version est simple et dépend du serveur de routage de la demande au point de terminaison approprié.</span><span class="sxs-lookup"><span data-stu-id="f71bf-199">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="f71bf-200">Toutefois, pour une gestion des versions plus sophistiquées et la meilleure méthode si vous utilisez REST, vous utilisez hypermédia et implémenter [HATEOAS (Hypertext en tant que le moteur d’état de l’Application)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="f71bf-200">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f71bf-201">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f71bf-201">Additional resources</span></span>

-   <span data-ttu-id="f71bf-202">**Scott Hanselman. Contrôle de version de l’API Web RESTful principale ASP.NET facilité**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="f71bf-202">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="f71bf-203">**Contrôle de version une API RESTful web**</span><span class="sxs-lookup"><span data-stu-id="f71bf-203">**Versioning a RESTful web API**</span></span>

    [<span data-ttu-id="f71bf-204">*https://docs.Microsoft.com/Azure/architecture/Best-Practices/API-Design#versioning-a-RESTful-Web-API*</span><span class="sxs-lookup"><span data-stu-id="f71bf-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   <span data-ttu-id="f71bf-205">**Roy fielding d’a. Le contrôle de version, hypermédia et reste**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="f71bf-205">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="f71bf-206">Génération des métadonnées de description de Swagger à partir de votre API Web de base ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f71bf-206">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="f71bf-207">[Swagger](http://swagger.io/) est une infrastructure couramment utilisés open source qui est soutenu par un grand écosystème d’outils qui vous permet de conception, de génération, de document et de consommer vos API RESTful.</span><span class="sxs-lookup"><span data-stu-id="f71bf-207">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="f71bf-208">Il est devenu la norme pour le domaine de métadonnées de description API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-208">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="f71bf-209">Vous devez inclure les métadonnées de description Swagger avec n’importe quel type de microservice, pilotés par les données de microservices soit plus avancé microservices de domaine (comme expliqué dans la section suivante).</span><span class="sxs-lookup"><span data-stu-id="f71bf-209">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="f71bf-210">Le cœur de Swagger est la spécification de Swagger, qui est l’API des métadonnées de description dans un fichier JSON ou YAML.</span><span class="sxs-lookup"><span data-stu-id="f71bf-210">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="f71bf-211">La spécification crée le contrat RESTful votre API, détaillant toutes ses ressources et opérations dans les deux un homme et machine readable format pour le développement, de découverte et d’intégration.</span><span class="sxs-lookup"><span data-stu-id="f71bf-211">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="f71bf-212">La spécification est la base de la spécification OpenAPI (OEA) et est développée dans une communauté open, transparente et de collaboration pour normaliser la façon dont les interfaces RESTful sont définies.</span><span class="sxs-lookup"><span data-stu-id="f71bf-212">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="f71bf-213">La spécification définit la structure pour le mode de détection de service et comment ses fonctionnalités compris.</span><span class="sxs-lookup"><span data-stu-id="f71bf-213">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="f71bf-214">Pour plus d’informations, notamment un éditeur web et des exemples de spécifications de Swagger d’entreprises comme Spotify, Uber, la marge et Microsoft, consultez le site Swagger (<http://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="f71bf-214">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="f71bf-215">Pourquoi utiliser Swagger ?</span><span class="sxs-lookup"><span data-stu-id="f71bf-215">Why use Swagger?</span></span>

<span data-ttu-id="f71bf-216">Voici les raisons principales pour générer des métadonnées Swagger pour votre API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-216">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="f71bf-217">**Possibilité pour les autres produits de consommer automatiquement et d’intégrer vos API**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-217">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="f71bf-218">Des dizaines de produits et [outils professionnelle](http://swagger.io/commercial-tools/) et plusieurs [bibliothèques et infrastructures](http://swagger.io/open-source-integrations/) Swagger de prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="f71bf-218">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="f71bf-219">Microsoft a des produits de haut niveau et des outils qui peuvent consommer automatiquement les API Swagger, tels que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f71bf-219">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="f71bf-220">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="f71bf-220">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="f71bf-221">Vous pouvez générer automatiquement des classes de client .NET pour l’appel de Swagger.</span><span class="sxs-lookup"><span data-stu-id="f71bf-221">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="f71bf-222">This</span><span class="sxs-lookup"><span data-stu-id="f71bf-222">This</span></span>

-   <span data-ttu-id="f71bf-223">outil peut être utilisé à partir de l’interface CLI et il intègre également Visual Studio pour une utilisation simple via l’interface utilisateur graphique.</span><span class="sxs-lookup"><span data-stu-id="f71bf-223">tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="f71bf-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="f71bf-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="f71bf-225">Vous pouvez automatiquement [et s’intègrent votre API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) dans un flux de travail Microsoft Flow haut niveau, sans aucune programmation compétences requises.</span><span class="sxs-lookup"><span data-stu-id="f71bf-225">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="f71bf-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="f71bf-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="f71bf-227">Vous pouvez consommer automatiquement votre API à partir de [PowerApps des applications mobiles](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) intègrent [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), avec aucune compétence de programmation requis.</span><span class="sxs-lookup"><span data-stu-id="f71bf-227">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="f71bf-228">[Service d’applications Azure Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="f71bf-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="f71bf-229">Vous pouvez automatiquement [et s’intègrent votre API dans une application Azure App Service logique](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), avec aucune compétence de programmation requis.</span><span class="sxs-lookup"><span data-stu-id="f71bf-229">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="f71bf-230">**Possibilité de générer automatiquement la documentation de l’API**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-230">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="f71bf-231">Lorsque vous créez des API RESTful à grande échelle, tels que les applications microservice complexes, vous devez gérer de nombreux points de terminaison avec différents modèles de données utilisés dans les charges utiles de demande et de réponse.</span><span class="sxs-lookup"><span data-stu-id="f71bf-231">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="f71bf-232">En la documentation appropriée et un solid Explorateur d’API, que vous obtenez avec Swagger, sont la clé pour la réussite de votre API et l’adoption par les développeurs.</span><span class="sxs-lookup"><span data-stu-id="f71bf-232">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="f71bf-233">Métadonnées de swagger sont ce que Microsoft Flow, PowerApps et Azure Logic Apps permet de comprendre comment utiliser les API et s’y connecter.</span><span class="sxs-lookup"><span data-stu-id="f71bf-233">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="f71bf-234">Comment faire pour automatiser la génération de métadonnées Swagger d’API avec le package NuGet de Swashbuckle</span><span class="sxs-lookup"><span data-stu-id="f71bf-234">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="f71bf-235">Génération des métadonnées Swagger manuellement (dans un fichier JSON ou YAML) peut être fastidieux travail.</span><span class="sxs-lookup"><span data-stu-id="f71bf-235">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="f71bf-236">Toutefois, vous pouvez automatiser la découverte de l’API des services d’API Web ASP.NET à l’aide de la [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) générer dynamiquement des métadonnées de l’API de Swagger.</span><span class="sxs-lookup"><span data-stu-id="f71bf-236">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="f71bf-237">Swashbuckle génère automatiquement les métadonnées Swagger pour vos projets d’API Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f71bf-237">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="f71bf-238">Il prend en charge les projets de l’API Web ASP.NET principale et l’API Web ASP.NET traditionnel et autres version, par exemple Azure API App, l’application Mobile Azure, microservices Azure Service Fabric reposant sur ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f71bf-238">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="f71bf-239">Il prend également en charge les API Web simple déployé sur les conteneurs, comme dans pour l’application de référence.</span><span class="sxs-lookup"><span data-stu-id="f71bf-239">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="f71bf-240">Swashbuckle combine Explorateur d’API et Swagger ou [swagger-ui](https://github.com/swagger-api/swagger-ui) pour fournir une détection riche documentation expérience et pour les consommateurs de votre API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-240">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="f71bf-241">En plus de son moteur de générateur de métadonnées Swagger, Swashbuckle contient également une version incorporée de swagger-ui, il sera automatiquement dynamisent lorsque Swashbuckle est installé.</span><span class="sxs-lookup"><span data-stu-id="f71bf-241">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="f71bf-242">Cela signifie que vous pouvez compléter votre API avec une découverte intéressante l’interface utilisateur pour aider les développeurs à utiliser votre API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-242">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="f71bf-243">Elle nécessite très peu de code et de maintenance, car il est généré automatiquement, ce qui vous permet de vous concentrer sur la création de votre API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-243">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="f71bf-244">Le résultat de l’Explorateur d’API se présente comme la Figure 8-8.</span><span class="sxs-lookup"><span data-stu-id="f71bf-244">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="f71bf-245">**Figure 8-8**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-245">**Figure 8-8**.</span></span> <span data-ttu-id="f71bf-246">Explorateur d’API Swashbuckle en fonction de métadonnées Swagger : eShopOnContainers catalogue microservice</span><span class="sxs-lookup"><span data-stu-id="f71bf-246">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="f71bf-247">L’Explorateur d’API n’est pas essentiel ici.</span><span class="sxs-lookup"><span data-stu-id="f71bf-247">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="f71bf-248">Une fois que vous avez une API Web qui peut se décrire lui-même dans les métadonnées Swagger, votre API peut être utilisé en toute transparence à partir de Swagger les outils, y compris les générateurs de code de classe de proxy de client qui peuvent cibler plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="f71bf-248">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="f71bf-249">Par exemple, comme indiqué, [AutoRest](https://github.com/Azure/AutoRest) génère automatiquement les classes de client .NET.</span><span class="sxs-lookup"><span data-stu-id="f71bf-249">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="f71bf-250">Mais d’autres outils tels que [swagger-codegen](https://github.com/swagger-api/swagger-codegen) sont également disponibles, qui autoriser la génération de code du client de l’API de bibliothèques, des stubs de serveur et la documentation automatiquement.</span><span class="sxs-lookup"><span data-stu-id="f71bf-250">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="f71bf-251">Actuellement, Swashbuckle se compose de deux packages NuGet : Swashbuckle.SwaggerGen et Swashbuckle.SwaggerUi.</span><span class="sxs-lookup"><span data-stu-id="f71bf-251">Currently, Swashbuckle consists of two NuGet packages: Swashbuckle.SwaggerGen and Swashbuckle.SwaggerUi.</span></span> <span data-ttu-id="f71bf-252">La première fournit des fonctionnalités permettant de générer un ou plusieurs documents Swagger directement à partir de votre implémentation de l’API et de les exposer en tant que points de terminaison JSON.</span><span class="sxs-lookup"><span data-stu-id="f71bf-252">The former provides functionality to generate one or more Swagger documents directly from your API implementation and expose them as JSON endpoints.</span></span> <span data-ttu-id="f71bf-253">Ce dernier fournit une version incorporée de l’outil de l’interface utilisateur de swagger qui peut être pris en charge par votre application et par les documents de Swagger générés pour décrire votre API Bing Maps.</span><span class="sxs-lookup"><span data-stu-id="f71bf-253">The latter provides an embedded version of the swagger-ui tool that can be served by your application and powered by the generated Swagger documents to describe your API.</span></span> <span data-ttu-id="f71bf-254">Toutefois, les dernières versions de Swashbuckle wrap avec le metapackage Swashbuckle.AspNetCore.</span><span class="sxs-lookup"><span data-stu-id="f71bf-254">However, the latest versions of Swashbuckle wrap these with the Swashbuckle.AspNetCore metapackage.</span></span>

<span data-ttu-id="f71bf-255">Notez que pour les projets .NET Core Web API, vous devez utiliser [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f71bf-255">Note that for .NET Core Web API projects, you need to use [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 or later.</span></span>

<span data-ttu-id="f71bf-256">Après avoir installé ces packages NuGet dans votre projet d’API Web, vous devez configurer Swagger dans la classe de démarrage, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f71bf-256">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
            });
        });
        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUi();
    }
}
```

<span data-ttu-id="f71bf-257">Après cela, vous pouvez démarrer votre application et parcourir les JSON de Swagger et de l’interface utilisateur points de terminaison suivants à l’aide de ces URL :</span><span class="sxs-lookup"><span data-stu-id="f71bf-257">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

<span data-ttu-id="f71bf-258">Vous avez déjà vu l’interface utilisateur générée créé par Swashbuckle pour une URL telle que http://&lt;votre url de racine &gt; /swagger / l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f71bf-258">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="f71bf-259">Dans la Figure 8-9. vous pouvez également voir comment vous pouvez tester n’importe quelle méthode d’API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-259">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="f71bf-260">**Figure 8-9**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-260">**Figure 8-9**.</span></span> <span data-ttu-id="f71bf-261">Swashbuckle UI testing la méthode d’API / des éléments de catalogue</span><span class="sxs-lookup"><span data-stu-id="f71bf-261">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="f71bf-262">Figure 8-10 montre les métadonnées Swagger un JSON générée à partir de la microservice eShopOnContainers (qui est ce que les outils à utiliser en dessous) lorsque vous demandez &lt;votre url de racine&gt;à l’aide de /swagger/v1/swagger.json [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="f71bf-262">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="f71bf-263">**Figure 8-10**.</span><span class="sxs-lookup"><span data-stu-id="f71bf-263">**Figure 8-10**.</span></span> <span data-ttu-id="f71bf-264">Métadonnées JSON swagger</span><span class="sxs-lookup"><span data-stu-id="f71bf-264">Swagger JSON metadata</span></span>

<span data-ttu-id="f71bf-265">Il est très simple.</span><span class="sxs-lookup"><span data-stu-id="f71bf-265">It is that simple.</span></span> <span data-ttu-id="f71bf-266">Et, car il est généré automatiquement, les métadonnées Swagger lorsque vous ajoutez des fonctionnalités à votre API.</span><span class="sxs-lookup"><span data-stu-id="f71bf-266">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f71bf-267">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f71bf-267">Additional resources</span></span>

-   <span data-ttu-id="f71bf-268">**API aide des Pages Web ASP.NET à l’aide de Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="f71bf-268">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f71bf-269">[Précédente] (microservice-application-design.md) [suivant] (multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="f71bf-269">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
