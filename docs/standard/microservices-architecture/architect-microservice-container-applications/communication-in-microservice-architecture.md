---
title: "Communication au sein d’une architecture de microservice"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Communication dans un architectures d’architecture de microservice"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8d38095a151b7568619b17340d768eff684d3271
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="communication-in-a-microservice-architecture"></a>Communication au sein d’une architecture de microservice

Dans une application monolithique en cours d’exécution sur un processus unique, les composants invoquer mutuellement à l’aide d’appels de fonction ou de méthode au niveau du langage. Ceux-ci peuvent être fortement couplés si vous créez des objets avec le code (par exemple, `new ClassName()`), ou peut être appelée de façon découplée si vous utilisez l’Injection de dépendances en faisant référence à des abstractions plutôt que des instances d’objet concret. Dans les deux cas, les objets sont en cours d’exécution dans le même processus. Le défi le plus important lors de la modification d’une application monolithique vers une application basée sur des microservices se trouve dans le mécanisme de communication. Une conversion directe dans le processus appels de méthode dans les appels aux services RPC provoque un bavard et une communication efficace pas qui ne s’exécutera pas correctement dans les environnements distribués. Les défis de la conception d’un système distribué correctement suffisamment bien connus qu’il existe encore un canon appelé le [les fallacies de l’informatique distribuée](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing) qui répertorie les hypothèses sur lesquelles les développeurs font souvent lors du déplacement de monolithique de conceptions distribuées.

Il est n’est pas une solution, mais plusieurs. Une solution consiste à isoler le microservices business autant que possible. Ensuite, utilisent la communication asynchrone entre les microservices interne et remplacez affinée communication standard dans une communication intra-PROCEDE entre les objets de communication de plus grande ampleur. Vous pouvez effectuer cela en regroupant les appels et en retournant des données qui agrège les résultats de plusieurs appels internes au client.

Une application basée sur des microservices est un système distribué en cours d’exécution sur plusieurs processus ou des services, généralement même entre plusieurs serveurs ou ordinateurs hôtes. Chaque instance de service est généralement un processus. Par conséquent, les services doivent interagissent à l’aide d’un protocole de communication inter-processus comme un protocole binaire, tel que TCP, selon la nature de chaque service, AMQP ou HTTP.

La Communauté microservice promeut la philosophie de «[actives des points de terminaison et des canaux passifs](http://simplicable.com/new/smart-endpoints-and-dumb-pipes). » Ce slogan encourage une conception qui est dissocié que possible entre microservices et aussi cohérents que possible au sein d’un seul microservice. Comme expliqué précédemment, chaque microservice possède ses propres données et sa propre logique de domaine. Mais les composition d’une application de bout en bout de microservices sont généralement simplement précis en utilisant les communications reste plutôt que les protocoles complexes telles que WS -\* et flexibles communications pilotée par événements au lieu de centralisé processus-Business-orchestrators.

Les deux protocoles couramment utilisées sont demande/réponse HTTP avec l’API (lors de l’interrogation de la plupart des tous) de ressources et léger de messagerie asynchrone lors de la communication des mises à jour sur plusieurs microservices. Ils sont expliqués plus en détail dans les sections suivantes.

## <a name="communication-types"></a>Types de communication

Client et services puissent communiquer via différents types de communication, chacun d'entre eux ciblant un autre scénario et vos objectifs. Au départ, ces types de communication peuvent être classées dans les deux axes.

Le premier axe consiste à définir si le protocole est synchrone ou asynchrone :

-   Protocole synchrone. HTTP est un protocole synchrone. Le client envoie une demande et attend une réponse du service. Qui est indépendante de l’exécution du code client qui peut être synchrone (le thread est bloqué) ou asynchrone (thread n’est pas bloqué, et la réponse atteindra un rappel par la suite). Le point important ici est que le protocole (HTTP/HTTPS) est synchrone et que le code client peut continuer uniquement sa tâche lorsqu’il reçoit la réponse du serveur HTTP.

-   Protocole asynchrone. D’autres protocoles comme AMQP (un protocole pris en charge par de nombreux systèmes d’exploitation et les environnements de cloud) utilisent des messages asynchrones. Généralement, l’expéditeur du message ou le code client n’attend pas de réponse. Il transmet le message en tant que lors de l’envoi d’un message à une file d’attente RabbitMQ ou tout autre service broker de message.

Le deuxième axe consiste à définir si la communication a un destinataire unique ou plusieurs destinataires :

-   Destinataire unique. Chaque demande doit être traité par un seul récepteur ou service. Un exemple de cette communication est la [modèle Command](https://en.wikipedia.org/wiki/Command_pattern).

-   Plusieurs destinataires. Chaque demande peut être traité par zéro à plusieurs destinataires. Ce type de communication doit être asynchrone. Par exemple le [de publication/abonnement](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) mécanisme utilisé dans les modèles comme [pilotée par événements une architecture](http://microservices.io/patterns/data/event-driven-architecture.html). Il repose sur un broker de message ou d’interface de bus d’événements lors de la propagation des mises à jour des données entre plusieurs microservices via des événements ; Il est généralement implémenté via un bus de service ou un artefact similaire comme [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) à l’aide de [rubriques et abonnements](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions).

Une application basée sur les microservice utilisent souvent une combinaison de ces styles de communication. Le type le plus courant est unique-récepteur la communication avec un protocole synchrone comme HTTP/HTTPS lors de l’appel d’un service Web API HTTP normal. Microservices utilisent également généralement les protocoles de messagerie pour la communication asynchrone entre microservices.

Ces axes sont important de connaître afin d’avoir plus de clarté sur les mécanismes de communication possibles, mais ils ne sont pas des préoccupations importantes lors de la création de microservices. La nature asynchrone de l’exécution dans le thread de client sans la nature asynchrone du protocole sélectionné sont les points importants lors de l’intégration de microservices. Ce que *est* important est en cours d’intégrer votre microservices asynchrone tout en conservant l’indépendance des microservices, comme expliqué dans la section suivante.

## <a name="asynchronous-microservice-integration-enforces-microservices-autonomy"></a>Intégration de microservice asynchrone applique l’autonomie de microservice.

Comme indiqué, le point important lors de la création d’une application basée sur des microservices est celle que vous intégrez votre microservices. Dans l’idéal, vous essayez de réduire la communication entre le microservices interne. Le moins les communications entre microservices, mieux ce. Mais bien entendu, dans de nombreux cas vous devez intégrer une certaine manière du microservices. Lorsque vous avez besoin pour ce faire, la règle essentielle ici est que la communication entre le microservices doit être asynchrone. Cela ne signifie pas que vous devez utiliser un protocole spécifique (par exemple, une messagerie asynchrone ou synchrone HTTP). Cela signifie simplement que la communication entre microservices doit être effectuée uniquement par la propagation des données de façon asynchrone, mais essayez de ne pas dépendent d’autres microservices interne dans le cadre de l’opération de demande/réponse HTTP du service initial.

Si possible, jamais dépendent de communication synchrone (requête/réponse) entre plusieurs microservices, même pour les requêtes. L’objectif de chaque microservice doit être autonome et disponible pour le consommateur du client, même si les autres services qui font partie de l’application de bout en bout sont en panne ou défectueux. Si vous pensez que vous avez besoin effectuer un appel à partir d’un microservice à d’autres microservices (par exemple, l’exécution d’une requête HTTP pour une requête de données) dans afin d’être en mesure de fournir une réponse à une application cliente, vous disposez d’une architecture qui ne sera pas résiliente quand certains Échec de microservices.

En outre, votre microservices ayant des dépendances HTTP entre microservices, comme lors de la création de longs cycles de demande/réponse avec HTTP demande chaînes, comme indiqué dans la première partie de la Figure 4-15, seulement ne rend pas autonome mais aussi leurs performances affectés dès que l’un des services dans cette chaîne n’effectue pas correctement. 

Plus vous ajoutez des dépendances synchrones entre microservices, comme les demandes de requête, plus le temps de réponse global obtient pour les applications clientes.

![](./media/image15.png)

**Figure 4-15**. Anti-modèles et modèles de communication entre microservices

Si votre microservice doit déclencher une action supplémentaire dans un autre microservice, si possible, n’effectuez pas cette action de façon synchrone et dans le cadre de l’opération de demande et réponse microservice d’origine. Effectuez plutôt de façon asynchrone (à l’aide de la messagerie asynchrone ou les événements d’intégration, les files d’attente, etc.). Toutefois, autant que possible, ne pas appeler l’action de façon synchrone dans le cadre de l’opération de demande et de réponse synchrone d’origine.

Et enfin (et il s’agit d’où la plupart des problèmes surviennent lors de la génération des microservices), si votre microservice initiale nécessite des données qui appartient à l’origine par les autres microservices, ne comptez pas sur effectuant des demandes synchrones pour ces données. Au lieu de cela, répliquer ou propager ces données (uniquement les attributs) dans la base de données du service initial à l’aide de la cohérence éventuelle (généralement par à l’aide des événements d’intégration, comme expliqué dans les prochaines sections).

Comme indiqué précédemment dans la section [identification des limites de modèle de domaine pour chaque microservice](#identifying-domain-model-boundaries-for-each-microservice), duplication des données entre plusieurs microservices n’est pas une conception incorrecte, au contraire, lorsque effectuant que vous pouvez traduire les données dans la langue spécifique ou les termes de ce domaine supplémentaire ou d’un contexte de limitées. Par exemple, dans le [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) application que vous avez un microservice nommé identity.api qui est responsable de la plupart des données de l’utilisateur avec une entité nommée utilisateur. Toutefois, lorsque vous avez besoin stocker les données relatives à l’utilisateur dans le classement microservice, vous le stocker en tant qu’une autre entité nommée acheteur. L’entité de l’acheteur partage la même identité avec l’entité d’utilisateur d’origine, mais il peut avoir uniquement le peu d’attributs requis par le domaine de classement et pas le profil utilisateur entière.

Vous pouvez utiliser n’importe quel protocole de communiquer et de propagation des données de façon asynchrone entre microservices pour disposer de la cohérence éventuelle. Comme mentionné, vous pouvez utiliser les événements d’intégration à l’aide d’un bus d’événements ou d’un message broker, ou vous pouvez même utiliser HTTP en interrogeant les autres services à la place. Il n’a pas d’importance. La règle importante est de ne pas créer de dépendances synchrones entre votre microservices.

Les sections suivantes expliquent les styles de communication plusieurs, que vous pouvez envisager d’utiliser dans une application basée sur un microservice.

## <a name="communication-styles"></a>Styles de communication

Il existe de nombreux protocoles et les choix que vous pouvez utiliser pour la communication, en fonction du type de communication que vous souhaitez utiliser. Si vous utilisez un mécanisme de communication synchrone de demande/réponse de, protocoles tels que HTTP et autres approches sont les plus courantes, notamment si vous publiez vos services hors du cluster hôte ou microservice de Docker. Si vous communiquez entre les services en interne (au sein de votre cluster hôte ou microservices Docker) vous souhaiterez également utiliser les mécanismes de communication de format binaire (par exemple, la communication à distance du Service Fabric ou WCF à l’aide de TCP et au format binaire). Vous pouvez également utiliser les mécanismes de communication asynchrone basée sur message, tels que AMQP.

Il existe également plusieurs message formats comme JSON ou XML, ou même binaire, qui peut être plus efficace. Si votre format binaire choisi n’est pas un standard, il n’est probablement pas judicieux de publiquement publier vos services à l’aide de ce format. Vous pouvez utiliser un format non standard pour la communication interne entre votre microservices. Vous pouvez effectuer cela lors de la communication entre microservices dans votre cluster Docker hôte ou microservice (orchestrators de Docker ou Azure Service Fabric), ou pour les applications clientes propriétaire qui communique avec le microservices.

### <a name="requestresponse-communication-with-http-and-rest"></a>Communication demande/réponse HTTP et REST 

Lorsqu’un client utilise une communication demande/réponse, il envoie une demande à un service, puis le service traite la demande et renvoie une réponse. Communication de demande/réponse est particulièrement bien adaptée pour interroger des données pour une interface utilisateur en temps réel (une interface utilisateur dynamique) à partir d’applications clientes. Par conséquent, dans une architecture de microservice vous allez probablement utiliser ce mécanisme de communication pour la plupart des requêtes, comme indiqué dans la Figure 4-16.

![](./media/image16.png)

**Figure 4-16**. À l’aide de la communication demande/réponse HTTP (synchrone ou asynchrone)

Lorsqu’un client utilise une communication demande/réponse, il suppose que la réponse arriveront dans une courte période, en général moins d’une seconde ou quelques secondes au maximum. Pour les réponses différées, vous devez implémenter la communication asynchrone basée sur [modèles de messagerie](https://docs.microsoft.com/azure/architecture/patterns/category/messaging) et [technologies de messagerie](https://en.wikipedia.org/wiki/Message-oriented_middleware), qui est une approche différente qui nous expliquons dans la section suivante.

Un style populaires architectural pour la communication de demande/réponse est [reste](https://en.wikipedia.org/wiki/Representational_state_transfer). Cette approche est basée sur et étroitement couplée, les [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) de protocole, adoptent les verbes HTTP tels que GET, POST et le placer. REST est l’approche architecturale communication couramment utilisées lors de la création de services. Vous pouvez implémenter des services REST lorsque vous développez des services de l’API Web ASP.NET principale.

A une valeur supplémentaire à l’aide des services HTTP REST comme votre langage de définition d’interface. Par exemple, si vous utilisez [Swagger métadonnées](http://swagger.io/) pour décrire votre API de service, vous pouvez utiliser les outils qui génèrent des stubs de client peuvent directement de détecter et d’utiliser vos services.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Martin Fowler. Richardson Maturity Model.** Description du modèle REST.
    [*http://martinfowler.com/articles/richardsonMaturityModel.HTML*](http://martinfowler.com/articles/richardsonMaturityModel.html)

-   **Swagger.** Le site officiel.
    [*http://swagger.IO/*](http://swagger.io/)

### <a name="push-and-real-time-communication-based-on-http"></a>Push et communication en temps réel basés sur HTTP

Une autre possibilité (généralement fins différentes reste) est une communication un-à-plusieurs et en temps réel avec les infrastructures de niveau supérieur telles que [ASP.NET SignalR](https://www.asp.net/signalr) et protocoles tels que [WebSockets](https://en.wikipedia.org/wiki/WebSocket).

Comme le montre la Figure 4-17, la communication HTTP en temps réel signifie que vous pouvez avoir le code serveur en exécutant un push contenu aux clients connectés à mesure que les données disponibles, au lieu du serveur attendre un client demander de nouvelles données.

![](./media/image17.png)

**Figure 4-17**. Communication d’un message d’asynchrone en temps réel

Étant donné que la communication est en temps réel, les applications clientes affichent les modifications quasiment instantanément. Cela est généralement gérée par un protocole tel que WebSockets, à l’aide de nombreuses connexions WebSocket (un par client). Un exemple classique est lorsqu’un service communique une modification dans le score d’un jeu de sports pour beaucoup d’applications web client simultanément.


>[!div class="step-by-step"]
[Précédente] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) [suivant] (asynchrone-message-base-communication.md)
