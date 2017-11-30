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
# <a name="subscribing-to-events"></a>S’abonner aux événements

Pour le bus d’événements à l’aide de la première étape consiste à s’abonner le microservices aux événements qu’ils veulent recevoir. Qui doit être effectuée dans le récepteur microservices.

L’exemple de code suivant montre ce que chaque microservice récepteur doit implémenter au démarrage du service (autrement dit, lors du démarrage de classe) afin qu’il s’abonne aux événements qu’il a besoin. Par exemple, le microservice basket.api doit s’abonner aux messages de ProductPriceChangedIntegrationEvent. Cela rend la microservice prenant en charge de toutes les modifications pour le prix du produit et que vous lui permet d’avertir l’utilisateur sur la modification si ce produit est dans le panier de l’utilisateur.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

Une fois ce code s’exécute, l’abonné microservice est à l’écoute via les canaux RabbitMQ. Quand un message de type ProductPriceChangedIntegrationEvent arrive, le code appelle le Gestionnaire d’événements qui est passé et qu’elle traite l’événement.

## <a name="publishing-events-through-the-event-bus"></a>Publier des événements via le bus d’événements

Enfin, l’expéditeur du message (origine microservice) publie les événements de l’intégration avec un code similaire à l’exemple suivant. (Il s’agit d’un exemple simplifié qui n’accepte pas l’atomicité en compte.) Vous implémente un code similaire chaque fois qu’un événement doit être propagé sur plusieurs microservices, généralement juste après la validation de données ou transactions à partir de l’origine de microservice.

Tout d’abord, l’objet d’implémentation du bus événement (en fonction de RabbitMQ ou sur un bus de service) serait injecté dans le constructeur du contrôleur, comme dans le code suivant :

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

Puis vous utilisez les méthodes de votre contrôleur, comme dans la méthode UpdateProduct :

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

Dans ce cas, l’origine microservice étant un microservice CRUD simple, ce code est placé à droite dans le contrôleur d’API Web. Dans microservices plus avancées, il pourrait être implémenté dans la classe CommandHandler, droite après que les données d’origine seront validées.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Conception d’atomicité et la résilience lors de la publication pour le bus d’événements

Lorsque vous publiez des événements d’intégration via une distribution de messages système telles que le bus d’événements, vous rencontrez le problème de mise à jour de la base de données d’origine atomique et de publication d’un événement. Par exemple, dans l’exemple simplifié indiqué précédemment, le code valide les données la base de données lorsque le prix du produit est modifié et qu’il publie ensuite un message ProductPriceChangedIntegrationEvent. Au départ, il peut se présenter essentiel que ces deux opérations atomiquement. Toutefois, si vous utilisez une transaction distribuée implique la base de données et le message broker, comme vous le feriez dans les anciens systèmes comme [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), cela n’est pas recommandée pour les raisons décrites par la [Théorème de CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

En fait, vous utilisez microservices pour créer des systèmes évolutifs et hautement disponibles. Ce qui simplifie quelque peu, le théorème CAP indique que vous ne pouvez pas créer une base de données (ou un microservice qui possède son modèle) qui est disponible en permanence, fortement cohérent, *et* à tolérance de panne à n’importe quelle partition. Vous devez choisir deux de ces trois propriétés.

Dans les architectures de microservices, vous devez choisir la disponibilité et la tolérance de panne et vous devez prisés cohérence forte. Par conséquent, dans les applications microservice les plus récents, vous généralement ne souhaitez pas utiliser les transactions distribuées dans la messagerie, comme vous le feriez lorsque vous implémentez [des transactions distribuées](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) en fonction de la Transaction distribuée Windows Coordinator (DTC) avec [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).

Revenons à l’émission initiale et exemple. Si le service tombe en panne après la mise à jour de la base de données (dans ce cas, avec le bouton droit une fois la ligne de code avec \_contexte. SaveChangesAsync()), mais avant l’événement de l’intégration est publié, l’ensemble du système risquent de devenir incohérent. Cela peut être critiques, en fonction de l’opération métier spécifique que vous traitez.

Comme mentionné précédemment dans la section architecture, vous pouvez avoir plusieurs approches pour traiter ce problème :

-   À l’aide de la version complète [modèle d’approvisionnement de l’événement](https://msdn.microsoft.com/en-us/library/dn589792.aspx).

-   À l’aide de [d’exploration de données du journal des transactions](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   À l’aide de la [modèle de boîte d’envoi](http://gistlabs.com/2014/05/the-outbox/). Il s’agit d’une table transactionnelle pour stocker les événements d’intégration (extension de la transaction locale).

Pour ce scénario, l’utilisation du modèle d’événement approvisionnement (ES) complet est une des meilleures approches, dans le cas contraire *le* meilleures. Toutefois, dans de nombreux scénarios d’application, vous peut-être pas en mesure d’implémenter un système ES complet. ES signifie stocker uniquement les événements de domaine dans votre base de données transactionnelle, au lieu de stocker les données d’état en cours. Stocker uniquement les événements de domaine peut avoir de nombreux avantages, tels que l’historique de votre système et en mesure de déterminer l’état de votre système à tout moment dans le passé. Toutefois, l’implémentation d’un système ES complète, vous devez remanier la majeure partie de votre système et introduit de nombreuses autres complexités et la configuration requise. Par exemple, vous pouvez utiliser une base de données apportée spécifiquement pour l’alimentation de l’événement, tel que [magasin d’événements](https://geteventstore.com/), ou une base de données telles que la base de données Azure Cosmos, MongoDB, Cassandra, CouchDB ou RavenDB orienté document. ES est une meilleure approche pour ce problème, mais pas la solution la plus simple, sauf si vous êtes déjà familiarisé avec la source d’événement.

La possibilité d’utiliser le journal des transactions d’exploration de données initialement semble très transparente. Toutefois, pour utiliser cette approche, la microservice doit être associé à votre journal des transactions SGBDR, telles que le journal des transactions SQL Server. Cela est probablement pas souhaitable. Un autre inconvénient est que les mises à jour de bas niveau enregistrés dans le journal des transactions ne peuvent pas être le même niveau que les événements d’intégration de haut niveau. Dans ce cas, le processus d’ingénierie à rebours ces opérations du journal des transactions peuvent être difficiles.

Une approche d’équilibrage de charge est une combinaison d’une table de base de données transactionnelle et d’un modèle de ES simplifié. Vous pouvez utiliser un état comme « prêt pour la publication de l’événement, » que vous définissez dans l’événement d’origine lorsque vous le validez dans la table d’événements de l’intégration. Vous essayez ensuite de publier l’événement vers le bus d’événements. Si l’action de l’événement de publication réussit, vous démarrez une autre transaction dans le service d’origine et déplacez l’état « prêt pour la publication de l’événement » à « événement déjà publiée ».

Si l’action de l’événement de publication de l’événement de bus échoue, les données toujours pas seront incohérentes dans le microservice d’origine, il est toujours marqué comme « prêt à publier l’événement », et en ce qui concerne le reste des services, il ne sera cohérente. Vous pouvez toujours avoir les tâches en arrière-plan vérification de l’état des transactions ou des événements d’intégration. Si la tâche détecte un événement dans l’état « prêt pour la publication de l’événement », il peut tenter de publier à nouveau cet événement avec le bus d’événements.

Notez qu’avec cette approche, vous rendez persistantes uniquement les événements d’intégration pour chaque microservice d’origine et uniquement les événements que vous souhaitez communiquer à d’autres microservices ou les systèmes externes. En revanche, dans un système ES complet, stocker tous les événements de domaine également.

Par conséquent, cette approche à charge équilibrée est un système ES simplifié. Vous avez besoin d’une liste des événements d’intégration avec leur état actuel (« prêt à publier » et « publié »). Mais vous devrez implémenter ces États pour les événements d’intégration. Et, dans cette approche, il est inutile stocker toutes les données de votre domaine en tant qu’événements dans la base de données transactionnelle, comme vous le feriez dans un système ES complet.

Si vous utilisez déjà une base de données relationnelle, vous pouvez utiliser une table transactionnelle pour stocker les événements d’intégration. Pour obtenir l’atomicité de votre application, vous utilisez un processus en deux étapes basé sur des transactions locales. En fait, vous avez une table de IntegrationEvent dans la même base de données où vous avez vos entités de domaine. Cette table fonctionne comme une assurance d’obtenir l’atomicité afin que vous incluez persistante des événements d’intégration dans les mêmes transactions en cours de validation les données du domaine.

Étape par étape, le processus se déroule comme suit : l’application commence une transaction de base de données locale. Ensuite, il met à jour l’état de vos entités de domaine et insère un événement dans la table d’événements de l’intégration. Enfin, il valide la transaction. Vous obtenez l’atomicité de votre choix.

Lorsque vous implémentez les étapes de la publication d’événements, vous avez ces possibilités :

-   Publier l’événement intégration juste après la validation de la transaction et une autre transaction locale permet de marquer les événements dans la table en cours de publication. Ensuite, utilisez le tableau comme un artefact pour suivre les événements d’intégration en cas de problèmes dans le microservices à distance et effectuer des actions de compensation basées sur les événements d’intégration stockée.

-   Utilisez le tableau comme un type de file d’attente. Un thread d’application distinct ou un processus interroge la table d’événements integration, publie les événements pour le bus d’événements, puis utilise une transaction locale pour marquer les événements publié.

Figure 8-22 illustre l’architecture de la première de ces approches.

![](./media/image23.png)

**Figure 8-22**. Atomicité lors de la publication d’événements pour le bus d’événements

L’approche illustrée dans la Figure 8-22 manque microservice un travail supplémentaire qui est responsable de la vérification et confirmant la réussite des événements d’intégration publiée. En cas de défaillance, ce microservice de travail de l’outil d’analyse supplémentaires permettre lire les événements à partir de la table et les republier.

Sur la deuxième approche : vous utilisez la table du journal des événements comme une file d’attente et un microservice de travail pour publier les messages. Dans ce cas, le processus est illustré comme cela dans la Figure 8-23. Cet exemple montre un microservice supplémentaire et la table est la seule source lors de la publication d’événements.

![](./media/image24.png)

**Figure 8-23**. Atomicité lors de la publication d’événements pour le bus d’événements avec un microservice de travail

Par souci de simplicité, l’exemple eShopOnContainers utilise la première approche (sans processus supplémentaires ou avec l’outil d’analyse microservices) ainsi que le bus d’événements. Toutefois, l’eShopOnContainers ne gère pas tous les cas de défaillance. Dans une application réelle déployée sur le cloud, le fait de problèmes surviendront par la suite, et vous devez implémenter qui vérifier et renvoyez la logique doit adopter. À l’aide de la table comme une file d’attente peut être plus efficace que la première approche si vous avez cette table comme une seule source d’événements lorsque vous les publiez via le bus d’événements.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implémentation d’atomicité lors de la publication d’événements d’intégration via le bus d’événements

Le code suivant montre comment vous pouvez créer une transaction impliquant plusieurs objets DbContext — un contexte liées aux données d’origine est mis à jour et le contexte de deuxième associées à la table IntegrationEventLog.

Notez que la transaction dans l’exemple de code ci-dessous ne sera pas résiliente si les connexions à la base de données n’importe quel problème au moment lorsque le code est en cours d’exécution. Cela peut se produire dans les systèmes cloud comme Azure SQL DB, qui peut déplacer des bases de données entre serveurs. Pour implémenter des transactions résilientes dans plusieurs contextes, consultez le [implémentation de connexions d’Entity Framework Core SQL résilientes](#implementing_resilient_EFCore_SQL_conns) section plus loin dans ce guide.

Pour plus de clarté, l’exemple suivant montre l’ensemble du processus dans un seul élément de code. Toutefois, l’implémentation d’eShopOnContainers est réellement refactorisée et fractionner cette logique dans plusieurs classes, par conséquent, il est plus facile à gérer.

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

Une fois l’événement d’intégration ProductPriceChangedIntegrationEvent est créé, la transaction qui stocke l’opération de domaine d’origine (mise à jour l’élément de catalogue) inclut également la persistance de l’événement dans la table du journal des événements. Cela rend une transaction unique, et vous serez toujours en mesure de vérifier si les messages d’événement ont été envoyés.

La table du journal des événements est mis à jour atomiquement avec l’opération de base de données d’origine, à l’aide d’une transaction locale par rapport à la même base de données. Si une des opérations échoue, une exception est levée et la transaction restaure toute opération terminée, ainsi maintenir la cohérence entre les opérations de domaine et les messages d’événement envoyés.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Réception de messages à partir d’abonnements : les gestionnaires d’événements dans le récepteur microservices

En plus de la logique d’abonnement événement, vous devez implémenter le code interne pour les gestionnaires d’événements integration (comme une méthode de rappel). Le Gestionnaire d’événements est où vous spécifiez où les messages d’un certain type d’événement sont reçus et traités.

Un gestionnaire d’événements reçoit d’abord une instance d’événement à partir du bus d’événements. Il localise ensuite le composant de traitement liés à cet événement d’intégration, multiplication et la conservation de l’événement en tant qu’une modification d’état dans le récepteur de microservice. Par exemple, un événement ProductPriceChanged proviennent du catalogue microservice, est gérée dans le panier d’achat microservice et modifie l’état de cette microservice de panier de récepteur ainsi, comme indiqué dans le code suivant.

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

Le Gestionnaire d’événements doit vérifier si le produit existe dans toutes les instances du panier d’achat. Il met également à jour du prix de chaque élément de ligne du panier d’achat associées. Enfin, il crée une alerte à afficher à l’utilisateur sur la modification de prix, comme indiqué dans la Figure 8 à 24.

![](./media/image25.png)

**Figure 8-24**. Affichage d’une variation de l’élément dans un panier, communiquée par les événements d’intégration

## <a name="idempotency-in-update-message-events"></a>Idempotence dans les événements de message de mise à jour

Un aspect important d’événements de message de mise à jour est qu’une défaillance dans n’importe quel point dans la communication doit entraîner le message à être réessayée. Sinon, une tâche en arrière-plan peut tenter de publier un événement qui a déjà été publié, création d’une condition de concurrence. Vous devez vous assurer que les mises à jour sont idempotents ou qu’ils fournissent suffisamment d’informations pour vous assurer que vous pouvez détecter un doublon, ignorer et envoyer arrière une seule réponse.

Comme indiqué précédemment, idempotence signifie qu’une opération peut être effectuée plusieurs fois sans modifier le résultat. Dans un environnement de messagerie, comme lors de la communication des événements, un événement est idempotente si elle peut être remis plusieurs fois sans modifier le résultat pour le récepteur de microservice. Cela peut être nécessaire en raison de la nature de l’événement lui-même, ou en raison du mode, le système gère l’événement. Message idempotence est importante dans toute application qui utilise la messagerie, pas seulement dans les applications qui implémentent le modèle de bus d’événements.

Un exemple d’une opération idempotente est une instruction SQL qui insère des données dans une table uniquement si ces données ne sont pas déjà dans la table. Il n’a pas d’importance combien de fois vous exécutez qu’insérez l’instruction SQL ; le résultat sera le même, la table contiendra ces données. Idempotence, comme cela peut également être nécessaire lorsque vous traitez des messages si les messages pourraient potentiellement être envoyés et par conséquent traité plus d’une fois. Par exemple, si la logique de nouvelle tentative entraîne un émetteur d’envoyer exactement le même message plusieurs fois, vous devez vous assurer qu’il est idempotente.

Il est possible de messages idempotent de conception. Par exemple, vous pouvez créer un événement indiquant que « le prix du produit la valeur \$25 » au lieu de « ajouter \$5 pour le prix du produit. » Vous pourriez traiter en toute sécurité le premier message n’importe quel nombre de fois et le résultat sera le même. Qui n’est pas vrai pour le second message. Mais même dans le premier cas, vous pouvez traiter le premier événement, car le système également a pu envoyer un événement de modification de prix plus récente et que vous feriez écraser le nouveau prix.

Un autre exemple est un événement de fin de commande été propagé à plusieurs abonnés. Il est important que les informations de commande être mis à jour une seule fois, dans d’autres systèmes même s’il existe des événements de message en double pour le même événement de commande terminée.

Il est utile d’avoir un type d’identité par événement afin que vous pouvez créer une logique qui impose que chaque événement est traité qu’une seule fois par le récepteur.

Un traitement de message est fondamentalement idempotent. Par exemple, si un système génère des images miniatures, il peut concerner pas combien de fois le traitement du message sur la miniature générée ; le résultat est que les miniatures sont générés et ils sont identiques à chaque fois. En revanche, opérations, telles que l’appel d’une passerelle de paiement pour charger une carte de crédit peut-être pas idempotent du tout. Dans ce cas, vous devez vous assurer que le traitement de message plusieurs fois a pour effet que vous attendez.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **En respectant le message idempotence** (sous-titre sur cette page) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>Messages d’événements de l’intégration de déduplication

Pour vous assurer que les événements de message sont envoyés et traités une fois par l’abonné à des niveaux différents. Première consiste à utiliser une fonctionnalité de déduplication offerte par l’infrastructure de messagerie que vous utilisez. Une autre consiste à implémenter une logique personnalisée dans votre microservice de destination. Validations au niveau du transport et de niveau de l’application est la meilleure solution.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Événements de message de déduplication au niveau EventHandler

Une pour vous assurer qu’un événement est traité une seule fois par n’importe quel récepteur consiste en implémentant une logique spécifique lors du traitement des événements de message dans les gestionnaires d’événements. Par exemple, qui est l’approche utilisée dans l’application eShopOnContainers, comme vous pouvez le voir dans le [code source](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) de la classe OrdersController lorsqu’il reçoit une commande CreateOrderCommand. (Dans ce cas, nous utilisons une commande de requête HTTP, pas une commande basée sur message, mais la logique que vous souhaitez apporter une idempotent basée sur message de commande est similaire).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>La déduplication de messages lors de l’utilisation de RabbitMQ

Lorsque des défaillances intermittentes du réseau se produisent, les messages peuvent être dupliquées et le récepteur du message doit être prêt à gérer ces messages en double. Si possible, les récepteurs doivent gérer les messages de manière idempotente, qui est meilleure qu’explicitement de les gérer avec la déduplication.

Conformément à la [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), « si un message est remis à un consommateur et puis remis (car il n’a pas accusé avant la suppression de la connexion de consommateur, par exemple), puis RabbitMQ définit l’indicateur de redistribution sur il lorsqu’il est remis à nouveau (s’il faut le même client ou une autre).

Si l’indicateur « redistribution » est défini, le récepteur doit tenir qui compte, car le message peut avoir déjà été traité. Mais qui n’est pas garantie ; le message peut ne jamais avoir atteint le récepteur après qu’il quitté le courtier de messages, peut-être en raison de problèmes de réseau. En revanche, si l’indicateur « redistribué » n’est pas défini, il est garanti que le message n’a pas été envoyé plusieurs fois. Par conséquent, le destinataire doit dédupliquer des messages ou traiter les messages de manière idempotente uniquement si l’indicateur « redistribution » est défini dans le message.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Événement piloté par messagerie**
    [*http://soapatterns.org/design\_modèles/événement\_par\_de messagerie*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Refactorisation vers résilience : L’évaluation de couplage**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Canal de publication-abonnement**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Communication entre délimitée contextes**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)

-   **Cohérence éventuelle**
    [*https://en.wikipedia.org/wiki/Eventual\_la cohérence*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Philip Brown. Stratégies d’intégration délimitée contextes**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Chris Richardson. Développement de Microservices transactionnelle à l’aide d’agrégats, la source d’événement et CQRS - partie 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Chris Richardson. Approvisionnement du modèle d’événement**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)

-   **Présentation d’approvisionnement de l’événement**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)

-   **Base de données du magasin d’événements**. Site officiel.
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen. Gestion des données pour Microservices basé sur l’événement**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*

-   **Le théorème CAP**
    [*https://en.wikipedia.org/wiki/CAP\_théorème*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Quel est le théorème de l’extrémité de fin ? ** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Manuel de la cohérence des données**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)

-   **Rick Saling. Le théorème CAP : Pourquoi « Tout est différente de « avec le Cloud et Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Eric Brewer. Extrémité de fin douze ans plus tard : comment les « règles » ont été modifiés**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Intervenant dans des Transactions externes (DTC)** (MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure Service Bus. Messagerie répartie : Détection des doublons**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Guide de fiabilité** (documentation RabbitMQ) [ *https://www.rabbitmq.com/reliability.html\#consommateur*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[Précédente] (rabbitmq-event-bus-development-test-environment.md) [suivant] (test-aspnet-core-services-web-apps.md)
