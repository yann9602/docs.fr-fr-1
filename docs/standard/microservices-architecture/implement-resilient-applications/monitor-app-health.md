---
title: "Contrôle d’intégrité"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Contrôle d’intégrité"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a>Contrôle d’intégrité

Contrôle d’intégrité permettent la proximité en temps réel des informations sur l’état de vos conteneurs microservices. Contrôle d’intégrité est essentiel à plusieurs aspects de fonctionnement microservices et est particulièrement important lorsque orchestrators effectuer des mises à niveau de l’application partielle en plusieurs phases, comme expliqué ultérieurement.

Applications basées sur des Microservices utilisent souvent des pulsations ou les contrôles d’intégrité pour activer leur analyseurs de performances planificateurs et orchestrators suivre la multitude de services. Si les services ne peut pas envoyer une sorte de signal « Je suis », à la demande ou selon une planification, votre application peut sont confrontés à des risques lorsque vous déployez des mises à jour, ou peut simplement détecter les défaillances trop tard et ne pas pouvoir arrêter les pannes en cascade peuvent finir à des pannes majeures.

Dans le modèle par défaut, les services envoient des rapports sur leur état, et ces informations sont agrégées afin de fournir une vue d’ensemble de l’état d’intégrité de votre application. Si vous utilisez un orchestrator, vous pouvez fournir des informations d’intégrité dans le cluster de votre orchestrator, afin que le cluster peut agir en conséquence. Si vous investissez dans le rapport d’intégrité de haute qualité personnalisé pour votre application, vous pouvez détecter et résoudre les problèmes de votre application en cours d’exécution beaucoup plus facilement.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Implémentation du contrôle d’intégrité vérifie dans les services ASP.NET Core

Lorsque vous développez une application de microservice ou web ASP.NET Core, vous pouvez utiliser une bibliothèque nommée vérifications de l’équipe de ASP.NET. (À compter de mai 2017, des premières versions sont disponible sur GitHub).

Cette bibliothèque est facile à utiliser et fournit des fonctionnalités qui permettent de que vous validez que n’importe quelle ressource externe spécifique nécessaire pour votre application (par exemple, une base de données SQL Server ou une API distante) fonctionne correctement. Lorsque vous utilisez cette bibliothèque, vous pouvez également décider de ce que cela signifie que la ressource est intègre, nous expliquerons ultérieurement.

Pour pouvoir utiliser cette bibliothèque, vous devez tout d’abord utiliser la bibliothèque dans votre microservices. En second lieu, vous avez besoin d’une application frontale qui interroge pour les rapports d’intégrité. Application frontale peut être une application de création de rapports personnalisée, ou elle peut être un orchestrator lui-même, de réagir en conséquence pour les États d’intégrité.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>À l’aide de la bibliothèque de vérifications dans votre système principal ASP.NET microservices

Vous pouvez voir comment la bibliothèque de vérifications est utilisée dans l’exemple d’application eShopOnContainers. Pour commencer, vous devez définir ce qui constitue un état sain pour chaque microservice. Dans l’exemple d’application, les microservices sont sains si l’API microservice est accessible via HTTP et si sa base de données SQL Server associée est également disponible.

À l’avenir, vous serez en mesure d’installer la bibliothèque de vérifications sous forme de package NuGet. Mais à ce jour, vous devez télécharger et compiler le code dans le cadre de votre solution. Clonage du code disponible à l’adresse https://github.com/aspnet/HealthChecks et copiez les dossiers suivants à votre solution.

  - src/commun
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Vous pouvez également utiliser des vérifications supplémentaires telles que celles pour Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mais étant donné que cette version d’eShopOnContainers ne dispose pas d’une dépendance sur Azure, vous n’avez pas besoin. Vous n’avez pas besoin des contrôles ASP.NET, eShopOnContainers étant basé sur ASP.NET Core.

Figure 10-6 montre la bibliothèque de vérifications dans Visual Studio, prêt à être utilisé comme un bloc de construction par n’importe quel microservices.

![](./media/image6.png)

**Figure 10-6**. Code source d’ASP.NET Core vérifications bibliothèque dans une solution Visual Studio

Introduit précédemment, la première chose à faire dans chaque projet microservice consiste à ajouter une référence pour les trois bibliothèques de vérifications. Après cela, vous ajoutez les actions de contrôle d’intégrité que vous souhaitez exécuter dans ce microservice. Ces actions sont essentiellement des dépendances sur d’autres microservices (HttpUrlCheck) ou les bases de données (actuellement SqlCheck\* pour les bases de données SQL Server). Vous ajoutez l’action au sein de la classe de démarrage de chaque microservice d’ASP.NET ou une application web ASP.NET.

Chaque service ou une application web doit être configurée en ajoutant toutes ses dépendances HTTP ou de la base de données comme une méthode AddHealthCheck. Par exemple, l’application web MVC eShopOnContainers dépend de nombreux services, par conséquent possède plusieurs méthodes de AddCheck ajoutés pour les vérifications d’intégrité.

Par exemple, dans le code suivant, vous pouvez voir comment le catalogue microservice ajoute une dépendance sur sa base de données SQL Server.

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

Toutefois, l’application web MVC d’eShopOnContainers a plusieurs dépendances sur le reste de la microservices. Par conséquent, il appelle une méthode AddUrlCheck pour chaque microservice, comme indiqué dans l’exemple suivant :

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

Par conséquent, un microservice ne fournira pas l’état « sain » jusqu'à ce que tous ses contrôles sont intègres également.

Si le microservice ne dispose pas d’une dépendance sur un service ou sur SQL Server, vous devez simplement ajouter une vérification Healthy("Ok"). Le code suivant provient de la microservice basket.api eShopOnContainers. (Le microservice du panier d’achat utilise le cache Redis, mais la bibliothèque ne comporte pas encore d’un fournisseur de contrôle d’intégrité Redis).

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Pour une application web ou de service exposer le point de terminaison de contrôle d’intégrité, il doit activer la UseHealthChecks (\[*url\_pour\_intégrité\_vérifie*\]) extension méthode. Cette méthode est envoyé à la WebHostBuilder au niveau de la méthode principale de la classe de programme de votre application web ou service ASP.NET Core, juste après UseKestrel comme indiqué dans le code ci-dessous.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

Le processus fonctionne comme suit : chaque microservice expose le/HC de point de terminaison. Ce point de terminaison est créé par la bibliothèque de vérifications intergiciel (middleware) ASP.NET Core. Lorsque ce point de terminaison est appelée, elle s’exécute tous les contrôles d’intégrité qui sont configurés dans la méthode AddHealthChecks dans la classe de démarrage.

La méthode UseHealthChecks attend un port ou un chemin d’accès. Ce port ou le chemin d’accès est le point de terminaison à utiliser pour vérifier l’état d’intégrité du service. Par exemple, le catalogue microservice utilise la/HC de chemin d’accès.

### <a name="caching-health-check-responses"></a>La mise en cache des réponses de vérification d’intégrité

Étant donné que vous ne souhaitez pas provoquer un déni de Service (DoS) dans vos services, ou simplement, vous ne souhaitez pas affecter les performances de service en vérifiant les ressources trop fréquemment, vous pouvez mettre en cache les retours et configurer une durée de cache pour chaque contrôle d’intégrité.

Par défaut, la durée du cache est définie en interne sur 5 minutes, mais vous pouvez modifier cette durée du cache sur chaque contrôle d’intégrité, comme dans le code suivant :

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Interrogation de votre microservices au rapport sur leur état d’intégrité

Lorsque vous avez configuré des vérifications d’intégrité comme décrit ici, une fois que le microservice est en cours d’exécution dans Docker, vous pouvez vérifier directement à partir d’un navigateur si elle est sain. (Ceci ne nécessite que vous publiez le port du conteneur de l’hôte Docker, donc vous pouvez accéder au conteneur via localhost ou via l’IP externe de l’hôte Docker.) Figure 10-7 illustre une demande dans un navigateur et la réponse correspondante.

![](./media/image7.png)

**Figure 10-7**. Vérification de l’état d’intégrité d’un service unique à partir d’un navigateur

Dans ce test, vous pouvez voir que la microservice catalog.api (en cours d’exécution sur le port 5101) est intègre, retourne l’état HTTP 200 et les informations d’état dans JSON. Cela signifie également qu’en interne le service également vérifié l’intégrité de ses dépendances de la base de données SQL Server et que contrôle d’intégrité a été signalé comme étant sain.

## <a name="using-watchdogs"></a>À l’aide d’agents de surveillance

Une surveillance est un service séparé qui peut surveiller l’intégrité et la charge entre les services et l’intégrité des rapports sur le microservices en interrogeant avec la bibliothèque de vérifications présentée précédemment. Cela peut aider à éviter les erreurs qui ne sont pas détectées en fonction de l’affichage d’un service unique. Agents de surveillance sont également judicieux de code de l’hôte que peut effectuer des actions de correction pour les conditions connues sans intervention de l’utilisateur.

L’exemple eShopOnContainers contient une page web qui affiche des exemples de rapports vérification d’intégrité, comme illustré dans la Figure 10-8. Il s’agit de la surveillance de la plus simple que vous pourriez avoir, il n’étant affiche l’état des applications web et de microservices dans eShopOnContainers. Une surveillance aussi prend généralement actions lorsqu’il détecte des États de fonctionnement anormal.

![](./media/image8.png)

**Figure 10-8**. Exemple de rapport vérification d’intégrité dans eShopOnContainers

En résumé, l’intergiciel (middleware) ASP.NET de la bibliothèque ASP.NET Core vérifications fournit un point de terminaison de contrôle d’intégrité unique pour chaque microservice. Cela exécute toutes les vérifications d’intégrité définies et retourner un état d’intégrité général en fonction de toutes ces vérifications.

La bibliothèque de vérifications est extensible via les nouveaux contrôles d’intégrité des ressources externes futures. Par exemple, nous espérons qu’à l’avenir la bibliothèque aura des contrôles d’intégrité pour le cache Redis et d’autres bases de données. Permet à la bibliothèque d’intégrité de la création de rapports à plusieurs dépendances de service ou d’application, et vous pouvez alors prendre des actions en fonction de ces contrôles d’intégrité.

## <a name="health-checks-when-using-orchestrators"></a>Contrôles d’intégrité lors de l’utilisation d’orchestrators

Pour surveiller la disponibilité de votre microservices, orchestrators, Docker Swarm, Kubernetes et Service Fabric effectuer régulièrement des contrôles d’intégrité en envoyant des requêtes pour tester le microservices. Quand un orchestrator détermine que/un conteneur de service est défectueux, qu'il arrête d’acheminer les demandes vers cette instance. Il crée également une nouvelle instance de ce conteneur.

Par exemple, orchestrators la plupart des peuvent utiliser des contrôles d’intégrité pour gérer les déploiements sans interruption de service. Uniquement lorsque l’état d’un service/conteneur rétabli sera orchestrateur de démarrer le routage du trafic vers les instances de service/conteneur.

Contrôle d’intégrité est particulièrement important lorsqu’un orchestrator effectue une mise à niveau de l’application. Certains orchestrators (par exemple, Azure Service Fabric) mettre à jour les services de phases, par exemple, ils peuvent mettre à jour un cinquième de la surface de cluster pour chaque mise à niveau de l’application. L’ensemble de nœuds est mis à niveau en même temps est appelé un *mise à niveau de domaine*. Après que chaque domaine de mise à niveau a été mis à niveau et est disponible pour les utilisateurs, ce domaine de mise à niveau doit passer les vérifications d’intégrité avant le déploiement se déplace vers le domaine de mise à niveau suivant.

Un autre aspect de l’intégrité du service signale les métriques à partir du service. Il s’agit d’une fonction avancée du modèle de contrôle d’intégrité de certaines orchestrators, comme Service Fabric. Métriques sont importantes lorsque vous utilisez un orchestrator car elles sont utilisées pour équilibrer l’utilisation des ressources. Métriques peuvent également être un indicateur de l’intégrité du système. Par exemple, vous pouvez avoir une application qui possède de nombreuses microservices, et chaque instance signale une métrique de demandes par seconde (RPS). Si un service utilise davantage de ressources (mémoire, processeur, etc.) qu’un autre service, l’orchestrateur peut déplacer des instances de service dans le cluster pour tenter de mettre à jour même l’utilisation des ressources.

Notez que si vous utilisez Azure Service Fabric, il fournit son propre [modèle de contrôle d’intégrité](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), qui est plus performant que les vérifications d’intégrité simple.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Surveillance avancée : visualisation et l’analyse, alertes

La dernière partie de l’analyse est visualiser le flux d’événements, création de rapports sur les performances du service et d’alerte lorsqu’un problème est détecté. Vous pouvez utiliser différentes solutions pour cet aspect de l’analyse.

Vous pouvez utiliser des applications personnalisées simples montrant l’état de vos services, telles que la page personnalisée, nous vous avons montré lorsque nous avons expliqué [ASP.NET Core vérifications](https://github.com/aspnet/HealthChecks). Ou vous pouvez utiliser des outils plus avancés tels que Azure Application Insights et Operations Management Suite pour déclencher des alertes en fonction du flux d’événements.

Enfin, si tous les flux d’événements ont été stockées, vous pouvez utiliser Microsoft Power BI ou une solution tierce comme Kibana ou Splunk pour visualiser les données.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **ASP.NET Core vérifications** (libération anticipée) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Introduction à la surveillance de l’infrastructure de Service d’intégrité**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Application Azure Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[Précédente] (mettre en œuvre-circuit-analyseur lexical-pattern.md) [suivant] (.. /Secure-NET-microservices-Web-applications/index.MD)
