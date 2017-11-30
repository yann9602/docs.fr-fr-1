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
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Création d’un simple microservice CRUD piloté par les données

Cette section décrit comment créer un simple microservice effectue créer, lire, mettre à jour et les opérations de suppression (CRUD) sur une source de données.

## <a name="designing-a-simple-crud-microservice"></a>Conception d’un microservice CRUD simple

Du point de vue de la conception, ce type de microservice en conteneur est très simple. Peut-être résoudre le problème est simple, ou l’implémentation est peut-être une preuve de concept uniquement.

![](./media/image4.png)

**Figure 8-4**. Conception interne pour simple CRUD microservices

Un exemple de ce type de service de lecteur de données simple est le catalogue microservice à partir de l’exemple d’application eShopOnContainers. Ce type de service implémente toutes ses fonctionnalités dans un seul projet de l’API Web ASP.NET principale qui inclut des classes pour son modèle de données, sa logique d’entreprise et son code d’accès aux données. Il stocke ses données associées dans une base de données en cours d’exécution dans SQL Server (comme un autre conteneur à des fins de développement/test), mais vous peut également être n’importe quel hôte de SQL Server standard, comme illustré dans la Figure 8-5.

![](./media/image5.png)

**Figure 8-5**. Conception de microservice de données-driven/CRUD simple

Lorsque vous développez ce type de service, vous devez uniquement [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) et une API d’accès aux données ou les ORM, par exemple [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Vous pouvez également générer [Swagger](http://swagger.io/) automatiquement par le biais de métadonnées [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) pour fournir une description des fonctions proposées par votre service, comme expliqué dans la section suivante.

Notez qu’un serveur de base de données tel que SQL Server dans un conteneur Docker est idéal pour les environnements de développement, car vous pouvez avoir toutes les dépendances de votre en cours d’exécution et en cours d’exécution sans avoir à configurer une base de données dans le nuage ou sur site. Cela est très utile lors de l’intégration en cours d’exécution de tests. Toutefois, pour les environnements de production, un serveur de base de données en cours d’exécution dans un conteneur est déconseillé, car vous n’obtiendrez généralement pas de haute disponibilité avec cette approche. Pour un environnement de production dans Azure, il est recommandé d’utiliser de base de données SQL Azure ou une autre technologie de base de données qui peut fournir une haute disponibilité et une haute évolutivité. Par exemple, une approche NoSQL, vous pouvez choisir de DocumentDB.

Enfin, en modifiant les fichiers de métadonnées Dockerfile et docker-compose.yml, vous pouvez configurer création de l’image de ce conteneur, quelle image de base sera utiliser et concevoir des paramètres tels que les noms internes et externes et les ports TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implémentation d’un microservice CRUD simple avec ASP.NET Core

Pour implémenter un microservice CRUD simple à l’aide de .NET Core et Visual Studio, commencez par créer un projet de l’API Web ASP.NET principale simple (en cours d’exécution sur .NET Core afin qu’il puisse s’exécuter sur un hôte Linux Docker), comme indiqué dans la Figure 8-6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Figure 8-6**. Création d’un projet de l’API Web ASP.NET principale dans Visual Studio

Après avoir créé le projet, vous pouvez implémenter vos contrôleurs MVC comme vous le feriez dans n’importe quel autre projet d’API Web, à l’aide de l’API Entity Framework ou autres API. Dans le projet eShopOnContainers.Catalog.API, vous pouvez voir que les dépendances principales pour ce microservice sont simplement ASP.NET Core lui-même, Entity Framework et Swashbuckle, comme indiqué dans la Figure 8-7.

![](./media/image8.PNG)

**Figure 8-7**. Dépendances dans un microservice CRUD Web API simple

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implémentation de services d’API Web de CRUD avec Entity Framework Core

Entity Framework (EF) Core est léger et extensible, et version inter-plateformes des données Entity Framework populaires technologie d’accès. EF Core est un mappeur objet / relationnel (ORM) qui permet aux développeurs .NET travailler avec une base de données à l’aide d’objets .NET.

Le catalogue microservice utilise EF et le fournisseur SQL Server, car sa base de données est en cours d’exécution dans un conteneur avec SQL Server pour une image Docker de Linux. Toutefois, la base de données peut être déployé dans n’importe quel serveur SQL, tels que Windows local ou de la base de données SQL Azure. La seule chose que vous devez modifier est la chaîne de connexion dans l’API Web ASP.NET microservice.

#### <a name="add-entity-framework-core-to-your-dependencies"></a>Ajouter d’Entity Framework Core à vos dépendances

Vous pouvez installer le package NuGet pour le fournisseur de base de données que vous souhaitez utiliser, dans ce cas, SQL Server, à partir de l’IDE de Visual Studio ou avec la console de NuGet. Utilisez la commande suivante :

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a>Le modèle de données

Avec EF de base, l’accès aux données est effectuée à l’aide d’un modèle. Un modèle est composé de classes d’entité et un contexte dérivé qui représente une session avec la base de données, ce qui vous permet d’interroger et d’enregistrer des données. Vous pouvez générer un modèle à partir d’une base de données existante, manuellement un modèle pour correspondre à votre base de données de code ou utiliser les migrations EF pour créer une base de données à partir de votre modèle (et évolue au même rythme que votre modèle change au fil du temps). Pour le catalogue microservice, nous utilisons la dernière approche. Vous pouvez voir un exemple de la classe d’entité CatalogItem dans l’exemple de code suivant, qui est un simple objet CLR simple ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) classe d’entité.

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

Vous devez également un DbContext qui représente une session avec la base de données. Pour le catalogue microservice, la classe CatalogContext dérive de la classe de base DbContext, comme indiqué dans l’exemple suivant :

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

Vous pouvez avoir code supplémentaire dans l’implémentation de DbContext. Par exemple, dans l’exemple d’application, nous avons une méthode OnModelCreating dans la classe CatalogContext qui remplit automatiquement la première fois, qu'il essaie d’accéder à la base de données à l’exemple de données. Cette méthode est utile pour les données de démonstration. Vous pouvez également utiliser la méthode OnModelCreating pour personnaliser les mappages d’entité objet/base de données avec nombreux autres [points d’extensibilité EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

Vous pouvez afficher plus de détails sur OnModelCreating dans le [mise en œuvre de la couche de persistance de l’infrastructure avec Entity Framework Core](#implementing_infrastructure_persistence) section plus loin dans ce guide.

##### <a name="querying-data-from-web-api-controllers"></a>Interrogation des données à partir des contrôleurs de l’API Web

Instances de vos classes d’entité sont généralement récupérées à partir de la base de données à l’aide de Language Integrated Query (LINQ), comme indiqué dans l’exemple suivant :

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

##### <a name="saving-data"></a>L’enregistrement de données

Données sont créées, supprimées et modifiées dans la base de données à l’aide d’instances de vos classes d’entité. Vous pouvez ajouter le code exemple suivant codée en dur (données fictives dans ce cas) à vos contrôleurs de l’API Web.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Injection de dépendances dans les contrôleurs ASP.NET Core et API Web

Dans ASP.NET Core, vous pouvez utiliser l’Injection de dépendance (DI) prêtes à l’emploi. Il est inutile configurer un conteneur Inversion de contrôle (IoC) tiers, même si votre conteneur inversion de contrôle par défaut peut s’intégrer à l’infrastructure ASP.NET Core si vous le souhaitez. Dans ce cas, cela signifie que vous pouvez injecter directement le requis DBContext EF ou autres référentiels via le constructeur du contrôleur. Dans l’exemple ci-dessus de la classe CatalogController, nous allons injecter un objet de type de CatalogContext ainsi que les autres objets par le biais du constructeur CatalogController.

Une configuration importante de dans le projet d’API Web est l’inscription de la classe DbContext dans le conteneur d’inversion de contrôle du service. En général, cela dans la classe de démarrage en appelant les services. Méthode AddDbContext à l’intérieur de la méthode ConfigureServices, comme indiqué dans l’exemple suivant :

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

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Interrogation des données**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **L’enregistrement de données**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Les variables de chaîne et l’environnement de connexion base de données utilisées par les conteneurs Docker

Vous pouvez utiliser les paramètres ASP.NET Core et ajouter une propriété ConnectionString à votre fichier settings.json comme indiqué dans l’exemple suivant :

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

Le fichier settings.json peut avoir des valeurs par défaut pour la propriété ConnectionString ou pour toute autre propriété. Toutefois, ces propriétés seront être remplacées par les valeurs des variables d’environnement que vous spécifiez dans le fichier compose.override.yml de docker.

À partir de vos fichiers docker-compose.yml ou compose.override.yml de docker, vous pouvez initialiser les variables d’environnement afin que Docker sera configurez-les en tant que variables d’environnement du système d’exploitation, comme indiqué dans le fichier docker-compose.override.yml suivant (la connexion chaîne et les autres lignes encapsulent dans cet exemple, mais il ne serait pas encapsuler dans votre propre fichier).

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

Les fichiers compose.yml de docker au niveau de la solution pas ne sont plus flexibles que les fichiers de configuration au niveau du projet ou microservice, mais également plus sécurisée. Considérez que les images Docker que vous générez par microservice ne contiennent pas le compose.yml de docker de fichiers, uniquement les fichiers binaires et les fichiers de configuration pour chaque microservice, y compris le fichier Dockerfile. Mais le fichier docker-compose.yml n’est pas déployé avec votre application ; Il est utilisé uniquement au moment du déploiement. Par conséquent, il est plus sécurisé que le placement de ces valeurs dans les fichiers de configuration .NET standards qui sont déployés avec votre code de placer des valeurs de variables d’environnement dans les fichiers de docker-compose.yml (même sans chiffrer les valeurs).

Enfin, vous pouvez obtenir cette valeur à partir de votre code à l’aide de Configuration\[« ConnectionString »\], comme illustré dans la méthode ConfigureServices dans un exemple de code précédent.

Toutefois, pour les environnements de production, vous pouvez à d’autres moyens de l’Explorateur sur la façon de stocker des secrets, comme les chaînes de connexion. Généralement qui seront gérés par votre orchestrator choisi, comme vous le feriez avec [Docker Swarm de gestion de clés secrètes](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implémenter le contrôle de version dans les API Web ASP.NET

En fonction de besoins de l’entreprise, des regroupements de ressources peuvent être ajoutés, les relations entre les ressources peuvent changer et la structure des données de ressources peut être modifiée. Une API Web pour gérer les nouvelles exigences en matière de mise à jour est un processus relativement simple, mais vous devez prendre en compte les effets de ces modifications sur l’utilisation de l’API Web des applications clientes. Bien que le développeur de conception et implémentation d’une API Web dispose d’un contrôle total sur cette API, le développeur n’a pas le même degré de contrôle sur les applications clientes qui peuvent être générées par des organisations tierce partie d’exploitation à distance.

Le contrôle de version permet à une API Web indiquer les fonctionnalités et les ressources qu’il expose. Une application cliente peut ensuite soumettre les demandes vers une version spécifique d’une fonctionnalité ou d’une ressource. Il existe plusieurs approches pour implémenter le contrôle de version :

-   Contrôle de version URI

-   Version de chaîne de requête

-   Contrôle de version en-tête

Chaîne de requête et le contrôle de version URI sont le plus simple à implémenter. Le contrôle de version en-tête est une bonne approche. Toutefois, le contrôle de version en-tête pas aussi explicite et simple que le contrôle de version URI. Étant donné que le contrôle de version URL est la plus simple et la plus explicite, l’exemple d’application eShopOnContainers utilise le contrôle de version URI.

Avec le contrôle de version URI, comme dans l’exemple d’application eShopOnContainers, chaque fois que vous modifiez l’API Web ou que vous modifiez le schéma de ressources, vous ajoutez un numéro de version à l’URI pour chaque ressource. URI existants doit continuer à fonctionner comme avant, retournant des ressources qui sont conformes au schéma qui correspond à la version demandée.

Comme indiqué dans l’exemple de code suivant, la version peut être définie à l’aide de l’attribut d’itinéraire dans l’API Web, ce qui rend la version explicite dans l’URI (v1 dans ce cas).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Ce mécanisme de contrôle de version est simple et dépend du serveur de routage de la demande au point de terminaison approprié. Toutefois, pour une gestion des versions plus sophistiquées et la meilleure méthode si vous utilisez REST, vous utilisez hypermédia et implémenter [HATEOAS (Hypertext en tant que le moteur d’état de l’Application)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Scott Hanselman. Contrôle de version de l’API Web RESTful principale ASP.NET facilité**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Contrôle de version une API RESTful web**

    [*https://docs.Microsoft.com/Azure/architecture/Best-Practices/API-Design#versioning-a-RESTful-Web-API*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy fielding d’a. Le contrôle de version, hypermédia et reste**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Génération des métadonnées de description de Swagger à partir de votre API Web de base ASP.NET 

[Swagger](http://swagger.io/) est une infrastructure couramment utilisés open source qui est soutenu par un grand écosystème d’outils qui vous permet de conception, de génération, de document et de consommer vos API RESTful. Il est devenu la norme pour le domaine de métadonnées de description API. Vous devez inclure les métadonnées de description Swagger avec n’importe quel type de microservice, pilotés par les données de microservices soit plus avancé microservices de domaine (comme expliqué dans la section suivante).

Le cœur de Swagger est la spécification de Swagger, qui est l’API des métadonnées de description dans un fichier JSON ou YAML. La spécification crée le contrat RESTful votre API, détaillant toutes ses ressources et opérations dans les deux un homme et machine readable format pour le développement, de découverte et d’intégration.

La spécification est la base de la spécification OpenAPI (OEA) et est développée dans une communauté open, transparente et de collaboration pour normaliser la façon dont les interfaces RESTful sont définies.

La spécification définit la structure pour le mode de détection de service et comment ses fonctionnalités compris. Pour plus d’informations, notamment un éditeur web et des exemples de spécifications de Swagger d’entreprises comme Spotify, Uber, la marge et Microsoft, consultez le site Swagger (<http://swagger.io>).

### <a name="why-use-swagger"></a>Pourquoi utiliser Swagger ?

Voici les raisons principales pour générer des métadonnées Swagger pour votre API.

**Possibilité pour les autres produits de consommer automatiquement et d’intégrer vos API**. Des dizaines de produits et [outils professionnelle](http://swagger.io/commercial-tools/) et plusieurs [bibliothèques et infrastructures](http://swagger.io/open-source-integrations/) Swagger de prendre en charge. Microsoft a des produits de haut niveau et des outils qui peuvent consommer automatiquement les API Swagger, tels que les éléments suivants :

-   [AutoRest](https://github.com/Azure/AutoRest). Vous pouvez générer automatiquement des classes de client .NET pour l’appel de Swagger. This

-   outil peut être utilisé à partir de l’interface CLI et il intègre également Visual Studio pour une utilisation simple via l’interface utilisateur graphique.

-   [Microsoft Flow](https://flow.microsoft.com/en-us/). Vous pouvez automatiquement [et s’intègrent votre API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) dans un flux de travail Microsoft Flow haut niveau, sans aucune programmation compétences requises.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Vous pouvez consommer automatiquement votre API à partir de [PowerApps des applications mobiles](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) intègrent [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), avec aucune compétence de programmation requis.

-   [Service d’applications Azure Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Vous pouvez automatiquement [et s’intègrent votre API dans une application Azure App Service logique](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), avec aucune compétence de programmation requis.

**Possibilité de générer automatiquement la documentation de l’API**. Lorsque vous créez des API RESTful à grande échelle, tels que les applications microservice complexes, vous devez gérer de nombreux points de terminaison avec différents modèles de données utilisés dans les charges utiles de demande et de réponse. En la documentation appropriée et un solid Explorateur d’API, que vous obtenez avec Swagger, sont la clé pour la réussite de votre API et l’adoption par les développeurs.

Métadonnées de swagger sont ce que Microsoft Flow, PowerApps et Azure Logic Apps permet de comprendre comment utiliser les API et s’y connecter.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Comment faire pour automatiser la génération de métadonnées Swagger d’API avec le package NuGet de Swashbuckle

Génération des métadonnées Swagger manuellement (dans un fichier JSON ou YAML) peut être fastidieux travail. Toutefois, vous pouvez automatiser la découverte de l’API des services d’API Web ASP.NET à l’aide de la [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) générer dynamiquement des métadonnées de l’API de Swagger.

Swashbuckle génère automatiquement les métadonnées Swagger pour vos projets d’API Web ASP.NET. Il prend en charge les projets de l’API Web ASP.NET principale et l’API Web ASP.NET traditionnel et autres version, par exemple Azure API App, l’application Mobile Azure, microservices Azure Service Fabric reposant sur ASP.NET. Il prend également en charge les API Web simple déployé sur les conteneurs, comme dans pour l’application de référence.

Swashbuckle combine Explorateur d’API et Swagger ou [swagger-ui](https://github.com/swagger-api/swagger-ui) pour fournir une détection riche documentation expérience et pour les consommateurs de votre API. En plus de son moteur de générateur de métadonnées Swagger, Swashbuckle contient également une version incorporée de swagger-ui, il sera automatiquement dynamisent lorsque Swashbuckle est installé.

Cela signifie que vous pouvez compléter votre API avec une découverte intéressante l’interface utilisateur pour aider les développeurs à utiliser votre API. Elle nécessite très peu de code et de maintenance, car il est généré automatiquement, ce qui vous permet de vous concentrer sur la création de votre API. Le résultat de l’Explorateur d’API se présente comme la Figure 8-8.

![](./media/image9.png)

**Figure 8-8**. Explorateur d’API Swashbuckle en fonction de métadonnées Swagger : eShopOnContainers catalogue microservice

L’Explorateur d’API n’est pas essentiel ici. Une fois que vous avez une API Web qui peut se décrire lui-même dans les métadonnées Swagger, votre API peut être utilisé en toute transparence à partir de Swagger les outils, y compris les générateurs de code de classe de proxy de client qui peuvent cibler plusieurs plateformes. Par exemple, comme indiqué, [AutoRest](https://github.com/Azure/AutoRest) génère automatiquement les classes de client .NET. Mais d’autres outils tels que [swagger-codegen](https://github.com/swagger-api/swagger-codegen) sont également disponibles, qui autoriser la génération de code du client de l’API de bibliothèques, des stubs de serveur et la documentation automatiquement.

Actuellement, Swashbuckle se compose de deux packages NuGet : Swashbuckle.SwaggerGen et Swashbuckle.SwaggerUi. La première fournit des fonctionnalités permettant de générer un ou plusieurs documents Swagger directement à partir de votre implémentation de l’API et de les exposer en tant que points de terminaison JSON. Ce dernier fournit une version incorporée de l’outil de l’interface utilisateur de swagger qui peut être pris en charge par votre application et par les documents de Swagger générés pour décrire votre API Bing Maps. Toutefois, les dernières versions de Swashbuckle wrap avec le metapackage Swashbuckle.AspNetCore.

Notez que pour les projets .NET Core Web API, vous devez utiliser [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 ou version ultérieure.

Après avoir installé ces packages NuGet dans votre projet d’API Web, vous devez configurer Swagger dans la classe de démarrage, comme dans le code suivant :

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

Après cela, vous pouvez démarrer votre application et parcourir les JSON de Swagger et de l’interface utilisateur points de terminaison suivants à l’aide de ces URL :

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

Vous avez déjà vu l’interface utilisateur générée créé par Swashbuckle pour une URL telle que http://&lt;votre url de racine &gt; /swagger / l’interface utilisateur. Dans la Figure 8-9. vous pouvez également voir comment vous pouvez tester n’importe quelle méthode d’API.

![](./media/image10.png)

**Figure 8-9**. Swashbuckle UI testing la méthode d’API / des éléments de catalogue

Figure 8-10 montre les métadonnées Swagger un JSON générée à partir de la microservice eShopOnContainers (qui est ce que les outils à utiliser en dessous) lorsque vous demandez &lt;votre url de racine&gt;à l’aide de /swagger/v1/swagger.json [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Figure 8-10**. Métadonnées JSON swagger

Il est très simple. Et, car il est généré automatiquement, les métadonnées Swagger lorsque vous ajoutez des fonctionnalités à votre API.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **API aide des Pages Web ASP.NET à l’aide de Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Précédente] (microservice-application-design.md) [suivant] (multi-container-applications-docker-compose.md)
