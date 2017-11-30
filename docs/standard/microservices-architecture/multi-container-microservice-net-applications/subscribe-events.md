---
title: "S’abonner aux événements"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | S’abonner aux événements"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: fe17b53a39ff2964cd60183e291e2936d3ba28df
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="subscribing-to-events"></a><span data-ttu-id="94ee7-104">S’abonner aux événements</span><span class="sxs-lookup"><span data-stu-id="94ee7-104">Subscribing to events</span></span>

<span data-ttu-id="94ee7-105">Pour le bus d’événements à l’aide de la première étape consiste à s’abonner le microservices aux événements qu’ils veulent recevoir.</span><span class="sxs-lookup"><span data-stu-id="94ee7-105">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="94ee7-106">Qui doit être effectuée dans le récepteur microservices.</span><span class="sxs-lookup"><span data-stu-id="94ee7-106">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="94ee7-107">L’exemple de code suivant montre ce que chaque microservice récepteur doit implémenter au démarrage du service (autrement dit, lors du démarrage de classe) afin qu’il s’abonne aux événements qu’il a besoin.</span><span class="sxs-lookup"><span data-stu-id="94ee7-107">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the Startup class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="94ee7-108">Par exemple, le microservice basket.api doit s’abonner aux messages de ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="94ee7-108">For instance, the basket.api microservice needs to subscribe to ProductPriceChangedIntegrationEvent messages.</span></span> <span data-ttu-id="94ee7-109">Cela rend la microservice prenant en charge de toutes les modifications pour le prix du produit et que vous lui permet d’avertir l’utilisateur sur la modification si ce produit est dans le panier de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94ee7-109">This makes the microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

<span data-ttu-id="94ee7-110">Une fois ce code s’exécute, l’abonné microservice est à l’écoute via les canaux RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="94ee7-110">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="94ee7-111">Quand un message de type ProductPriceChangedIntegrationEvent arrive, le code appelle le Gestionnaire d’événements qui est passé et qu’elle traite l’événement.</span><span class="sxs-lookup"><span data-stu-id="94ee7-111">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="94ee7-112">Publier des événements via le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="94ee7-112">Publishing events through the event bus</span></span>

<span data-ttu-id="94ee7-113">Enfin, l’expéditeur du message (origine microservice) publie les événements de l’intégration avec un code similaire à l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="94ee7-113">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="94ee7-114">(Il s’agit d’un exemple simplifié qui n’accepte pas l’atomicité en compte.) Vous implémente un code similaire chaque fois qu’un événement doit être propagé sur plusieurs microservices, généralement juste après la validation de données ou transactions à partir de l’origine de microservice.</span><span class="sxs-lookup"><span data-stu-id="94ee7-114">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="94ee7-115">Tout d’abord, l’objet d’implémentation du bus événement (en fonction de RabbitMQ ou sur un bus de service) serait injecté dans le constructeur du contrôleur, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="94ee7-115">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

<span data-ttu-id="94ee7-116">Puis vous utilisez les méthodes de votre contrôleur, comme dans la méthode UpdateProduct :</span><span class="sxs-lookup"><span data-stu-id="94ee7-116">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

```csharp
[Route("update")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

<span data-ttu-id="94ee7-117">Dans ce cas, l’origine microservice étant un microservice CRUD simple, ce code est placé à droite dans le contrôleur d’API Web.</span><span class="sxs-lookup"><span data-stu-id="94ee7-117">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> <span data-ttu-id="94ee7-118">Dans microservices plus avancées, il pourrait être implémenté dans la classe CommandHandler, droite après que les données d’origine seront validées.</span><span class="sxs-lookup"><span data-stu-id="94ee7-118">In more advanced microservices, it could be implemented in the CommandHandler class, right after the original data is committed.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="94ee7-119">Conception d’atomicité et la résilience lors de la publication pour le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="94ee7-119">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="94ee7-120">Lorsque vous publiez des événements d’intégration via une distribution de messages système telles que le bus d’événements, vous rencontrez le problème de mise à jour de la base de données d’origine atomique et de publication d’un événement.</span><span class="sxs-lookup"><span data-stu-id="94ee7-120">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="94ee7-121">Par exemple, dans l’exemple simplifié indiqué précédemment, le code valide les données la base de données lorsque le prix du produit est modifié et qu’il publie ensuite un message ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="94ee7-121">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="94ee7-122">Au départ, il peut se présenter essentiel que ces deux opérations atomiquement.</span><span class="sxs-lookup"><span data-stu-id="94ee7-122">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="94ee7-123">Toutefois, si vous utilisez une transaction distribuée implique la base de données et le message broker, comme vous le feriez dans les anciens systèmes comme [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), cela n’est pas recommandée pour les raisons décrites par la [Théorème de CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="94ee7-123">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="94ee7-124">En fait, vous utilisez microservices pour créer des systèmes évolutifs et hautement disponibles.</span><span class="sxs-lookup"><span data-stu-id="94ee7-124">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="94ee7-125">Ce qui simplifie quelque peu, le théorème CAP indique que vous ne pouvez pas créer une base de données (ou un microservice qui possède son modèle) qui est disponible en permanence, fortement cohérent, *et* à tolérance de panne à n’importe quelle partition.</span><span class="sxs-lookup"><span data-stu-id="94ee7-125">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="94ee7-126">Vous devez choisir deux de ces trois propriétés.</span><span class="sxs-lookup"><span data-stu-id="94ee7-126">You must choose two of these three properties.</span></span>

<span data-ttu-id="94ee7-127">Dans les architectures de microservices, vous devez choisir la disponibilité et la tolérance de panne et vous devez prisés cohérence forte.</span><span class="sxs-lookup"><span data-stu-id="94ee7-127">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="94ee7-128">Par conséquent, dans les applications microservice les plus récents, vous généralement ne souhaitez pas utiliser les transactions distribuées dans la messagerie, comme vous le feriez lorsque vous implémentez [des transactions distribuées](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) en fonction de la Transaction distribuée Windows Coordinator (DTC) avec [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="94ee7-128">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="94ee7-129">Revenons à l’émission initiale et exemple.</span><span class="sxs-lookup"><span data-stu-id="94ee7-129">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="94ee7-130">Si le service tombe en panne après la mise à jour de la base de données (dans ce cas, avec le bouton droit une fois la ligne de code avec \_contexte. SaveChangesAsync()), mais avant l’événement de l’intégration est publié, l’ensemble du système risquent de devenir incohérent.</span><span class="sxs-lookup"><span data-stu-id="94ee7-130">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="94ee7-131">Cela peut être critiques, en fonction de l’opération métier spécifique que vous traitez.</span><span class="sxs-lookup"><span data-stu-id="94ee7-131">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="94ee7-132">Comme mentionné précédemment dans la section architecture, vous pouvez avoir plusieurs approches pour traiter ce problème :</span><span class="sxs-lookup"><span data-stu-id="94ee7-132">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="94ee7-133">À l’aide de la version complète [modèle d’approvisionnement de l’événement](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="94ee7-133">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="94ee7-134">À l’aide de [d’exploration de données du journal des transactions](http://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="94ee7-134">Using [transaction log mining](http://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="94ee7-135">À l’aide de la [modèle de boîte d’envoi](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="94ee7-135">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="94ee7-136">Il s’agit d’une table transactionnelle pour stocker les événements d’intégration (extension de la transaction locale).</span><span class="sxs-lookup"><span data-stu-id="94ee7-136">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="94ee7-137">Pour ce scénario, l’utilisation du modèle d’événement approvisionnement (ES) complet est une des meilleures approches, dans le cas contraire *le* meilleures.</span><span class="sxs-lookup"><span data-stu-id="94ee7-137">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="94ee7-138">Toutefois, dans de nombreux scénarios d’application, vous peut-être pas en mesure d’implémenter un système ES complet.</span><span class="sxs-lookup"><span data-stu-id="94ee7-138">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="94ee7-139">ES signifie stocker uniquement les événements de domaine dans votre base de données transactionnelle, au lieu de stocker les données d’état en cours.</span><span class="sxs-lookup"><span data-stu-id="94ee7-139">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="94ee7-140">Stocker uniquement les événements de domaine peut avoir de nombreux avantages, tels que l’historique de votre système et en mesure de déterminer l’état de votre système à tout moment dans le passé.</span><span class="sxs-lookup"><span data-stu-id="94ee7-140">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="94ee7-141">Toutefois, l’implémentation d’un système ES complète, vous devez remanier la majeure partie de votre système et introduit de nombreuses autres complexités et la configuration requise.</span><span class="sxs-lookup"><span data-stu-id="94ee7-141">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="94ee7-142">Par exemple, vous pouvez utiliser une base de données apportée spécifiquement pour l’alimentation de l’événement, tel que [magasin d’événements](https://geteventstore.com/), ou une base de données telles que la base de données Azure Cosmos, MongoDB, Cassandra, CouchDB ou RavenDB orienté document.</span><span class="sxs-lookup"><span data-stu-id="94ee7-142">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="94ee7-143">ES est une meilleure approche pour ce problème, mais pas la solution la plus simple, sauf si vous êtes déjà familiarisé avec la source d’événement.</span><span class="sxs-lookup"><span data-stu-id="94ee7-143">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="94ee7-144">La possibilité d’utiliser le journal des transactions d’exploration de données initialement semble très transparente.</span><span class="sxs-lookup"><span data-stu-id="94ee7-144">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="94ee7-145">Toutefois, pour utiliser cette approche, la microservice doit être associé à votre journal des transactions SGBDR, telles que le journal des transactions SQL Server.</span><span class="sxs-lookup"><span data-stu-id="94ee7-145">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="94ee7-146">Cela est probablement pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="94ee7-146">This is probably not desirable.</span></span> <span data-ttu-id="94ee7-147">Un autre inconvénient est que les mises à jour de bas niveau enregistrés dans le journal des transactions ne peuvent pas être le même niveau que les événements d’intégration de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="94ee7-147">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="94ee7-148">Dans ce cas, le processus d’ingénierie à rebours ces opérations du journal des transactions peuvent être difficiles.</span><span class="sxs-lookup"><span data-stu-id="94ee7-148">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="94ee7-149">Une approche d’équilibrage de charge est une combinaison d’une table de base de données transactionnelle et d’un modèle de ES simplifié.</span><span class="sxs-lookup"><span data-stu-id="94ee7-149">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="94ee7-150">Vous pouvez utiliser un état comme « prêt pour la publication de l’événement, » que vous définissez dans l’événement d’origine lorsque vous le validez dans la table d’événements de l’intégration.</span><span class="sxs-lookup"><span data-stu-id="94ee7-150">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="94ee7-151">Vous essayez ensuite de publier l’événement vers le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-151">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="94ee7-152">Si l’action de l’événement de publication réussit, vous démarrez une autre transaction dans le service d’origine et déplacez l’état « prêt pour la publication de l’événement » à « événement déjà publiée ».</span><span class="sxs-lookup"><span data-stu-id="94ee7-152">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="94ee7-153">Si l’action de l’événement de publication de l’événement de bus échoue, les données toujours pas seront incohérentes dans le microservice d’origine, il est toujours marqué comme « prêt à publier l’événement », et en ce qui concerne le reste des services, il ne sera cohérente.</span><span class="sxs-lookup"><span data-stu-id="94ee7-153">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="94ee7-154">Vous pouvez toujours avoir les tâches en arrière-plan vérification de l’état des transactions ou des événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="94ee7-154">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="94ee7-155">Si la tâche détecte un événement dans l’état « prêt pour la publication de l’événement », il peut tenter de publier à nouveau cet événement avec le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-155">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="94ee7-156">Notez qu’avec cette approche, vous rendez persistantes uniquement les événements d’intégration pour chaque microservice d’origine et uniquement les événements que vous souhaitez communiquer à d’autres microservices ou les systèmes externes.</span><span class="sxs-lookup"><span data-stu-id="94ee7-156">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="94ee7-157">En revanche, dans un système ES complet, stocker tous les événements de domaine également.</span><span class="sxs-lookup"><span data-stu-id="94ee7-157">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="94ee7-158">Par conséquent, cette approche à charge équilibrée est un système ES simplifié.</span><span class="sxs-lookup"><span data-stu-id="94ee7-158">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="94ee7-159">Vous avez besoin d’une liste des événements d’intégration avec leur état actuel (« prêt à publier » et « publié »).</span><span class="sxs-lookup"><span data-stu-id="94ee7-159">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="94ee7-160">Mais vous devrez implémenter ces États pour les événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="94ee7-160">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="94ee7-161">Et, dans cette approche, il est inutile stocker toutes les données de votre domaine en tant qu’événements dans la base de données transactionnelle, comme vous le feriez dans un système ES complet.</span><span class="sxs-lookup"><span data-stu-id="94ee7-161">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="94ee7-162">Si vous utilisez déjà une base de données relationnelle, vous pouvez utiliser une table transactionnelle pour stocker les événements d’intégration.</span><span class="sxs-lookup"><span data-stu-id="94ee7-162">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="94ee7-163">Pour obtenir l’atomicité de votre application, vous utilisez un processus en deux étapes basé sur des transactions locales.</span><span class="sxs-lookup"><span data-stu-id="94ee7-163">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="94ee7-164">En fait, vous avez une table de IntegrationEvent dans la même base de données où vous avez vos entités de domaine.</span><span class="sxs-lookup"><span data-stu-id="94ee7-164">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="94ee7-165">Cette table fonctionne comme une assurance d’obtenir l’atomicité afin que vous incluez persistante des événements d’intégration dans les mêmes transactions en cours de validation les données du domaine.</span><span class="sxs-lookup"><span data-stu-id="94ee7-165">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="94ee7-166">Étape par étape, le processus se déroule comme suit : l’application commence une transaction de base de données locale.</span><span class="sxs-lookup"><span data-stu-id="94ee7-166">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="94ee7-167">Ensuite, il met à jour l’état de vos entités de domaine et insère un événement dans la table d’événements de l’intégration.</span><span class="sxs-lookup"><span data-stu-id="94ee7-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="94ee7-168">Enfin, il valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="94ee7-168">Finally, it commits the transaction.</span></span> <span data-ttu-id="94ee7-169">Vous obtenez l’atomicité de votre choix.</span><span class="sxs-lookup"><span data-stu-id="94ee7-169">You get the desired atomicity.</span></span>

<span data-ttu-id="94ee7-170">Lorsque vous implémentez les étapes de la publication d’événements, vous avez ces possibilités :</span><span class="sxs-lookup"><span data-stu-id="94ee7-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="94ee7-171">Publier l’événement intégration juste après la validation de la transaction et une autre transaction locale permet de marquer les événements dans la table en cours de publication.</span><span class="sxs-lookup"><span data-stu-id="94ee7-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="94ee7-172">Ensuite, utilisez le tableau comme un artefact pour suivre les événements d’intégration en cas de problèmes dans le microservices à distance et effectuer des actions de compensation basées sur les événements d’intégration stockée.</span><span class="sxs-lookup"><span data-stu-id="94ee7-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="94ee7-173">Utilisez le tableau comme un type de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="94ee7-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="94ee7-174">Un thread d’application distinct ou un processus interroge la table d’événements integration, publie les événements pour le bus d’événements, puis utilise une transaction locale pour marquer les événements publié.</span><span class="sxs-lookup"><span data-stu-id="94ee7-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="94ee7-175">Figure 8-22 illustre l’architecture de la première de ces approches.</span><span class="sxs-lookup"><span data-stu-id="94ee7-175">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="94ee7-176">**Figure 8-22**.</span><span class="sxs-lookup"><span data-stu-id="94ee7-176">**Figure 8-22**.</span></span> <span data-ttu-id="94ee7-177">Atomicité lors de la publication d’événements pour le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="94ee7-177">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="94ee7-178">L’approche illustrée dans la Figure 8-22 manque microservice un travail supplémentaire qui est responsable de la vérification et confirmant la réussite des événements d’intégration publiée.</span><span class="sxs-lookup"><span data-stu-id="94ee7-178">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="94ee7-179">En cas de défaillance, ce microservice de travail de l’outil d’analyse supplémentaires permettre lire les événements à partir de la table et les republier.</span><span class="sxs-lookup"><span data-stu-id="94ee7-179">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="94ee7-180">Sur la deuxième approche : vous utilisez la table du journal des événements comme une file d’attente et un microservice de travail pour publier les messages.</span><span class="sxs-lookup"><span data-stu-id="94ee7-180">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="94ee7-181">Dans ce cas, le processus est illustré comme cela dans la Figure 8-23.</span><span class="sxs-lookup"><span data-stu-id="94ee7-181">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="94ee7-182">Cet exemple montre un microservice supplémentaire et la table est la seule source lors de la publication d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-182">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="94ee7-183">**Figure 8-23**.</span><span class="sxs-lookup"><span data-stu-id="94ee7-183">**Figure 8-23**.</span></span> <span data-ttu-id="94ee7-184">Atomicité lors de la publication d’événements pour le bus d’événements avec un microservice de travail</span><span class="sxs-lookup"><span data-stu-id="94ee7-184">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="94ee7-185">Par souci de simplicité, l’exemple eShopOnContainers utilise la première approche (sans processus supplémentaires ou avec l’outil d’analyse microservices) ainsi que le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-185">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="94ee7-186">Toutefois, l’eShopOnContainers ne gère pas tous les cas de défaillance.</span><span class="sxs-lookup"><span data-stu-id="94ee7-186">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="94ee7-187">Dans une application réelle déployée sur le cloud, le fait de problèmes surviendront par la suite, et vous devez implémenter qui vérifier et renvoyez la logique doit adopter.</span><span class="sxs-lookup"><span data-stu-id="94ee7-187">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="94ee7-188">À l’aide de la table comme une file d’attente peut être plus efficace que la première approche si vous avez cette table comme une seule source d’événements lorsque vous les publiez via le bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-188">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="94ee7-189">Implémentation d’atomicité lors de la publication d’événements d’intégration via le bus d’événements</span><span class="sxs-lookup"><span data-stu-id="94ee7-189">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="94ee7-190">Le code suivant montre comment vous pouvez créer une transaction impliquant plusieurs objets DbContext — un contexte liées aux données d’origine est mis à jour et le contexte de deuxième associées à la table IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="94ee7-190">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="94ee7-191">Notez que la transaction dans l’exemple de code ci-dessous ne sera pas résiliente si les connexions à la base de données n’importe quel problème au moment lorsque le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="94ee7-191">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="94ee7-192">Cela peut se produire dans les systèmes cloud comme Azure SQL DB, qui peut déplacer des bases de données entre serveurs.</span><span class="sxs-lookup"><span data-stu-id="94ee7-192">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="94ee7-193">Pour implémenter des transactions résilientes dans plusieurs contextes, consultez le [implémentation de connexions d’Entity Framework Core SQL résilientes](#implementing_resilient_EFCore_SQL_conns) section plus loin dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="94ee7-193">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="94ee7-194">Pour plus de clarté, l’exemple suivant montre l’ensemble du processus dans un seul élément de code.</span><span class="sxs-lookup"><span data-stu-id="94ee7-194">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="94ee7-195">Toutefois, l’implémentation d’eShopOnContainers est réellement refactorisée et fractionner cette logique dans plusieurs classes, par conséquent, il est plus facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="94ee7-195">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult>
    UpdateProduct([FromBody]CatalogItem productToUpdate)
{
    var catalogItem = await _catalogContext.CatalogItems
        .SingleOrDefaultAsync(i => i.Id == productToUpdate.Id);

    if (catalogItem == null) return NotFound();

    bool raiseProductPriceChangedEvent = false;

    IntegrationEvent priceChangedEvent = null;

    if (catalogItem.Price != productToUpdate.Price)
        raiseProductPriceChangedEvent = true;

    if (raiseProductPriceChangedEvent) // Create event if price has changed
    {
        var oldPrice = catalogItem.Price;
        priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
            productToUpdate.Price,
            oldPrice);
    }

    // Update current product
    catalogItem = productToUpdate;
    // Achieving atomicity between original DB and the IntegrationEventLog
    // with a local transaction

    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);

        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if(raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
   }

   // Publish to event bus only if product price changed

   if (raiseProductPriceChangedEvent)
   {
       _eventBus.Publish(priceChangedEvent);
       integrationEventLogService.MarkEventAsPublishedAsync(
           priceChangedEvent);
   }

   return Ok();
}
```

<span data-ttu-id="94ee7-196">Une fois l’événement d’intégration ProductPriceChangedIntegrationEvent est créé, la transaction qui stocke l’opération de domaine d’origine (mise à jour l’élément de catalogue) inclut également la persistance de l’événement dans la table du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-196">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="94ee7-197">Cela rend une transaction unique, et vous serez toujours en mesure de vérifier si les messages d’événement ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="94ee7-197">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="94ee7-198">La table du journal des événements est mis à jour atomiquement avec l’opération de base de données d’origine, à l’aide d’une transaction locale par rapport à la même base de données.</span><span class="sxs-lookup"><span data-stu-id="94ee7-198">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="94ee7-199">Si une des opérations échoue, une exception est levée et la transaction restaure toute opération terminée, ainsi maintenir la cohérence entre les opérations de domaine et les messages d’événement envoyés.</span><span class="sxs-lookup"><span data-stu-id="94ee7-199">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="94ee7-200">Réception de messages à partir d’abonnements : les gestionnaires d’événements dans le récepteur microservices</span><span class="sxs-lookup"><span data-stu-id="94ee7-200">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="94ee7-201">En plus de la logique d’abonnement événement, vous devez implémenter le code interne pour les gestionnaires d’événements integration (comme une méthode de rappel).</span><span class="sxs-lookup"><span data-stu-id="94ee7-201">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="94ee7-202">Le Gestionnaire d’événements est où vous spécifiez où les messages d’un certain type d’événement sont reçus et traités.</span><span class="sxs-lookup"><span data-stu-id="94ee7-202">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="94ee7-203">Un gestionnaire d’événements reçoit d’abord une instance d’événement à partir du bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-203">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="94ee7-204">Il localise ensuite le composant de traitement liés à cet événement d’intégration, multiplication et la conservation de l’événement en tant qu’une modification d’état dans le récepteur de microservice.</span><span class="sxs-lookup"><span data-stu-id="94ee7-204">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="94ee7-205">Par exemple, un événement ProductPriceChanged proviennent du catalogue microservice, est gérée dans le panier d’achat microservice et modifie l’état de cette microservice de panier de récepteur ainsi, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="94ee7-205">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

<span data-ttu-id="94ee7-206">Le Gestionnaire d’événements doit vérifier si le produit existe dans toutes les instances du panier d’achat.</span><span class="sxs-lookup"><span data-stu-id="94ee7-206">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="94ee7-207">Il met également à jour du prix de chaque élément de ligne du panier d’achat associées.</span><span class="sxs-lookup"><span data-stu-id="94ee7-207">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="94ee7-208">Enfin, il crée une alerte à afficher à l’utilisateur sur la modification de prix, comme indiqué dans la Figure 8 à 24.</span><span class="sxs-lookup"><span data-stu-id="94ee7-208">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="94ee7-209">**Figure 8-24**.</span><span class="sxs-lookup"><span data-stu-id="94ee7-209">**Figure 8-24**.</span></span> <span data-ttu-id="94ee7-210">Affichage d’une variation de l’élément dans un panier, communiquée par les événements d’intégration</span><span class="sxs-lookup"><span data-stu-id="94ee7-210">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="94ee7-211">Idempotence dans les événements de message de mise à jour</span><span class="sxs-lookup"><span data-stu-id="94ee7-211">Idempotency in update message events</span></span>

<span data-ttu-id="94ee7-212">Un aspect important d’événements de message de mise à jour est qu’une défaillance dans n’importe quel point dans la communication doit entraîner le message à être réessayée.</span><span class="sxs-lookup"><span data-stu-id="94ee7-212">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="94ee7-213">Sinon, une tâche en arrière-plan peut tenter de publier un événement qui a déjà été publié, création d’une condition de concurrence.</span><span class="sxs-lookup"><span data-stu-id="94ee7-213">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="94ee7-214">Vous devez vous assurer que les mises à jour sont idempotents ou qu’ils fournissent suffisamment d’informations pour vous assurer que vous pouvez détecter un doublon, ignorer et envoyer arrière une seule réponse.</span><span class="sxs-lookup"><span data-stu-id="94ee7-214">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="94ee7-215">Comme indiqué précédemment, idempotence signifie qu’une opération peut être effectuée plusieurs fois sans modifier le résultat.</span><span class="sxs-lookup"><span data-stu-id="94ee7-215">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="94ee7-216">Dans un environnement de messagerie, comme lors de la communication des événements, un événement est idempotente si elle peut être remis plusieurs fois sans modifier le résultat pour le récepteur de microservice.</span><span class="sxs-lookup"><span data-stu-id="94ee7-216">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="94ee7-217">Cela peut être nécessaire en raison de la nature de l’événement lui-même, ou en raison du mode, le système gère l’événement.</span><span class="sxs-lookup"><span data-stu-id="94ee7-217">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="94ee7-218">Message idempotence est importante dans toute application qui utilise la messagerie, pas seulement dans les applications qui implémentent le modèle de bus d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-218">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="94ee7-219">Un exemple d’une opération idempotente est une instruction SQL qui insère des données dans une table uniquement si ces données ne sont pas déjà dans la table.</span><span class="sxs-lookup"><span data-stu-id="94ee7-219">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="94ee7-220">Il n’a pas d’importance combien de fois vous exécutez qu’insérez l’instruction SQL ; le résultat sera le même, la table contiendra ces données.</span><span class="sxs-lookup"><span data-stu-id="94ee7-220">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="94ee7-221">Idempotence, comme cela peut également être nécessaire lorsque vous traitez des messages si les messages pourraient potentiellement être envoyés et par conséquent traité plus d’une fois.</span><span class="sxs-lookup"><span data-stu-id="94ee7-221">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="94ee7-222">Par exemple, si la logique de nouvelle tentative entraîne un émetteur d’envoyer exactement le même message plusieurs fois, vous devez vous assurer qu’il est idempotente.</span><span class="sxs-lookup"><span data-stu-id="94ee7-222">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="94ee7-223">Il est possible de messages idempotent de conception.</span><span class="sxs-lookup"><span data-stu-id="94ee7-223">It is possible to design idempotent messages.</span></span> <span data-ttu-id="94ee7-224">Par exemple, vous pouvez créer un événement indiquant que « le prix du produit la valeur \$25 » au lieu de « ajouter \$5 pour le prix du produit. »</span><span class="sxs-lookup"><span data-stu-id="94ee7-224">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="94ee7-225">Vous pourriez traiter en toute sécurité le premier message n’importe quel nombre de fois et le résultat sera le même.</span><span class="sxs-lookup"><span data-stu-id="94ee7-225">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="94ee7-226">Qui n’est pas vrai pour le second message.</span><span class="sxs-lookup"><span data-stu-id="94ee7-226">That is not true for the second message.</span></span> <span data-ttu-id="94ee7-227">Mais même dans le premier cas, vous pouvez traiter le premier événement, car le système également a pu envoyer un événement de modification de prix plus récente et que vous feriez écraser le nouveau prix.</span><span class="sxs-lookup"><span data-stu-id="94ee7-227">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="94ee7-228">Un autre exemple est un événement de fin de commande été propagé à plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="94ee7-228">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="94ee7-229">Il est important que les informations de commande être mis à jour une seule fois, dans d’autres systèmes même s’il existe des événements de message en double pour le même événement de commande terminée.</span><span class="sxs-lookup"><span data-stu-id="94ee7-229">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="94ee7-230">Il est utile d’avoir un type d’identité par événement afin que vous pouvez créer une logique qui impose que chaque événement est traité qu’une seule fois par le récepteur.</span><span class="sxs-lookup"><span data-stu-id="94ee7-230">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="94ee7-231">Un traitement de message est fondamentalement idempotent.</span><span class="sxs-lookup"><span data-stu-id="94ee7-231">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="94ee7-232">Par exemple, si un système génère des images miniatures, il peut concerner pas combien de fois le traitement du message sur la miniature générée ; le résultat est que les miniatures sont générés et ils sont identiques à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="94ee7-232">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="94ee7-233">En revanche, opérations, telles que l’appel d’une passerelle de paiement pour charger une carte de crédit peut-être pas idempotent du tout.</span><span class="sxs-lookup"><span data-stu-id="94ee7-233">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="94ee7-234">Dans ce cas, vous devez vous assurer que le traitement de message plusieurs fois a pour effet que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="94ee7-234">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="94ee7-235">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="94ee7-235">Additional resources</span></span>

-   <span data-ttu-id="94ee7-236">**En respectant le message idempotence** (sous-titre sur cette page) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="94ee7-236">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="94ee7-237">Messages d’événements de l’intégration de déduplication</span><span class="sxs-lookup"><span data-stu-id="94ee7-237">Deduplicating integration event messages</span></span>

<span data-ttu-id="94ee7-238">Pour vous assurer que les événements de message sont envoyés et traités une fois par l’abonné à des niveaux différents.</span><span class="sxs-lookup"><span data-stu-id="94ee7-238">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="94ee7-239">Première consiste à utiliser une fonctionnalité de déduplication offerte par l’infrastructure de messagerie que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="94ee7-239">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="94ee7-240">Une autre consiste à implémenter une logique personnalisée dans votre microservice de destination.</span><span class="sxs-lookup"><span data-stu-id="94ee7-240">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="94ee7-241">Validations au niveau du transport et de niveau de l’application est la meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="94ee7-241">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="94ee7-242">Événements de message de déduplication au niveau EventHandler</span><span class="sxs-lookup"><span data-stu-id="94ee7-242">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="94ee7-243">Une pour vous assurer qu’un événement est traité une seule fois par n’importe quel récepteur consiste en implémentant une logique spécifique lors du traitement des événements de message dans les gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="94ee7-243">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="94ee7-244">Par exemple, qui est l’approche utilisée dans l’application eShopOnContainers, comme vous pouvez le voir dans le [code source](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) de la classe OrdersController lorsqu’il reçoit une commande CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="94ee7-244">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="94ee7-245">(Dans ce cas, nous utilisons une commande de requête HTTP, pas une commande basée sur message, mais la logique que vous souhaitez apporter une idempotent basée sur message de commande est similaire).</span><span class="sxs-lookup"><span data-stu-id="94ee7-245">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="94ee7-246">La déduplication de messages lors de l’utilisation de RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="94ee7-246">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="94ee7-247">Lorsque des défaillances intermittentes du réseau se produisent, les messages peuvent être dupliquées et le récepteur du message doit être prêt à gérer ces messages en double.</span><span class="sxs-lookup"><span data-stu-id="94ee7-247">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="94ee7-248">Si possible, les récepteurs doivent gérer les messages de manière idempotente, qui est meilleure qu’explicitement de les gérer avec la déduplication.</span><span class="sxs-lookup"><span data-stu-id="94ee7-248">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="94ee7-249">Conformément à la [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), « si un message est remis à un consommateur et puis remis (car il n’a pas accusé avant la suppression de la connexion de consommateur, par exemple), puis RabbitMQ définit l’indicateur de redistribution sur il lorsqu’il est remis à nouveau (s’il faut le même client ou une autre).</span><span class="sxs-lookup"><span data-stu-id="94ee7-249">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="94ee7-250">Si l’indicateur « redistribution » est défini, le récepteur doit tenir qui compte, car le message peut avoir déjà été traité.</span><span class="sxs-lookup"><span data-stu-id="94ee7-250">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="94ee7-251">Mais qui n’est pas garantie ; le message peut ne jamais avoir atteint le récepteur après qu’il quitté le courtier de messages, peut-être en raison de problèmes de réseau.</span><span class="sxs-lookup"><span data-stu-id="94ee7-251">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="94ee7-252">En revanche, si l’indicateur « redistribué » n’est pas défini, il est garanti que le message n’a pas été envoyé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="94ee7-252">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="94ee7-253">Par conséquent, le destinataire doit dédupliquer des messages ou traiter les messages de manière idempotente uniquement si l’indicateur « redistribution » est défini dans le message.</span><span class="sxs-lookup"><span data-stu-id="94ee7-253">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="94ee7-254">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="94ee7-254">Additional resources</span></span>

-   <span data-ttu-id="94ee7-255">**Événement piloté par messagerie**
    [*http://soapatterns.org/design\_modèles/événement\_par\_de messagerie*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="94ee7-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="94ee7-256">**Jimmy Bogard. Refactorisation vers résilience : L’évaluation de couplage**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="94ee7-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="94ee7-257">**Canal de publication-abonnement**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="94ee7-257">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="94ee7-258">**Communication entre délimitée contextes**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="94ee7-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="94ee7-259">**Cohérence éventuelle**
    [*https://en.wikipedia.org/wiki/Eventual\_la cohérence*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="94ee7-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="94ee7-260">**Philip Brown. Stratégies d’intégration délimitée contextes**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="94ee7-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="94ee7-261">**Chris Richardson. Développement de Microservices transactionnelle à l’aide d’agrégats, la source d’événement et CQRS - partie 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="94ee7-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="94ee7-262">**Chris Richardson. Approvisionnement du modèle d’événement**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="94ee7-262">**Chris Richardson. Event Sourcing pattern**
[*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="94ee7-263">**Présentation d’approvisionnement de l’événement**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="94ee7-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="94ee7-264">**Base de données du magasin d’événements**.</span><span class="sxs-lookup"><span data-stu-id="94ee7-264">**Event Store database**.</span></span> <span data-ttu-id="94ee7-265">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="94ee7-265">Official site.</span></span>
    [<span data-ttu-id="94ee7-266">*https://geteventstore.com/*</span><span class="sxs-lookup"><span data-stu-id="94ee7-266">*https://geteventstore.com/*</span></span>](https://geteventstore.com/)

-   <span data-ttu-id="94ee7-267">**Patrick Nommensen. Gestion des données pour Microservices basé sur l’événement**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*</span><span class="sxs-lookup"><span data-stu-id="94ee7-267">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="94ee7-268">**Le théorème CAP**
    [*https://en.wikipedia.org/wiki/CAP\_théorème*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="94ee7-268">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="94ee7-269">**Quel est le théorème de l’extrémité de fin ? ** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="94ee7-269">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="94ee7-270">**Manuel de la cohérence des données**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="94ee7-270">**Data Consistency Primer**
[*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="94ee7-271">**Rick Saling. Le théorème CAP : Pourquoi « Tout est différente de « avec le Cloud et Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="94ee7-271">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="94ee7-272">**Eric Brewer. Extrémité de fin douze ans plus tard : comment les « règles » ont été modifiés**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="94ee7-272">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="94ee7-273">**Intervenant dans des Transactions externes (DTC)** (MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="94ee7-273">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="94ee7-274">**Azure Service Bus. Messagerie répartie : Détection des doublons**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="94ee7-274">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="94ee7-275">**Guide de fiabilité** (documentation RabbitMQ) [ *https://www.rabbitmq.com/reliability.html\#consommateur*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="94ee7-275">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="94ee7-276">[Précédente] (rabbitmq-event-bus-development-test-environment.md) [suivant] (test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="94ee7-276">[Previous] (rabbitmq-event-bus-development-test-environment.md) [Next] (test-aspnet-core-services-web-apps.md)</span></span>
