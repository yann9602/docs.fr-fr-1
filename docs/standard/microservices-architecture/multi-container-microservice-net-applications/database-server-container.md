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
# <a name="using-a-database-server-running-as-a-container"></a>À l’aide d’un serveur de base de données en cours d’exécution en tant que conteneur

Vous pouvez avoir vos bases de données (SQL Server, PostgreSQL, MySQL, etc.) sur les serveurs autonomes régulières, dans les clusters sur site ou dans les services PaaS dans le cloud comme base de données SQL Azure. Toutefois, pour les environnements de développement et de test, vos bases de données en cours d’exécution en tant que conteneurs est pratique, car vous ne disposez pas d’une dépendance externe et en cours d’exécution simplement le composer de docker commande démarre l’application entière. Ayant ces bases de données en tant que conteneurs est également très utile pour les tests d’intégration, car la base de données est démarré dans le conteneur et est toujours renseigné avec les mêmes données d’exemple, les tests peuvent être plus prévisibles.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server s’exécutant en tant que conteneur avec une base de données liées de microservice

Dans eShopOnContainers, il existe un conteneur nommé sql.data défini dans le [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) fichier qui s’exécute SQL Server pour Linux avec toutes les bases de données SQL Server nécessaires pour le microservices. (Vous pouvez aussi avoir un seul conteneur de SQL Server pour chaque base de données, mais qui nécessiterait davantage de mémoire assignée à Docker). Le point important dans microservices est que chaque microservice possède ses données associées, par conséquent, sa base de données SQL connexe dans ce cas. Mais les bases de données peuvent être n’importe quel endroit.

Le conteneur dans l’exemple d’application est configuré avec le code YAML suivant dans le fichier compose.yml de docker, qui est exécuté lorsque vous exécutez SQL Server docker-composer des. Notez que le code YAML a consolidée des informations de configuration dans le fichier docker-compose.yml générique et le fichier compose.override.yml de docker. (Généralement vous serez séparer les paramètres d’environnement à partir des informations de base ou statiques associée à l’image de SQL Server).

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

La suivante commande docker run peut s’exécuter que le conteneur :

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

Toutefois, si vous déployez une application conteneur multi comme eShopOnContainers, il est plus pratique d’utiliser le docker-composer des commandes afin qu’il déploie tous les conteneurs requis pour l’application.

Lorsque vous démarrez ce conteneur de SQL Server pour la première fois, le conteneur initialise SQL Server avec le mot de passe que vous fournissez. Une fois que SQL Server est en cours d’exécution en tant que conteneur, vous pouvez mettre à jour la base de données en vous connectant via toute connexion SQL standard, comme dans SQL Server Management Studio, Visual Studio ou C\# code.

L’application eShopOnContainers initialise chaque base de données de microservice avec des exemples de données par l’amorçage avec des données au démarrage, comme expliqué dans la section suivante.

SQL Server s’exécutant en tant que conteneur n'est pas seulement utile pour une démonstration où vous peut-être pas accès à une instance de SQL Server. Comme indiqué, il est également très utile pour les environnements de test et de développement afin que vous pouvez facilement exécuter des tests d’intégration à partir d’une nouvelle image de SQL Server et les données connues par l’amorçage de nouveaux exemples de données.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Exécuter l’image de SQL Server Docker sur Windows, Mac ou Linux**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **Se connecter et de requêtes SQL Server sur Linux avec sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>L’amorçage de données de test sur le démarrage de l’application Web

Pour ajouter des données à la base de données au démarrage de l’application, vous pouvez ajouter le code comme suit à la méthode de configuration dans la classe de démarrage du projet Web API :

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

Le code suivant dans la classe CatalogContextSeed personnalisée remplit les données.

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

Lorsque vous exécutez des tests d’intégration, il est utile d’avoir un moyen de générer des données cohérentes avec vos tests d’intégration. Possibilité créer toutes sortes de toutes pièces, y compris une instance de SQL Server est en cours d’exécution sur un conteneur, est idéal pour les environnements de test.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory base de données pour SQL Server s’exécutant en tant que conteneur

Un autre bon choix lors de l’exécution des tests est d’utiliser le fournisseur de base de données Entity Framework InMemory. Vous pouvez spécifier que la configuration de la méthode ConfigureServices de la classe de démarrage dans votre projet d’API Web :

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

Il existe une catch importante, cependant. La base de données en mémoire ne prend pas en charge plusieurs contraintes sont spécifiques à une base de données. Par exemple, vous pouvez ajouter un index unique sur une colonne dans votre modèle EF Core et écrire un test par rapport à votre base de données en mémoire pour vérifier qu’il ne permet pas d’ajouter une valeur en double. Mais lorsque vous utilisez la base de données en mémoire, vous ne peut pas gérer un index unique sur une colonne. Par conséquent, la base de données en mémoire ne comporte pas exactement identique à une base de données SQL Server réel : il n’émule pas de contraintes propres à la base de données.

Même dans ce cas, une base de données en mémoire est toujours utile pour tester et de prototypage. Mais si vous souhaitez créer des tests d’intégration précis qui prennent en compte le comportement d’une implémentation de base de données spécifique, vous devez utiliser une base de données réel, telles que SQL Server. À cet effet, SQL Server en cours d’exécution dans un conteneur est une bonne choice et plus précise que le fournisseur de base de données EF Core InMemory.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>À l’aide d’un service de cache Redis en cours d’exécution dans un conteneur

Vous pouvez exécuter Redis sur un conteneur, en particulier pour le développement et de test et pour les scénarios de la preuve de concept. Ce scénario est pratique, car vous pouvez avoir toutes les dépendances de votre en cours d’exécution sur les conteneurs, pas seulement pour vos ordinateurs de développement local, mais pour vos environnements de test dans des pipelines de votre élément de configuration/CD.

Toutefois, lorsque vous exécutez Redis en production, il est préférable de rechercher une solution de haute disponibilité comme Redis Microsoft Azure, qui s’exécute comme un PaaS (plateforme en tant que Service). Dans votre code, il vous suffit de modifier vos chaînes de connexion.

Redis fournit une image Docker avec Redis. Cette image est disponible à partir du Hub Docker à cette URL :

<https://Hub.docker.com/_/redis/>

Vous pouvez exécuter directement un conteneur Docker Redis en exécutant la commande Docker CLI suivante dans l’invite de commandes :

```
  docker run --name some-redis -d redis
```

L’image de Redis inclut exposent : 6379 (le port utilisé par Redis), liaison de conteneur donc standard rend automatiquement disponible pour les conteneurs liés.

Dans eShopOnContainers, le microservice basket.api utilise un cache Redis en cours d’exécution en tant que conteneur. Ce conteneur basket.data est défini en tant que partie du fichier conteneur multi docker-compose.yml, comme indiqué dans l’exemple suivant :

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Ce code dans le docker-compose.yml définit un conteneur nommé basket.data basée sur l’image de redis et le port 6379 de publication en interne, ce qui signifie qu’il sera accessible uniquement à partir d’autres conteneurs en cours d’exécution au sein de l’hôte Docker.

Enfin, dans le fichier compose.override.yml de docker, le microservice basket.api de l’exemple eShopOnContainers définit la chaîne de connexion à utiliser pour ce conteneur Redis :

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[Précédente] (multiples-container-applications-docker-compose.md) [suivant] (intégration-événements-base-microservice-communications.md)
