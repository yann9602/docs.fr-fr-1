---
title: "Communication asynchrone basée sur message"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Communication asynchrone basée sur message"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df39771295d12e122edbe27e91cd899e3318e301
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="asynchronous-message-based-communication"></a>Communication asynchrone basée sur message

Messagerie asynchrone et pilotés par les événements de communication sont critiques lors de la propagation des modifications sur plusieurs microservices et leurs modèles de domaine connexes. Comme mentionné précédemment dans la discussion microservices et contextes délimitée (BCs), les modèles (utilisateur, client, produit, compte, etc.) peuvent signifier différentes choses pour différentes microservices ou BCs. Cela signifie que lorsque des modifications se produisent, vous devez rapprocher les modifications dans les différents modèles. Une solution est la cohérence éventuelle et communication pilotée par événements en fonction de la messagerie asynchrone.

Lorsque vous utilisez la messagerie, les processus communiquent en échangeant des messages de façon asynchrone. Un client établit une commande ou une demande à un service en l’envoyant un message. Si le service doit répondre, il envoie un autre message au client. Dans la mesure où il s’agit d’une communication basée sur message, le client suppose que la réponse ne reçoit pas immédiatement, et qu’il ne peut y avoir aucune réponse du tout.

Un message est composé d’un en-tête (métadonnées telles que les informations d’identification ou de sécurité) et un corps. Les messages sont généralement envoyés via les protocoles asynchrones comme AMQP.

L’infrastructure préféré pour ce type de communication au sein de la Communauté microservices est un léger de message service broker, qui est différent de celle de la grandes courtiers et orchestrators utilisées dans SOA. Dans un service broker de message léger, l’infrastructure est en général « passif, « agissent uniquement comme un courtier de messages avec des implémentations simples telles que RabbitMQ ou un bus des services évolutifs dans le cloud comme Azure Service Bus. Dans ce scénario, la majeure partie de l’approche « intelligente » se trouve toujours dans les points de terminaison qui sont de production et de consommer des messages, autrement dit, dans le microservices.

Une autre règle, qu'il est conseillé de suivre autant que possible, consiste à utiliser la messagerie asynchrone uniquement entre les services internes et pour utiliser la communication synchrone (par exemple, HTTP) uniquement à partir des applications client pour les services frontaux (passerelles API ainsi que le premier niveau de microservices).

Il existe deux types de communication asynchrone : récepteur unique basée sur message communications et plusieurs récepteurs basée sur message. Dans les sections suivantes, nous fournir plus d’informations.

## <a name="single-receiver-message-based-communication"></a>Communication de messagerie unique-récepteur 

Une communication asynchrone basée sur message avec un seul destinataire signifie communication point à point qui remet un message à un seul des consommateurs qui lit à partir du canal, et que le message est traité une seule fois. Toutefois, il existe des situations particulières. Par exemple, dans un système de cloud qui tente de récupérer automatiquement des défaillances, le même message peut être envoyé plusieurs fois. En raison de réseau ou d’autres défaillances, le client doit être en mesure de nouvelles tentatives d’envoi de messages, et le serveur doit implémenter une opération idempotente afin de traiter un message particulier qu’une seule fois.

Communication de messagerie unique-récepteur est particulièrement bien adaptée pour l’envoi de commandes asynchrones à partir d’un microservice à un autre comme indiqué dans la Figure 4-18 qui illustre cette approche.

Une fois que vous démarrez l’envoi de communication basée sur message (soit à des commandes ou des événements), vous devez éviter de mélanger les communication basée sur le message avec la communication HTTP synchrone.

![](./media/image18.PNG)

**Figure 4-18**. Un seul microservice réception d’un message asynchrone

Notez que, lorsque les commandes proviennent des applications clientes, ils peuvent être implémentés en tant que les commandes synchrones HTTP. Vous devez utiliser basée sur message des commandes lorsque vous avez besoin d’une évolutivité plus élevée ou si vous êtes déjà dans un processus d’entreprise basé sur le message.

## <a name="multiple-receivers-message-based-communication"></a>Communication basée sur message de récepteurs de multiples 

Une approche plus souple, vous souhaiterez également utiliser un mécanisme de publication/abonnement afin que votre communication de l’expéditeur sera disponible pour les microservices supplémentaires pour les abonnés ou des applications externes. Par conséquent, il vous aide à suivre le [principe d’ouverture/fermeture](https://en.wikipedia.org/wiki/Open/closed_principle) dans le service d’envoi. De cette façon, les abonnés supplémentaires peuvent être ajoutés à l’avenir sans avoir besoin de modifier le service de l’expéditeur.

Lorsque vous utilisez une communication de publication/abonnement, vous utilisez peut-être interface du bus d’événements aux événements de publication à un abonné.

## <a name="asynchronous-event-driven-communication"></a>Communication asynchrone pilotée par événements

Lorsque vous utilisez une communication asynchrone commandé par événement, un microservice publie un événement de l’intégration lorsque quelque chose se produit au sein de son domaine et microservice un autre doit connaître, comme une modification de prix dans un microservice de catalogue de produits. Microservices supplémentaires s’abonner aux événements afin qu’ils peuvent les recevoir en mode asynchrone. Lorsque cela se produit, les destinataires peuvent mettre à jour leurs entités de domaine, ce qui peuvent entraîner plusieurs événements d’intégration à publier. Ce système de publication/abonnement est généralement effectué à l’aide d’une implémentation d’un bus d’événements. Le bus d’événements peut être conçu comme une abstraction ou une interface, avec l’API qui est nécessaire pour s’abonner ou annuler l’abonnement aux événements et publier des événements. Le bus d’événements peut également avoir l’une ou plusieurs implémentations en fonction de n’importe quel broker entre les processus et de messagerie, telle qu’une file d’attente de messagerie ou le bus de service qui prend en charge les communications asynchrones et un modèle de publication/abonnement.

Si un système utilise la cohérence éventuelle pilotée par les événements d’intégration, il est recommandé que cette approche sont complètement clair à l’utilisateur final. Le système ne doit pas utiliser une approche qui reproduit les événements d’intégration, telles que SignalR ou des systèmes d’interrogation du client. L’utilisateur final et le propriétaire de l’entreprise doivent explicitement adopter la cohérence éventuelle dans le système et notez que dans de nombreux cas l’entreprise n’a pas de problème avec cette approche, à condition qu’il soit explicite.

Comme indiqué précédemment dans le [défis et solutions pour la gestion de données distribuée](#challenges-and-solutions-for-distributed-data-management) section, vous pouvez utiliser des événements d’intégration pour implémenter des tâches d’entreprise qui s’étendent sur plusieurs microservices. Vous aurez ainsi la cohérence éventuelle entre ces services. Une transaction cohérente est constituée d’une collection d’actions distribuées. À chaque action, le microservice connexe met à jour une entité de domaine et publie un autre événement d’intégration qui déclenche l’action suivante dans la même tâche professionnelle de bout en bout.

Un point important est que vous pouvez souhaiter communiquer avec plusieurs microservices qui sont abonnés au même événement. Pour ce faire, vous pouvez utiliser la publication/abonnement de messagerie en fonction de communication pilotée par événements, comme indiqué dans la Figure 4-19. Ce mécanisme de publication/abonnement n’est pas exclusif à l’architecture de microservice. Il est similaire à la façon dont [limitées de contextes](http://martinfowler.com/bliki/BoundedContext.html) dans DDD doit communiquer, ou à la façon dont vous propagez les mises à jour à partir de la base de données de l’écriture de la base de données en lecture la [commande et requête responsabilité répartition (CQRS)](http://martinfowler.com/bliki/CQRS.html)modèle d’architecture. L’objectif est d’avoir cohérence éventuelle entre plusieurs sources de données sur votre système distribué.

![](./media/image19.png)

**Figure 4-19**. Communication par message asynchrone de pilotée par événements

Votre implémentation de détermine ce que le protocole à utiliser pour les communications pilotée par événements, basée sur message. [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) peuvent aider à atteindre une communication en file d’attente fiable.

Lorsque vous utilisez un bus d’événements, vous souhaiterez peut-être utiliser un niveau d’abstraction (par exemple, une interface de bus d’événements) basé sur une implémentation connexe dans les classes avec le code à l’aide de l’API à partir d’un service broker de message comme [RabbitMQ](https://www.rabbitmq.com/) ou un service bus comme [Azure Service Bus avec rubriques](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Vous souhaiterez également utiliser un bus de service de niveau supérieur comme NServiceBus, MassTransit ou Brighter à formuler votre bus d’événements et de système de publication/abonnement.

## <a name="a-note-about-messaging-technologies-for-production-systems"></a>Remarque à propos des technologies pour les systèmes de production de messagerie

Les technologies de messagerie disponibles pour l’implémentation de votre bus d’événements abstraits sont à des niveaux différents. Par exemple, les produits comme RabbitMQ (transport de messagerie service broker) et Azure Service Bus se trouvent à un niveau inférieur à d’autres produits comme, NServiceBus, MassTransit ou Brighter, ce qui peut fonctionner sur RabbitMQ et Azure Service Bus. Votre choix dépend du nombre de fonctionnalités au niveau de l’application et l’évolutivité de l’emploi que vous avez besoin pour votre application. Pour l’implémentation de simplement un bus d’événements de la preuve de concept pour votre environnement de développement, comme nous l’avons fait dans l’exemple eShopOnContainers, une implémentation simple de RabbitMQ en cours d’exécution sur un conteneur Docker peut être suffisant.

Toutefois, pour les applications stratégiques et les systèmes de production devant hyper évolutivité, vous pouvez évaluer Azure Service Bus. Pour les fonctionnalités qui facilitent le développement d’applications distribuées et des abstractions, nous vous recommandons d’évaluer autres bus de service commercial et open source, tels que NServiceBus, MassTransit et Brighter. Bien entendu, vous pouvez créer vos propres fonctionnalités de service bus sur les technologies de bas niveau telles que RabbitMQ et Docker. Mais ce travail plomberie coûtent trop important pour une application d’entreprise.

## <a name="resiliently-publishing-to-the-event-bus"></a>Élastique publication sur le bus d’événements

Un lors de l’implémentation d’une architecture pilotée par événements entre plusieurs microservices consiste à mettre à jour atomiquement d’état dans le microservice d’origine lors de la publication élastique de son événement intégration connexes dans le bus d’événements, en fonction d’une certaine manière transactions. Voici quelques manières d’effectuer cette opération, bien qu’il peut y avoir des approches supplémentaires.

-   À l’aide d’une file transactionnelle (basé sur le DTC) tels que MSMQ. (Toutefois, il s’agit une approche héritée.)

-   À l’aide de [d’exploration de données du journal des transactions](http://www.scoop.it/t/sql-server-transaction-log-mining).

-   À l’aide complète [événement approvisionnement](https://msdn.microsoft.com/en-us/library/dn589792.aspx) modèle.

-   À l’aide de la [modèle de boîte d’envoi](http://gistlabs.com/2014/05/the-outbox/): une table de base de données transactionnelle comme une file d’attente qui sera la base d’un composant créateur de l’événement qui serait créer l’événement et le publier.

Rubriques supplémentaires à prendre en compte lors de l’utilisation d’une communication asynchrone sont l’idempotence de message et la déduplication de message. Ces rubriques sont traitées dans la section [mise en œuvre de la communication basée sur les événements entre microservices (événements d’intégration)](#implementing_event_based_comms_microserv) plus loin dans ce guide.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Événement piloté par messagerie**
    [*http://soapatterns.org/design\_modèles/événement\_par\_de messagerie*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Canal de publication/abonnement**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **UDI Dahan. Clarification CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Commande et de répartition de responsabilité (CQRS) de la requête**
    [*https://docs.microsoft.com/azure/architecture/patterns/cqrs*](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

-   **Communication entre délimitée contextes**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Cohérence éventuelle**
    [*https://en.wikipedia.org/wiki/Eventual\_la cohérence*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Jimmy Bogard. Refactorisation vers résilience : L’évaluation de couplage**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)


>[!div class="step-by-step"]
[Précédente] (communication-de-microservice-architecture.md) [suivant] (mettre à jour-microservice-apis.md)
