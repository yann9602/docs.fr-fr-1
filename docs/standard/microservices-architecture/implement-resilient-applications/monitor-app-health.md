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
# <a name="health-monitoring"></a><span data-ttu-id="9e89e-104">Contrôle d’intégrité</span><span class="sxs-lookup"><span data-stu-id="9e89e-104">Health monitoring</span></span>

<span data-ttu-id="9e89e-105">Contrôle d’intégrité permettent la proximité en temps réel des informations sur l’état de vos conteneurs microservices.</span><span class="sxs-lookup"><span data-stu-id="9e89e-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="9e89e-106">Contrôle d’intégrité est essentiel à plusieurs aspects de fonctionnement microservices et est particulièrement important lorsque orchestrators effectuer des mises à niveau de l’application partielle en plusieurs phases, comme expliqué ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9e89e-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="9e89e-107">Applications basées sur des Microservices utilisent souvent des pulsations ou les contrôles d’intégrité pour activer leur analyseurs de performances planificateurs et orchestrators suivre la multitude de services.</span><span class="sxs-lookup"><span data-stu-id="9e89e-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="9e89e-108">Si les services ne peut pas envoyer une sorte de signal « Je suis », à la demande ou selon une planification, votre application peut sont confrontés à des risques lorsque vous déployez des mises à jour, ou peut simplement détecter les défaillances trop tard et ne pas pouvoir arrêter les pannes en cascade peuvent finir à des pannes majeures.</span><span class="sxs-lookup"><span data-stu-id="9e89e-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="9e89e-109">Dans le modèle par défaut, les services envoient des rapports sur leur état, et ces informations sont agrégées afin de fournir une vue d’ensemble de l’état d’intégrité de votre application.</span><span class="sxs-lookup"><span data-stu-id="9e89e-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="9e89e-110">Si vous utilisez un orchestrator, vous pouvez fournir des informations d’intégrité dans le cluster de votre orchestrator, afin que le cluster peut agir en conséquence.</span><span class="sxs-lookup"><span data-stu-id="9e89e-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="9e89e-111">Si vous investissez dans le rapport d’intégrité de haute qualité personnalisé pour votre application, vous pouvez détecter et résoudre les problèmes de votre application en cours d’exécution beaucoup plus facilement.</span><span class="sxs-lookup"><span data-stu-id="9e89e-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="9e89e-112">Implémentation du contrôle d’intégrité vérifie dans les services ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9e89e-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="9e89e-113">Lorsque vous développez une application de microservice ou web ASP.NET Core, vous pouvez utiliser une bibliothèque nommée vérifications de l’équipe de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e89e-113">When developing an ASP.NET Core microservice or web application, you can use a library named HealthChecks from the ASP.NET team.</span></span> <span data-ttu-id="9e89e-114">(À compter de mai 2017, des premières versions sont disponible sur GitHub).</span><span class="sxs-lookup"><span data-stu-id="9e89e-114">(As of May 2017, an early release is available on GitHub).</span></span>

<span data-ttu-id="9e89e-115">Cette bibliothèque est facile à utiliser et fournit des fonctionnalités qui permettent de que vous validez que n’importe quelle ressource externe spécifique nécessaire pour votre application (par exemple, une base de données SQL Server ou une API distante) fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="9e89e-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="9e89e-116">Lorsque vous utilisez cette bibliothèque, vous pouvez également décider de ce que cela signifie que la ressource est intègre, nous expliquerons ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="9e89e-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="9e89e-117">Pour pouvoir utiliser cette bibliothèque, vous devez tout d’abord utiliser la bibliothèque dans votre microservices.</span><span class="sxs-lookup"><span data-stu-id="9e89e-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="9e89e-118">En second lieu, vous avez besoin d’une application frontale qui interroge pour les rapports d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="9e89e-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="9e89e-119">Application frontale peut être une application de création de rapports personnalisée, ou elle peut être un orchestrator lui-même, de réagir en conséquence pour les États d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="9e89e-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="9e89e-120">À l’aide de la bibliothèque de vérifications dans votre système principal ASP.NET microservices</span><span class="sxs-lookup"><span data-stu-id="9e89e-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="9e89e-121">Vous pouvez voir comment la bibliothèque de vérifications est utilisée dans l’exemple d’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9e89e-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="9e89e-122">Pour commencer, vous devez définir ce qui constitue un état sain pour chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="9e89e-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="9e89e-123">Dans l’exemple d’application, les microservices sont sains si l’API microservice est accessible via HTTP et si sa base de données SQL Server associée est également disponible.</span><span class="sxs-lookup"><span data-stu-id="9e89e-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="9e89e-124">À l’avenir, vous serez en mesure d’installer la bibliothèque de vérifications sous forme de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="9e89e-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="9e89e-125">Mais à ce jour, vous devez télécharger et compiler le code dans le cadre de votre solution.</span><span class="sxs-lookup"><span data-stu-id="9e89e-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="9e89e-126">Clonage du code disponible à l’adresse https://github.com/aspnet/HealthChecks et copiez les dossiers suivants à votre solution.</span><span class="sxs-lookup"><span data-stu-id="9e89e-126">Clone the code available at https://github.com/aspnet/HealthChecks and copy the following folders to your solution.</span></span>

  - <span data-ttu-id="9e89e-127">src/commun</span><span class="sxs-lookup"><span data-stu-id="9e89e-127">src/common</span></span>
  - <span data-ttu-id="9e89e-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="9e89e-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="9e89e-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="9e89e-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="9e89e-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="9e89e-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="9e89e-131">Vous pouvez également utiliser des vérifications supplémentaires telles que celles pour Azure (Microsoft.Extensions.HealthChecks.AzureStorage), mais étant donné que cette version d’eShopOnContainers ne dispose pas d’une dépendance sur Azure, vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="9e89e-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="9e89e-132">Vous n’avez pas besoin des contrôles ASP.NET, eShopOnContainers étant basé sur ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e89e-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="9e89e-133">Figure 10-6 montre la bibliothèque de vérifications dans Visual Studio, prêt à être utilisé comme un bloc de construction par n’importe quel microservices.</span><span class="sxs-lookup"><span data-stu-id="9e89e-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="9e89e-134">**Figure 10-6**.</span><span class="sxs-lookup"><span data-stu-id="9e89e-134">**Figure 10-6**.</span></span> <span data-ttu-id="9e89e-135">Code source d’ASP.NET Core vérifications bibliothèque dans une solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9e89e-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="9e89e-136">Introduit précédemment, la première chose à faire dans chaque projet microservice consiste à ajouter une référence pour les trois bibliothèques de vérifications.</span><span class="sxs-lookup"><span data-stu-id="9e89e-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="9e89e-137">Après cela, vous ajoutez les actions de contrôle d’intégrité que vous souhaitez exécuter dans ce microservice.</span><span class="sxs-lookup"><span data-stu-id="9e89e-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="9e89e-138">Ces actions sont essentiellement des dépendances sur d’autres microservices (HttpUrlCheck) ou les bases de données (actuellement SqlCheck\* pour les bases de données SQL Server).</span><span class="sxs-lookup"><span data-stu-id="9e89e-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="9e89e-139">Vous ajoutez l’action au sein de la classe de démarrage de chaque microservice d’ASP.NET ou une application web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e89e-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="9e89e-140">Chaque service ou une application web doit être configurée en ajoutant toutes ses dépendances HTTP ou de la base de données comme une méthode AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="9e89e-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="9e89e-141">Par exemple, l’application web MVC eShopOnContainers dépend de nombreux services, par conséquent possède plusieurs méthodes de AddCheck ajoutés pour les vérifications d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="9e89e-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="9e89e-142">Par exemple, dans le code suivant, vous pouvez voir comment le catalogue microservice ajoute une dépendance sur sa base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9e89e-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="9e89e-143">Toutefois, l’application web MVC d’eShopOnContainers a plusieurs dépendances sur le reste de la microservices.</span><span class="sxs-lookup"><span data-stu-id="9e89e-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="9e89e-144">Par conséquent, il appelle une méthode AddUrlCheck pour chaque microservice, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9e89e-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="9e89e-145">Par conséquent, un microservice ne fournira pas l’état « sain » jusqu'à ce que tous ses contrôles sont intègres également.</span><span class="sxs-lookup"><span data-stu-id="9e89e-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="9e89e-146">Si le microservice ne dispose pas d’une dépendance sur un service ou sur SQL Server, vous devez simplement ajouter une vérification Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="9e89e-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="9e89e-147">Le code suivant provient de la microservice basket.api eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9e89e-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="9e89e-148">(Le microservice du panier d’achat utilise le cache Redis, mais la bibliothèque ne comporte pas encore d’un fournisseur de contrôle d’intégrité Redis).</span><span class="sxs-lookup"><span data-stu-id="9e89e-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="9e89e-149">Pour une application web ou de service exposer le point de terminaison de contrôle d’intégrité, il doit activer la UseHealthChecks (\[*url\_pour\_intégrité\_vérifie*\]) extension méthode.</span><span class="sxs-lookup"><span data-stu-id="9e89e-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="9e89e-150">Cette méthode est envoyé à la WebHostBuilder au niveau de la méthode principale de la classe de programme de votre application web ou service ASP.NET Core, juste après UseKestrel comme indiqué dans le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9e89e-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="9e89e-151">Le processus fonctionne comme suit : chaque microservice expose le/HC de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9e89e-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="9e89e-152">Ce point de terminaison est créé par la bibliothèque de vérifications intergiciel (middleware) ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e89e-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="9e89e-153">Lorsque ce point de terminaison est appelée, elle s’exécute tous les contrôles d’intégrité qui sont configurés dans la méthode AddHealthChecks dans la classe de démarrage.</span><span class="sxs-lookup"><span data-stu-id="9e89e-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="9e89e-154">La méthode UseHealthChecks attend un port ou un chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9e89e-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="9e89e-155">Ce port ou le chemin d’accès est le point de terminaison à utiliser pour vérifier l’état d’intégrité du service.</span><span class="sxs-lookup"><span data-stu-id="9e89e-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="9e89e-156">Par exemple, le catalogue microservice utilise la/HC de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9e89e-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="9e89e-157">La mise en cache des réponses de vérification d’intégrité</span><span class="sxs-lookup"><span data-stu-id="9e89e-157">Caching health check responses</span></span>

<span data-ttu-id="9e89e-158">Étant donné que vous ne souhaitez pas provoquer un déni de Service (DoS) dans vos services, ou simplement, vous ne souhaitez pas affecter les performances de service en vérifiant les ressources trop fréquemment, vous pouvez mettre en cache les retours et configurer une durée de cache pour chaque contrôle d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="9e89e-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="9e89e-159">Par défaut, la durée du cache est définie en interne sur 5 minutes, mais vous pouvez modifier cette durée du cache sur chaque contrôle d’intégrité, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="9e89e-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="9e89e-160">Interrogation de votre microservices au rapport sur leur état d’intégrité</span><span class="sxs-lookup"><span data-stu-id="9e89e-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="9e89e-161">Lorsque vous avez configuré des vérifications d’intégrité comme décrit ici, une fois que le microservice est en cours d’exécution dans Docker, vous pouvez vérifier directement à partir d’un navigateur si elle est sain.</span><span class="sxs-lookup"><span data-stu-id="9e89e-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="9e89e-162">(Ceci ne nécessite que vous publiez le port du conteneur de l’hôte Docker, donc vous pouvez accéder au conteneur via localhost ou via l’IP externe de l’hôte Docker.) Figure 10-7 illustre une demande dans un navigateur et la réponse correspondante.</span><span class="sxs-lookup"><span data-stu-id="9e89e-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="9e89e-163">**Figure 10-7**.</span><span class="sxs-lookup"><span data-stu-id="9e89e-163">**Figure 10-7**.</span></span> <span data-ttu-id="9e89e-164">Vérification de l’état d’intégrité d’un service unique à partir d’un navigateur</span><span class="sxs-lookup"><span data-stu-id="9e89e-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="9e89e-165">Dans ce test, vous pouvez voir que la microservice catalog.api (en cours d’exécution sur le port 5101) est intègre, retourne l’état HTTP 200 et les informations d’état dans JSON.</span><span class="sxs-lookup"><span data-stu-id="9e89e-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="9e89e-166">Cela signifie également qu’en interne le service également vérifié l’intégrité de ses dépendances de la base de données SQL Server et que contrôle d’intégrité a été signalé comme étant sain.</span><span class="sxs-lookup"><span data-stu-id="9e89e-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="9e89e-167">À l’aide d’agents de surveillance</span><span class="sxs-lookup"><span data-stu-id="9e89e-167">Using watchdogs</span></span>

<span data-ttu-id="9e89e-168">Une surveillance est un service séparé qui peut surveiller l’intégrité et la charge entre les services et l’intégrité des rapports sur le microservices en interrogeant avec la bibliothèque de vérifications présentée précédemment.</span><span class="sxs-lookup"><span data-stu-id="9e89e-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="9e89e-169">Cela peut aider à éviter les erreurs qui ne sont pas détectées en fonction de l’affichage d’un service unique.</span><span class="sxs-lookup"><span data-stu-id="9e89e-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="9e89e-170">Agents de surveillance sont également judicieux de code de l’hôte que peut effectuer des actions de correction pour les conditions connues sans intervention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9e89e-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="9e89e-171">L’exemple eShopOnContainers contient une page web qui affiche des exemples de rapports vérification d’intégrité, comme illustré dans la Figure 10-8.</span><span class="sxs-lookup"><span data-stu-id="9e89e-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="9e89e-172">Il s’agit de la surveillance de la plus simple que vous pourriez avoir, il n’étant affiche l’état des applications web et de microservices dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9e89e-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="9e89e-173">Une surveillance aussi prend généralement actions lorsqu’il détecte des États de fonctionnement anormal.</span><span class="sxs-lookup"><span data-stu-id="9e89e-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="9e89e-174">**Figure 10-8**.</span><span class="sxs-lookup"><span data-stu-id="9e89e-174">**Figure 10-8**.</span></span> <span data-ttu-id="9e89e-175">Exemple de rapport vérification d’intégrité dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="9e89e-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="9e89e-176">En résumé, l’intergiciel (middleware) ASP.NET de la bibliothèque ASP.NET Core vérifications fournit un point de terminaison de contrôle d’intégrité unique pour chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="9e89e-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="9e89e-177">Cela exécute toutes les vérifications d’intégrité définies et retourner un état d’intégrité général en fonction de toutes ces vérifications.</span><span class="sxs-lookup"><span data-stu-id="9e89e-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="9e89e-178">La bibliothèque de vérifications est extensible via les nouveaux contrôles d’intégrité des ressources externes futures.</span><span class="sxs-lookup"><span data-stu-id="9e89e-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="9e89e-179">Par exemple, nous espérons qu’à l’avenir la bibliothèque aura des contrôles d’intégrité pour le cache Redis et d’autres bases de données.</span><span class="sxs-lookup"><span data-stu-id="9e89e-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="9e89e-180">Permet à la bibliothèque d’intégrité de la création de rapports à plusieurs dépendances de service ou d’application, et vous pouvez alors prendre des actions en fonction de ces contrôles d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="9e89e-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="9e89e-181">Contrôles d’intégrité lors de l’utilisation d’orchestrators</span><span class="sxs-lookup"><span data-stu-id="9e89e-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="9e89e-182">Pour surveiller la disponibilité de votre microservices, orchestrators, Docker Swarm, Kubernetes et Service Fabric effectuer régulièrement des contrôles d’intégrité en envoyant des requêtes pour tester le microservices.</span><span class="sxs-lookup"><span data-stu-id="9e89e-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="9e89e-183">Quand un orchestrator détermine que/un conteneur de service est défectueux, qu'il arrête d’acheminer les demandes vers cette instance.</span><span class="sxs-lookup"><span data-stu-id="9e89e-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="9e89e-184">Il crée également une nouvelle instance de ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="9e89e-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="9e89e-185">Par exemple, orchestrators la plupart des peuvent utiliser des contrôles d’intégrité pour gérer les déploiements sans interruption de service.</span><span class="sxs-lookup"><span data-stu-id="9e89e-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="9e89e-186">Uniquement lorsque l’état d’un service/conteneur rétabli sera orchestrateur de démarrer le routage du trafic vers les instances de service/conteneur.</span><span class="sxs-lookup"><span data-stu-id="9e89e-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="9e89e-187">Contrôle d’intégrité est particulièrement important lorsqu’un orchestrator effectue une mise à niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="9e89e-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="9e89e-188">Certains orchestrators (par exemple, Azure Service Fabric) mettre à jour les services de phases, par exemple, ils peuvent mettre à jour un cinquième de la surface de cluster pour chaque mise à niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="9e89e-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="9e89e-189">L’ensemble de nœuds est mis à niveau en même temps est appelé un *mise à niveau de domaine*.</span><span class="sxs-lookup"><span data-stu-id="9e89e-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="9e89e-190">Après que chaque domaine de mise à niveau a été mis à niveau et est disponible pour les utilisateurs, ce domaine de mise à niveau doit passer les vérifications d’intégrité avant le déploiement se déplace vers le domaine de mise à niveau suivant.</span><span class="sxs-lookup"><span data-stu-id="9e89e-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="9e89e-191">Un autre aspect de l’intégrité du service signale les métriques à partir du service.</span><span class="sxs-lookup"><span data-stu-id="9e89e-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="9e89e-192">Il s’agit d’une fonction avancée du modèle de contrôle d’intégrité de certaines orchestrators, comme Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="9e89e-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="9e89e-193">Métriques sont importantes lorsque vous utilisez un orchestrator car elles sont utilisées pour équilibrer l’utilisation des ressources.</span><span class="sxs-lookup"><span data-stu-id="9e89e-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="9e89e-194">Métriques peuvent également être un indicateur de l’intégrité du système.</span><span class="sxs-lookup"><span data-stu-id="9e89e-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="9e89e-195">Par exemple, vous pouvez avoir une application qui possède de nombreuses microservices, et chaque instance signale une métrique de demandes par seconde (RPS).</span><span class="sxs-lookup"><span data-stu-id="9e89e-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="9e89e-196">Si un service utilise davantage de ressources (mémoire, processeur, etc.) qu’un autre service, l’orchestrateur peut déplacer des instances de service dans le cluster pour tenter de mettre à jour même l’utilisation des ressources.</span><span class="sxs-lookup"><span data-stu-id="9e89e-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="9e89e-197">Notez que si vous utilisez Azure Service Fabric, il fournit son propre [modèle de contrôle d’intégrité](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), qui est plus performant que les vérifications d’intégrité simple.</span><span class="sxs-lookup"><span data-stu-id="9e89e-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="9e89e-198">Surveillance avancée : visualisation et l’analyse, alertes</span><span class="sxs-lookup"><span data-stu-id="9e89e-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="9e89e-199">La dernière partie de l’analyse est visualiser le flux d’événements, création de rapports sur les performances du service et d’alerte lorsqu’un problème est détecté.</span><span class="sxs-lookup"><span data-stu-id="9e89e-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="9e89e-200">Vous pouvez utiliser différentes solutions pour cet aspect de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="9e89e-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="9e89e-201">Vous pouvez utiliser des applications personnalisées simples montrant l’état de vos services, telles que la page personnalisée, nous vous avons montré lorsque nous avons expliqué [ASP.NET Core vérifications](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="9e89e-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="9e89e-202">Ou vous pouvez utiliser des outils plus avancés tels que Azure Application Insights et Operations Management Suite pour déclencher des alertes en fonction du flux d’événements.</span><span class="sxs-lookup"><span data-stu-id="9e89e-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="9e89e-203">Enfin, si tous les flux d’événements ont été stockées, vous pouvez utiliser Microsoft Power BI ou une solution tierce comme Kibana ou Splunk pour visualiser les données.</span><span class="sxs-lookup"><span data-stu-id="9e89e-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9e89e-204">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9e89e-204">Additional resources</span></span>

-   <span data-ttu-id="9e89e-205">**ASP.NET Core vérifications** (libération anticipée) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="9e89e-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="9e89e-206">**Introduction à la surveillance de l’infrastructure de Service d’intégrité**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="9e89e-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="9e89e-207">**Application Azure Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="9e89e-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="9e89e-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="9e89e-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="9e89e-209">[Précédente] (mettre en œuvre-circuit-analyseur lexical-pattern.md) [suivant] (.. /Secure-NET-microservices-Web-applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="9e89e-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>
