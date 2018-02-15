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
# <a name="working-with-data-in-aspnet-core-apps"></a>Utilisation des données dans les applications ASP.NET Core

> « Données sont une chose précieuse et durent plus longtemps que les systèmes eux-mêmes. »

Tim Berners-Lee

## <a name="summary"></a>Récapitulatif

Accès aux données est une partie importante de la plupart des applications logicielles. ASP.NET Core prend en charge une variété d’options d’accès aux données, y compris l’Entity Framework Core (et ainsi de Entity Framework 6) et peuvent fonctionner avec tout accès de données .NET framework. Le choix des accès aux données framework à utiliser dépend des besoins de l’application. En faisant abstraction de ces choix à partir des projets ApplicationCore et l’interface utilisateur et encapsuler les détails d’implémentation dans une Infrastructure, permettant de produire des logiciels faiblement couplée, testable.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (pour les bases de données relationnelles)

Si vous écrivez une application ASP.NET Core qui doit fonctionner avec des données relationnelles, Entity Framework Core (noyaux EF) est la méthode recommandée pour votre application à accéder à ses données. EF Core est un mappeur objet / relationnel (O/RM) qui permet aux développeurs .NET conserver des objets vers et à partir d’une source de données. Elle élimine la nécessité pour la plupart des développeurs ont généralement besoin d’écrire le code d’accès données. Comme ASP.NET Core, EF Core a été réécrit entièrement prise en charge les applications inter-plateformes modulaires. Vous ajoutez à votre application sous forme de package NuGet, configurez de démarrage et demandez à l’injection de dépendance vous en aurez besoin.

Pour utiliser EF Core avec une base de données SQL Server, exécutez la commande CLI de dotnet à l’adresse suivante :

dotnet ajouter package Microsoft.EntityFrameworkCore.SqlServer

Pour ajouter la prise en charge pour une source de données en mémoire, de test :

dotnet ajouter package Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>Le DbContext

Pour travailler avec EF de base, vous avez besoin d’une sous-classe de DbContext. Cette classe contient des propriétés qui représentent des collections d’entités d’avec que votre application fonctionnera. L’exemple d’eShopOnWeb inclut un CatalogContext avec des collections d’éléments, les marques et les types :

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

Votre DbContext doit avoir un constructeur qui accepte une DbContextOptions et passer cet argument au constructeur DbContext base. Notez que si vous avez uniquement un DbContext dans votre application, vous pouvez passer une instance de DbContextOptions, mais si vous avez plusieurs vous devez utiliser les DbContextOptions génériques<T> type, en passant dans votre type DbContext comme paramètre générique.

### <a name="configuring-ef-core"></a>Configuration des principaux EF

Dans votre application ASP.NET Core, vous devez généralement configurer EF Core dans votre méthode ConfigureServices. EF Core utilise un DbContextOptionsBuilder, qui prend en charge plusieurs méthodes d’extension utile pour simplifier sa configuration. Pour configurer CatalogContext pour utiliser une base de données SQL Server avec une chaîne de connexion définie dans la Configuration, vous devez ajouter le code suivant à ConfigureServices :

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Pour utiliser la base de données en mémoire :

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Après avoir installé Core EF, créé un type enfant DbContext et configuré dans ConfigureServices, vous êtes prêt à utiliser EF Core. Vous pouvez demander une instance de votre type DbContext dans n’importe quel service qui en a besoin et commencer à travailler avec vos entités persistantes à l’aide de LINQ comme s’ils étaient simplement dans une collection. EF Core effectue le travail de traduire vos expressions LINQ dans les requêtes SQL pour stocker et récupérer vos données.

Vous pouvez voir les requêtes EF Core s’exécute en configurant un enregistreur d’événements et de garantir son niveau a au moins plus d’informations, comme indiqué dans la Figure 8-1.

![](./media/image8-1.png)

Requêtes de journalisation des noyaux EF figure 8-1 à la console

### <a name="fetching-and-storing-data"></a>Extraction et stockage des données

Pour récupérer des données à partir de EF, vous accédez à la propriété appropriée et utilisez LINQ pour filtrer le résultat. Vous pouvez également utiliser LINQ pour effectuer la projection, de transformation du résultat d’un type à un autre. L’exemple suivant permet de récupérer CatalogBrands, classés par nom, filtrés par leur propriété Enabled et projeté sur un type SelectListItem :

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Il est important dans l’exemple ci-dessus pour ajouter l’appel à ToListAsync afin d’exécuter la requête immédiatement. Sinon, l’instruction affectera IQueryable<SelectListItem> à brandItems, qui ne seront pas exécuté avant son énumération. Voici les avantages et inconvénients à retourner les résultats de IQueryable de méthodes. Il permet la requête construit pour être modifiée, mais peut également donnent les erreurs qui se produisent uniquement pendant l’exécution, si les opérations sont ajoutées à la requête EF principal ne peut pas traduire EF Core. Il est généralement plus sûr transmettre tous les filtres dans la méthode d’exécution de l’accès aux données et de retour arrière d’une collection en mémoire (par exemple, liste<T>) comme résultat.

EF Core effectue le suivi des modifications sur les entités qu’il est extrait de la persistance. Pour enregistrer les modifications apportées à une entité suivie, appelez uniquement la méthode SaveChanges sur le DbContext sorte qu’il soit la même instance de DbContext qui a été utilisée pour récupérer de l’entité. Ajout et suppression d’entités sont directement sur la propriété DbSet appropriée, en utilisant un appel à SaveChanges pour exécuter les commandes de base de données. L’exemple suivant illustre l’ajout, la mise à jour et suppression d’entités de la persistance.

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

EF Core prend en charge à la fois synchrones et asynchrones des méthodes pour l’extraction et l’enregistrement. Dans les applications web, il est recommandé d’utiliser le modèle asynchrones / d’attente avec les méthodes async, afin que les threads du serveur web ne sont pas bloqués lors de l’attente de fin des opérations d’accès des données.

### <a name="fetching-related-data"></a>L’extraction de données associées

Quand EF Core récupère les entités, il remplit toutes les propriétés qui sont stockées directement avec cette entité dans la base de données. Les propriétés de navigation, telles que les listes des entités associées, ne sont pas remplies et peuvent avoir leur valeur est définie sur null. Cela garantit que EF Core n’extrait pas plus de données que nécessaire, ce qui est particulièrement important pour les applications web qui doivent rapidement traiter les demandes et renvoie des réponses de manière efficace. Pour inclure des relations à une entité en utilisant *chargement hâtif*, vous spécifiez la propriété à l’aide de la méthode d’extension Include sur la requête, comme indiqué :

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Vous pouvez inclure plusieurs relations, et vous pouvez également inclure des relations secondaire à l’aide de ThenInclude. EF Core exécutera une seule requête pour récupérer le jeu d’entités.

Une autre option de chargement des données connexes consiste à utiliser *chargement explicite*. Chargement explicite vous permet de charger des données supplémentaires dans une entité qui a déjà été récupérée. Étant donné que cela implique une demande distincte à la base de données, il n’est pas recommandé pour les applications web qui doivent réduire le nombre de base de données les allers-retours effectuées par demande.

*Chargement différé* est une fonctionnalité qui charge automatiquement les données associées, car il est référencé par l’application. Il n’est pas actuellement pris en charge par cœur de EF, mais comme avec le chargement explicit il doit généralement être désactivé pour les applications web.

### <a name="resilient-connections"></a>Connexions résilientes

Ressources externes telles que des bases de données SQL peuvent parfois être indisponibles. En cas d’indisponibilité temporaire, applications peuvent utiliser la logique de nouvelle tentative pour éviter de lever une exception. Cette technique est communément appelé *résilience des connexions*. Vous pouvez implémenter votre [propre nouvelle tentative avec interruption exponentielle](https://docs.microsoft.com/azure/architecture/patterns/retry) technique en tentant de débarrassée avec un temps d’attente augmente de manière exponentielle, jusqu'à ce qu’un nombre maximal de tentatives a été atteint. Cette technique prend en compte le fait que les ressources de cloud par intermittence peut-être pas disponibles pour courtes périodes de temps, ce qui entraîne l’échec de certaines demandes.

Pour la base de données SQL Azure, Entity Framework Core fournit déjà la logique de résilience et de nouvelle tentative de connexion de base de données interne. Mais vous devez activer la stratégie de l’exécution d’Entity Framework pour chaque connexion DbContext si vous souhaitez ayant connexions EF Core.

Par exemple, le code suivant au niveau de la connexion EF Core permet des connexions SQL résilientes qui sont retentées si la connexion échoue.

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

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Stratégies d’exécution et les transactions explicites à l’aide de BeginTransaction et plusieurs DbContexts 
  
  Lorsque de nouvelles tentatives sont activées dans les connexions EF Core, chaque opération que vous effectuez à l’aide de EF Core devient son propre opération reproductible. Chaque requête et chaque appel à SaveChanges va être retentées en tant qu’unité si une défaillance temporaire se produit.
  
  Toutefois, si votre code initie une transaction à l’aide de BeginTransaction, vous définissez votre propre groupe d’opérations qui doivent être traités en tant qu’unité, tous les éléments à l’intérieur de la transaction est restaurée si une défaillance se produit. Une exception à ce qui suit s’affiche si vous tentez d’exécuter cette transaction lors de l’utilisation d’une stratégie d’exécution EF (stratégie de nouvelle tentative) et vous incluez plusieurs SaveChanges à partir de plusieurs DbContexts qu’il contient.

System.InvalidOperationException : La stratégie d’exécution configurée 'SqlServerRetryingExecutionStrategy' ne prend pas en charge les transactions démarrées par l’utilisateur. Utilisez la stratégie d’exécution retournée par 'DbContext.Database.CreateExecutionStrategy()' pour exécuter toutes les opérations dans la transaction comme une unité reproductible.

La solution consiste à appeler manuellement la stratégie d’exécution EF avec un délégué qui représente tous les éléments qui doit être exécutée. Si une défaillance temporaire se produit, la stratégie d’exécution appelle le délégué à nouveau. Le code suivant montre comment implémenter cette approche :

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

Le premier DbContext est la \_catalogContext et le second DbContext se trouve dans le \_integrationEventLogService objet. Enfin, la validation action sera effectuée plusieurs DbContexts et à l’aide d’une stratégie d’exécution EF.

> ### <a name="references--entity-framework-core"></a>Références : Entity Framework Core
> - **Documentation de base EF**  
> <https://docs.microsoft.com/ef/>
> - **EF principale : Les données associées**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Éviter le chargement tardif des entités dans les Applications ASPNET**  
> <http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core ou micro-ORM ?

Bien que EF Core est un bon choix pour la gestion de persistance et encapsule pour la plupart des détails de la base de données à partir des développeurs d’applications, il n’est pas le seul choix possible. Une autre solution open source populaires est [Dapper](https://github.com/StackExchange/Dapper), un micro-ORM dit. Un micro-ORM est léger et moins outil complet pour le mappage d’objets à des structures de données. Dans le cas Dapper, sa conception objectifs concentrent sur les performances, plutôt qu’entièrement encapsulant sous-jacent interroge utilise pour récupérer et mettre à jour des données. Car il n’abstraite SQL du développeur, Dapper est « la plus proche du métal » et permet aux développeurs d’écrire le texte exact à utiliser pour une donnée de requêtes accéder à l’opération.

EF Core a deux fonctionnalités importantes, il fournit qui séparer de Dapper, mais également ajouter à une surcharge de ses performances. La première est la traduction à partir d’expressions LINQ dans SQL. Ces conversions sont mis en cache, mais même dans ce cas il est surcharge lors de la première fois. Le deuxième est le suivi des modifications sur les entités (de sorte que les instructions de mise à jour efficace peuvent être générées). Ce comportement peut être désactivé pour des requêtes spécifiques à l’aide de l’extension AsNotTracking. EF Core génère également des requêtes SQL qui sont généralement très efficace et dans tous les cas parfaitement acceptable à partir d’un point de vue des performances, mais si vous avez besoin de fine contrôler la requête précise doit être exécutée, vous pouvez passer dans SQL personnalisée (ou exécuter une procédure stockée) à l’aide de EF Principaux trop. Dans ce cas, toujours Dapper devance EF Core, mais légèrement. Affiche le nombre Julie Lerman certaines données de performances dans son peuvent 2016 à l’article MSDN [Dapper, Entity Framework et applications hybrides](https://msdn.microsoft.com/magazine/mt703432.aspx). Données de test d’évaluation des performances supplémentaires pour diverses méthodes d’accès aux données se trouvent sur [le site Dapper](https://github.com/StackExchange/Dapper).

Pour voir comment la syntaxe Dapper varie à partir de EF, prenez en compte ces deux versions de la même méthode pour récupérer une liste d’éléments :

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

Si vous avez besoin générer des graphiques d’objets plus complexes avec Dapper, vous devez écrire les requêtes associées (par opposition à l’ajout d’un élément Include comme vous le feriez dans EF Core). Cela est pris en charge via une variété de syntaxes, y compris une fonctionnalité appelée multiples de mappage qui vous permet de mapper des lignes individuelles pour plusieurs objets mappés. Par exemple, étant donné une classe Post avec un propriétaire de la propriété de type utilisateur, l’instruction SQL suivante renvoie toutes les données nécessaires :

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

Chaque ligne retournée inclut des données utilisateur et Post. Étant donné que les données utilisateur doivent être attachées à des données de publication via sa propriété de propriétaire, la fonction suivante est utilisée :

```csharp
(post, user) => { post.Owner = user; return post; }
```

La liste de code complète pour retourner une collection de publications dont la propriété Owner remplie avec les données utilisateur associées serait :

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Car il offre moins encapsulation, Dapper requiert les développeurs en savoir plus sur la façon dont leurs données sont stockées, comment interroger efficacement et d’écrire plus de code pour récupérer. Lorsque le modèle change, au lieu de simplement créer une nouvelle migration (une autre fonctionnalité EF Core), et/ou mise à jour des informations de mappage dans un emplacement d’un DbContext, chaque requête qui est affecté doit être mis à jour. Ces requêtes n’ont pas les garanties de temps de compilation, afin qu’ils peuvent arrêter lors de l’exécution en réponse aux modifications au modèle ou de la base de données, à des erreurs plus difficiles à détecter rapidement. En échange de ces compromis, Dapper offre des performances extrêmement rapides.

Pour la plupart des applications et la plupart des parties de presque toutes les applications, EF Core offre des performances acceptables. Par conséquent, ses avantages de la productivité du développeur sont probable que la baisse des performances. Pour les requêtes qui peuvent tirer parti de la mise en cache, la requête réelle peut uniquement être exécutée un petit pourcentage du temps, ce qui réduit les moot des différences de performances de requête.

## <a name="sql-or-nosql"></a>SQL ou NoSQL

En règle générale, les bases de données relationnelles telles que SQL Server ont dominée marketplace pour le stockage des données persistantes, mais ils ne sont pas la seule solution possible. Comme les bases de données NoSQL [MongoDB](https://www.mongodb.com/what-is-mongodb) offrent une approche différente pour le stockage d’objets. Au lieu de mappage d’objets à des tables et des lignes, une autre option consiste à sérialiser le graphique d’objets et stocker le résultat. Les avantages de cette approche, au moins au départ, sont plus de simplicité et de performances. Il est certainement plus simple stocker un objet sérialisé unique avec une clé aux décomposer l’objet en plusieurs tables avec des relations et mise à jour et des lignes qui peuvent avoir changé depuis l’objet a été récupéré à partir de la base de données. De même, l’extraction et la désérialisation d’un objet unique à partir d’un stockage basé sur la clé sont généralement beaucoup plus rapide et plus facile que dans des jointures complexes ou de plusieurs requêtes de base de données requises pour composer des entièrement le même objet à partir d’une base de données relationnelle. L’absence de verrous ou de transactions ou d’un schéma fixe permet également de bases de données NoSQL très adaptées à l’échelle entre plusieurs machines, prise en charge des jeux de données très volumineux.

En revanche, les bases de données NoSQL (comme ils sont généralement appelées) ont leurs inconvénients. Bases de données relationnelles utilisent la normalisation à appliquer la cohérence et éviter la duplication de données. Cela réduit la taille totale de la base de données et garantit que les mises à jour des données partagées sont disponibles immédiatement dans l’ensemble de la base de données. Dans une base de données relationnelle, une table d’adresses peut-être référencer une table de pays par ID, tel que si le nom d’un pays ont été modifié, les enregistrements d’adresse bénéficierait de la mise à jour sans eux-mêmes être mis à jour. Toutefois, dans une base de données NoSQL, adresse et son pays associé peuvent être sérialisée dans le cadre de nombreux objets stockés. Une mise à jour pour un nom de pays nécessiterait tous ces objets à mettre à jour, au lieu d’une seule ligne. Bases de données relationnelles peuvent également garantir l’intégrité relationnelle en appliquant des règles, comme des clés étrangères. En règle générale, les bases de données NoSQL n’offrent pas ces contraintes sur leurs données.

Une autre complexité NoSQL doivent respecter des bases de données est le contrôle de version. Lorsque les propriétés d’un objet changent, il n’est peut-être pas en mesure de désérialiser à partir de versions antérieures qui ont été stockées. Par conséquent, tous les objets existants qui ont une version sérialisée (précédente) de l’objet doivent être actualisées pour être conforme à son nouveau schéma. Cela n’est pas sur le plan conceptuel différent à partir d’une base de données relationnelle, où les modifications de schéma parfois nécessitent des scripts de mise à jour ou le mappage de mises à jour. Toutefois, le nombre d’entrées qui doit être modifiée est souvent beaucoup plus dans l’approche NoSQL, car il existe plus de duplication de données.

Il est possible dans les bases de données NoSQL pour stocker plusieurs versions d’objets, schéma fixe quelque chose de bases de données relationnelles en général, ne pas prennent en charge. Toutefois, dans ce cas votre code d’application devez prendre en compte l’existence de versions d’objets et l’ajout de complexité supplémentaire.

Bases de données NoSQL n’appliquent pas généralement [ACID](http://en.wikipedia.org/wiki/ACID), ce qui signifie qu’ils présentent des avantages de performances et l’évolutivité sur les bases de données relationnelles. Ils sont bien adaptées à des datasets très volumineux et les objets qui ne sont pas adaptés au stockage dans des structures de table normalisée. Il est inutile pour lesquelles une application unique ne peut pas tirer parti des deux relationnelle et adapté de bases de données NoSQL, utilisant chacun où il est préférable.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB est un service de base de données NoSQL entièrement géré qui offre un stockage en cloud des données sans schéma. DocumentDB est conçu pour des performances rapides et prévisibles, haute disponibilité, la mise à l’échelle élastique et distribution globale. Bien qu’étant une base de données NoSQL, les développeurs peuvent utiliser des fonctions de requête SQL riches et familiers sur des données JSON. Toutes les ressources DocumentDB sont stockés en tant que documents JSON. Les ressources sont gérées en tant que *éléments*, qui sont des documents contenant les métadonnées, et *flux*, qui sont des collections d’éléments. Figure 8-2 montre la relation entre les différentes ressources DocumentDB.


![La relation hiérarchique entre les ressources DocumentDB, une base de données NoSQL JSON](./media/image8-2.png)

**Figure 8-2.** Organisation de ressource de DocumentDB.

Le langage de requête DocumentDB est une interface simple et puissante permettant d’interroger des documents JSON. Le langage prend en charge un sous-ensemble de la grammaire SQL ANSI et ajoute l’intégration en profondeur de l’objet JavaScript, tableaux, construction d’objet et l’appel de fonction.

**Références – DocumentDB**

-   DocumentDB Introduction\
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Autres Options de persistance

Outre relationnelle et les options de stockage NoSQL, les applications ASP.NET Core permet le stockage Azure pour stocker une variété de formats de données et fichiers de façon évolutive et basée sur le cloud. Le stockage Azure est très évolutif, donc vous pouvez commencer le stockage de petites quantités de données et de monter le stockage des centaines, voire des téraoctets si votre application l’exige. Le stockage Azure prend en charge quatre types de données :

-   Stockage d’objets BLOB pour texte non structuré ou stockage binaire, également appelée stockage d’objets.

-   Stockage de table pour les datasets structurés, accessibles via les clés de ligne.

-   Stockage de file d’attente pour la messagerie fiable basée sur la file d’attente.

-   Stockage de fichier pour l’accès de fichier partagé entre les machines virtuelles et des applications locales.

**Références – stockage Azure**

-   Introduction\ de stockage Azure
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Mise en cache

Dans les applications web, chaque requête web doit être effectuée dans les plus brefs délais. Un pour y parvenir consiste à limiter le nombre d’appels externes, que le serveur doit effectuer pour terminer la demande. La mise en cache implique de stocker une copie des données sur le serveur (ou un autre magasin de données qui est plus facilement interrogée à la source de données). Applications Web et en particulier les applications web classiques de non-SPA doivent générer l’interface utilisateur entière avec chaque demande. Cela implique souvent de nombreux des mêmes requêtes de base de données à plusieurs reprises à partir de la demande d’un utilisateur à l’autre. Dans la plupart des cas, ces données changent rarement, par conséquent, il est peu de raisons d’en permanence de la demande à partir de la base de données. ASP.NET Core prend en charge la réponse mise en cache, de mise en cache des pages entières et la mise en cache des données, qui prend en charge le comportement de mise en cache plus granulaire.

Lors de l’implémentation de la mise en cache, il est important de garder à séparation tenant compte des problèmes. Évitez d’implémentation de la logique de mise en cache dans votre logique d’accès aux données, ou dans votre interface utilisateur. Au lieu de cela, encapsuler ses propres classes de mise en cache et la configuration permet de gérer son comportement. Cela suit les ouvrir/fermé et les principes de responsabilité unique et le rend plus facile de gérer la façon dont vous utilisez la mise en cache dans votre application qu’elle se développe.

### <a name="aspnet-core-response-caching"></a>La mise en cache de réponse ASP.NET Core

ASP.NET Core prend en charge deux niveaux de mise en cache de la réponse. Le premier niveau ne met pas en cache quoi que ce soit sur le serveur, mais ajoute des en-têtes HTTP qui commandent aux clients et serveurs proxy en cache les réponses. Cela est implémenté en ajoutant l’attribut ResponseCache contrôleurs individuels ou des actions :

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

L’intergiciel (middleware) réponse mise en cache met en cache automatiquement selon un ensemble de conditions que vous pouvez personnaliser les réponses. Par défaut, les réponses que 200 (OK) demandés par le biais des méthodes GET ou HEAD sont mis en cache. En outre, les demandes doivent avoir une réponse avec un Cache-Control : en-tête public et ne peut pas inclure des en-têtes de l’autorisation ou Set-Cookie. Consultez un [la liste complète des conditions de mise en cache utilisé par la réponse mise en cache d’intergiciel (middleware)](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>La mise en cache des données

Au lieu de (ou en plus) mise en cache les réponses web complète, vous pouvez mettre en cache les résultats des requêtes de données individuels. Pour ce faire, vous pouvez utiliser la mise en mémoire cache sur le serveur web, ou [un cache distribué](https://docs.microsoft.com/aspnet/core/performance/caching/distributed). Cette section va vous montrer comment implémenter la mise en mémoire cache.

Vous ajoutez la prise en charge de mémoire (ou distributed) mise en cache dans ConfigureServices :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Veillez à ajouter le package NuGet de Microsoft.Extensions.Caching.Memory également.

Une fois que vous avez ajouté le service, vous demandez IMemoryCache via l’injection de dépendances partout où vous avez besoin accéder au cache. Dans cet exemple, le CachedCatalogService utilise le modèle de conception Proxy (ou Decorator), en fournissant une autre implémentation de ICatalogService qui contrôle l’accès à (ou ajoute le comportement à) l’implémentation CatalogService sous-jacente.

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

Pour configurer l’application pour utiliser la version mise en cache du service, mais autoriser le service obtenir de l’instance de CatalogService dont il a besoin dans son constructeur, vous devez ajouter les éléments suivants dans ConfigureServices :

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Tout cela en place, les appels de base de données pour extraire les données de catalogue ne seront une fois par minute, plutôt qu’à chaque demande. Selon le trafic vers le site, cela peut avoir un impact considérable sur le nombre de requêtes effectuées sur la base de données et le temps de chargement de page moyen pour la page d’accueil actuellement varie selon les trois requêtes exposées par ce service.

Un problème qui se produit lorsque la mise en cache est implémentée est *des données obsolètes* : autrement dit, les données qui ont été modifiées à la source, mais une version obsolète restent dans le cache. Un moyen simple de résoudre ce problème consiste à utiliser les durées de petit cache, étant donné que pour une application occupée est limitée avantage supplémentaire à l’extension de la longueur de données mises en cache. Par exemple, considérez une page qui effectue une requête de base de données unique, et est demandé 10 fois par seconde. Si cette page est mise en cache pendant une minute, elle entraîne le nombre de requêtes de base de données effectuées par minute à supprimer de 600 à 1, une réduction de 99,8 %. Si à la place la durée du cache a été apportée à une heure, la réduction globale serait 99.997 %, mais maintenant l’âge de probabilité et risque de données obsolètes sont ont augmenté considérablement.

Une autre approche consiste à supprimer proactive des entrées de cache lors de la mise à jour les données qu’ils contiennent. Toute entrée individuelle peut être supprimée si sa clé est constitue :

```csharp
_cache.Remove(cacheKey);
```

Si votre application expose les fonctionnalités de mise à jour des entrées de mise en cache, vous pouvez supprimer les entrées de cache correspondante dans votre code qui effectue les mises à jour. Il peut être parfois de nombreuses entrées différentes qui dépendent d’un jeu de données particulier. Dans ce cas, il peut être utile de créer des dépendances entre les entrées du cache, à l’aide d’un CancellationChangeToken. Avec un CancellationChangeToken, vous pouvez faire expirer plusieurs entrées de cache à la fois en annulant le jeton.

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
[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)
