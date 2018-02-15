---
title: "Développer des applications MVC ASP.NET Core"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | développement d’applications de MVC ASP.NET Core"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10bf66dd37f0d99c038db7f95999d84986152fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a>Développer des applications MVC ASP.NET Core

> « Il n’est pas important de faire au mieux la première fois. Il est essentiel de faire au mieux la dernière fois. »  
> _-Recherche d’Andrew et David Thomas_

## <a name="summary"></a>Récapitulatif

ASP.NET Core est une infrastructure inter-plateformes, open source pour la création d’applications web modernes d’optimisée pour le cloud. Applications ASP.NET Core sont légers et modulaires, avec prise en charge intégrée pour l’injection de dépendance, l’activation dans supérieur de testabilité et de facilité de maintenance. Combiné avec MVC, qui prend en charge la génération web moderne API en plus des applications basées sur une vue, ASP.NET Core est une puissante infrastructure permettant de générer des applications web d’entreprise.

## <a name="mapping-requests-to-responses"></a>Mappage des demandes aux réponses

Son cœur, les applications ASP.NET Core mappent les demandes pour les réponses sortantes. Cette opération s’effectue avec un intergiciel (middleware) de bas niveau et simple applications ASP.NET Core microservices peut être constitué uniquement d’intergiciel (middleware) personnalisé. Lorsque vous utilisez ASP.NET MVC de base, vous pouvez travailler à un niveau supérieur de quelque peu, pensez en termes de *itinéraires*, *contrôleurs*, et *actions*. Chaque demande entrante est comparée à la table de routage de l’application, et si un itinéraire correspondant est trouvé, la méthode d’action associés (appartenant à un contrôleur) est appelée pour traiter cette demande. Si aucun itinéraire correspondant n’est trouvé, un gestionnaire d’erreurs (dans ce cas, retourner un résultat introuvable) est appelé.

Les applications MVC ASP.NET Core peuvent utiliser itinéraires classiques, les itinéraires d’attribut ou les deux. Itinéraires classiques sont définis dans le code, en spécifiant le routage *conventions* à l’aide de la syntaxe, comme dans l’exemple ci-dessous :

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

Dans cet exemple, un itinéraire nommé « default » a été ajouté à la table de routage. Il définit un modèle d’itinéraire avec des espaces réservés pour *contrôleur*, *action*, et *id*. Les espaces réservés de contrôleur et d’action ont par défaut spécifié (« Home » et « Index », respectivement), et l’espace réservé d’id est facultatif (en raison d’un « ? » appliqué). La convention définis ici États la première partie d’une demande doit correspondre au nom du contrôleur, la deuxième partie de l’action, et puis si nécessaire une troisième partie représente un paramètre id. Itinéraires classiques sont généralement définies dans un seul emplacement pour l’application, comme dans la méthode de configuration de la classe de démarrage.

Itinéraires d’attribut sont appliquées directement aux contrôleurs et les actions, non spécifiés globalement. Cela a l’avantage de rendre détectable beaucoup plus lorsque vous envisagez d’utiliser une méthode particulière, mais il signifie que les informations de routage ne sont pas conservées dans un seul emplacement dans l’application. Avec les itinéraires d’attribut, vous pouvez facilement spécifier plusieurs itinéraires pour une action donnée, ainsi combiner des itinéraires entre les contrôleurs et les actions. Exemple :

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

Itinéraires peuvent être spécifiés sur [HttpGet] et la séparer des attributs similaires, ce qui évite de devoir ajouter [itinéraire\] attributs. Itinéraires d’attribut peuvent également utiliser des jetons afin de réduire la nécessité de répéter des noms de contrôleur ou d’action, comme indiqué ci-dessous :

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

Une fois qu’une demande donnée a été mis en correspondance avec un itinéraire, mais avant l’action de la méthode est appelée, ASP.NET MVC de base effectuera [liaison de modèle](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) et [validation des modèles](https://docs.microsoft.com/aspnet/core/mvc/models/validation) sur la demande. Liaison de modèle est chargé de convertir des données HTTP entrantes en les types .NET spécifiés en tant que paramètres de la méthode d’action à appeler. Par exemple, si la méthode d’action attend un paramètre d’id int, liaison de modèle tente de fournir ce paramètre à partir d’une valeur fournie dans le cadre de la demande. Pour ce faire, la liaison de modèle recherche de valeurs dans un formulaire publié, les valeurs de l’itinéraire lui-même et les valeurs de chaîne de requête. En supposant qu’une valeur d’id est trouvée, elle sera convertie en un entier avant d’être passé dans la méthode d’action.

Une fois le modèle de liaison, mais avant d’appeler la méthode d’action, la validation du modèle se produit. Validation du modèle utilise des attributs facultatifs sur le type de modèle et peut aider à garantir que l’objet de modèle fourni est conforme à certaines exigences de données. Certaines valeurs peuvent être spécifiées comme requis, ou limités à une longueur ou une plage numérique, etc. Si le modèle n’est pas conforme aux exigences de leurs attributs de validation sont spécifiés, la propriété ModelState.IsValid aura la valeur false et le jeu de ne pas les règles de validation sera disponible pour envoyer au client qui effectue la requête.

Si vous utilisez la validation du modèle, vous devez être sûr de toujours vérifier que le modèle est valide avant d’exécuter les commandes de modification d’état, pour vous assurer de que votre application n’est pas endommagée par les données non valides. Vous pouvez utiliser un [filtre](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) afin d’éviter la nécessité d’ajouter du code pour ce dans chaque action. Filtres MVC ASP.NET Core offrent un moyen d’interception des groupes de requêtes, afin que les stratégies courantes et des problèmes transversaux peuvent être appliquées sur une base ciblée. Filtres peuvent être appliqués à des actions individuelles, contrôleurs de l’ensemble, ou pour une application.

Pour l’API web, ASP.NET MVC de base prend en charge [ *négociation de contenu*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), ce qui permet de spécifier comment les réponses doivent être mis en forme les demandes. Actions de renvoi de données mettra en forme, selon les en-têtes fournis dans la demande, la réponse en XML, JSON ou un autre format pris en charge. Cette fonctionnalité permet la même API utilisable par plusieurs clients avec les exigences de format de données différent.

> ### <a name="references--mapping-requests-to-responses"></a>Références : mappage des demandes aux réponses
> - **Routage vers les Actions de contrôleur**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Liaison de modèle** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **Validation des modèles**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>Utilisation des dépendances

Prend en charge intégrée et ASP.NET Core en interne utilise une technique appelée [injection de dépendance](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection). Injection de dépendances est une technique qui a activé le couplage lâche entre les différentes parties d’une application. Un couplage est souhaitable, car elle facilite l’isoler des parties de l’application, ce qui permet de test ou de remplacement. Il est également moins probable qu’une modification dans une partie de l’application aura un impact d’inattendue ailleurs dans l’application. Injection de dépendances est basée sur le principe d’inversion de dépendance et est souvent clé le principe ouvert ou fermé. Lorsque vous évaluez le fonctionnement de votre application avec ses dépendances, soyez prudent lors de la [adhésives statique](http://deviq.com/static-cling/) odeur de code et n’oubliez pas l’aphorismes «[nouveau est de type glue](http://ardalis.com/new-is-glue). »

Adhésives statique se produit lorsque vos classes d’effectuent des appels aux méthodes statiques ou accéder aux propriétés statiques, qui ont des effets secondaires ou des dépendances sur l’infrastructure. Par exemple, si vous disposez d’une méthode qui appelle une méthode statique, qui à son tour écrit pour une base de données, votre méthode est étroitement liée à la base de données. Tout ce qui interrompt l’appel de cette base de données s’arrêtera votre méthode. Ces méthodes de test est notoirement difficile, étant donné que ces tests nécessitent des bibliothèques factices commerciales pour simuler les appels statiques, ou peuvent être testés uniquement avec une base de données de test en place. Les appels statiques qui n’ont pas toute dépendance sur l’infrastructure, notamment celles qui sont complètement sans état, conviennent appeler et n’ont aucun impact sur le couplage ou testabilité (au-delà de couplage de code à l’appel statique proprement dit).

De nombreux développeurs comprennent les risques d’adhésives statique et état global, mais il seront toujours étroitement associer de leur code pour les implémentations spécifiques à l’instanciation directe. « Nouvelle est type glue » est destiné à être un rappel de cette association et pas un condamnant générale de l’utilisation du nouveau mot clé. Tout comme avec les appels de méthode statique, nouvelles instances de types qui n’ont aucune dépendance externe en général, ne pas étroitement associer le code pour les détails d’implémentation ou compliquer le test. Cependant, chaque fois qu’une classe est instanciée, quelques instants à prendre en compte qu’elle soit logique coder en dur cette instance spécifique à cet emplacement spécifique, ou si elle serait une meilleure conception pour demander de cette instance en tant que dépendance.

### <a name="declare-your-dependencies"></a>Déclarer les dépendances

ASP.NET Core est construit autour des méthodes et classes déclarent leurs dépendances, en les demandant en tant qu’arguments. Les applications ASP.NET sont généralement configurées dans une classe de démarrage, qui elle-même est configuré pour prendre en charge l’injection de dépendances sur plusieurs points. Si votre classe de démarrage a un constructeur, il peut demander des dépendances par le biais du constructeur, comme suit :

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

La classe de démarrage est intéressante dans la mesure où il n’existe aucune exigence de type explicite pour celle-ci. Il n’hérite pas d’une classe de base de démarrage spéciale, ni il implémente une interface particulière. Vous pouvez lui attribuer un constructeur, ou non, et vous pouvez spécifier autant de paramètres dans le constructeur que vous le souhaitez. Lorsque l’hôte web que vous avez configuré pour votre application démarre, il appelle la classe de démarrage que vous avez indiqué qu’il soit utilisé et permet l’injection de dépendances de remplir toutes les dépendances de que la classe de démarrage nécessite. Bien entendu, si vous demandez des paramètres qui ne sont pas configurés dans le conteneur de services utilisé par ASP.NET Core, vous obtiendrez une exception, mais tant que vous respectez les dépendances du conteneur connaît, vous pouvez demander à ce que vous voulez.

Injection de dépendances est intégrée à vos applications ASP.NET Core dès le départ, lorsque vous créez l’instance de démarrage. Il ne s’arrête pas il pour la classe de démarrage. Vous pouvez également demander les dépendances dans la méthode de configuration :

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

La méthode ConfigureServices est l’exception à ce comportement ; Il doit prendre qu’un seul paramètre de type IServiceCollection. Il n’a pas vraiment besoin prendre en charge l’injection de dépendances, étant donné que d’une part, il est chargé d’ajouter des objets dans le conteneur de services et d’autre part, il a accès à tous les services actuellement configurés via le paramètre IServiceCollection. Par conséquent, vous pouvez travailler avec les dépendances définies dans la collection de services ASP.NET Core dans chaque partie de la classe de démarrage, soit en demandant le service nécessaire en tant que paramètre ou en travaillant avec la IServiceCollection dans ConfigureServices.

> [!NOTE]
> Si vous devez vous assurer de certains services sont disponibles pour votre classe de démarrage, vous pouvez les configurer à l’aide de WebHostBuilder et sa méthode ConfigureServices.

La classe de démarrage est un modèle pour comment structurer les autres parties de votre application ASP.NET Core, à partir de contrôleurs de l’intergiciel (middleware) pour les filtres à vos propres Services. Dans chaque cas, vous devez suivre le [principe de dépendances explicites](http://deviq.com/explicit-dependencies-principle/), demandant les dépendances, plutôt que directement les créer et tirant parti de l’injection de dépendances dans votre application. Soyez prudent d’où et comment vous instanciez directement des implémentations, notamment les services et les objets qui fonctionnent avec l’infrastructure ou aient des effets secondaires. Préférez utiliser abstractions définies dans votre base de l’application et passé en tant qu’arguments à coder en dur les références aux types d’implémentation spécifique.

## <a name="structuring-the-application"></a>Structuration de l’Application

Les applications monolithiques ont généralement un point d’entrée unique. Dans le cas d’une application web ASP.NET Core, le point d’entrée sera le projet web ASP.NET Core. Toutefois, cela ne signifie pas que la solution doit être composé de simplement un projet unique. Il est utile de diviser l’application en différentes couches pour suivre la séparation des problèmes. Une fois divisé en couches, il est utile d’aller au-delà de dossiers pour séparer les projets, qui peuvent aider à atteindre une meilleure encapsulation. La meilleure approche pour atteindre ces objectifs avec une application ASP.NET Core est une variante de l’Architecture de nettoyage décrite dans le chapitre 5. Suite de cette approche, solution de l’application est constituée de bibliothèques distincts pour l’interface utilisateur, l’Infrastructure et ApplicationCore.

En plus de ces projets, projets de test distinct sont également inclus (test est décrite dans le chapitre 9).

Modèle d’objet et les interfaces de l’application doivent être placés dans le projet ApplicationCore. Ce projet sera ont des dépendances aussi peu que possible, et les autres projets dans la solution de référence. Entités métier qui doivent être persistants sont définies dans le projet ApplicationCore, comme le sont les services qui ne dépendent pas directement sur l’infrastructure.

Détails d’implémentation, telles que la persistance est effectuée ou comment les notifications peuvent être envoyées à un utilisateur, sont conservés dans le projet d’Infrastructure. Ce projet fait référence à des packages spécifiques à l’implémentation telles que Entity Framework Core, mais ne doit pas exposer de détails sur ces implémentations en dehors du projet. Services d’infrastructure et de référentiels doivent implémenter les interfaces qui sont définies dans le projet ApplicationCore et ses implémentations de persistance sont responsables de la récupération et l’enregistrement des entités définies dans ApplicationCore.

Le projet ASP.NET Core lui-même est chargé de cas de problèmes au niveau de l’interface utilisateur, mais ne doit pas inclure de détails logique ou d’infrastructure d’entreprise. En fait, dans l’idéal, il ne doit pas même ont une dépendance sur le projet d’Infrastructure, ce qui permet de s’assurer qu'aucune dépendance entre les deux projets n’a été introduite par inadvertance. Cela est possible à l’aide d’un conteneur de DI tiers comme StructureMap, ce qui vous permet de définir les règles de DI dans les classes de Registre dans chaque projet.

Une autre approche pour découpler l’application à partir des détails d’implémentation est d’avoir le microservices application appel, éventuellement déployés dans des conteneurs Docker individuels. Cela fournit le même meilleure séparation des préoccupations et le découplage à tirer parti de DI entre deux projets, mais a une complexité supplémentaire.

### <a name="feature-organization"></a>Organisation de fonctionnalité

Par défaut, les applications ASP.NET Core organisent leur structure de dossiers à inclure les contrôleurs et les vues et fréquemment ViewModel. Code côté client pour prendre en charge de ces structures côté serveur est généralement stocké séparément dans le dossier wwwroot. Toutefois, les applications volumineuses peuvent rencontrer des problèmes cette organisation, car fonctionne sur n’importe quelle fonctionnalité donnée souvent requiert l’accès entre ces dossiers. Vous obtenez ainsi plus difficile à mesure que le nombre de fichiers et sous-dossiers dans chaque dossier augmente, ce qui entraîne une grande partie de défilement dans l’Explorateur de solutions. Une solution à ce problème consiste à organiser le code d’application par *fonctionnalité* plutôt que par le type de fichier. Ce style d’organisation est généralement appelé dossiers de fonctionnalités ou des segments de fonctionnalité (voir aussi : [tranches Vertical](http://deviq.com/vertical-slices/)).

Base d’ASP.NET MVC prend en charge les zones à cet effet. L’utilisation de zones, vous pouvez créer des ensembles distincts de contrôleurs et vues dossiers (ainsi que tous les modèles associés) dans chaque dossier de zone. Figure 7-1 montre un exemple de structure de dossier, à l’aide de zones.

![](./media/image7-1.png)

Figure 7-1 exemple d’organisation zone

Lorsque vous utilisez des zones, vous devez utiliser des attributs pour décorer vos contrôleurs avec le nom de la zone à laquelle ils appartiennent :

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Vous devez également ajouter la prise en charge de la zone votre les itinéraires :

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

Outre la prise en charge intégrée pour les domaines, vous pouvez également utiliser votre propre structure de dossiers et des conventions à la place des attributs et des itinéraires personnalisés. Cela vous permettrait d’avoir des dossiers de fonctionnalité qui n’a pas d’inclure des dossiers distincts pour les vues, contrôleurs, etc., en conservant la hiérarchie plate et la rendre plus facile de voir que tous les fichiers associés dans un emplacement unique pour chaque fonctionnalité.

ASP.NET Core utilise les types intégrés de convention de contrôler son comportement. Vous pouvez modifier ou remplacer ces conventions. Par exemple, vous pouvez créer une convention qui obtiennent automatiquement le nom d’un contrôleur donné en fonction de son espace de noms (qui correspond généralement au dossier dans lequel se trouve le contrôleur de) :

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

Puis, vous spécifiez cette convention en tant qu’option lorsque vous ajoutez la prise en charge pour MVC à votre application dans ConfigureServices :

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC utilise également une convention pour trouver les vues. Vous pouvez la remplacer par une convention personnalisée afin que les vues se trouvent dans vos dossiers de fonctionnalité (en utilisant le nom de la fonctionnalité fourni par la FeatureConvention, ci-dessus). Vous pouvez en savoir plus sur cette approche et télécharger un exemple fonctionnel de l’article MSDN, [tranches de fonctionnalité pour ASP.NET MVC de base](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Problèmes transversaux

À mesure que les applications augmentent, il devient plus en plus important d’isoler les problèmes transversaux pour éliminer les doublons et maintenir la cohérence. Quelques exemples de problèmes transversaux dans les applications ASP.NET Core sont l’authentification, les règles de validation de modèle, la mise en cache de sortie et une gestion d’erreurs, s’il existe beaucoup d’autres. ASP.NET Core MVC [filtres](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) vous permettent d’exécuter du code avant ou après certaines opérations dans le pipeline de traitement de la requête. Par exemple, un filtre peut s’exécuter avant et après la liaison de modèle, avant et après une action, ou avant et après les résultats d’une action. Vous pouvez également utiliser un filtre d’autorisation pour contrôler l’accès au reste du pipeline. Montre des figures 7-2 de demander des flux d’exécution des filtres si configuré.

![La requête est traitée à travers les filtres d’autorisations, les filtres de ressources, la liaison de modèle, les filtres d’actions, l’exécution d’actions et la conversion des résultats d’actions, les filtres d’exceptions, les filtres de résultats et l’exécution de résultats. En sortie, la requête est traitée seulement par les filtres de résultats et les filtres de ressources avant de devenir une réponse envoyée au client.](./media/image7-2.png)

Exécution de la demande figure 7-2 via des filtres et le pipeline de requête.

Les filtres sont généralement implémentés en tant qu’attributs, que vous puissiez les appliquer contrôleurs ou les actions. Lors de l’ajout de cette manière, les filtres spécifiés au remplacement de niveau action ou s’appuient les filtres spécifiés au niveau du contrôleur, qui à leur tour remplacer les filtres globaux. Par exemple, le \[itinéraire\] attribut peut être utilisé pour générer des itinéraires entre les contrôleurs et les actions. De même, autorisation peut être configurée au niveau du contrôleur et puis remplacée par des actions, comme l’exemple suivant montre comment :

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

La première méthode, la connexion, utilise le filtre AllowAnonymous (attribut) pour remplacer le filtre Authorize définie au niveau du contrôleur. L’action motdepasse oublié (et toute autre action dans la classe qui n’a pas un attribut AllowAnonymous) nécessite une demande authentifiée.

Filtres peuvent être utilisés pour éliminer les doublons sous la forme d’erreur courants, la gestion des stratégies pour les API. Par exemple, une stratégie d’API par défaut est pour renvoyer une réponse non trouvé pour les demandes faisant référence à des clés qui n’existent pas et un BadRequest si la validation du modèle échoue. L’exemple suivant illustre ces deux stratégies en action :

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Ne pas autoriser vos méthodes d’action à encombrer avec code conditionnel comme suit. Au lieu de cela, extrayez les stratégies dans les filtres qui peuvent être appliquées en fonction des besoins. Dans cet exemple, le contrôle de validation de modèle, ce qui se produit chaque fois qu’une commande est envoyée à l’API, peut être remplacé par l’attribut suivant :

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

De même, un filtre peut être utilisé pour vérifier si un enregistrement existe et qu’elle retourne une erreur 404 avant l’exécution de l’action, en éliminant la nécessité pour effectuer ces vérifications dans l’action. Une fois que vous avez retiré aux conventions communes et organisées de votre solution pour séparer les infrastructure code et la logique métier à partir de votre interface utilisateur, vos méthodes d’action MVC doivent être extrêmement dynamique :

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Vous pouvez en savoir plus sur les filtres de mise en œuvre et télécharger un exemple fonctionnel de l’article MSDN, [Real World ASP.NET Core MVC filtres](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Références : structuration des Applications
> - **Zones**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN – tranches de fonctionnalité pour les principaux d’ASP.NET MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtres**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – filtres MVC ASP.NET Core réel**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Sécurité

Sécurisation des applications web est une rubrique de grande taille, avec plusieurs considérations. À son niveau le plus élémentaire, sécurité implique de vérifier que vous savez provenant d’une demande donnée, et puis en vérifiant que cette demande a uniquement accès aux ressources, qu'il doit. L’authentification est le processus de la comparaison des informations d’identification fournies avec une demande à celles figurant dans un magasin de données approuvé pour voir si la demande doit être traitée comme provenant d’une entité connue. L’autorisation est le processus de limiter l’accès à certaines ressources en fonction de l’identité de l’utilisateur. Un problème de sécurité tiers protège les demandes d’écoute clandestine par des tiers pour lequel vous devez au moins [garantir que SSL est utilisé par votre application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Authentification

Identité de ASP.NET Core est un système d’appartenance que vous pouvez utiliser pour prendre en charge des fonctionnalités de connexion pour votre application. Il est prise en charge pour les comptes d’utilisateurs locaux, ainsi que la prise en charge du fournisseur de connexion externe à partir de fournisseurs, tels que Microsoft Account, Twitter, Facebook, Google et bien plus encore. En plus de ASP.NET Core Identity, votre application peut utiliser l’authentification windows ou un fournisseur d’identité tiers comme [Identity Server](https://github.com/IdentityServer/IdentityServer4).

Identité de ASP.NET Core est incluse dans les nouveaux modèles de projet si les comptes d’utilisateur individuels est sélectionnée. Ce modèle inclut la prise en charge de l’inscription, login, logins externes, les mots de passe oubliés et des fonctionnalités supplémentaires.

![](./media/image7-3.png)

Figure 7-3 Sélectionnez comptes d’utilisateur individuels d’identité préconfigurée.

Prise en charge de l’identité est configuré dans le démarrage, à la fois dans ConfigureServices et de configuration :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

Il est important que UseIdentity apparaissent avant UseMvc dans la méthode de configuration. Lorsque vous configurez l’identité dans ConfigureServices, vous remarquerez un appel à AddDefaultTokenProviders. Cela n’a rien à faire avec les jetons qui peuvent être utilisés pour sécuriser les communications web, mais au lieu de cela fait référence aux fournisseurs de créer des invites qui peuvent être envoyés aux utilisateurs via SMS ou par courrier électronique afin de les confirmer leur identité.

Vous pouvez en savoir plus sur [configuration de l’authentification à deux facteurs](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) et [activer les fournisseurs de connexion externe](https://docs.microsoft.com/aspnet/core/security/authentication/social/) à partir de la documentation officielle de ASP.NET Core.

### <a name="authorization"></a>Autorisation

La forme la plus simple d’autorisation consiste à restreindre l’accès aux utilisateurs anonymes. Cela peut être obtenue en appliquant simplement le \[Authorize\] à certains contrôleurs ou les actions d’attribut. Si les rôles sont utilisés, l’attribut peut être plus étendu pour restreindre l’accès aux utilisateurs qui appartiennent à certains rôles, comme indiqué :

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Dans ce cas, les utilisateurs appartenant aux rôles du chef de service ou Finance (ou les deux) aient accès à la SalaryController. Pour exiger qu’un utilisateur appartient à plusieurs rôles (pas seulement un des nombreux), vous pouvez appliquer l’attribut à plusieurs reprises, en spécifiant un rôle requis chaque fois.

En spécifiant certains ensembles de rôles comme chaînes dans de nombreux différents contrôleurs et les actions peuvent entraîner une répétition indésirable. Vous pouvez configurer des stratégies d’autorisation, qui encapsulent les règles d’autorisation, et ensuite spécifier la stratégie au lieu des rôles individuels lors de l’application le \[Authorize\] attribut :

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

À l’aide de stratégies de cette façon, vous pouvez séparer les types d’actions en cours d’empêcher les rôles spécifiques ou les règles qui s’appliquent à celui-ci. Ultérieurement, si vous créez un nouveau rôle qui a besoin d’accéder à certaines ressources, vous pouvez simplement mettre à jour une stratégie, plutôt que de mise à jour de chaque liste de rôles sur chaque \[Authorize\] attribut.

#### <a name="claims"></a>Revendications

Les revendications sont des paires nom / valeur qui représentent les propriétés d’un utilisateur authentifié. Par exemple, vous pouvez stocker matricule d’utilisateurs en tant que revendication. Revendications peuvent ensuite être utilisées dans le cadre de stratégies d’autorisation. Vous pouvez créer une stratégie nommée « EmployeeOnly » qui requiert l’existence d’une revendication appelée « EmployeeNumber », comme illustré dans cet exemple :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

Cette stratégie peut ensuite être utilisée avec la \[Authorize\] attribut pour protéger n’importe quel contrôleur et/ou l’action, comme décrit ci-dessus.

#### <a name="securing-web-apis"></a>Sécurisation des API Web

La plupart des API de web doit implémenter un système d’authentification par jeton. L’authentification de jeton est sans état et conçu pour être évolutive. Dans un système d’authentification par jeton, le client doit s’authentifier auprès du fournisseur d’authentification. En cas de réussite, le client est émis un jeton, qui est une simple chaîne de caractères significatif par chiffrement. Lorsque le client doit émettre une demande à une API puis, il ajoute ce jeton en tant qu’un en-tête de la demande. Le serveur valide alors le jeton trouvé dans l’en-tête de demande avant la fin de la demande. Figure 7-4 illustre ce processus.

![TokenAuth](./media/image7-4.png)

**Figure 7-4.** Authentification basée sur les jetons pour l’API Web.

> ### <a name="references--security"></a>Références : sécurité
> - **Vue d’ensemble des documents de sécurité**  
> https://docs.microsoft.com/aspnet/core/security/
> - **Application de SSL dans une application ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Présentation d’Identity**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Introduction à l’autorisation**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Authentification et autorisation pour API Apps dans Azure App Service**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>Communication du client

En plus de servir des pages et répondre aux requêtes de données via l’API web, les applications ASP.NET Core peuvent communiquer directement avec les clients connectés. Cette communication sortante peut utiliser diverses technologies de transport, les plus courantes étant WebSocket. ASP.NET Core SignalR est une bibliothèque qui facilite leur type de fonctionnalité de communication client-server en temps réel à vos applications. SignalR prend en charge de diverses technologies de transport, y compris les WebSockets et résume les détails d’implémentation du développeur de nombreuses absent.

ASP.NET Core SignalR est actuellement en cours de développement et sera disponible dans la prochaine version de ASP.NET Core. Toutefois, autres [Ouvrir source WebSockets bibliothèques](https://github.com/radu-matei/websocket-manager) sont actuellement disponibles.

Communication des clients en temps réel, si à l’aide du protocole WebSocket directement ou autres techniques, sont utiles dans différents scénarios d’application. Voici quelques exemples :

-   Applications de salle de conversation en direct

-   Analyse des applications

-   Mises à jour de progression de tâche

-   Notifications

-   Applications de formulaires interactifs

Lors de la génération de communication des clients dans vos applications, il existe généralement deux composants :

-   Gestionnaire de connexion côté serveur (concentrateur SignalR, WebSocketManager WebSocketHandler)

-   Bibliothèque côté client

Les clients ne sont pas limités aux navigateurs – les applications mobiles, les applications console, et d’autres applications natives peuvent également communiquer à l’aide de SignalR/WebSockets. L’exemple de programme suivant retourne tout le contenu envoyé à une application de conversation dans la console, dans le cadre d’une application d’exemple WebSocketManager :

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }
    
    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }
    
    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
```

Envisagez de rencontrer des manières de vos applications communiquent directement avec les applications clientes et considérez si une communication en temps réel sont susceptibles d’améliorer les utilisateurs de votre application.

> ### <a name="references--client-communication"></a>Références : la Communication Client
> - **ASP.NET Core SignalR**  
> <https://github.com/aspnet/SignalR>
> - **Gestionnaire de WebSocket**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Domaine piloté par une conception doit appliquer ?

Conception pilotée par domaine (DDD) est une approche agile pour la création de logiciels qui met l’accent sur en mettant l’accent sur la *domaine d’entreprise*. Elle place une lourde mettant l’accent sur les communications et les interactions avec expert(s) de domaine d’entreprise qui peut être lié aux développeurs comment fonctionne le système réel. Par exemple, si vous créez un système qui gère les transactions boursières, votre expert du domaine peut-être un broker stock expérimenté. DDD est conçu pour résoudre des problèmes volumineuses et complexes et n’est pas souvent approprié pour les applications plus petites et plus simples, comme l’investissement dans la compréhension et la modélisation du domaine n’est pas peine.

Lors de la génération de logiciel en suivant une approche DDD, votre équipe (y compris les parties prenantes non techniques et les contributeurs) doit développer une *langage omniprésent* pour le problème d’espace. Autrement dit, la même terminologie doit être utilisée pour le concept de réelles en cours de modélisation, l’équivalent de logiciel et les structures qui peuvent exister pour rendre persistant le concept (par exemple, les tables de base de données). Par conséquent, les concepts décrits dans le langage omniprésent forment la base de votre *modèle de domaine*.

Votre modèle de domaine est composé d’objets qui interagissent entre eux pour représenter le comportement du système. Ces objets peuvent être comprises dans les catégories suivantes :

-   [Entités](http://deviq.com/entity/), qui représentent des objets avec un thread d’identité. Les entités sont généralement stockées dans la persistance avec une clé à laquelle ils peuvent être récupérées ultérieurement.

-   [Agrégats](http://deviq.com/aggregate-pattern/), qui représentent des groupes d’objets qui doivent être rendues persistantes en tant qu’unité.

-   [Objets de valeur](http://deviq.com/value-object/), qui représentent des concepts qui peuvent être comparés en fonction de la somme de leurs valeurs de propriété. Par exemple, DateRange consistant en une date de début et de fin.

-   [Événements de domaine](https://martinfowler.com/eaaDev/DomainEvent.html), qui représentent les éléments qui passe au sein du système qui présentent un intérêt à d’autres parties du système.

Notez qu’un modèle de domaine DDD doit encapsuler un comportement complexe dans le modèle. Entités, en particulier, ne doivent pas simplement être collections de propriétés. Lorsque le modèle de domaine ne possède pas de comportement et simplement représente l’état du système, elle est dite un [anemic modèle](http://deviq.com/anemic-model/), ce qui n’est pas souhaitable dans DDD.

En plus de ces types de modèles, DDD utilise généralement une variété de modèles :

-   [Référentiel](http://deviq.com/repository-pattern/), pour l’abstraction des détails de la persistance.

-   [Fabrique](https://en.wikipedia.org/wiki/Factory_method_pattern), pour l’encapsulation de la création d’objets complexes.

-   Événements de domaine, de découplage comportement dépendant de déclencher le comportement.

-   [Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), pour l’encapsulation comportement complexe et/ou les détails d’implémentation infrastructure.

-   [Commande](https://en.wikipedia.org/wiki/Command_pattern), de découplage émettre des commandes et l’exécution de la commande elle-même.

-   [Spécification](http://deviq.com/specification-pattern/), pour encapsuler les détails de la requête.

DDD recommande également l’utilisation de l’Architecture de nettoyer indiqué précédemment, ce qui permet un couplage faible, l’encapsulation et le code qui peut facilement être vérifié à l’aide de tests unitaires.

### <a name="when-should-you-apply-ddd"></a>Lorsque doit s’appliquer DDD

DDD convient bien pour les applications volumineuses avec la complexité de l’entreprise importantes (pas seulement techniques). L’application doit nécessiter la base de connaissances des experts du domaine. Il doit y avoir un comportement significatif dans le modèle de domaine lui-même, représentant les règles d’entreprise et les interactions au-delà de simplement le stockage et la récupération de l’état actuel de plusieurs enregistrements à partir de magasins de données.

### <a name="when-shouldnt-you-apply-ddd"></a>Quand ne doit pas appliquer DDD

DDD implique des investissements dans les communications qui ne peuvent pas être justifiée aux petites applications ou les applications qui sont essentiellement simplement CRUD (création/lecture/mise à jour/suppression), l’architecture et la modélisation. Si vous choisissez d’approche de votre application suivant DDD, mais que votre domaine dispose d’un modèle anemic avec aucun comportement à trouver, vous devrez peut-être de repenser votre approche. Votre application n’est peut-être pas DDD, ou vous devrez peut-être contacter refactoriser votre application pour encapsuler la logique métier dans le modèle de domaine, plutôt que dans votre base de données ou l’interface utilisateur.

Une approche hybride serait d’utiliser uniquement les DDD pour les zones transactionnelles ou plus complexes de l’application, mais pas pour CRUD plus simple ou en lecture seule des parties de l’application. Par exemple, pas besoin d’avoir les contraintes d’un agrégat si vous interrogez des données pour afficher un rapport ou pour visualiser les données d’un tableau de bord. Il est parfaitement acceptable d’avoir un modèle de lecture distinct, le plus simple pour ces exigences.

> ### <a name="references--domain-driven-design"></a>Références – conception pilotée par domaine
> - **DDD en anglais (dépassement de capacité de réponse)**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Déploiement

Il existe quelques étapes impliqués dans le déploiement de votre application ASP.NET Core, quel que soit l’endroit où il sera hébergé. La première étape consiste à publier l’application, ce qui peut être effectuée à l’aide de la dotnet publier des commandes CLI. Vous compilez l’application et placer tous les fichiers nécessaires à l’exécution de l’application dans un dossier désigné. Lorsque vous déployez à partir de Visual Studio, cette étape est effectuée automatiquement pour vous. Le dossier de publication contient des fichiers .exe et .dll de l’application et ses dépendances. Une application autonome inclut également une version du runtime .NET. Les applications ASP.NET Core inclut également les fichiers de configuration, les ressources de client statique et les vues MVC.

Les applications ASP.NET Core sont des applications console qui doivent être démarrées lorsque le serveur démarre et redémarré en cas de panne de l’application (ou serveur). Un gestionnaire de processus peut être utilisé pour automatiser ce processus. Les gestionnaires de processus courants pour ASP.NET Core sont Nginx et Apache sur Linux et les services IIS ou un Service Windows sur Windows.

En plus d’un gestionnaire de processus, les applications de ASP.NET Core hébergées sur le serveur web de Kestrel doivent utiliser un serveur proxy inverse. Un serveur proxy inverse reçoit des demandes HTTP à partir d’internet et les transfère à Kestrel après une gestion préliminaire. Serveurs de proxy inverse fournissent une couche de sécurité pour l’application et sont requis pour les déploiements de bord (exposés au trafic Internet). Kestrel est relativement nouveau et n’offre pas encore défenses contre certaines attaques. Kestrel également ne prend en charge plusieurs applications sur le même port, d’hébergement afin de techniques telles que des en-têtes d’hôte ne peut pas être utilisés avec lui pour permettre l’hébergement de plusieurs applications sur le même port et l’adresse IP.

![Kestrel à Internet](./media/image7-5.png)

Figure 7-5 ASP.NET hébergée dans Kestrel derrière un serveur proxy inverse

Un autre scénario dans lequel un proxy inverse peut être utile est sécurisé de plusieurs applications à l’aide de SSL/HTTPS. Dans ce cas, seul le proxy inverse devrez avoir configuré SSL. Communication entre le serveur proxy inverse et Kestrel puisse avoir lieu via HTTP, comme indiqué dans la Figure 7-6.

![](./media/image7-6.png)

Figure 7-6 ASP.NET hébergée derrière un serveur HTTPS sécurisée de proxy inverse

Une approche plus en plus répandue consiste à héberger votre application ASP.NET Core dans un conteneur Docker, qui ensuite peut être hébergé localement ou déployé sur Azure pour l’hébergement de nuage. Le conteneur Docker peut contenir votre code d’application en cours d’exécution sur Kestrel et il est déployé derrière un serveur proxy inverse, comme indiqué ci-dessus.

Si vous hébergez votre application sur Azure, vous pouvez utiliser la passerelle d’Application Microsoft Azure en tant qu’un équipement virtuel dédié pour fournir plusieurs services. En plus d’agissant comme un proxy inverse pour des applications individuelles, passerelle d’Application peut également proposer les fonctionnalités suivantes :

-   L’équilibrage de charge HTTP

-   Déchargement SSL (protocole SSL uniquement à Internet)

-   SSL de bout en bout

-   Routage de plusieurs sites (consolidation jusqu'à 20 sites sur une seule passerelle d’Application)

-   Pare-feu d’applications Web

-   Prise en charge de WebSocket

-   Diagnostics avancés

*En savoir plus sur les options de déploiement d’Azure dans le chapitre 10.*

> ### <a name="references--deployment"></a>Références : déploiement
> - **Hébergement et vue d’ensemble du déploiement**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Quand utiliser Kestrel avec un proxy inverse**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Applications ASP.NET Core hôte dans Docker**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Présentation de passerelle d’Application Windows Azure**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[Précédente] (commun-client-côté-web-technologies.md) [suivant] (work-with-data-in-asp-net-core-apps.md)
