---
title: "Implémentation d’un bus d’événements avec RabbitMQ pour l’environnement de développement ou de test"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation d’un bus d’événements avec RabbitMQ pour l’environnement de développement ou de test"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f58d355b6f5fd31a21791d3b072c77f70f90c387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>Implémentation d’un bus d’événements avec RabbitMQ pour l’environnement de développement ou de test

Nous devons commencer en disant que si vous créez votre bus d’événements personnalisés en fonction de RabbitMQ en cours d’exécution dans un conteneur, comme le fait de l’application eShopOnContainers, il doit être utilisé uniquement pour vos environnements de test et de développement. Vous ne devez pas l’utiliser pour votre environnement de production, sauf si vous l’avez créée dans le cadre d’un bus de service de l’environnement de production. Un bus d’événements personnalisé simple peuvent être absentes de nombreuses fonctionnalités critiques opérationnelle qui dispose d’un bus de service commercial.

L’implémentation personnalisée d’eShopOnContainers d’un bus d’événements est essentiellement une bibliothèque à l’aide de l’API RabbitMQ. L’implémentation permet de microservices s’abonner à des événements, de publier des événements et de recevoir des événements, comme indiqué dans la Figure 8-21.

![](./media/image22.png)

**Figure 8-21.** Implémentation de RabbitMQ de bus d’événements

Dans le code, la classe EventBusRabbitMQ implémente l’interface IEventBus générique. Cela est basée sur l’Injection de dépendance afin que vous pouvez permuter à partir de cette version de développement et de test vers une version de production.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

L’implémentation de RabbitMQ d’un bus d’événements de développement/test exemple est un code réutilisable. Il doit gérer la connexion au serveur RabbitMQ et fournissez du code pour la publication d’un événement de message dans les files d’attente. Il doit également implémenter un dictionnaire de collections à l’intégration de gestionnaires d’événements pour chaque type d’événement ; ces types d’événements peuvent avoir une instanciation différente et des abonnements différents pour chaque récepteur microservice, comme indiqué dans la Figure 8-21.

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>Implémentation d’un simple publier avec RabbitMQ (méthode)

Le code suivant fait partie de l’implémentation de bus d’événements eShopOnContainers pour RabbitMQ, généralement, vous n’avez pas besoin pour le code, sauf si vous apportez des améliorations. Le code obtient une connexion et un canal RabbitMQ, crée un message, puis publie le message dans la file d’attente.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

Le [code réel](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de la publier méthode dans l’application eShopOnContainers est améliorée en utilisant un [Polly](https://github.com/App-vNext/Polly) réessayer la stratégie, qui tente de la tâche d’un certain nombre de fois au cas où le conteneur RabbitMQ est n’est pas prêt. Cela peut se produire lorsque de composer docker démarre les conteneurs ; par exemple, le conteneur RabbitMQ peut commencer plus lentement que les autres conteneurs.

Comme mentionné précédemment, il existe plusieurs configurations possibles dans RabbitMQ, donc ce code doit être utilisé uniquement pour les environnements de développement et de test.

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>Implémentation du code de l’abonnement avec l’API RabbitMQ

Comme avec le code de la publication, le code suivant est une simplification de la partie de l’implémentation de bus d’événements pour RabbitMQ. Là encore, généralement inutile pour le modifier, sauf si vous la réduction.

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...
    public void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent
    {
        var eventName = typeof(T).Name;
        if (_handlers.ContainsKey(eventName))
        {
            _handlers[eventName].Add(handler);
        }
        else
        {
            var channel = GetChannel();
            channel.QueueBind(queue: _queueName,
                exchange: _brokerName,
                routingKey: eventName);
            _handlers.Add(eventName, new List<IIntegrationEventHandler>());
            _handlers[eventName].Add(handler);
            _eventTypes.Add(typeof(T));
        }
    }
}
```

Chaque type d’événement a un canal associé pour obtenir les événements à partir de RabbitMQ. Vous pouvez ensuite configurer qu’un grand nombre de gestionnaires d’événements par type de canal et les événements en fonction des besoins.

La méthode Subscribe accepte un objet IIntegrationEventHandler, ce qui ressemble à une méthode de rappel dans le microservice actuel, ainsi que son objet IntegrationEvent connexe. Le code ajoute ensuite ce gestionnaire d’événements à la liste des gestionnaires d’événements qui peut avoir des chaque type d’événement intégration par le client microservice. Si le code client n’est pas déjà abonné à l’événement, le code crée un canal pour le type d’événement afin qu’il peut recevoir des événements dans un style push à partir de RabbitMQ lorsque cet événement est publié à partir de n’importe quel autre service.


>[!div class="step-by-step"]
[Précédente] (intégration-événements-base-microservice-communications.md) [suivant] (events.md s’abonner)
