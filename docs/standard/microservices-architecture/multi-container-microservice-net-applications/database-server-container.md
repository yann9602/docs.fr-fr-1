---
title: "À l’aide d’un serveur de base de données en cours d’exécution en tant que conteneur"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | À l’aide d’un serveur de base de données en cours d’exécution en tant que conteneur"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7e5f33c4e7edf9d0d4551c5125976fcb8fda392f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="fadc9-104">À l’aide d’un serveur de base de données en cours d’exécution en tant que conteneur</span><span class="sxs-lookup"><span data-stu-id="fadc9-104">Using a database server running as a container</span></span>

<span data-ttu-id="fadc9-105">Vous pouvez avoir vos bases de données (SQL Server, PostgreSQL, MySQL, etc.) sur les serveurs autonomes régulières, dans les clusters sur site ou dans les services PaaS dans le cloud comme base de données SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="fadc9-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="fadc9-106">Toutefois, pour les environnements de développement et de test, vos bases de données en cours d’exécution en tant que conteneurs est pratique, car vous ne disposez pas d’une dépendance externe et en cours d’exécution simplement le composer de docker commande démarre l’application entière.</span><span class="sxs-lookup"><span data-stu-id="fadc9-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency, and simply running the docker-compose command starts the whole application.</span></span> <span data-ttu-id="fadc9-107">Ayant ces bases de données en tant que conteneurs est également très utile pour les tests d’intégration, car la base de données est démarré dans le conteneur et est toujours renseigné avec les mêmes données d’exemple, les tests peuvent être plus prévisibles.</span><span class="sxs-lookup"><span data-stu-id="fadc9-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="fadc9-108">SQL Server s’exécutant en tant que conteneur avec une base de données liées de microservice</span><span class="sxs-lookup"><span data-stu-id="fadc9-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="fadc9-109">Dans eShopOnContainers, il existe un conteneur nommé sql.data défini dans le [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) fichier qui s’exécute SQL Server pour Linux avec toutes les bases de données SQL Server nécessaires pour le microservices.</span><span class="sxs-lookup"><span data-stu-id="fadc9-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="fadc9-110">(Vous pouvez aussi avoir un seul conteneur de SQL Server pour chaque base de données, mais qui nécessiterait davantage de mémoire assignée à Docker). Le point important dans microservices est que chaque microservice possède ses données associées, par conséquent, sa base de données SQL connexe dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="fadc9-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="fadc9-111">Mais les bases de données peuvent être n’importe quel endroit.</span><span class="sxs-lookup"><span data-stu-id="fadc9-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="fadc9-112">Le conteneur dans l’exemple d’application est configuré avec le code YAML suivant dans le fichier compose.yml de docker, qui est exécuté lorsque vous exécutez SQL Server docker-composer des.</span><span class="sxs-lookup"><span data-stu-id="fadc9-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run docker-compose up.</span></span> <span data-ttu-id="fadc9-113">Notez que le code YAML a consolidée des informations de configuration dans le fichier docker-compose.yml générique et le fichier compose.override.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="fadc9-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="fadc9-114">(Généralement vous serez séparer les paramètres d’environnement à partir des informations de base ou statiques associée à l’image de SQL Server).</span><span class="sxs-lookup"><span data-stu-id="fadc9-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

<span data-ttu-id="fadc9-115">La suivante commande docker run peut s’exécuter que le conteneur :</span><span class="sxs-lookup"><span data-stu-id="fadc9-115">The following docker run command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

<span data-ttu-id="fadc9-116">Toutefois, si vous déployez une application conteneur multi comme eShopOnContainers, il est plus pratique d’utiliser le docker-composer des commandes afin qu’il déploie tous les conteneurs requis pour l’application.</span><span class="sxs-lookup"><span data-stu-id="fadc9-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the docker-compose up command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="fadc9-117">Lorsque vous démarrez ce conteneur de SQL Server pour la première fois, le conteneur initialise SQL Server avec le mot de passe que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="fadc9-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="fadc9-118">Une fois que SQL Server est en cours d’exécution en tant que conteneur, vous pouvez mettre à jour la base de données en vous connectant via toute connexion SQL standard, comme dans SQL Server Management Studio, Visual Studio ou C\# code.</span><span class="sxs-lookup"><span data-stu-id="fadc9-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="fadc9-119">L’application eShopOnContainers initialise chaque base de données de microservice avec des exemples de données par l’amorçage avec des données au démarrage, comme expliqué dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="fadc9-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="fadc9-120">SQL Server s’exécutant en tant que conteneur n'est pas seulement utile pour une démonstration où vous peut-être pas accès à une instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fadc9-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="fadc9-121">Comme indiqué, il est également très utile pour les environnements de test et de développement afin que vous pouvez facilement exécuter des tests d’intégration à partir d’une nouvelle image de SQL Server et les données connues par l’amorçage de nouveaux exemples de données.</span><span class="sxs-lookup"><span data-stu-id="fadc9-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="fadc9-122">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="fadc9-122">Additional resources</span></span>

-   <span data-ttu-id="fadc9-123">**Exécuter l’image de SQL Server Docker sur Windows, Mac ou Linux**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span><span class="sxs-lookup"><span data-stu-id="fadc9-123">**Run the SQL Server Docker image on Linux, Mac, or Windows**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span></span>

-   <span data-ttu-id="fadc9-124">**Se connecter et de requêtes SQL Server sur Linux avec sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="fadc9-124">**Connect and query SQL Server on Linux with sqlcmd**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span></span>

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="fadc9-125">L’amorçage de données de test sur le démarrage de l’application Web</span><span class="sxs-lookup"><span data-stu-id="fadc9-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="fadc9-126">Pour ajouter des données à la base de données au démarrage de l’application, vous pouvez ajouter le code comme suit à la méthode de configuration dans la classe de démarrage du projet Web API :</span><span class="sxs-lookup"><span data-stu-id="fadc9-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="fadc9-127">Le code suivant dans la classe CatalogContextSeed personnalisée remplit les données.</span><span class="sxs-lookup"><span data-stu-id="fadc9-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="fadc9-128">Lorsque vous exécutez des tests d’intégration, il est utile d’avoir un moyen de générer des données cohérentes avec vos tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="fadc9-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="fadc9-129">Possibilité créer toutes sortes de toutes pièces, y compris une instance de SQL Server est en cours d’exécution sur un conteneur, est idéal pour les environnements de test.</span><span class="sxs-lookup"><span data-stu-id="fadc9-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="fadc9-130">EF Core InMemory base de données pour SQL Server s’exécutant en tant que conteneur</span><span class="sxs-lookup"><span data-stu-id="fadc9-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="fadc9-131">Un autre bon choix lors de l’exécution des tests est d’utiliser le fournisseur de base de données Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="fadc9-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="fadc9-132">Vous pouvez spécifier que la configuration de la méthode ConfigureServices de la classe de démarrage dans votre projet d’API Web :</span><span class="sxs-lookup"><span data-stu-id="fadc9-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...

}
```

<span data-ttu-id="fadc9-133">Il existe une catch importante, cependant.</span><span class="sxs-lookup"><span data-stu-id="fadc9-133">There is an important catch, though.</span></span> <span data-ttu-id="fadc9-134">La base de données en mémoire ne prend pas en charge plusieurs contraintes sont spécifiques à une base de données.</span><span class="sxs-lookup"><span data-stu-id="fadc9-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="fadc9-135">Par exemple, vous pouvez ajouter un index unique sur une colonne dans votre modèle EF Core et écrire un test par rapport à votre base de données en mémoire pour vérifier qu’il ne permet pas d’ajouter une valeur en double.</span><span class="sxs-lookup"><span data-stu-id="fadc9-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="fadc9-136">Mais lorsque vous utilisez la base de données en mémoire, vous ne peut pas gérer un index unique sur une colonne.</span><span class="sxs-lookup"><span data-stu-id="fadc9-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="fadc9-137">Par conséquent, la base de données en mémoire ne comporte pas exactement identique à une base de données SQL Server réel : il n’émule pas de contraintes propres à la base de données.</span><span class="sxs-lookup"><span data-stu-id="fadc9-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="fadc9-138">Même dans ce cas, une base de données en mémoire est toujours utile pour tester et de prototypage.</span><span class="sxs-lookup"><span data-stu-id="fadc9-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="fadc9-139">Mais si vous souhaitez créer des tests d’intégration précis qui prennent en compte le comportement d’une implémentation de base de données spécifique, vous devez utiliser une base de données réel, telles que SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fadc9-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="fadc9-140">À cet effet, SQL Server en cours d’exécution dans un conteneur est une bonne choice et plus précise que le fournisseur de base de données EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="fadc9-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="fadc9-141">À l’aide d’un service de cache Redis en cours d’exécution dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="fadc9-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="fadc9-142">Vous pouvez exécuter Redis sur un conteneur, en particulier pour le développement et de test et pour les scénarios de la preuve de concept.</span><span class="sxs-lookup"><span data-stu-id="fadc9-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="fadc9-143">Ce scénario est pratique, car vous pouvez avoir toutes les dépendances de votre en cours d’exécution sur les conteneurs, pas seulement pour vos ordinateurs de développement local, mais pour vos environnements de test dans des pipelines de votre élément de configuration/CD.</span><span class="sxs-lookup"><span data-stu-id="fadc9-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="fadc9-144">Toutefois, lorsque vous exécutez Redis en production, il est préférable de rechercher une solution de haute disponibilité comme Redis Microsoft Azure, qui s’exécute comme un PaaS (plateforme en tant que Service).</span><span class="sxs-lookup"><span data-stu-id="fadc9-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="fadc9-145">Dans votre code, il vous suffit de modifier vos chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="fadc9-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="fadc9-146">Redis fournit une image Docker avec Redis.</span><span class="sxs-lookup"><span data-stu-id="fadc9-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="fadc9-147">Cette image est disponible à partir du Hub Docker à cette URL :</span><span class="sxs-lookup"><span data-stu-id="fadc9-147">That image is available from Docker Hub at this URL:</span></span>

<span data-ttu-id="fadc9-148"><https://Hub.docker.com/_/redis/></span><span class="sxs-lookup"><span data-stu-id="fadc9-148"><https://hub.docker.com/_/redis/></span></span>

<span data-ttu-id="fadc9-149">Vous pouvez exécuter directement un conteneur Docker Redis en exécutant la commande Docker CLI suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="fadc9-149">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="fadc9-150">L’image de Redis inclut exposent : 6379 (le port utilisé par Redis), liaison de conteneur donc standard rend automatiquement disponible pour les conteneurs liés.</span><span class="sxs-lookup"><span data-stu-id="fadc9-150">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="fadc9-151">Dans eShopOnContainers, le microservice basket.api utilise un cache Redis en cours d’exécution en tant que conteneur.</span><span class="sxs-lookup"><span data-stu-id="fadc9-151">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="fadc9-152">Ce conteneur basket.data est défini en tant que partie du fichier conteneur multi docker-compose.yml, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="fadc9-152">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="fadc9-153">Ce code dans le docker-compose.yml définit un conteneur nommé basket.data basée sur l’image de redis et le port 6379 de publication en interne, ce qui signifie qu’il sera accessible uniquement à partir d’autres conteneurs en cours d’exécution au sein de l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="fadc9-153">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="fadc9-154">Enfin, dans le fichier compose.override.yml de docker, le microservice basket.api de l’exemple eShopOnContainers définit la chaîne de connexion à utiliser pour ce conteneur Redis :</span><span class="sxs-lookup"><span data-stu-id="fadc9-154">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
<span data-ttu-id="fadc9-155">[Précédente] (multiples-container-applications-docker-compose.md) [suivant] (intégration-événements-base-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="fadc9-155">[Previous] (multi-container-applications-docker-compose.md) [Next] (integration-event-based-microservice-communications.md)</span></span>
