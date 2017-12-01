---
title: "Mise en œuvre de la communication basée sur les événements entre microservices (événements d’intégration)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Mise en œuvre de la communication basée sur les événements entre microservices (événements d’intégration)"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e438607ab3549d63b89bef6af64c6723a4cac950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Mise en œuvre de la communication basée sur les événements entre microservices (événements d’intégration)

Comme décrit précédemment, lorsque vous utilisez la communication basée sur des événements, un microservice publie un événement lorsque quelque chose notables se produit, par exemple quand il met à jour une entité commerciale. Autres microservices s’abonner à ces événements. Lorsqu’un microservice reçoit un événement, il peut mettre à jour ses propres entités métier, ce qui peuvent provoquer des événements plus en cours de publication. Ce système de publication/abonnement est généralement effectué à l’aide d’une implémentation d’un bus d’événements. Le bus d’événements peut être conçu comme une interface avec l’API nécessaire pour s’abonner et annuler l’abonnement aux événements et publier des événements. Il peut également avoir une ou plusieurs implémentations selon toute communication entre processus ou de messagerie, comme une file d’attente de messagerie ou un bus de service qui prend en charge les communications asynchrones et un modèle de publication/abonnement.

Vous pouvez utiliser des événements pour implémenter des transactions commerciales qui s’étendent sur plusieurs services, ce qui vous donne la cohérence éventuelle entre ces services. Une transaction cohérente se compose d’une série d’actions distribuées. À chaque action, le microservice met à jour une entité commerciale et publie un événement qui déclenche l’action suivante.

![](./media/image19.PNG)

**Figure 8-18**. Communication pilotée par événements basée sur un bus d’événements

Cette section décrit comment vous pouvez implémenter ce type de communication avec .NET à l’aide d’une interface de bus d’événements génériques, comme indiqué dans la Figure 8-18. Il existe plusieurs implémentations possibles, chacun à l’aide d’une technologie différente ou une infrastructure telles que RabbitMQ, Azure Service Bus, ou tout autre tiers ouvrir la source ou le bus des services commerciaux.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>À l’aide du bus de services et aux courtiers de message pour les systèmes de production

Comme indiqué dans la section architecture, vous pouvez choisir parmi plusieurs technologies de messagerie pour l’implémentation de votre bus d’événements abstraite. Mais ces technologies sont à des niveaux différents. Par exemple, RabbitMQ, transport service broker de messagerie, est à un niveau inférieur à des produits commerciaux comme Azure Service Bus, NServiceBus, MassTransit ou Brighter. La plupart de ces produits peut fonctionnent par-dessus RabbitMQ ou d’Azure Service Bus. Votre choix de produit dépend de combien de fonctionnalités et de l’évolutivité de combien out-of-the-box dont vous avez besoin pour votre application.

Pour l’implémentation de simplement un événement bus preuve de concept pour votre environnement de développement, comme dans l’exemple eShopOnContainers, une implémentation simple de RabbitMQ en cours d’exécution en tant que conteneur peut être suffisant. Mais pour les applications stratégiques et les systèmes de production nécessitant une haute évolutivité, vous souhaiterez peut-être évaluer et utiliser Azure Service Fabric. Si vous avez besoin des abstractions de haut niveau et de fonctionnalités plus riches comme [sagas](https://docs.particular.net/nservicebus/sagas/) pour les processus longs qui rendent développement distribué des bus de service plus facile et autres de commerciaux et open source comme NServiceBus, MassTransit, et Éléments de l’évaluation sont valorisent votre travail. Bien entendu, vous pouvez toujours la générer vos propres fonctionnalités de bus de service sur les technologies de bas niveau telles que RabbitMQ et Docker, mais le travail nécessaire à réinventer la roue peut être trop importante pour une application d’entreprise.

En résumé : les abstractions de bus d’événements exemple et l’implémentation présentée dans l’exemple eShopOnContainers sont destinés à être utilisés uniquement comme une preuve de concept. Une fois que vous avez décidé que vous souhaitez bénéficier d’une communication asynchrone et pilotées par événements, comme expliqué dans la section en cours, vous devez choisir le produit de bus de service qui répond le mieux à vos besoins.

## <a name="integration-events"></a>Événements d’intégration

Événements d’intégration sont utilisées pour mettre l’état du domaine de synchronisation entre plusieurs microservices ou systèmes externes. Pour cela, vous devez publier les événements d’intégration à l’extérieur de la microservice. Lorsqu’un événement est publié sur plusieurs microservices récepteur (pour microservices autant que vous êtes abonné à l’événement d’intégration), le Gestionnaire d’événements approprié dans chaque récepteur de microservice gère l’événement.

Un événement d’intégration est essentiellement une classe de l’exploitation de données, comme dans l’exemple suivant :

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

La classe d’événements intégration peut être simple ; par exemple, il peut contenir un GUID pour son ID.

Les événements d’intégration peuvent être définis au niveau de l’application de chaque microservice, afin qu’ils sont dissociés d’autres microservices, d’une manière comparable à la façon dont les ViewModel est définies dans le serveur et le client. Ce qui n’est pas recommandé partage une bibliothèque d’événements intégration commune entre plusieurs microservices ; Cela serait être association étroite entre ces microservices et une bibliothèque de définition de données événement unique. Vous ne souhaitez pas le faire pour les mêmes raisons que vous ne souhaitez pas partager un modèle de domaine commun sur plusieurs microservices : microservices doit être complètement autonome.

Il existe seulement certains types de bibliothèques, que vous devez partager sur microservices. Un est bibliothèques qui sont des blocs d’application finale, comme le [API client de Bus d’événements](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), comme dans eShopOnContainers. Un autre est bibliothèques qui constituent des outils qui pourraient également être partagées en tant que composants NuGet, comme les sérialiseurs JSON.

## <a name="the-event-bus"></a>Le bus d’événements

Un bus d’événements permet de publier/abonner-style de communiquer microservices sans nécessiter les composants explicitement prenant en charge les unes des autres, comme indiqué dans la Figure 8-19.

![](./media/image20.png)

**Figure 8-19**. Principes de base avec un bus d’événements de publication/abonnement

Le bus d’événements lié au modèle observateur et de la publication-abonnement modèle.

### <a name="observer-pattern"></a>Modèle Observateur

Dans le [modèle Observateur](https://en.wikipedia.org/wiki/Observer_pattern), votre objet principal (appelé l’Observable) informe les autres objets intéressées (appelées observateurs) avec les informations pertinentes (événements).

### <a name="publish-subscribe-pubsub-pattern"></a>Modèle de publication et d’abonnement (Pub/Sub) 

L’objectif de la [modèle de Pub/Sub](https://msdn.microsoft.com/en-us/library/ff649664.aspx) est le même que le modèle Observateur : vous souhaitez notifier les autres services lorsque certains événements se produisent. Mais il existe une différence de sémantique importante entre les modèles observateur et Pub/Sub. Dans le modèle Pub/Sub, le focus est sur la diffusion de messages. En revanche, dans le modèle Observateur, l’Observable ne connaît pas devant les événements, qu’ils ont été envoyées. En d’autres termes, l’Observable (l’éditeur) ne sait pas sont des observateurs (les abonnés).

### <a name="the-middleman-or-event-bus"></a>Le bus intermédiaire ou l’événement 

Comment atteindre anonymat entre le serveur de publication et abonné ? Un moyen simple consiste à laisser un intermédiaire de prendre en charge toutes les communications. Un bus d’événements est un intermédiaire de ce type.

Un bus d’événements est généralement constitué de deux parties :

-   L’abstraction ou une interface.

-   Une ou plusieurs implémentations.

Dans la Figure 8-19 que vous pouvez voir comment, à partir du point de vue d’application, le bus d’événements est rien de plus qu’un canal Pub/Sub. La méthode que vous implémentez cette communication asynchrone peut varier. Il peut avoir plusieurs implémentations afin que vous pouvez permuter entre eux, selon les besoins de l’environnement (par exemple, la production et les environnements de développement).

Figure 8-20, vous pouvez voir une abstraction d’un bus d’événements avec plusieurs implémentations basées sur l’infrastructure de technologies telles que RabbitMQ, Azure Service Bus ou autres bus de service comme NServiceBus, MassTransit, etc. de messagerie.

![](./media/image21.png)

**Figure 8 : 20.** Plusieurs implémentations de bus d’événements

Toutefois, mise en évidence précédemment, à l’aide des abstractions (l’interface de bus d’événements) est possible uniquement si vous avez besoin de fonctionnalités de bus d’événements de base pris en charge par votre abstractions. Si vous avez besoin de plus riches fonctionnalités de bus de service, vous devez probablement utiliser l’API fournie par votre bus de service préférée à la place votre propre abstractions.

### <a name="defining-an-event-bus-interface"></a>Définition d’une interface de bus d’événements

Commençons par du code d’implémentation pour l’interface de bus d’événements et les implémentations possibles pour des raisons d’exploration. L’interface doit être générique et simple, comme dans l’interface suivante.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);
    void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T: IntegrationEvent;

    void Unsubscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent;
}
```

La méthode de publication est simple. Le bus d’événements diffuse l’événement intégration lui est passé à n’importe quel microservice abonnée à cet événement. Cette méthode est utilisée par le microservice qui publie l’événement.

La méthode Subscribe est utilisée par le microservices que vous souhaitez recevoir des événements. Cette méthode comporte deux parties. Le premier est l’événement d’intégration pour vous abonner à (IntegrationEvent). La deuxième partie est le Gestionnaire d’événements integration (ou la méthode de rappel) à appeler (IIntegrationEventHandler&lt;T&gt;) lorsque le microservice reçoit ce message d’événement de l’intégration.


>[!div class="step-by-step"]
[Précédente] (base de données-server-container.md) [suivant] (rabbitmq-event-bus-development-test-environment.md)
