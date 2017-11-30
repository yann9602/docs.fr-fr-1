---
title: "Implémentation de la couche d’application microservice à l’aide de l’API Web"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Implémentation de la couche d’application microservice à l’aide de l’API Web"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>Implémentation de la couche d’application microservice à l’aide de l’API Web

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>À l’aide de l’Injection de dépendances d’injecter des objets de l’infrastructure dans votre couche application

Comme mentionné précédemment, la couche application peut être implémentée en tant que partie de l’artefact que vous générez, tel qu’au sein d’un projet d’API Web ou un projet d’application web MVC. Dans le cas d’un microservice généré avec ASP.NET Core, la couche application aura votre bibliothèque d’API Web. Si vous souhaitez séparer les nouveautés à venir à partir de ASP.NET (son infrastructure plus vos contrôleurs) à partir de votre code de couche application personnalisée, vous pouvez également placer votre couche application dans une bibliothèque de classes distinct, mais qui est facultatif.

Par exemple, le code de couche application de la commande microservice est implémenté directement dans le cadre de la **Ordering.API** projet (un projet de l’API Web ASP.NET principale), comme indiqué dans la Figure 9-19.

![](./media/image20.png)

**Figure 9-19**. La couche d’application dans le projet Ordering.API ASP.NET Core Web API

ASP.NET Core inclut un simple [conteneur inversion de contrôle prédéfini](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (représenté par l’interface IServiceProvider) qui prend en charge d’injection de constructeur par défaut, et ASP.NET rend certains services disponibles via DI. ASP.NET Core utilise le terme *service* pour les types qui seront injectées par DI vous inscrivez. Vous configurez les services du conteneur intégré dans la méthode ConfigureServices dans la classe de démarrage de votre application. Les dépendances sont implémentés dans les services nécessaires à un type.

En règle générale, vous voulez injecter des dépendances qui implémentent des objets de l’infrastructure. Une dépendance très courant pour injecter est un référentiel. Mais vous pouvez injecter n’importe quel autre dépendance d’infrastructure que vous pouvez rencontrer. Pour des implémentations plus simples, vous pouvez directement injecter la votre objet de modèle d’unité de travail (l’objet DbContext EF), car le DBContext est également l’implémentation de vos objets de persistance d’infrastructure.

Dans l’exemple suivant, vous pouvez voir comment le .NET Core injecte les objets de référentiel requis par le biais du constructeur. La classe est un gestionnaire de commandes, nous allons aborder, dans la section suivante.

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

La classe utilise les référentiels injectées d’exécuter la transaction et de conserver les modifications d’état. Il n’a pas d’importance si cette classe est un gestionnaire de commandes, une méthode de contrôleur de l’API Web ASP.NET principale, ou un [Service d’Application DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Il est finalement une classe simple qui utilise des référentiels, des entités de domaine et coordination des autres applications de manière similaire à un gestionnaire de commandes. Dépendance d’Injection exploite la même manière pour toutes les classes mentionnées, comme dans l’exemple à l’aide de DI le constructeur.

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Inscrire les types de mise en œuvre des dépendances et les interfaces ou les abstractions

Avant d’utiliser les objets injectées par les constructeurs, vous devez savoir où enregistrer les interfaces et les classes qui produisent les objets injectés dans vos classes d’application via DI. (Comme DI basé sur le constructeur, comme indiqué précédemment.)

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>L’aide du conteneur inversion de contrôle intégré fourni par ASP.NET Core

Lorsque vous utilisez le conteneur inversion de contrôle intégré fourni par ASP.NET Core, vous inscrivez les types que vous souhaitez insérer dans la méthode ConfigureServices dans le fichier Startup.cs, comme dans le code suivant :

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

Le modèle le plus courant lors de l’inscription des types dans un conteneur inversion de contrôle consiste à inscrire des deux types : une interface et sa classe de mise en œuvre associée. Ensuite, lorsque vous demandez un objet à partir du conteneur inversion de contrôle via tout autre constructeur, vous demandez un objet d’un certain type d’interface. Par exemple, dans l’exemple précédent, la dernière ligne indique que lorsqu’un des constructeurs de votre ont une dépendance sur IMyCustomRepository (interface ou abstraction), le conteneur IoC injecter une instance de l’implémentation de MyCustomSQLServerRepository classe.

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>À l’aide de la bibliothèque Scrutor pour l’inscription des types automatique

Lorsque vous utilisez DI dans .NET Core, vous souhaiterez peut-être être en mesure d’analyser un assembly et inscrire automatiquement ses types par convention. Cette fonctionnalité n’est pas actuellement disponible dans ASP.NET Core. Toutefois, vous pouvez utiliser la [Scrutor](https://github.com/khellang/Scrutor) bibliothèque correspondant. Cette approche est pratique lorsque vous avez des dizaines de types qui doivent être inscrits dans votre conteneur inversion de contrôle.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Matthew ROI. Inscription des services avec Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang. Scrutor.** Référentiel GitHub.
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>À l’aide de Autofac comme un conteneur inversion de contrôle

Vous pouvez également utiliser d’autres conteneurs d’inversion de contrôle et les incorporer dans le pipeline ASP.NET Core, comme dans l’ordre de tri microservice dans eShopOnContainers, qui utilise [Autofac](https://autofac.org/). Lorsque vous utilisez Autofac vous inscrire en général, les types via des modules, ce qui vous permet de fractionner les types d’enregistrements entre plusieurs fichiers en fonction de l’avancement de vos types, tout comme vous pourriez avoir les types d’applications distribuées sur plusieurs bibliothèques de classes.

Par exemple, ce qui suit est la [module d’application Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pour le [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projet avec les types que vous pouvez injecter.

```csharp
public class ApplicationModule
    :Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

Le processus d’inscription et les concepts sont très similaires à la façon dont vous pouvez inscrire les types avec le conteneur d’iOS ASP.NET Core intégré, mais la syntaxe lors de l’utilisation de Autofac est un peu différente.

Dans l’exemple de code, l’abstraction IOrderRepository est enregistrée en même temps que la classe d’implémentation OrderRepository. Cela signifie que chaque fois qu’un constructeur déclare une dépendance par l’interface ou IOrderRepository abstraction, le conteneur IoC injecter une instance de la classe OrderRepository.

Le type d’instance étendue détermine la façon dont une instance est partagée entre les demandes de service ou une dépendance. Lorsqu’une demande est faite pour une dépendance, le conteneur inversion de contrôle peut retourner les éléments suivants :

-   Une instance unique par l’étendue de la durée de vie (dans le conteneur inversion de contrôle ASP.NET Core comme *étendue*).

-   Une nouvelle instance par dépendance (dans le conteneur inversion de contrôle ASP.NET Core comme *temporaire*).

-   Une seule instance partagée entre tous les objets à l’aide du conteneur inversion de contrôle (dans le conteneur inversion de contrôle ASP.NET Core comme *singleton*).

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Introduction à l’Injection de dépendances dans ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac.** Documentation officielle.
    [*http://docs.autofac.org/en/Latest/*](http://docs.autofac.org/en/latest/)

-   **Cesar de la Torre. Comparaison des durées de vie du service ASP.NET Core IoC conteneur avec des étendues d’instance Autofac IoC conteneur**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>Implémenter des modèles de commande et le Gestionnaire de commandes

Dans l’exemple DI via ce constructeur est indiqué dans la section précédente, le conteneur inversion de contrôle a été injecter des référentiels via un constructeur dans une classe. Mais exactement où ont été ils injectés ? Dans une API Web simple (par exemple, le catalogue microservice dans eShopOnContainers), vous les injectez au niveau des contrôleurs MVC, dans un constructeur de contrôleur. Toutefois, dans le code initial de cette section (la [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) classe à partir du service Ordering.API dans eShopOnContainers), l’injection de dépendances est effectuée via le constructeur d’une commande spécifique Gestionnaire. Nous expliquer ce qu’est un gestionnaire de commandes et la raison pour laquelle vous pouvez l’utiliser.

Le modèle de commande est intrinsèquement lié au modèle CQRS introduite plus haut dans ce guide. CQRS comporte deux parties. La première zone est requêtes, à l’aide de requêtes simplifiés avec la [Dapper](https://github.com/StackExchange/dapper-dot-net) ORM micro, ce qui a été expliqué précédemment. La deuxième zone est commandes, qui sont le point de départ pour les transactions et le canal d’entrée à partir d’en dehors du service.

Comme indiqué dans la Figure 9-20, le modèle est basé sur l’acceptation des commandes à partir du côté client, le traitement en fonction des règles du modèle de domaine et enfin persistantes les États des transactions.

![](./media/image21.png)

**Figure 9-20**. Vue d’ensemble des commandes ou « côté transactionnelle » dans un modèle CQRS

### <a name="the-command-class"></a>La classe de commande

Une commande est une demande au système effectuer une action qui modifie l’état du système. Commandes sont impératifs et doivent être traités en une seule fois.

Étant donné que les commandes sont impératifs, ils sont généralement nommés avec un verbe d’humeur impératif (par exemple, « créer » ou « update »), et incluent le type d’agrégation, telles que CreateOrderCommand. Contrairement à un événement, une commande n’est pas fait précédemment ; Il est uniquement une demande et donc ne peut être refusée.

Commandes peuvent provenir de l’interface utilisateur à la suite d’un utilisateur qui démarre une demande ou à partir d’un gestionnaire de processus lorsque le Gestionnaire de processus dirige un agrégat pour exécuter une action.

Une caractéristique importante d’une commande est qu’il doit être traité une seule fois par un destinataire unique. Il s’agit d’une commande étant une seule action ou une transaction à effectuer dans l’application. Par exemple, la même commande de création de commande ne doit pas traitée plusieurs fois. Il s’agit d’une différence importante entre les commandes et les événements. Les événements peuvent être traitées plusieurs fois, car de nombreux systèmes ou microservices d’intéresser l’événement.

En outre, il est important de traiter une commande qu’une seule fois d’au cas où la commande n’est pas idempotentes. Une commande est idempotente si elle peut être exécutée plusieurs fois sans modifier le résultat, soit en raison de la nature de la commande, soit en raison de la manière dont le système gère la commande.

Il est recommandé de rendre vos commandes d’et idempotent des mises à jour quand il est judicieux sous règles d’entreprise de votre domaine et les invariants. Par exemple, pour utiliser le même exemple, si pour une raison quelconque (logique de nouvelle tentative de piratage, etc.) la même commande CreateOrder atteint votre système plusieurs fois, vous devez être en mesure d’identifier et assurez-vous que vous ne créez pas plusieurs commandes. Pour ce faire, vous devez attacher un type d’identité dans les opérations et de déterminer si la commande ou la mise à jour a déjà été traité.

Vous envoyez une commande à un seul destinataire ; Vous ne publiez pas une commande. La publication est pour les événements d’intégration qui fait de l’état — que quelque chose s’est produit et qu’il peut être intéressant pour les récepteurs d’événements. Dans le cas d’événements, l’éditeur n’a aucun problème sur les récepteurs d’obtiennent l’événement ou qu’ils le faire. Mais les événements d’intégration sont un autre article déjà été présentée dans les sections précédentes.

Une commande est implémentée avec une classe qui contient des champs de données ou des regroupements avec toutes les informations qui est nécessaire pour exécuter cette commande. Une commande est un type spécial de données transfert objet (DTO), qui est utilisé spécifiquement pour demander des modifications ou des transactions. La commande elle-même est basée sur exactement les informations nécessaires pour le traitement de la commande et rien de plus.

L’exemple suivant montre la classe CreateOrderCommand simplifiée. Il s’agit d’une commande immuable qui est utilisée dans l’ordre de tri microservice dans eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

En fait, la classe de commande contient toutes les données que vous avez besoin pour effectuer une transaction commerciale en utilisant les objets de modèle de domaine. Par conséquent, les commandes sont simplement des structures de données qui contiennent des données en lecture seule et pas de comportement. Nom de la commande indique son objectif. Dans de nombreux langages tels que C\#, les commandes sont représentés en tant que classes, mais ils ne sont pas des classes trues dans le sens réel et orienté objet.

Comme le des caractéristiques supplémentaires, les commandes sont immuables, car l’utilisation attendue est qu’ils sont traités directement par le modèle de domaine. Ils n’avez pas besoin de changer au cours de leur durée de vie prévue. Dans un C\# (classe), que l’immuabilité peut être obtenue en n’ayant ne pas toutes les méthodes setter ou autres méthodes qui modifient l’état interne.

Par exemple, la classe de commande pour la création d’une commande est probablement similaire en termes de données à la commande que vous souhaitez créer, mais vous n’avez probablement pas besoin les mêmes attributs. Par exemple, CreateOrderCommand n’a pas un ID de commande, car l’ordre n’a pas encore été créé.

De nombreuses classes de commande peuvent être simples, il nécessite que quelques champs sur un état qui doit être modifiée. Ce serait le cas si vous modifiez simplement l’état d’une commande à partir de « en cours » à « payé » ou « livré » à l’aide d’une commande semblable à la suivante :

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

Certains développeurs rendre leurs objets de requête de l’interface utilisateur distinct à partir de leurs données de commande, mais qui est simplement une question de préférence. Il s’agit d’une séparation fastidieuse à pas de valeur ajoutée, et les objets sont presque exactement la même forme. Par exemple, dans eShopOnContainers, les commandes sont fournis directement à partir du client.

### <a name="the-command-handler-class"></a>La classe de gestionnaire de commandes

Vous devez implémenter une classe de gestionnaire de commande spécifique pour chaque commande. Comment le modèle fonctionne, et il est où vous allez utiliser l’objet de commande, les objets de domaine et les objets de référentiel d’infrastructure. Le Gestionnaire de commandes est en fait le cœur de la couche d’application en termes de CQRS et DDD. Toutefois, toute la logique de domaine doit être contenue dans les classes de domaine, dans les racines d’agrégation (entités racine), les entités enfants, ou [services de domaine](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mais pas dans le Gestionnaire de commandes, qui est une classe à partir de l’application couche.

Un gestionnaire de commandes reçoit une commande et obtient un résultat à partir de l’agrégat qui est utilisé. Le résultat doit être l’exécution réussie de la commande, ou une exception. En cas d’exception, l’état du système doit être inchangée.

Le Gestionnaire de commandes prend généralement les étapes suivantes :

-   Il reçoit l’objet de commande, comme un DTO (à partir de la [médiateur](https://en.wikipedia.org/wiki/Mediator_pattern) ou un autre objet de l’infrastructure).

-   Il vérifie que la commande est valide (le cas ne pas validé par le médiateur).

-   Il instancie l’instance racine d’agrégation qui est la cible de la commande actuelle.

-   Il exécute la méthode sur l’instance racine d’agrégat, obtenir les données requises à partir de la commande.

-   Il conserve le nouvel état de l’agrégat pour sa base de données connexe. Cette dernière opération est la transaction réelle.

En règle générale, un gestionnaire de commandes porte sur un agrégat unique dus à la racine d’agrégation (entité racine). Si plusieurs agrégats doivent être affectées par la réception d’une commande unique, vous pouvez utiliser des événements de domaine pour propager des États ou des actions sur plusieurs agrégats

Le point important ici est que lorsqu’une commande est en cours de traitement, la logique de domaine doit être au sein du modèle de domaine (agrégation), entièrement encapsulé et prêt pour les tests unitaires. Le Gestionnaire de commandes sert simplement un moyen d’obtenir le modèle de domaine à partir de la base de données et l’étape finale, pour indiquer à la couche d’infrastructure (référentiels) pour conserver les modifications lorsque le modèle est modifié. L’avantage de cette approche est que vous pouvez refactoriser la logique de domaine dans un modèle de domaine isolé, entièrement encapsulé, enrichi, comportement sans modifier le code dans l’application ou les couches d’infrastructure, qui sont le niveau de plomberie (gestionnaires de commandes, l’API Web, référentiels, etc.).

Lorsque les gestionnaires de commandes obtenir complexes, avec trop de logique, ce qui peut être une odeur de code. Passez en revue les et si vous trouvez la logique de domaine, refactoriser le code pour déplacer ce comportement de domaine pour les méthodes des objets de domaine (le regroupement racine et enfant entity).

Un exemple d’une classe de gestionnaire de commande, le code suivant montre la même classe CreateOrderCommandHandler que vous avez vu au début de ce chapitre. Dans ce cas nous avons mis en surbrillance la méthode Handle et les opérations avec les objets de modèle de domaine/agrégats.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

Il s’agit d’un gestionnaire de commandes devez suivre des étapes supplémentaires :

-   Utilisez les données de la commande fonctionne avec les méthodes et le comportement de la racine d’agrégation.

-   En interne dans les objets de domaine, déclencher des événements de domaine lors de la transaction est exécutée, mais qui est transparente à partir d’un point de vue de commande Gestionnaire.

-   Si le résultat de l’agrégat de l’opération a réussi, et une fois la transaction terminée, déclencher le Gestionnaire de commandes d’événements integration. (Il peuvent également être levée par les classes d’infrastructure tels que les référentiels.)

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Mark Seemann. Dans les limites, les Applications sont orientés objet pas**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, orienté sur ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **Commandes et les événements**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **À quoi un gestionnaire de commandes ? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard. Modèles de commande du domaine – gestionnaires**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard. Modèles de commande du domaine – Validation**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Le pipeline de processus de commande : le déclenchement d’un gestionnaire de commandes

La question suivante consiste à appeler un gestionnaire de commandes. Vous pouvez l’appeler manuellement à partir de chaque contrôleur ASP.NET Core connexe. Toutefois, l’approche serait trop couplé et n’est pas idéale.

Les autres deux options principales, qui sont les options recommandées, sont :

-   Via un artefact de modèle médiateur en mémoire.

-   Avec une file d’attente message asynchrone, entre les contrôleurs et les gestionnaires.

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Utilisation du modèle de médiateur (mémoire) dans le pipeline de commande

Comme indiqué dans la Figure 9-21, dans une approche CQRS, vous utilisez un médiateur intelligent, similaire à un bus en mémoire, ce qui est assez intelligent pour rediriger vers le Gestionnaire de commande appropriée en fonction du type de la commande DTO reçus. Les flèches noires uniques entre les composants représentent les dépendances entre les objets (dans de nombreux cas, injectés via DI) avec leurs interactions associées.

![](./media/image22.png)

**Figure 9-21**. Utilisation du modèle de médiateur dans le processus dans un microservice CQRS unique

La raison pour laquelle l’utilisation du modèle de médiateur de sens est que dans les applications d’entreprise, les demandes de traitement peuvent se compliquer. Vous souhaitez être en mesure d’ajouter un nombre ouvert de problèmes transversaux comme la journalisation, validations, d’audit et de sécurité. Dans ce cas, vous pouvez compter sur un pipeline de médiateur (consultez [modèle de médiateur](https://en.wikipedia.org/wiki/Mediator_pattern)) pour fournir un moyen de ces comportements supplémentaires ou des problèmes transversaux.

Médiateur est un objet qui encapsule le « comment » de ce processus : Il coordonne l’exécution basée sur l’état, la façon un gestionnaire de commandes est appelée ou la charge utile de fournir au gestionnaire. Avec un composant de médiateur vous pouvez appliquer des problèmes transversaux de manière centralisée et transparente en appliquant des éléments décoratifs (ou [pipeline comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) depuis médiateur v3). (Pour plus d’informations, consultez la [modèle d’élément décoratif](https://en.wikipedia.org/wiki/Decorator_pattern).)

Éléments décoratifs et les comportements sont semblables aux [de programmation orientée Aspect (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), uniquement être appliquée à un pipeline de processus spécifique géré par le composant de médiateur. Aspects dans AOP qui implémentent des problèmes transversaux sont appliquées selon *Tisseurs d’aspect* injecté au moment de la compilation ou en fonction d’interception des appels. Les deux approches AOP classiques sont considérés comme parfois fonctionne « comme par magie », car il n’est pas facile de voir comment AOP effectue son travail. Lorsque vous traitez des problèmes graves ou des bogues, AOP peut être difficile à déboguer. En revanche, ces éléments décoratifs/comportements étant explicite et appliquées uniquement dans le contexte de la médiateur, le débogage est beaucoup plus prévisible et plus facile.

Par exemple, dans l’ordre de microservice eShopOnContainers, nous avons implémenté deux décorateurs d’exemple, un [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe et un [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe. Mise en œuvre de l’élément décoratif est expliquée dans la section suivante. Notez que dans une version ultérieure, eShopOnContainers la faire migrer vers [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) et déplacer vers [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) au lieu d’utiliser des éléments décoratifs.

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>Dans le pipeline de la commande à l’aide de files d’attente de message (out-of-process)

Un autre choix consiste à utiliser des messages asynchrones selon les courtiers et les files d’attente de messages, comme indiqué dans la Figure 9-22. Cette option peut aussi être combinée avec le composant de médiateur juste avant le Gestionnaire de commandes.

![](./media/image23.png)

**Figure 9-22**. À l’aide de files d’attente de message (hors processus et la communication interprocessue) avec les commandes CQRS

À l’aide de files d’attente pour accepter que les commandes peuvent être plus compliquent le pipeline de votre commande, de message, car vous devrez probablement divisez le pipeline en deux processus connecté via la file d’attente de message externe. Toujours, elle doit être utilisée si vous avez besoin ont amélioré les performances en fonction de la messagerie asynchrone et l’extensibilité. Tenez compte des points dans le cas de Figure 9-22, le contrôleur simplement publie le message de commande dans la file d’attente et retourne. Ensuite, les gestionnaires de commandes traitent les messages à leur propre rythme. Autrement dit un énorme avantage des files d’attente, la file d’attente peut agir comme une mémoire tampon dans le cas lorsque l’extensibilité hyper est nécessaire, par exemple pour des stocks ou tout autre scénario un important volume de données entrantes.

Toutefois, en raison de la nature asynchrone des files d’attente, vous devez déterminer comment communiquer avec l’application cliente sur la réussite ou l’échec du processus de la commande. En règle générale, vous devez jamais utiliser les commandes « fire and forget ». Chaque application d’entreprise doit savoir si une commande a été traitée correctement, ou au moins validée et acceptée.

Par conséquent, être en mesure de répondre au client après la validation d’un message de commande qui a été soumis à une file d’attente asynchrone ajoute une complexité à votre système, par rapport à un processus de commande de processus qui retourne le résultat de l’opération après l’exécution de la transaction. À l’aide de files d’attente, vous devrez peut-être renvoyer les résultats du processus de commande via d’autres messages de résultat d’opération, qui nécessite des composants supplémentaires et communication personnalisées dans votre système.

En outre, les commandes d’async sont les commandes unidirectionnels qui, dans de nombreux cas, peut ne pas être nécessaire, comme indiqué dans l’échange suivant intéressante entre Burtsev Alexey et Greg Young dans un [conversation en ligne](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\] rechercher une grande quantité de code où les personnes utilisent la gestion des commandes d’async ou une commande monodirectionnelle messagerie sans une raison quelconque pour ce faire (ils n’effectuent pas une opération longue, ils n’exécutent pas de code asynchrone externe, qu’elles ne traversent pas encore d’application limite à l’utilisation de bus de messages). Pourquoi ils introduisent cette complexité inutile ? Et en fait, je n’ai vu un exemple de code CQRS avec le blocage des gestionnaires de commandes jusqu'à présent, si elle fonctionne correctement dans la plupart des cas.

\[Greg Young\] \[... \] n’existe pas une commande asynchrone ; il s’agit en fait un autre événement. Si je dois accepter ce que vous m’envoyez et déclencher un événement si je n’accepte pas, il n’est plus vous m’indiquant d’effectuer une action. Il est vous m’indiquant qu'un élément a été effectué. Cela semble être une légère différence dans un premier temps, mais il a des implications en matière de nombre.

Commandes asynchrones augmentent considérablement la complexité d’un système, car il n’existe aucun moyen simple d’indiquent des échecs. Par conséquent, commandes asynchrones sont déconseillées autre que lors de la mise à l’échelle est nécessaires ou dans des cas spéciaux lors de la communication du microservices interne via la messagerie. Dans ce cas, vous devez concevoir un système de création de rapports et de récupération distinct pour les échecs.

Dans la version initiale d’eShopOnContainers, nous avons décidé d’utiliser le traitement des commandes synchrones, démarré à partir de requêtes HTTP et piloté par le modèle de médiateur. Qui permet de facilement vous permet de retourner la réussite ou l’échec du processus, comme dans le [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) mise en œuvre.

Dans tous les cas, cela doit être une décision basée sur les besoins de votre application ou une de microservice.

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Mise en œuvre le pipeline de processus de commande avec un modèle de médiateur (MediatR)

Comme un exemple d’implémentation, ce guide propose à l’aide du pipeline de processus basée sur le modèle de médiateur de réception de commande de lecteur et le routage, dans la mémoire, les gestionnaires de commandes à droite. Le guide propose également l’application des éléments décoratifs ou [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) afin de séparer les problèmes transversaux.

Plusieurs bibliothèques d’open source disponibles qui implémentent le modèle de médiateur sont pour l’implémentation du .NET Core. La bibliothèque utilisée dans ce guide est le [MediatR](https://github.com/jbogard/MediatR) bibliothèque open source (créée par Jimmy Bogard), mais vous pouvez utiliser une autre approche. MediatR est une bibliothèque de petite et simple qui permet de traiter les messages en mémoire comme une commande, lors de l’application des éléments décoratifs ou des comportements.

L’utilisation du modèle de médiateur vous aide à réduire le couplage et pour isoler les problèmes de la tâche demandée, lors de la connexion automatique au gestionnaire qui effectue ce travail, dans ce cas, aux gestionnaires de commandes.

Une autre bonne raison d’utiliser le modèle de médiateur a été expliquée par Jimmy Bogard lors de la consultation de ce guide :

Je pense qu’il peut être intéressant de mentionner test ici : il fournit une fenêtre de cohérente intéressante dans le comportement de votre système. Demande, hors de la réponse. Nous avons trouvé cet aspect très utiles dans le bâtiment comporte toujours des tests.

Tout d’abord, nous examinons pour le code du contrôleur où vous pouvez réellement utiliser l’objet de médiateur. Si vous n’utilisiez pas l’objet de médiateur, vous devez insérer toutes les dépendances de ce contrôleur, un objet de l’enregistreur d’événements et des autres. Par conséquent, le constructeur serait relativement complexe. En revanche, si vous utilisez l’objet médiateur, le constructeur de votre contrôleur peut être beaucoup plus simple, avec seulement quelques dépendances plutôt que de nombreuses dépendances que vous devriez si vous aviez un par opération composites, comme dans l’exemple suivant :

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

Vous pouvez voir que le médiateur fournit un constructeur de contrôleur Web API propre et lean. En outre, dans les méthodes de contrôleur, le code d’envoyer une commande à l’objet médiateur est presque une seule ligne :

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

Dans l’ordre pour MediatR connaître vos classes de gestionnaire de commandes, vous devez inscrire les classes de médiateur et les classes de gestionnaire de commande dans votre conteneur inversion de contrôle. Par défaut, MediatR utilise Autofac comme conteneur d’inversion de contrôle, mais vous pouvez également utiliser le conteneur inversion de contrôle ASP.NET Core prédéfini ou tout autre conteneur pris en charge par MediatR.

Le code suivant montre comment inscrire les types et les commandes de médiateur lors de l’utilisation des modules de Autofac.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

Étant donné que chaque gestionnaire de commandes implémente l’interface générique IAsyncRequestHandler&lt;T&gt; et puis inspecte le RegisteredAssemblyTypes de l’objet, le gestionnaire est en mesure de lier chaque commande avec son gestionnaire de commandes, car qui relation est indiquée dans la classe CommandHandler, comme dans l’exemple suivant :

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Voici le code qui met en corrélation les commandes avec les gestionnaires de commandes. Le gestionnaire est simplement une classe simple, mais elle hérite RequestHandler&lt;T&gt;, et MediatR permet de s’assurer qu’il est appelé avec la charge utile correcte.

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>Application des problèmes transversaux lors du traitement de commandes avec les modèles de médiateur et Decorator

Il existe une dernière chose : d’appliquer des problèmes transversaux au pipeline médiateur. Vous pouvez également afficher à la fin du code de module d’enregistrement Autofac comment il inscrit un décorateur de type, plus précisément, une classe LogDecorator personnalisée.

Là encore, notez qu’une future version d’eShopOnContainers il migre vers [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) et déplacer vers [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) au lieu d’utiliser des éléments décoratifs.

Que [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe peut être implémentée en tant que le code suivant, qui enregistre des informations sur le Gestionnaire de commandes en cours d’exécution et si elle a réussi ou non.

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

L’implémentation de cette classe decorator et en décorant le pipeline avec lui, toutes les commandes traitées via MediatR seront connecté plus d’informations sur l’exécution.

L’eShopOnContainers classement microservice s’applique également un deuxième decorator pour les validations de base, le [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe qui s’appuie sur le [FluentValidation](https://github.com/JeremySkinner/FluentValidation) bibliothèque, comme indiqué dans les code suivant :

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

Ensuite, selon le [FluentValidation](https://github.com/JeremySkinner/FluentValidation) bibliothèque, nous avons créé la validation pour les données passées avec CreateOrderCommand, comme dans le code suivant :

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}
```

Vous pouvez créer des validations supplémentaires. Il s’agit d’un moyen très propre et élégant pour implémenter vos validations de commande.

De la même façon, vous pouvez implémenter d’autres décorateurs pour des aspects supplémentaires ou des problèmes transversaux que vous souhaitez appliquer aux commandes lors de leur traitement.

#### <a name="additional-resources"></a>Ressources supplémentaires

##### <a name="the-mediator-pattern"></a>Le modèle de médiateur

-   **Modèle de médiateur**
    [*https://en.wikipedia.org/wiki/Mediator\_modèle*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Le modèle d’élément décoratif

-   **Modèle d’élément décoratif**
    [*https://en.wikipedia.org/wiki/Decorator\_modèle*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR.** Référentiel GitHub.
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **CQRS avec MediatR et AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **Placer vos contrôleurs un régime : publications et les commandes. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **Résolution des problèmes transversaux avec un pipeline médiateur**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS et reste : la solution idéale**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **Exemples de Pipeline de MediatR**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **Contextes de Test de tranche verticale pour MediatR et ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **Extensions MediatR pour l’Injection de dépendance de Microsoft publié**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Validation Fluent

-   **Jeremy Skinner. FluentValidation.** Référentiel GitHub.
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[Précédente] (microservice-application-layer-web-api-design.md) [suivant] (.. /Implement-RESILIENT-applications/index.MD)
