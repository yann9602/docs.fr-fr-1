---
title: "Utiliser des données dans les applications ASP.NET Core"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | utilisation des données dans asp"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648e0a4cdd388cf4a322f0fc049d5dcfca53d54b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="bf34a-103">Utilisation des données dans les applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bf34a-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="bf34a-104">« Données sont une chose précieuse et durent plus longtemps que les systèmes eux-mêmes. »</span><span class="sxs-lookup"><span data-stu-id="bf34a-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="bf34a-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="bf34a-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="bf34a-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="bf34a-106">Summary</span></span>

<span data-ttu-id="bf34a-107">Accès aux données est une partie importante de la plupart des applications logicielles.</span><span class="sxs-lookup"><span data-stu-id="bf34a-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="bf34a-108">ASP.NET Core prend en charge une variété d’options d’accès aux données, y compris l’Entity Framework Core (et ainsi de Entity Framework 6) et peuvent fonctionner avec tout accès de données .NET framework.</span><span class="sxs-lookup"><span data-stu-id="bf34a-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="bf34a-109">Le choix des accès aux données framework à utiliser dépend des besoins de l’application.</span><span class="sxs-lookup"><span data-stu-id="bf34a-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="bf34a-110">En faisant abstraction de ces choix à partir des projets ApplicationCore et l’interface utilisateur et encapsuler les détails d’implémentation dans une Infrastructure, permettant de produire des logiciels faiblement couplée, testable.</span><span class="sxs-lookup"><span data-stu-id="bf34a-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="bf34a-111">Entity Framework Core (pour les bases de données relationnelles)</span><span class="sxs-lookup"><span data-stu-id="bf34a-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="bf34a-112">Si vous écrivez une application ASP.NET Core qui doit fonctionner avec des données relationnelles, Entity Framework Core (noyaux EF) est la méthode recommandée pour votre application à accéder à ses données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="bf34a-113">EF Core est un mappeur objet / relationnel (O/RM) qui permet aux développeurs .NET conserver des objets vers et à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="bf34a-114">Elle élimine la nécessité pour la plupart des développeurs ont généralement besoin d’écrire le code d’accès données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="bf34a-115">Comme ASP.NET Core, EF Core a été réécrit entièrement prise en charge les applications inter-plateformes modulaires.</span><span class="sxs-lookup"><span data-stu-id="bf34a-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="bf34a-116">Vous ajoutez à votre application sous forme de package NuGet, configurez de démarrage et demandez à l’injection de dépendance vous en aurez besoin.</span><span class="sxs-lookup"><span data-stu-id="bf34a-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="bf34a-117">Pour utiliser EF Core avec une base de données SQL Server, exécutez la commande CLI de dotnet à l’adresse suivante :</span><span class="sxs-lookup"><span data-stu-id="bf34a-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="bf34a-118">dotnet ajouter package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="bf34a-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="bf34a-119">Pour ajouter la prise en charge pour une source de données en mémoire, de test :</span><span class="sxs-lookup"><span data-stu-id="bf34a-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="bf34a-120">dotnet ajouter package Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="bf34a-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="bf34a-121">Le DbContext</span><span class="sxs-lookup"><span data-stu-id="bf34a-121">The DbContext</span></span>

<span data-ttu-id="bf34a-122">Pour travailler avec EF de base, vous avez besoin d’une sous-classe de DbContext.</span><span class="sxs-lookup"><span data-stu-id="bf34a-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="bf34a-123">Cette classe contient des propriétés qui représentent des collections d’entités d’avec que votre application fonctionnera.</span><span class="sxs-lookup"><span data-stu-id="bf34a-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="bf34a-124">L’exemple d’eShopOnWeb inclut un CatalogContext avec des collections d’éléments, les marques et les types :</span><span class="sxs-lookup"><span data-stu-id="bf34a-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="bf34a-125">Votre DbContext doit avoir un constructeur qui accepte une DbContextOptions et passer cet argument au constructeur DbContext base.</span><span class="sxs-lookup"><span data-stu-id="bf34a-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="bf34a-126">Notez que si vous avez uniquement un DbContext dans votre application, vous pouvez passer une instance de DbContextOptions, mais si vous avez plusieurs vous devez utiliser les DbContextOptions génériques<T> type, en passant dans votre type DbContext comme paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="bf34a-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="bf34a-127">Configuration des principaux EF</span><span class="sxs-lookup"><span data-stu-id="bf34a-127">Configuring EF Core</span></span>

<span data-ttu-id="bf34a-128">Dans votre application ASP.NET Core, vous devez généralement configurer EF Core dans votre méthode ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="bf34a-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="bf34a-129">EF Core utilise un DbContextOptionsBuilder, qui prend en charge plusieurs méthodes d’extension utile pour simplifier sa configuration.</span><span class="sxs-lookup"><span data-stu-id="bf34a-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="bf34a-130">Pour configurer CatalogContext pour utiliser une base de données SQL Server avec une chaîne de connexion définie dans la Configuration, vous devez ajouter le code suivant à ConfigureServices :</span><span class="sxs-lookup"><span data-stu-id="bf34a-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="bf34a-131">Pour utiliser la base de données en mémoire :</span><span class="sxs-lookup"><span data-stu-id="bf34a-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="bf34a-132">Après avoir installé Core EF, créé un type enfant DbContext et configuré dans ConfigureServices, vous êtes prêt à utiliser EF Core.</span><span class="sxs-lookup"><span data-stu-id="bf34a-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="bf34a-133">Vous pouvez demander une instance de votre type DbContext dans n’importe quel service qui en a besoin et commencer à travailler avec vos entités persistantes à l’aide de LINQ comme s’ils étaient simplement dans une collection.</span><span class="sxs-lookup"><span data-stu-id="bf34a-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="bf34a-134">EF Core effectue le travail de traduire vos expressions LINQ dans les requêtes SQL pour stocker et récupérer vos données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="bf34a-135">Vous pouvez voir les requêtes EF Core s’exécute en configurant un enregistreur d’événements et de garantir son niveau a au moins plus d’informations, comme indiqué dans la Figure 8-1.</span><span class="sxs-lookup"><span data-stu-id="bf34a-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="bf34a-136">Requêtes de journalisation des noyaux EF figure 8-1 à la console</span><span class="sxs-lookup"><span data-stu-id="bf34a-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="bf34a-137">Extraction et stockage des données</span><span class="sxs-lookup"><span data-stu-id="bf34a-137">Fetching and Storing Data</span></span>

<span data-ttu-id="bf34a-138">Pour récupérer des données à partir de EF, vous accédez à la propriété appropriée et utilisez LINQ pour filtrer le résultat.</span><span class="sxs-lookup"><span data-stu-id="bf34a-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="bf34a-139">Vous pouvez également utiliser LINQ pour effectuer la projection, de transformation du résultat d’un type à un autre.</span><span class="sxs-lookup"><span data-stu-id="bf34a-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="bf34a-140">L’exemple suivant permet de récupérer CatalogBrands, classés par nom, filtrés par leur propriété Enabled et projeté sur un type SelectListItem :</span><span class="sxs-lookup"><span data-stu-id="bf34a-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="bf34a-141">Il est important dans l’exemple ci-dessus pour ajouter l’appel à ToListAsync afin d’exécuter la requête immédiatement.</span><span class="sxs-lookup"><span data-stu-id="bf34a-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="bf34a-142">Sinon, l’instruction affectera IQueryable<SelectListItem> à brandItems, qui ne seront pas exécuté avant son énumération.</span><span class="sxs-lookup"><span data-stu-id="bf34a-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="bf34a-143">Voici les avantages et inconvénients à retourner les résultats de IQueryable de méthodes.</span><span class="sxs-lookup"><span data-stu-id="bf34a-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="bf34a-144">Il permet la requête construit pour être modifiée, mais peut également donnent les erreurs qui se produisent uniquement pendant l’exécution, si les opérations sont ajoutées à la requête EF principal ne peut pas traduire EF Core.</span><span class="sxs-lookup"><span data-stu-id="bf34a-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="bf34a-145">Il est généralement plus sûr transmettre tous les filtres dans la méthode d’exécution de l’accès aux données et de retour arrière d’une collection en mémoire (par exemple, liste<T>) comme résultat.</span><span class="sxs-lookup"><span data-stu-id="bf34a-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="bf34a-146">EF Core effectue le suivi des modifications sur les entités qu’il est extrait de la persistance.</span><span class="sxs-lookup"><span data-stu-id="bf34a-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="bf34a-147">Pour enregistrer les modifications apportées à une entité suivie, appelez uniquement la méthode SaveChanges sur le DbContext sorte qu’il soit la même instance de DbContext qui a été utilisée pour récupérer de l’entité.</span><span class="sxs-lookup"><span data-stu-id="bf34a-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="bf34a-148">Ajout et suppression d’entités sont directement sur la propriété DbSet appropriée, en utilisant un appel à SaveChanges pour exécuter les commandes de base de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="bf34a-149">L’exemple suivant illustre l’ajout, la mise à jour et suppression d’entités de la persistance.</span><span class="sxs-lookup"><span data-stu-id="bf34a-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="bf34a-150">EF Core prend en charge à la fois synchrones et asynchrones des méthodes pour l’extraction et l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="bf34a-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="bf34a-151">Dans les applications web, il est recommandé d’utiliser le modèle asynchrones / d’attente avec les méthodes async, afin que les threads du serveur web ne sont pas bloqués lors de l’attente de fin des opérations d’accès des données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="bf34a-152">L’extraction de données associées</span><span class="sxs-lookup"><span data-stu-id="bf34a-152">Fetching Related Data</span></span>

<span data-ttu-id="bf34a-153">Quand EF Core récupère les entités, il remplit toutes les propriétés qui sont stockées directement avec cette entité dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="bf34a-154">Les propriétés de navigation, telles que les listes des entités associées, ne sont pas remplies et peuvent avoir leur valeur est définie sur null.</span><span class="sxs-lookup"><span data-stu-id="bf34a-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="bf34a-155">Cela garantit que EF Core n’extrait pas plus de données que nécessaire, ce qui est particulièrement important pour les applications web qui doivent rapidement traiter les demandes et renvoie des réponses de manière efficace.</span><span class="sxs-lookup"><span data-stu-id="bf34a-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="bf34a-156">Pour inclure des relations à une entité en utilisant *chargement hâtif*, vous spécifiez la propriété à l’aide de la méthode d’extension Include sur la requête, comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="bf34a-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="bf34a-157">Vous pouvez inclure plusieurs relations, et vous pouvez également inclure des relations secondaire à l’aide de ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="bf34a-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="bf34a-158">EF Core exécutera une seule requête pour récupérer le jeu d’entités.</span><span class="sxs-lookup"><span data-stu-id="bf34a-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="bf34a-159">Une autre option de chargement des données connexes consiste à utiliser *chargement explicite*.</span><span class="sxs-lookup"><span data-stu-id="bf34a-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="bf34a-160">Chargement explicite vous permet de charger des données supplémentaires dans une entité qui a déjà été récupérée.</span><span class="sxs-lookup"><span data-stu-id="bf34a-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="bf34a-161">Étant donné que cela implique une demande distincte à la base de données, il n’est pas recommandé pour les applications web qui doivent réduire le nombre de base de données les allers-retours effectuées par demande.</span><span class="sxs-lookup"><span data-stu-id="bf34a-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="bf34a-162">*Chargement différé* est une fonctionnalité qui charge automatiquement les données associées, car il est référencé par l’application.</span><span class="sxs-lookup"><span data-stu-id="bf34a-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="bf34a-163">Il n’est pas actuellement pris en charge par cœur de EF, mais comme avec le chargement explicit il doit généralement être désactivé pour les applications web.</span><span class="sxs-lookup"><span data-stu-id="bf34a-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="bf34a-164">Connexions résilientes</span><span class="sxs-lookup"><span data-stu-id="bf34a-164">Resilient Connections</span></span>

<span data-ttu-id="bf34a-165">Ressources externes telles que des bases de données SQL peuvent parfois être indisponibles.</span><span class="sxs-lookup"><span data-stu-id="bf34a-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="bf34a-166">En cas d’indisponibilité temporaire, applications peuvent utiliser la logique de nouvelle tentative pour éviter de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="bf34a-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="bf34a-167">Cette technique est communément appelé *résilience des connexions*.</span><span class="sxs-lookup"><span data-stu-id="bf34a-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="bf34a-168">Vous pouvez implémenter votre [propre nouvelle tentative avec interruption exponentielle](https://docs.microsoft.com/azure/architecture/patterns/retry) technique en tentant de débarrassée avec un temps d’attente augmente de manière exponentielle, jusqu'à ce qu’un nombre maximal de tentatives a été atteint.</span><span class="sxs-lookup"><span data-stu-id="bf34a-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="bf34a-169">Cette technique prend en compte le fait que les ressources de cloud par intermittence peut-être pas disponibles pour courtes périodes de temps, ce qui entraîne l’échec de certaines demandes.</span><span class="sxs-lookup"><span data-stu-id="bf34a-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="bf34a-170">Pour la base de données SQL Azure, Entity Framework Core fournit déjà la logique de résilience et de nouvelle tentative de connexion de base de données interne.</span><span class="sxs-lookup"><span data-stu-id="bf34a-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="bf34a-171">Mais vous devez activer la stratégie de l’exécution d’Entity Framework pour chaque connexion DbContext si vous souhaitez ayant connexions EF Core.</span><span class="sxs-lookup"><span data-stu-id="bf34a-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="bf34a-172">Par exemple, le code suivant au niveau de la connexion EF Core permet des connexions SQL résilientes qui sont retentées si la connexion échoue.</span><span class="sxs-lookup"><span data-stu-id="bf34a-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="bf34a-173">Stratégies d’exécution et les transactions explicites à l’aide de BeginTransaction et plusieurs DbContexts</span><span class="sxs-lookup"><span data-stu-id="bf34a-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="bf34a-174">Lorsque de nouvelles tentatives sont activées dans les connexions EF Core, chaque opération que vous effectuez à l’aide de EF Core devient son propre opération reproductible.</span><span class="sxs-lookup"><span data-stu-id="bf34a-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="bf34a-175">Chaque requête et chaque appel à SaveChanges va être retentées en tant qu’unité si une défaillance temporaire se produit.</span><span class="sxs-lookup"><span data-stu-id="bf34a-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="bf34a-176">Toutefois, si votre code initie une transaction à l’aide de BeginTransaction, vous définissez votre propre groupe d’opérations qui doivent être traités en tant qu’unité, tous les éléments à l’intérieur de la transaction est restaurée si une défaillance se produit.</span><span class="sxs-lookup"><span data-stu-id="bf34a-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="bf34a-177">Une exception à ce qui suit s’affiche si vous tentez d’exécuter cette transaction lors de l’utilisation d’une stratégie d’exécution EF (stratégie de nouvelle tentative) et vous incluez plusieurs SaveChanges à partir de plusieurs DbContexts qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="bf34a-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="bf34a-178">System.InvalidOperationException : La stratégie d’exécution configurée 'SqlServerRetryingExecutionStrategy' ne prend pas en charge les transactions démarrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bf34a-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="bf34a-179">Utilisez la stratégie d’exécution retournée par 'DbContext.Database.CreateExecutionStrategy()' pour exécuter toutes les opérations dans la transaction comme une unité reproductible.</span><span class="sxs-lookup"><span data-stu-id="bf34a-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="bf34a-180">La solution consiste à appeler manuellement la stratégie d’exécution EF avec un délégué qui représente tous les éléments qui doit être exécutée.</span><span class="sxs-lookup"><span data-stu-id="bf34a-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="bf34a-181">Si une défaillance temporaire se produit, la stratégie d’exécution appelle le délégué à nouveau.</span><span class="sxs-lookup"><span data-stu-id="bf34a-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="bf34a-182">Le code suivant montre comment implémenter cette approche :</span><span class="sxs-lookup"><span data-stu-id="bf34a-182">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="bf34a-183">Le premier DbContext est la \_catalogContext et le second DbContext se trouve dans le \_integrationEventLogService objet.</span><span class="sxs-lookup"><span data-stu-id="bf34a-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="bf34a-184">Enfin, la validation action sera effectuée plusieurs DbContexts et à l’aide d’une stratégie d’exécution EF.</span><span class="sxs-lookup"><span data-stu-id="bf34a-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="bf34a-185">Références : Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="bf34a-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="bf34a-186">**Documentation de base EF**</span><span class="sxs-lookup"><span data-stu-id="bf34a-186">**EF Core Docs**</span></span>  
> <span data-ttu-id="bf34a-187"><https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="bf34a-187"><https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="bf34a-188">**EF principale : Les données associées**</span><span class="sxs-lookup"><span data-stu-id="bf34a-188">**EF Core: Related Data**</span></span>  
> <span data-ttu-id="bf34a-189"><https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="bf34a-189"><https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="bf34a-190">**Éviter le chargement tardif des entités dans les Applications ASPNET**</span><span class="sxs-lookup"><span data-stu-id="bf34a-190">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <span data-ttu-id="bf34a-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="bf34a-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="bf34a-192">EF Core ou micro-ORM ?</span><span class="sxs-lookup"><span data-stu-id="bf34a-192">EF Core or micro-ORM?</span></span>

<span data-ttu-id="bf34a-193">Bien que EF Core est un bon choix pour la gestion de persistance et encapsule pour la plupart des détails de la base de données à partir des développeurs d’applications, il n’est pas le seul choix possible.</span><span class="sxs-lookup"><span data-stu-id="bf34a-193">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="bf34a-194">Une autre solution open source populaires est [Dapper](https://github.com/StackExchange/Dapper), un micro-ORM dit.</span><span class="sxs-lookup"><span data-stu-id="bf34a-194">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="bf34a-195">Un micro-ORM est léger et moins outil complet pour le mappage d’objets à des structures de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-195">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="bf34a-196">Dans le cas Dapper, sa conception objectifs concentrent sur les performances, plutôt qu’entièrement encapsulant sous-jacent interroge utilise pour récupérer et mettre à jour des données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-196">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="bf34a-197">Car il n’abstraite SQL du développeur, Dapper est « la plus proche du métal » et permet aux développeurs d’écrire le texte exact à utiliser pour une donnée de requêtes accéder à l’opération.</span><span class="sxs-lookup"><span data-stu-id="bf34a-197">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="bf34a-198">EF Core a deux fonctionnalités importantes, il fournit qui séparer de Dapper, mais également ajouter à une surcharge de ses performances.</span><span class="sxs-lookup"><span data-stu-id="bf34a-198">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="bf34a-199">La première est la traduction à partir d’expressions LINQ dans SQL.</span><span class="sxs-lookup"><span data-stu-id="bf34a-199">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="bf34a-200">Ces conversions sont mis en cache, mais même dans ce cas il est surcharge lors de la première fois.</span><span class="sxs-lookup"><span data-stu-id="bf34a-200">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="bf34a-201">Le deuxième est le suivi des modifications sur les entités (de sorte que les instructions de mise à jour efficace peuvent être générées).</span><span class="sxs-lookup"><span data-stu-id="bf34a-201">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="bf34a-202">Ce comportement peut être désactivé pour des requêtes spécifiques à l’aide de l’extension AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="bf34a-202">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="bf34a-203">EF Core génère également des requêtes SQL qui sont généralement très efficace et dans tous les cas parfaitement acceptable à partir d’un point de vue des performances, mais si vous avez besoin de fine contrôler la requête précise doit être exécutée, vous pouvez passer dans SQL personnalisée (ou exécuter une procédure stockée) à l’aide de EF Principaux trop.</span><span class="sxs-lookup"><span data-stu-id="bf34a-203">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="bf34a-204">Dans ce cas, toujours Dapper devance EF Core, mais légèrement.</span><span class="sxs-lookup"><span data-stu-id="bf34a-204">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="bf34a-205">Affiche le nombre Julie Lerman certaines données de performances dans son peuvent 2016 à l’article MSDN [Dapper, Entity Framework et applications hybrides](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="bf34a-205">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="bf34a-206">Données de test d’évaluation des performances supplémentaires pour diverses méthodes d’accès aux données se trouvent sur [le site Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="bf34a-206">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="bf34a-207">Pour voir comment la syntaxe Dapper varie à partir de EF, prenez en compte ces deux versions de la même méthode pour récupérer une liste d’éléments :</span><span class="sxs-lookup"><span data-stu-id="bf34a-207">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="bf34a-208">Si vous avez besoin générer des graphiques d’objets plus complexes avec Dapper, vous devez écrire les requêtes associées (par opposition à l’ajout d’un élément Include comme vous le feriez dans EF Core).</span><span class="sxs-lookup"><span data-stu-id="bf34a-208">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="bf34a-209">Cela est pris en charge via une variété de syntaxes, y compris une fonctionnalité appelée multiples de mappage qui vous permet de mapper des lignes individuelles pour plusieurs objets mappés.</span><span class="sxs-lookup"><span data-stu-id="bf34a-209">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="bf34a-210">Par exemple, étant donné une classe Post avec un propriétaire de la propriété de type utilisateur, l’instruction SQL suivante renvoie toutes les données nécessaires :</span><span class="sxs-lookup"><span data-stu-id="bf34a-210">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="bf34a-211">Chaque ligne retournée inclut des données utilisateur et Post.</span><span class="sxs-lookup"><span data-stu-id="bf34a-211">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="bf34a-212">Étant donné que les données utilisateur doivent être attachées à des données de publication via sa propriété de propriétaire, la fonction suivante est utilisée :</span><span class="sxs-lookup"><span data-stu-id="bf34a-212">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="bf34a-213">La liste de code complète pour retourner une collection de publications dont la propriété Owner remplie avec les données utilisateur associées serait :</span><span class="sxs-lookup"><span data-stu-id="bf34a-213">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="bf34a-214">Car il offre moins encapsulation, Dapper requiert les développeurs en savoir plus sur la façon dont leurs données sont stockées, comment interroger efficacement et d’écrire plus de code pour récupérer.</span><span class="sxs-lookup"><span data-stu-id="bf34a-214">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="bf34a-215">Lorsque le modèle change, au lieu de simplement créer une nouvelle migration (une autre fonctionnalité EF Core), et/ou mise à jour des informations de mappage dans un emplacement d’un DbContext, chaque requête qui est affecté doit être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="bf34a-215">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="bf34a-216">Ces requêtes n’ont pas les garanties de temps de compilation, afin qu’ils peuvent arrêter lors de l’exécution en réponse aux modifications au modèle ou de la base de données, à des erreurs plus difficiles à détecter rapidement.</span><span class="sxs-lookup"><span data-stu-id="bf34a-216">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="bf34a-217">En échange de ces compromis, Dapper offre des performances extrêmement rapides.</span><span class="sxs-lookup"><span data-stu-id="bf34a-217">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="bf34a-218">Pour la plupart des applications et la plupart des parties de presque toutes les applications, EF Core offre des performances acceptables.</span><span class="sxs-lookup"><span data-stu-id="bf34a-218">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="bf34a-219">Par conséquent, ses avantages de la productivité du développeur sont probable que la baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="bf34a-219">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="bf34a-220">Pour les requêtes qui peuvent tirer parti de la mise en cache, la requête réelle peut uniquement être exécutée un petit pourcentage du temps, ce qui réduit les moot des différences de performances de requête.</span><span class="sxs-lookup"><span data-stu-id="bf34a-220">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="bf34a-221">SQL ou NoSQL</span><span class="sxs-lookup"><span data-stu-id="bf34a-221">SQL or NoSQL</span></span>

<span data-ttu-id="bf34a-222">En règle générale, les bases de données relationnelles telles que SQL Server ont dominée marketplace pour le stockage des données persistantes, mais ils ne sont pas la seule solution possible.</span><span class="sxs-lookup"><span data-stu-id="bf34a-222">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="bf34a-223">Comme les bases de données NoSQL [MongoDB](https://www.mongodb.com/what-is-mongodb) offrent une approche différente pour le stockage d’objets.</span><span class="sxs-lookup"><span data-stu-id="bf34a-223">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="bf34a-224">Au lieu de mappage d’objets à des tables et des lignes, une autre option consiste à sérialiser le graphique d’objets et stocker le résultat.</span><span class="sxs-lookup"><span data-stu-id="bf34a-224">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="bf34a-225">Les avantages de cette approche, au moins au départ, sont plus de simplicité et de performances.</span><span class="sxs-lookup"><span data-stu-id="bf34a-225">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="bf34a-226">Il est certainement plus simple stocker un objet sérialisé unique avec une clé aux décomposer l’objet en plusieurs tables avec des relations et mise à jour et des lignes qui peuvent avoir changé depuis l’objet a été récupéré à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-226">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="bf34a-227">De même, l’extraction et la désérialisation d’un objet unique à partir d’un stockage basé sur la clé sont généralement beaucoup plus rapide et plus facile que dans des jointures complexes ou de plusieurs requêtes de base de données requises pour composer des entièrement le même objet à partir d’une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="bf34a-227">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="bf34a-228">L’absence de verrous ou de transactions ou d’un schéma fixe permet également de bases de données NoSQL très adaptées à l’échelle entre plusieurs machines, prise en charge des jeux de données très volumineux.</span><span class="sxs-lookup"><span data-stu-id="bf34a-228">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="bf34a-229">En revanche, les bases de données NoSQL (comme ils sont généralement appelées) ont leurs inconvénients.</span><span class="sxs-lookup"><span data-stu-id="bf34a-229">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="bf34a-230">Bases de données relationnelles utilisent la normalisation à appliquer la cohérence et éviter la duplication de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-230">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="bf34a-231">Cela réduit la taille totale de la base de données et garantit que les mises à jour des données partagées sont disponibles immédiatement dans l’ensemble de la base de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-231">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="bf34a-232">Dans une base de données relationnelle, une table d’adresses peut-être référencer une table de pays par ID, tel que si le nom d’un pays ont été modifié, les enregistrements d’adresse bénéficierait de la mise à jour sans eux-mêmes être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="bf34a-232">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="bf34a-233">Toutefois, dans une base de données NoSQL, adresse et son pays associé peuvent être sérialisée dans le cadre de nombreux objets stockés.</span><span class="sxs-lookup"><span data-stu-id="bf34a-233">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="bf34a-234">Une mise à jour pour un nom de pays nécessiterait tous ces objets à mettre à jour, au lieu d’une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="bf34a-234">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="bf34a-235">Bases de données relationnelles peuvent également garantir l’intégrité relationnelle en appliquant des règles, comme des clés étrangères.</span><span class="sxs-lookup"><span data-stu-id="bf34a-235">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="bf34a-236">En règle générale, les bases de données NoSQL n’offrent pas ces contraintes sur leurs données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-236">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="bf34a-237">Une autre complexité NoSQL doivent respecter des bases de données est le contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="bf34a-237">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="bf34a-238">Lorsque les propriétés d’un objet changent, il n’est peut-être pas en mesure de désérialiser à partir de versions antérieures qui ont été stockées.</span><span class="sxs-lookup"><span data-stu-id="bf34a-238">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="bf34a-239">Par conséquent, tous les objets existants qui ont une version sérialisée (précédente) de l’objet doivent être actualisées pour être conforme à son nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="bf34a-239">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="bf34a-240">Cela n’est pas sur le plan conceptuel différent à partir d’une base de données relationnelle, où les modifications de schéma parfois nécessitent des scripts de mise à jour ou le mappage de mises à jour.</span><span class="sxs-lookup"><span data-stu-id="bf34a-240">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="bf34a-241">Toutefois, le nombre d’entrées qui doit être modifiée est souvent beaucoup plus dans l’approche NoSQL, car il existe plus de duplication de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-241">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="bf34a-242">Il est possible dans les bases de données NoSQL pour stocker plusieurs versions d’objets, schéma fixe quelque chose de bases de données relationnelles en général, ne pas prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="bf34a-242">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="bf34a-243">Toutefois, dans ce cas votre code d’application devez prendre en compte l’existence de versions d’objets et l’ajout de complexité supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="bf34a-243">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="bf34a-244">Bases de données NoSQL n’appliquent pas généralement [ACID](http://en.wikipedia.org/wiki/ACID), ce qui signifie qu’ils présentent des avantages de performances et l’évolutivité sur les bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="bf34a-244">NoSQL databases typically do not enforce [ACID](http://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="bf34a-245">Ils sont bien adaptées à des datasets très volumineux et les objets qui ne sont pas adaptés au stockage dans des structures de table normalisée.</span><span class="sxs-lookup"><span data-stu-id="bf34a-245">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="bf34a-246">Il est inutile pour lesquelles une application unique ne peut pas tirer parti des deux relationnelle et adapté de bases de données NoSQL, utilisant chacun où il est préférable.</span><span class="sxs-lookup"><span data-stu-id="bf34a-246">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="bf34a-247">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="bf34a-247">Azure DocumentDB</span></span>

<span data-ttu-id="bf34a-248">Azure DocumentDB est un service de base de données NoSQL entièrement géré qui offre un stockage en cloud des données sans schéma.</span><span class="sxs-lookup"><span data-stu-id="bf34a-248">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="bf34a-249">DocumentDB est conçu pour des performances rapides et prévisibles, haute disponibilité, la mise à l’échelle élastique et distribution globale.</span><span class="sxs-lookup"><span data-stu-id="bf34a-249">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="bf34a-250">Bien qu’étant une base de données NoSQL, les développeurs peuvent utiliser des fonctions de requête SQL riches et familiers sur des données JSON.</span><span class="sxs-lookup"><span data-stu-id="bf34a-250">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="bf34a-251">Toutes les ressources DocumentDB sont stockés en tant que documents JSON.</span><span class="sxs-lookup"><span data-stu-id="bf34a-251">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="bf34a-252">Les ressources sont gérées en tant que *éléments*, qui sont des documents contenant les métadonnées, et *flux*, qui sont des collections d’éléments.</span><span class="sxs-lookup"><span data-stu-id="bf34a-252">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="bf34a-253">Figure 8-2 montre la relation entre les différentes ressources DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="bf34a-253">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![La relation hiérarchique entre les ressources DocumentDB, une base de données NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="bf34a-255">**Figure 8-2.**</span><span class="sxs-lookup"><span data-stu-id="bf34a-255">**Figure 8-2.**</span></span> <span data-ttu-id="bf34a-256">Organisation de ressource de DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="bf34a-256">DocumentDB resource organization.</span></span>

<span data-ttu-id="bf34a-257">Le langage de requête DocumentDB est une interface simple et puissante permettant d’interroger des documents JSON.</span><span class="sxs-lookup"><span data-stu-id="bf34a-257">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="bf34a-258">Le langage prend en charge un sous-ensemble de la grammaire SQL ANSI et ajoute l’intégration en profondeur de l’objet JavaScript, tableaux, construction d’objet et l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="bf34a-258">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="bf34a-259">**Références – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="bf34a-259">**References – DocumentDB**</span></span>

-   <span data-ttu-id="bf34a-260">DocumentDB Introduction\\</span><span class="sxs-lookup"><span data-stu-id="bf34a-260">DocumentDB Introduction\\</span></span>
    <span data-ttu-id="bf34a-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span><span class="sxs-lookup"><span data-stu-id="bf34a-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="bf34a-262">Autres Options de persistance</span><span class="sxs-lookup"><span data-stu-id="bf34a-262">Other Persistence Options</span></span>

<span data-ttu-id="bf34a-263">Outre relationnelle et les options de stockage NoSQL, les applications ASP.NET Core permet le stockage Azure pour stocker une variété de formats de données et fichiers de façon évolutive et basée sur le cloud.</span><span class="sxs-lookup"><span data-stu-id="bf34a-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="bf34a-264">Le stockage Azure est très évolutif, donc vous pouvez commencer le stockage de petites quantités de données et de monter le stockage des centaines, voire des téraoctets si votre application l’exige.</span><span class="sxs-lookup"><span data-stu-id="bf34a-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="bf34a-265">Le stockage Azure prend en charge quatre types de données :</span><span class="sxs-lookup"><span data-stu-id="bf34a-265">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="bf34a-266">Stockage d’objets BLOB pour texte non structuré ou stockage binaire, également appelée stockage d’objets.</span><span class="sxs-lookup"><span data-stu-id="bf34a-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="bf34a-267">Stockage de table pour les datasets structurés, accessibles via les clés de ligne.</span><span class="sxs-lookup"><span data-stu-id="bf34a-267">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="bf34a-268">Stockage de file d’attente pour la messagerie fiable basée sur la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="bf34a-268">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="bf34a-269">Stockage de fichier pour l’accès de fichier partagé entre les machines virtuelles et des applications locales.</span><span class="sxs-lookup"><span data-stu-id="bf34a-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="bf34a-270">**Références – stockage Azure**</span><span class="sxs-lookup"><span data-stu-id="bf34a-270">**References – Azure Storage**</span></span>

-   <span data-ttu-id="bf34a-271">Introduction\ de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="bf34a-271">Azure Storage Introduction\\</span></span>
    <span data-ttu-id="bf34a-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="bf34a-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="bf34a-273">Mise en cache</span><span class="sxs-lookup"><span data-stu-id="bf34a-273">Caching</span></span>

<span data-ttu-id="bf34a-274">Dans les applications web, chaque requête web doit être effectuée dans les plus brefs délais.</span><span class="sxs-lookup"><span data-stu-id="bf34a-274">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="bf34a-275">Un pour y parvenir consiste à limiter le nombre d’appels externes, que le serveur doit effectuer pour terminer la demande.</span><span class="sxs-lookup"><span data-stu-id="bf34a-275">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="bf34a-276">La mise en cache implique de stocker une copie des données sur le serveur (ou un autre magasin de données qui est plus facilement interrogée à la source de données).</span><span class="sxs-lookup"><span data-stu-id="bf34a-276">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="bf34a-277">Applications Web et en particulier les applications web classiques de non-SPA doivent générer l’interface utilisateur entière avec chaque demande.</span><span class="sxs-lookup"><span data-stu-id="bf34a-277">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="bf34a-278">Cela implique souvent de nombreux des mêmes requêtes de base de données à plusieurs reprises à partir de la demande d’un utilisateur à l’autre.</span><span class="sxs-lookup"><span data-stu-id="bf34a-278">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="bf34a-279">Dans la plupart des cas, ces données changent rarement, par conséquent, il est peu de raisons d’en permanence de la demande à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="bf34a-279">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="bf34a-280">ASP.NET Core prend en charge la réponse mise en cache, de mise en cache des pages entières et la mise en cache des données, qui prend en charge le comportement de mise en cache plus granulaire.</span><span class="sxs-lookup"><span data-stu-id="bf34a-280">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="bf34a-281">Lors de l’implémentation de la mise en cache, il est important de garder à séparation tenant compte des problèmes.</span><span class="sxs-lookup"><span data-stu-id="bf34a-281">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="bf34a-282">Évitez d’implémentation de la logique de mise en cache dans votre logique d’accès aux données, ou dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bf34a-282">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="bf34a-283">Au lieu de cela, encapsuler ses propres classes de mise en cache et la configuration permet de gérer son comportement.</span><span class="sxs-lookup"><span data-stu-id="bf34a-283">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="bf34a-284">Cela suit les ouvrir/fermé et les principes de responsabilité unique et le rend plus facile de gérer la façon dont vous utilisez la mise en cache dans votre application qu’elle se développe.</span><span class="sxs-lookup"><span data-stu-id="bf34a-284">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="bf34a-285">La mise en cache de réponse ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bf34a-285">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="bf34a-286">ASP.NET Core prend en charge deux niveaux de mise en cache de la réponse.</span><span class="sxs-lookup"><span data-stu-id="bf34a-286">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="bf34a-287">Le premier niveau ne met pas en cache quoi que ce soit sur le serveur, mais ajoute des en-têtes HTTP qui commandent aux clients et serveurs proxy en cache les réponses.</span><span class="sxs-lookup"><span data-stu-id="bf34a-287">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="bf34a-288">Cela est implémenté en ajoutant l’attribut ResponseCache contrôleurs individuels ou des actions :</span><span class="sxs-lookup"><span data-stu-id="bf34a-288">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="bf34a-289">L’intergiciel (middleware) réponse mise en cache met en cache automatiquement selon un ensemble de conditions que vous pouvez personnaliser les réponses.</span><span class="sxs-lookup"><span data-stu-id="bf34a-289">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="bf34a-290">Par défaut, les réponses que 200 (OK) demandés par le biais des méthodes GET ou HEAD sont mis en cache.</span><span class="sxs-lookup"><span data-stu-id="bf34a-290">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="bf34a-291">En outre, les demandes doivent avoir une réponse avec un Cache-Control : en-tête public et ne peut pas inclure des en-têtes de l’autorisation ou Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="bf34a-291">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="bf34a-292">Consultez un [la liste complète des conditions de mise en cache utilisé par la réponse mise en cache d’intergiciel (middleware)](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="bf34a-292">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="bf34a-293">La mise en cache des données</span><span class="sxs-lookup"><span data-stu-id="bf34a-293">Data Caching</span></span>

<span data-ttu-id="bf34a-294">Au lieu de (ou en plus) mise en cache les réponses web complète, vous pouvez mettre en cache les résultats des requêtes de données individuels.</span><span class="sxs-lookup"><span data-stu-id="bf34a-294">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="bf34a-295">Pour ce faire, vous pouvez utiliser la mise en mémoire cache sur le serveur web, ou [un cache distribué](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="bf34a-295">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="bf34a-296">Cette section va vous montrer comment implémenter la mise en mémoire cache.</span><span class="sxs-lookup"><span data-stu-id="bf34a-296">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="bf34a-297">Vous ajoutez la prise en charge de mémoire (ou distributed) mise en cache dans ConfigureServices :</span><span class="sxs-lookup"><span data-stu-id="bf34a-297">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="bf34a-298">Veillez à ajouter le package NuGet de Microsoft.Extensions.Caching.Memory également.</span><span class="sxs-lookup"><span data-stu-id="bf34a-298">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="bf34a-299">Une fois que vous avez ajouté le service, vous demandez IMemoryCache via l’injection de dépendances partout où vous avez besoin accéder au cache.</span><span class="sxs-lookup"><span data-stu-id="bf34a-299">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="bf34a-300">Dans cet exemple, le CachedCatalogService utilise le modèle de conception Proxy (ou Decorator), en fournissant une autre implémentation de ICatalogService qui contrôle l’accès à (ou ajoute le comportement à) l’implémentation CatalogService sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="bf34a-300">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="bf34a-301">Pour configurer l’application pour utiliser la version mise en cache du service, mais autoriser le service obtenir de l’instance de CatalogService dont il a besoin dans son constructeur, vous devez ajouter les éléments suivants dans ConfigureServices :</span><span class="sxs-lookup"><span data-stu-id="bf34a-301">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="bf34a-302">Tout cela en place, les appels de base de données pour extraire les données de catalogue ne seront une fois par minute, plutôt qu’à chaque demande.</span><span class="sxs-lookup"><span data-stu-id="bf34a-302">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="bf34a-303">Selon le trafic vers le site, cela peut avoir un impact considérable sur le nombre de requêtes effectuées sur la base de données et le temps de chargement de page moyen pour la page d’accueil actuellement varie selon les trois requêtes exposées par ce service.</span><span class="sxs-lookup"><span data-stu-id="bf34a-303">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="bf34a-304">Un problème qui se produit lorsque la mise en cache est implémentée est *des données obsolètes* : autrement dit, les données qui ont été modifiées à la source, mais une version obsolète restent dans le cache.</span><span class="sxs-lookup"><span data-stu-id="bf34a-304">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="bf34a-305">Un moyen simple de résoudre ce problème consiste à utiliser les durées de petit cache, étant donné que pour une application occupée est limitée avantage supplémentaire à l’extension de la longueur de données mises en cache.</span><span class="sxs-lookup"><span data-stu-id="bf34a-305">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="bf34a-306">Par exemple, considérez une page qui effectue une requête de base de données unique, et est demandé 10 fois par seconde.</span><span class="sxs-lookup"><span data-stu-id="bf34a-306">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="bf34a-307">Si cette page est mise en cache pendant une minute, elle entraîne le nombre de requêtes de base de données effectuées par minute à supprimer de 600 à 1, une réduction de 99,8 %.</span><span class="sxs-lookup"><span data-stu-id="bf34a-307">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="bf34a-308">Si à la place la durée du cache a été apportée à une heure, la réduction globale serait 99.997 %, mais maintenant l’âge de probabilité et risque de données obsolètes sont ont augmenté considérablement.</span><span class="sxs-lookup"><span data-stu-id="bf34a-308">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="bf34a-309">Une autre approche consiste à supprimer proactive des entrées de cache lors de la mise à jour les données qu’ils contiennent.</span><span class="sxs-lookup"><span data-stu-id="bf34a-309">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="bf34a-310">Toute entrée individuelle peut être supprimée si sa clé est constitue :</span><span class="sxs-lookup"><span data-stu-id="bf34a-310">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="bf34a-311">Si votre application expose les fonctionnalités de mise à jour des entrées de mise en cache, vous pouvez supprimer les entrées de cache correspondante dans votre code qui effectue les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="bf34a-311">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="bf34a-312">Il peut être parfois de nombreuses entrées différentes qui dépendent d’un jeu de données particulier.</span><span class="sxs-lookup"><span data-stu-id="bf34a-312">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="bf34a-313">Dans ce cas, il peut être utile de créer des dépendances entre les entrées du cache, à l’aide d’un CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="bf34a-313">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="bf34a-314">Avec un CancellationChangeToken, vous pouvez faire expirer plusieurs entrées de cache à la fois en annulant le jeton.</span><span class="sxs-lookup"><span data-stu-id="bf34a-314">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
<span data-ttu-id="bf34a-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="bf34a-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
