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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="0ece2-104">Implémentation d’un bus d’événements avec RabbitMQ pour l’environnement de développement ou de test</span><span class="sxs-lookup"><span data-stu-id="0ece2-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="0ece2-105">Nous devons commencer en disant que si vous créez votre bus d’événements personnalisés en fonction de RabbitMQ en cours d’exécution dans un conteneur, comme le fait de l’application eShopOnContainers, il doit être utilisé uniquement pour vos environnements de test et de développement.</span><span class="sxs-lookup"><span data-stu-id="0ece2-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="0ece2-106">Vous ne devez pas l’utiliser pour votre environnement de production, sauf si vous l’avez créée dans le cadre d’un bus de service de l’environnement de production.</span><span class="sxs-lookup"><span data-stu-id="0ece2-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="0ece2-107">Un bus d’événements personnalisé simple peuvent être absentes de nombreuses fonctionnalités critiques opérationnelle qui dispose d’un bus de service commercial.</span><span class="sxs-lookup"><span data-stu-id="0ece2-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="0ece2-108">L’implémentation personnalisée d’eShopOnContainers d’un bus d’événements est essentiellement une bibliothèque à l’aide de l’API RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="0ece2-108">The eShopOnContainers custom implementation of an event bus is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="0ece2-109">L’implémentation permet de microservices s’abonner à des événements, de publier des événements et de recevoir des événements, comme indiqué dans la Figure 8-21.</span><span class="sxs-lookup"><span data-stu-id="0ece2-109">The implementation lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="0ece2-110">**Figure 8-21.**</span><span class="sxs-lookup"><span data-stu-id="0ece2-110">**Figure 8-21.**</span></span> <span data-ttu-id="0ece2-111">Implémentation de RabbitMQ de bus d’événements</span><span class="sxs-lookup"><span data-stu-id="0ece2-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="0ece2-112">Dans le code, la classe EventBusRabbitMQ implémente l’interface IEventBus générique.</span><span class="sxs-lookup"><span data-stu-id="0ece2-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="0ece2-113">Cela est basée sur l’Injection de dépendance afin que vous pouvez permuter à partir de cette version de développement et de test vers une version de production.</span><span class="sxs-lookup"><span data-stu-id="0ece2-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="0ece2-114">L’implémentation de RabbitMQ d’un bus d’événements de développement/test exemple est un code réutilisable.</span><span class="sxs-lookup"><span data-stu-id="0ece2-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="0ece2-115">Il doit gérer la connexion au serveur RabbitMQ et fournissez du code pour la publication d’un événement de message dans les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="0ece2-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="0ece2-116">Il doit également implémenter un dictionnaire de collections à l’intégration de gestionnaires d’événements pour chaque type d’événement ; ces types d’événements peuvent avoir une instanciation différente et des abonnements différents pour chaque récepteur microservice, comme indiqué dans la Figure 8-21.</span><span class="sxs-lookup"><span data-stu-id="0ece2-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="0ece2-117">Implémentation d’un simple publier avec RabbitMQ (méthode)</span><span class="sxs-lookup"><span data-stu-id="0ece2-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="0ece2-118">Le code suivant fait partie de l’implémentation de bus d’événements eShopOnContainers pour RabbitMQ, généralement, vous n’avez pas besoin pour le code, sauf si vous apportez des améliorations.</span><span class="sxs-lookup"><span data-stu-id="0ece2-118">The following code is part of the eShopOnContainers event bus implementation for RabbitMQ, so you usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="0ece2-119">Le code obtient une connexion et un canal RabbitMQ, crée un message, puis publie le message dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="0ece2-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="0ece2-120">Le [code réel](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) de la publier méthode dans l’application eShopOnContainers est améliorée en utilisant un [Polly](https://github.com/App-vNext/Polly) réessayer la stratégie, qui tente de la tâche d’un certain nombre de fois au cas où le conteneur RabbitMQ est n’est pas prêt.</span><span class="sxs-lookup"><span data-stu-id="0ece2-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="0ece2-121">Cela peut se produire lorsque de composer docker démarre les conteneurs ; par exemple, le conteneur RabbitMQ peut commencer plus lentement que les autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="0ece2-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="0ece2-122">Comme mentionné précédemment, il existe plusieurs configurations possibles dans RabbitMQ, donc ce code doit être utilisé uniquement pour les environnements de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="0ece2-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="0ece2-123">Implémentation du code de l’abonnement avec l’API RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="0ece2-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="0ece2-124">Comme avec le code de la publication, le code suivant est une simplification de la partie de l’implémentation de bus d’événements pour RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="0ece2-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="0ece2-125">Là encore, généralement inutile pour le modifier, sauf si vous la réduction.</span><span class="sxs-lookup"><span data-stu-id="0ece2-125">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="0ece2-126">Chaque type d’événement a un canal associé pour obtenir les événements à partir de RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="0ece2-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="0ece2-127">Vous pouvez ensuite configurer qu’un grand nombre de gestionnaires d’événements par type de canal et les événements en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="0ece2-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="0ece2-128">La méthode Subscribe accepte un objet IIntegrationEventHandler, ce qui ressemble à une méthode de rappel dans le microservice actuel, ainsi que son objet IntegrationEvent connexe.</span><span class="sxs-lookup"><span data-stu-id="0ece2-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="0ece2-129">Le code ajoute ensuite ce gestionnaire d’événements à la liste des gestionnaires d’événements qui peut avoir des chaque type d’événement intégration par le client microservice.</span><span class="sxs-lookup"><span data-stu-id="0ece2-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="0ece2-130">Si le code client n’est pas déjà abonné à l’événement, le code crée un canal pour le type d’événement afin qu’il peut recevoir des événements dans un style push à partir de RabbitMQ lorsque cet événement est publié à partir de n’importe quel autre service.</span><span class="sxs-lookup"><span data-stu-id="0ece2-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0ece2-131">[Précédente] (intégration-événements-base-microservice-communications.md) [suivant] (events.md s’abonner)</span><span class="sxs-lookup"><span data-stu-id="0ece2-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
