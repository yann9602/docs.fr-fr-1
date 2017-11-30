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
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="be73f-104">Implémentation de la couche d’application microservice à l’aide de l’API Web</span><span class="sxs-lookup"><span data-stu-id="be73f-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="be73f-105">À l’aide de l’Injection de dépendances d’injecter des objets de l’infrastructure dans votre couche application</span><span class="sxs-lookup"><span data-stu-id="be73f-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="be73f-106">Comme mentionné précédemment, la couche application peut être implémentée en tant que partie de l’artefact que vous générez, tel qu’au sein d’un projet d’API Web ou un projet d’application web MVC.</span><span class="sxs-lookup"><span data-stu-id="be73f-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="be73f-107">Dans le cas d’un microservice généré avec ASP.NET Core, la couche application aura votre bibliothèque d’API Web.</span><span class="sxs-lookup"><span data-stu-id="be73f-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="be73f-108">Si vous souhaitez séparer les nouveautés à venir à partir de ASP.NET (son infrastructure plus vos contrôleurs) à partir de votre code de couche application personnalisée, vous pouvez également placer votre couche application dans une bibliothèque de classes distinct, mais qui est facultatif.</span><span class="sxs-lookup"><span data-stu-id="be73f-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="be73f-109">Par exemple, le code de couche application de la commande microservice est implémenté directement dans le cadre de la **Ordering.API** projet (un projet de l’API Web ASP.NET principale), comme indiqué dans la Figure 9-19.</span><span class="sxs-lookup"><span data-stu-id="be73f-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="be73f-110">**Figure 9-19**.</span><span class="sxs-lookup"><span data-stu-id="be73f-110">**Figure 9-19**.</span></span> <span data-ttu-id="be73f-111">La couche d’application dans le projet Ordering.API ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="be73f-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="be73f-112">ASP.NET Core inclut un simple [conteneur inversion de contrôle prédéfini](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (représenté par l’interface IServiceProvider) qui prend en charge d’injection de constructeur par défaut, et ASP.NET rend certains services disponibles via DI.</span><span class="sxs-lookup"><span data-stu-id="be73f-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="be73f-113">ASP.NET Core utilise le terme *service* pour les types qui seront injectées par DI vous inscrivez.</span><span class="sxs-lookup"><span data-stu-id="be73f-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="be73f-114">Vous configurez les services du conteneur intégré dans la méthode ConfigureServices dans la classe de démarrage de votre application.</span><span class="sxs-lookup"><span data-stu-id="be73f-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="be73f-115">Les dépendances sont implémentés dans les services nécessaires à un type.</span><span class="sxs-lookup"><span data-stu-id="be73f-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="be73f-116">En règle générale, vous voulez injecter des dépendances qui implémentent des objets de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="be73f-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="be73f-117">Une dépendance très courant pour injecter est un référentiel.</span><span class="sxs-lookup"><span data-stu-id="be73f-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="be73f-118">Mais vous pouvez injecter n’importe quel autre dépendance d’infrastructure que vous pouvez rencontrer.</span><span class="sxs-lookup"><span data-stu-id="be73f-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="be73f-119">Pour des implémentations plus simples, vous pouvez directement injecter la votre objet de modèle d’unité de travail (l’objet DbContext EF), car le DBContext est également l’implémentation de vos objets de persistance d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="be73f-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="be73f-120">Dans l’exemple suivant, vous pouvez voir comment le .NET Core injecte les objets de référentiel requis par le biais du constructeur.</span><span class="sxs-lookup"><span data-stu-id="be73f-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="be73f-121">La classe est un gestionnaire de commandes, nous allons aborder, dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="be73f-121">The class is a command handler, which we will cover in the next section.</span></span>

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

<span data-ttu-id="be73f-122">La classe utilise les référentiels injectées d’exécuter la transaction et de conserver les modifications d’état.</span><span class="sxs-lookup"><span data-stu-id="be73f-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="be73f-123">Il n’a pas d’importance si cette classe est un gestionnaire de commandes, une méthode de contrôleur de l’API Web ASP.NET principale, ou un [Service d’Application DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="be73f-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="be73f-124">Il est finalement une classe simple qui utilise des référentiels, des entités de domaine et coordination des autres applications de manière similaire à un gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="be73f-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="be73f-125">Dépendance d’Injection exploite la même manière pour toutes les classes mentionnées, comme dans l’exemple à l’aide de DI le constructeur.</span><span class="sxs-lookup"><span data-stu-id="be73f-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="be73f-126">Inscrire les types de mise en œuvre des dépendances et les interfaces ou les abstractions</span><span class="sxs-lookup"><span data-stu-id="be73f-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="be73f-127">Avant d’utiliser les objets injectées par les constructeurs, vous devez savoir où enregistrer les interfaces et les classes qui produisent les objets injectés dans vos classes d’application via DI.</span><span class="sxs-lookup"><span data-stu-id="be73f-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="be73f-128">(Comme DI basé sur le constructeur, comme indiqué précédemment.)</span><span class="sxs-lookup"><span data-stu-id="be73f-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="be73f-129">L’aide du conteneur inversion de contrôle intégré fourni par ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="be73f-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="be73f-130">Lorsque vous utilisez le conteneur inversion de contrôle intégré fourni par ASP.NET Core, vous inscrivez les types que vous souhaitez insérer dans la méthode ConfigureServices dans le fichier Startup.cs, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="be73f-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

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

<span data-ttu-id="be73f-131">Le modèle le plus courant lors de l’inscription des types dans un conteneur inversion de contrôle consiste à inscrire des deux types : une interface et sa classe de mise en œuvre associée.</span><span class="sxs-lookup"><span data-stu-id="be73f-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="be73f-132">Ensuite, lorsque vous demandez un objet à partir du conteneur inversion de contrôle via tout autre constructeur, vous demandez un objet d’un certain type d’interface.</span><span class="sxs-lookup"><span data-stu-id="be73f-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="be73f-133">Par exemple, dans l’exemple précédent, la dernière ligne indique que lorsqu’un des constructeurs de votre ont une dépendance sur IMyCustomRepository (interface ou abstraction), le conteneur IoC injecter une instance de l’implémentation de MyCustomSQLServerRepository classe.</span><span class="sxs-lookup"><span data-stu-id="be73f-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="be73f-134">À l’aide de la bibliothèque Scrutor pour l’inscription des types automatique</span><span class="sxs-lookup"><span data-stu-id="be73f-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="be73f-135">Lorsque vous utilisez DI dans .NET Core, vous souhaiterez peut-être être en mesure d’analyser un assembly et inscrire automatiquement ses types par convention.</span><span class="sxs-lookup"><span data-stu-id="be73f-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="be73f-136">Cette fonctionnalité n’est pas actuellement disponible dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="be73f-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="be73f-137">Toutefois, vous pouvez utiliser la [Scrutor](https://github.com/khellang/Scrutor) bibliothèque correspondant.</span><span class="sxs-lookup"><span data-stu-id="be73f-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="be73f-138">Cette approche est pratique lorsque vous avez des dizaines de types qui doivent être inscrits dans votre conteneur inversion de contrôle.</span><span class="sxs-lookup"><span data-stu-id="be73f-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="be73f-139">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="be73f-139">Additional resources</span></span>

-   <span data-ttu-id="be73f-140">**Matthew ROI. Inscription des services avec Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="be73f-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="be73f-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="be73f-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="be73f-142">Référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="be73f-142">GitHub repo.</span></span>
    [<span data-ttu-id="be73f-143">*https://github.com/khellang/Scrutor*</span><span class="sxs-lookup"><span data-stu-id="be73f-143">*https://github.com/khellang/Scrutor*</span></span>](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="be73f-144">À l’aide de Autofac comme un conteneur inversion de contrôle</span><span class="sxs-lookup"><span data-stu-id="be73f-144">Using Autofac as an IoC container</span></span>

<span data-ttu-id="be73f-145">Vous pouvez également utiliser d’autres conteneurs d’inversion de contrôle et les incorporer dans le pipeline ASP.NET Core, comme dans l’ordre de tri microservice dans eShopOnContainers, qui utilise [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="be73f-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="be73f-146">Lorsque vous utilisez Autofac vous inscrire en général, les types via des modules, ce qui vous permet de fractionner les types d’enregistrements entre plusieurs fichiers en fonction de l’avancement de vos types, tout comme vous pourriez avoir les types d’applications distribuées sur plusieurs bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="be73f-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="be73f-147">Par exemple, ce qui suit est la [module d’application Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pour le [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projet avec les types que vous pouvez injecter.</span><span class="sxs-lookup"><span data-stu-id="be73f-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

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

<span data-ttu-id="be73f-148">Le processus d’inscription et les concepts sont très similaires à la façon dont vous pouvez inscrire les types avec le conteneur d’iOS ASP.NET Core intégré, mais la syntaxe lors de l’utilisation de Autofac est un peu différente.</span><span class="sxs-lookup"><span data-stu-id="be73f-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="be73f-149">Dans l’exemple de code, l’abstraction IOrderRepository est enregistrée en même temps que la classe d’implémentation OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="be73f-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="be73f-150">Cela signifie que chaque fois qu’un constructeur déclare une dépendance par l’interface ou IOrderRepository abstraction, le conteneur IoC injecter une instance de la classe OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="be73f-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="be73f-151">Le type d’instance étendue détermine la façon dont une instance est partagée entre les demandes de service ou une dépendance.</span><span class="sxs-lookup"><span data-stu-id="be73f-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="be73f-152">Lorsqu’une demande est faite pour une dépendance, le conteneur inversion de contrôle peut retourner les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="be73f-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="be73f-153">Une instance unique par l’étendue de la durée de vie (dans le conteneur inversion de contrôle ASP.NET Core comme *étendue*).</span><span class="sxs-lookup"><span data-stu-id="be73f-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="be73f-154">Une nouvelle instance par dépendance (dans le conteneur inversion de contrôle ASP.NET Core comme *temporaire*).</span><span class="sxs-lookup"><span data-stu-id="be73f-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="be73f-155">Une seule instance partagée entre tous les objets à l’aide du conteneur inversion de contrôle (dans le conteneur inversion de contrôle ASP.NET Core comme *singleton*).</span><span class="sxs-lookup"><span data-stu-id="be73f-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="be73f-156">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="be73f-156">Additional resources</span></span>

-   <span data-ttu-id="be73f-157">**Introduction à l’Injection de dépendances dans ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="be73f-157">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="be73f-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="be73f-158">**Autofac.**</span></span> <span data-ttu-id="be73f-159">Documentation officielle.</span><span class="sxs-lookup"><span data-stu-id="be73f-159">Official documentation.</span></span>
    [<span data-ttu-id="be73f-160">*http://docs.autofac.org/en/Latest/*</span><span class="sxs-lookup"><span data-stu-id="be73f-160">*http://docs.autofac.org/en/latest/*</span></span>](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="be73f-161">**Cesar de la Torre. Comparaison des durées de vie du service ASP.NET Core IoC conteneur avec des étendues d’instance Autofac IoC conteneur**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IoC-Service-Life-Times-and-autofac-IoC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="be73f-161">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="be73f-162">Implémenter des modèles de commande et le Gestionnaire de commandes</span><span class="sxs-lookup"><span data-stu-id="be73f-162">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="be73f-163">Dans l’exemple DI via ce constructeur est indiqué dans la section précédente, le conteneur inversion de contrôle a été injecter des référentiels via un constructeur dans une classe.</span><span class="sxs-lookup"><span data-stu-id="be73f-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="be73f-164">Mais exactement où ont été ils injectés ?</span><span class="sxs-lookup"><span data-stu-id="be73f-164">But exactly where were they injected?</span></span> <span data-ttu-id="be73f-165">Dans une API Web simple (par exemple, le catalogue microservice dans eShopOnContainers), vous les injectez au niveau des contrôleurs MVC, dans un constructeur de contrôleur.</span><span class="sxs-lookup"><span data-stu-id="be73f-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="be73f-166">Toutefois, dans le code initial de cette section (la [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) classe à partir du service Ordering.API dans eShopOnContainers), l’injection de dépendances est effectuée via le constructeur d’une commande spécifique Gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="be73f-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="be73f-167">Nous expliquer ce qu’est un gestionnaire de commandes et la raison pour laquelle vous pouvez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="be73f-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="be73f-168">Le modèle de commande est intrinsèquement lié au modèle CQRS introduite plus haut dans ce guide.</span><span class="sxs-lookup"><span data-stu-id="be73f-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="be73f-169">CQRS comporte deux parties.</span><span class="sxs-lookup"><span data-stu-id="be73f-169">CQRS has two sides.</span></span> <span data-ttu-id="be73f-170">La première zone est requêtes, à l’aide de requêtes simplifiés avec la [Dapper](https://github.com/StackExchange/dapper-dot-net) ORM micro, ce qui a été expliqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="be73f-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="be73f-171">La deuxième zone est commandes, qui sont le point de départ pour les transactions et le canal d’entrée à partir d’en dehors du service.</span><span class="sxs-lookup"><span data-stu-id="be73f-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="be73f-172">Comme indiqué dans la Figure 9-20, le modèle est basé sur l’acceptation des commandes à partir du côté client, le traitement en fonction des règles du modèle de domaine et enfin persistantes les États des transactions.</span><span class="sxs-lookup"><span data-stu-id="be73f-172">As shown in Figure 9-20, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="be73f-173">**Figure 9-20**.</span><span class="sxs-lookup"><span data-stu-id="be73f-173">**Figure 9-20**.</span></span> <span data-ttu-id="be73f-174">Vue d’ensemble des commandes ou « côté transactionnelle » dans un modèle CQRS</span><span class="sxs-lookup"><span data-stu-id="be73f-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="be73f-175">La classe de commande</span><span class="sxs-lookup"><span data-stu-id="be73f-175">The command class</span></span>

<span data-ttu-id="be73f-176">Une commande est une demande au système effectuer une action qui modifie l’état du système.</span><span class="sxs-lookup"><span data-stu-id="be73f-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="be73f-177">Commandes sont impératifs et doivent être traités en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="be73f-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="be73f-178">Étant donné que les commandes sont impératifs, ils sont généralement nommés avec un verbe d’humeur impératif (par exemple, « créer » ou « update »), et incluent le type d’agrégation, telles que CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="be73f-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="be73f-179">Contrairement à un événement, une commande n’est pas fait précédemment ; Il est uniquement une demande et donc ne peut être refusée.</span><span class="sxs-lookup"><span data-stu-id="be73f-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="be73f-180">Commandes peuvent provenir de l’interface utilisateur à la suite d’un utilisateur qui démarre une demande ou à partir d’un gestionnaire de processus lorsque le Gestionnaire de processus dirige un agrégat pour exécuter une action.</span><span class="sxs-lookup"><span data-stu-id="be73f-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="be73f-181">Une caractéristique importante d’une commande est qu’il doit être traité une seule fois par un destinataire unique.</span><span class="sxs-lookup"><span data-stu-id="be73f-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="be73f-182">Il s’agit d’une commande étant une seule action ou une transaction à effectuer dans l’application.</span><span class="sxs-lookup"><span data-stu-id="be73f-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="be73f-183">Par exemple, la même commande de création de commande ne doit pas traitée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="be73f-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="be73f-184">Il s’agit d’une différence importante entre les commandes et les événements.</span><span class="sxs-lookup"><span data-stu-id="be73f-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="be73f-185">Les événements peuvent être traitées plusieurs fois, car de nombreux systèmes ou microservices d’intéresser l’événement.</span><span class="sxs-lookup"><span data-stu-id="be73f-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="be73f-186">En outre, il est important de traiter une commande qu’une seule fois d’au cas où la commande n’est pas idempotentes.</span><span class="sxs-lookup"><span data-stu-id="be73f-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="be73f-187">Une commande est idempotente si elle peut être exécutée plusieurs fois sans modifier le résultat, soit en raison de la nature de la commande, soit en raison de la manière dont le système gère la commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="be73f-188">Il est recommandé de rendre vos commandes d’et idempotent des mises à jour quand il est judicieux sous règles d’entreprise de votre domaine et les invariants.</span><span class="sxs-lookup"><span data-stu-id="be73f-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="be73f-189">Par exemple, pour utiliser le même exemple, si pour une raison quelconque (logique de nouvelle tentative de piratage, etc.) la même commande CreateOrder atteint votre système plusieurs fois, vous devez être en mesure d’identifier et assurez-vous que vous ne créez pas plusieurs commandes.</span><span class="sxs-lookup"><span data-stu-id="be73f-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="be73f-190">Pour ce faire, vous devez attacher un type d’identité dans les opérations et de déterminer si la commande ou la mise à jour a déjà été traité.</span><span class="sxs-lookup"><span data-stu-id="be73f-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="be73f-191">Vous envoyez une commande à un seul destinataire ; Vous ne publiez pas une commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="be73f-192">La publication est pour les événements d’intégration qui fait de l’état — que quelque chose s’est produit et qu’il peut être intéressant pour les récepteurs d’événements.</span><span class="sxs-lookup"><span data-stu-id="be73f-192">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="be73f-193">Dans le cas d’événements, l’éditeur n’a aucun problème sur les récepteurs d’obtiennent l’événement ou qu’ils le faire.</span><span class="sxs-lookup"><span data-stu-id="be73f-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="be73f-194">Mais les événements d’intégration sont un autre article déjà été présentée dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="be73f-194">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="be73f-195">Une commande est implémentée avec une classe qui contient des champs de données ou des regroupements avec toutes les informations qui est nécessaire pour exécuter cette commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="be73f-196">Une commande est un type spécial de données transfert objet (DTO), qui est utilisé spécifiquement pour demander des modifications ou des transactions.</span><span class="sxs-lookup"><span data-stu-id="be73f-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="be73f-197">La commande elle-même est basée sur exactement les informations nécessaires pour le traitement de la commande et rien de plus.</span><span class="sxs-lookup"><span data-stu-id="be73f-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="be73f-198">L’exemple suivant montre la classe CreateOrderCommand simplifiée.</span><span class="sxs-lookup"><span data-stu-id="be73f-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="be73f-199">Il s’agit d’une commande immuable qui est utilisée dans l’ordre de tri microservice dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="be73f-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

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

<span data-ttu-id="be73f-200">En fait, la classe de commande contient toutes les données que vous avez besoin pour effectuer une transaction commerciale en utilisant les objets de modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="be73f-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="be73f-201">Par conséquent, les commandes sont simplement des structures de données qui contiennent des données en lecture seule et pas de comportement.</span><span class="sxs-lookup"><span data-stu-id="be73f-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="be73f-202">Nom de la commande indique son objectif.</span><span class="sxs-lookup"><span data-stu-id="be73f-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="be73f-203">Dans de nombreux langages tels que C\#, les commandes sont représentés en tant que classes, mais ils ne sont pas des classes trues dans le sens réel et orienté objet.</span><span class="sxs-lookup"><span data-stu-id="be73f-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="be73f-204">Comme le des caractéristiques supplémentaires, les commandes sont immuables, car l’utilisation attendue est qu’ils sont traités directement par le modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="be73f-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="be73f-205">Ils n’avez pas besoin de changer au cours de leur durée de vie prévue.</span><span class="sxs-lookup"><span data-stu-id="be73f-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="be73f-206">Dans un C\# (classe), que l’immuabilité peut être obtenue en n’ayant ne pas toutes les méthodes setter ou autres méthodes qui modifient l’état interne.</span><span class="sxs-lookup"><span data-stu-id="be73f-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="be73f-207">Par exemple, la classe de commande pour la création d’une commande est probablement similaire en termes de données à la commande que vous souhaitez créer, mais vous n’avez probablement pas besoin les mêmes attributs.</span><span class="sxs-lookup"><span data-stu-id="be73f-207">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="be73f-208">Par exemple, CreateOrderCommand n’a pas un ID de commande, car l’ordre n’a pas encore été créé.</span><span class="sxs-lookup"><span data-stu-id="be73f-208">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="be73f-209">De nombreuses classes de commande peuvent être simples, il nécessite que quelques champs sur un état qui doit être modifiée.</span><span class="sxs-lookup"><span data-stu-id="be73f-209">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="be73f-210">Ce serait le cas si vous modifiez simplement l’état d’une commande à partir de « en cours » à « payé » ou « livré » à l’aide d’une commande semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="be73f-210">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="be73f-211">Certains développeurs rendre leurs objets de requête de l’interface utilisateur distinct à partir de leurs données de commande, mais qui est simplement une question de préférence.</span><span class="sxs-lookup"><span data-stu-id="be73f-211">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="be73f-212">Il s’agit d’une séparation fastidieuse à pas de valeur ajoutée, et les objets sont presque exactement la même forme.</span><span class="sxs-lookup"><span data-stu-id="be73f-212">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="be73f-213">Par exemple, dans eShopOnContainers, les commandes sont fournis directement à partir du client.</span><span class="sxs-lookup"><span data-stu-id="be73f-213">For instance, in eShopOnContainers, the commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="be73f-214">La classe de gestionnaire de commandes</span><span class="sxs-lookup"><span data-stu-id="be73f-214">The Command Handler class</span></span>

<span data-ttu-id="be73f-215">Vous devez implémenter une classe de gestionnaire de commande spécifique pour chaque commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-215">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="be73f-216">Comment le modèle fonctionne, et il est où vous allez utiliser l’objet de commande, les objets de domaine et les objets de référentiel d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="be73f-216">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="be73f-217">Le Gestionnaire de commandes est en fait le cœur de la couche d’application en termes de CQRS et DDD.</span><span class="sxs-lookup"><span data-stu-id="be73f-217">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="be73f-218">Toutefois, toute la logique de domaine doit être contenue dans les classes de domaine, dans les racines d’agrégation (entités racine), les entités enfants, ou [services de domaine](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), mais pas dans le Gestionnaire de commandes, qui est une classe à partir de l’application couche.</span><span class="sxs-lookup"><span data-stu-id="be73f-218">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="be73f-219">Un gestionnaire de commandes reçoit une commande et obtient un résultat à partir de l’agrégat qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="be73f-219">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="be73f-220">Le résultat doit être l’exécution réussie de la commande, ou une exception.</span><span class="sxs-lookup"><span data-stu-id="be73f-220">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="be73f-221">En cas d’exception, l’état du système doit être inchangée.</span><span class="sxs-lookup"><span data-stu-id="be73f-221">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="be73f-222">Le Gestionnaire de commandes prend généralement les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="be73f-222">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="be73f-223">Il reçoit l’objet de commande, comme un DTO (à partir de la [médiateur](https://en.wikipedia.org/wiki/Mediator_pattern) ou un autre objet de l’infrastructure).</span><span class="sxs-lookup"><span data-stu-id="be73f-223">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="be73f-224">Il vérifie que la commande est valide (le cas ne pas validé par le médiateur).</span><span class="sxs-lookup"><span data-stu-id="be73f-224">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="be73f-225">Il instancie l’instance racine d’agrégation qui est la cible de la commande actuelle.</span><span class="sxs-lookup"><span data-stu-id="be73f-225">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="be73f-226">Il exécute la méthode sur l’instance racine d’agrégat, obtenir les données requises à partir de la commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-226">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="be73f-227">Il conserve le nouvel état de l’agrégat pour sa base de données connexe.</span><span class="sxs-lookup"><span data-stu-id="be73f-227">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="be73f-228">Cette dernière opération est la transaction réelle.</span><span class="sxs-lookup"><span data-stu-id="be73f-228">This last operation is the actual transaction.</span></span>

<span data-ttu-id="be73f-229">En règle générale, un gestionnaire de commandes porte sur un agrégat unique dus à la racine d’agrégation (entité racine).</span><span class="sxs-lookup"><span data-stu-id="be73f-229">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="be73f-230">Si plusieurs agrégats doivent être affectées par la réception d’une commande unique, vous pouvez utiliser des événements de domaine pour propager des États ou des actions sur plusieurs agrégats</span><span class="sxs-lookup"><span data-stu-id="be73f-230">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates</span></span>

<span data-ttu-id="be73f-231">Le point important ici est que lorsqu’une commande est en cours de traitement, la logique de domaine doit être au sein du modèle de domaine (agrégation), entièrement encapsulé et prêt pour les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="be73f-231">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="be73f-232">Le Gestionnaire de commandes sert simplement un moyen d’obtenir le modèle de domaine à partir de la base de données et l’étape finale, pour indiquer à la couche d’infrastructure (référentiels) pour conserver les modifications lorsque le modèle est modifié.</span><span class="sxs-lookup"><span data-stu-id="be73f-232">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="be73f-233">L’avantage de cette approche est que vous pouvez refactoriser la logique de domaine dans un modèle de domaine isolé, entièrement encapsulé, enrichi, comportement sans modifier le code dans l’application ou les couches d’infrastructure, qui sont le niveau de plomberie (gestionnaires de commandes, l’API Web, référentiels, etc.).</span><span class="sxs-lookup"><span data-stu-id="be73f-233">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="be73f-234">Lorsque les gestionnaires de commandes obtenir complexes, avec trop de logique, ce qui peut être une odeur de code.</span><span class="sxs-lookup"><span data-stu-id="be73f-234">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="be73f-235">Passez en revue les et si vous trouvez la logique de domaine, refactoriser le code pour déplacer ce comportement de domaine pour les méthodes des objets de domaine (le regroupement racine et enfant entity).</span><span class="sxs-lookup"><span data-stu-id="be73f-235">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="be73f-236">Un exemple d’une classe de gestionnaire de commande, le code suivant montre la même classe CreateOrderCommandHandler que vous avez vu au début de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="be73f-236">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="be73f-237">Dans ce cas nous avons mis en surbrillance la méthode Handle et les opérations avec les objets de modèle de domaine/agrégats.</span><span class="sxs-lookup"><span data-stu-id="be73f-237">In this case we have highlighted the Handle method and the operations with the domain model objects/aggregates.</span></span>

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

<span data-ttu-id="be73f-238">Il s’agit d’un gestionnaire de commandes devez suivre des étapes supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="be73f-238">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="be73f-239">Utilisez les données de la commande fonctionne avec les méthodes et le comportement de la racine d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="be73f-239">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="be73f-240">En interne dans les objets de domaine, déclencher des événements de domaine lors de la transaction est exécutée, mais qui est transparente à partir d’un point de vue de commande Gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="be73f-240">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="be73f-241">Si le résultat de l’agrégat de l’opération a réussi, et une fois la transaction terminée, déclencher le Gestionnaire de commandes d’événements integration.</span><span class="sxs-lookup"><span data-stu-id="be73f-241">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="be73f-242">(Il peuvent également être levée par les classes d’infrastructure tels que les référentiels.)</span><span class="sxs-lookup"><span data-stu-id="be73f-242">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="be73f-243">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="be73f-243">Additional resources</span></span>

-   <span data-ttu-id="be73f-244">**Mark Seemann. Dans les limites, les Applications sont orientés objet pas**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, orienté sur ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="be73f-244">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="be73f-245">**Commandes et les événements**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="be73f-245">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="be73f-246">**À quoi un gestionnaire de commandes ? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="be73f-246">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="be73f-247">**Jimmy Bogard. Modèles de commande du domaine – gestionnaires**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="be73f-247">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="be73f-248">**Jimmy Bogard. Modèles de commande du domaine – Validation**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="be73f-248">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="be73f-249">Le pipeline de processus de commande : le déclenchement d’un gestionnaire de commandes</span><span class="sxs-lookup"><span data-stu-id="be73f-249">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="be73f-250">La question suivante consiste à appeler un gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="be73f-250">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="be73f-251">Vous pouvez l’appeler manuellement à partir de chaque contrôleur ASP.NET Core connexe.</span><span class="sxs-lookup"><span data-stu-id="be73f-251">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="be73f-252">Toutefois, l’approche serait trop couplé et n’est pas idéale.</span><span class="sxs-lookup"><span data-stu-id="be73f-252">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="be73f-253">Les autres deux options principales, qui sont les options recommandées, sont :</span><span class="sxs-lookup"><span data-stu-id="be73f-253">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="be73f-254">Via un artefact de modèle médiateur en mémoire.</span><span class="sxs-lookup"><span data-stu-id="be73f-254">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="be73f-255">Avec une file d’attente message asynchrone, entre les contrôleurs et les gestionnaires.</span><span class="sxs-lookup"><span data-stu-id="be73f-255">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="be73f-256">Utilisation du modèle de médiateur (mémoire) dans le pipeline de commande</span><span class="sxs-lookup"><span data-stu-id="be73f-256">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="be73f-257">Comme indiqué dans la Figure 9-21, dans une approche CQRS, vous utilisez un médiateur intelligent, similaire à un bus en mémoire, ce qui est assez intelligent pour rediriger vers le Gestionnaire de commande appropriée en fonction du type de la commande DTO reçus.</span><span class="sxs-lookup"><span data-stu-id="be73f-257">As shown in Figure 9-21, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="be73f-258">Les flèches noires uniques entre les composants représentent les dépendances entre les objets (dans de nombreux cas, injectés via DI) avec leurs interactions associées.</span><span class="sxs-lookup"><span data-stu-id="be73f-258">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="be73f-259">**Figure 9-21**.</span><span class="sxs-lookup"><span data-stu-id="be73f-259">**Figure 9-21**.</span></span> <span data-ttu-id="be73f-260">Utilisation du modèle de médiateur dans le processus dans un microservice CQRS unique</span><span class="sxs-lookup"><span data-stu-id="be73f-260">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="be73f-261">La raison pour laquelle l’utilisation du modèle de médiateur de sens est que dans les applications d’entreprise, les demandes de traitement peuvent se compliquer.</span><span class="sxs-lookup"><span data-stu-id="be73f-261">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="be73f-262">Vous souhaitez être en mesure d’ajouter un nombre ouvert de problèmes transversaux comme la journalisation, validations, d’audit et de sécurité.</span><span class="sxs-lookup"><span data-stu-id="be73f-262">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="be73f-263">Dans ce cas, vous pouvez compter sur un pipeline de médiateur (consultez [modèle de médiateur](https://en.wikipedia.org/wiki/Mediator_pattern)) pour fournir un moyen de ces comportements supplémentaires ou des problèmes transversaux.</span><span class="sxs-lookup"><span data-stu-id="be73f-263">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="be73f-264">Médiateur est un objet qui encapsule le « comment » de ce processus : Il coordonne l’exécution basée sur l’état, la façon un gestionnaire de commandes est appelée ou la charge utile de fournir au gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="be73f-264">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="be73f-265">Avec un composant de médiateur vous pouvez appliquer des problèmes transversaux de manière centralisée et transparente en appliquant des éléments décoratifs (ou [pipeline comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) depuis médiateur v3).</span><span class="sxs-lookup"><span data-stu-id="be73f-265">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since Mediator v3).</span></span> <span data-ttu-id="be73f-266">(Pour plus d’informations, consultez la [modèle d’élément décoratif](https://en.wikipedia.org/wiki/Decorator_pattern).)</span><span class="sxs-lookup"><span data-stu-id="be73f-266">(For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).)</span></span>

<span data-ttu-id="be73f-267">Éléments décoratifs et les comportements sont semblables aux [de programmation orientée Aspect (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), uniquement être appliquée à un pipeline de processus spécifique géré par le composant de médiateur.</span><span class="sxs-lookup"><span data-stu-id="be73f-267">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="be73f-268">Aspects dans AOP qui implémentent des problèmes transversaux sont appliquées selon *Tisseurs d’aspect* injecté au moment de la compilation ou en fonction d’interception des appels.</span><span class="sxs-lookup"><span data-stu-id="be73f-268">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="be73f-269">Les deux approches AOP classiques sont considérés comme parfois fonctionne « comme par magie », car il n’est pas facile de voir comment AOP effectue son travail.</span><span class="sxs-lookup"><span data-stu-id="be73f-269">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="be73f-270">Lorsque vous traitez des problèmes graves ou des bogues, AOP peut être difficile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="be73f-270">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="be73f-271">En revanche, ces éléments décoratifs/comportements étant explicite et appliquées uniquement dans le contexte de la médiateur, le débogage est beaucoup plus prévisible et plus facile.</span><span class="sxs-lookup"><span data-stu-id="be73f-271">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="be73f-272">Par exemple, dans l’ordre de microservice eShopOnContainers, nous avons implémenté deux décorateurs d’exemple, un [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe et un [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe.</span><span class="sxs-lookup"><span data-stu-id="be73f-272">For example, in the eShopOnContainers ordering microservice, we implemented two sample decorators, a [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class and a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class.</span></span> <span data-ttu-id="be73f-273">Mise en œuvre de l’élément décoratif est expliquée dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="be73f-273">The decorator’s implementation is explained in the next section.</span></span> <span data-ttu-id="be73f-274">Notez que dans une version ultérieure, eShopOnContainers la faire migrer vers [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) et déplacer vers [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) au lieu d’utiliser des éléments décoratifs.</span><span class="sxs-lookup"><span data-stu-id="be73f-274">Note that in a future version, eShopOnContainers will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="be73f-275">Dans le pipeline de la commande à l’aide de files d’attente de message (out-of-process)</span><span class="sxs-lookup"><span data-stu-id="be73f-275">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="be73f-276">Un autre choix consiste à utiliser des messages asynchrones selon les courtiers et les files d’attente de messages, comme indiqué dans la Figure 9-22.</span><span class="sxs-lookup"><span data-stu-id="be73f-276">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-22.</span></span> <span data-ttu-id="be73f-277">Cette option peut aussi être combinée avec le composant de médiateur juste avant le Gestionnaire de commandes.</span><span class="sxs-lookup"><span data-stu-id="be73f-277">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="be73f-278">**Figure 9-22**.</span><span class="sxs-lookup"><span data-stu-id="be73f-278">**Figure 9-22**.</span></span> <span data-ttu-id="be73f-279">À l’aide de files d’attente de message (hors processus et la communication interprocessue) avec les commandes CQRS</span><span class="sxs-lookup"><span data-stu-id="be73f-279">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="be73f-280">À l’aide de files d’attente pour accepter que les commandes peuvent être plus compliquent le pipeline de votre commande, de message, car vous devrez probablement divisez le pipeline en deux processus connecté via la file d’attente de message externe.</span><span class="sxs-lookup"><span data-stu-id="be73f-280">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="be73f-281">Toujours, elle doit être utilisée si vous avez besoin ont amélioré les performances en fonction de la messagerie asynchrone et l’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="be73f-281">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="be73f-282">Tenez compte des points dans le cas de Figure 9-22, le contrôleur simplement publie le message de commande dans la file d’attente et retourne.</span><span class="sxs-lookup"><span data-stu-id="be73f-282">Consider that in the case of Figure 9-22, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="be73f-283">Ensuite, les gestionnaires de commandes traitent les messages à leur propre rythme.</span><span class="sxs-lookup"><span data-stu-id="be73f-283">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="be73f-284">Autrement dit un énorme avantage des files d’attente, la file d’attente peut agir comme une mémoire tampon dans le cas lorsque l’extensibilité hyper est nécessaire, par exemple pour des stocks ou tout autre scénario un important volume de données entrantes.</span><span class="sxs-lookup"><span data-stu-id="be73f-284">That is a great benefit of queues—the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="be73f-285">Toutefois, en raison de la nature asynchrone des files d’attente, vous devez déterminer comment communiquer avec l’application cliente sur la réussite ou l’échec du processus de la commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-285">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="be73f-286">En règle générale, vous devez jamais utiliser les commandes « fire and forget ».</span><span class="sxs-lookup"><span data-stu-id="be73f-286">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="be73f-287">Chaque application d’entreprise doit savoir si une commande a été traitée correctement, ou au moins validée et acceptée.</span><span class="sxs-lookup"><span data-stu-id="be73f-287">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="be73f-288">Par conséquent, être en mesure de répondre au client après la validation d’un message de commande qui a été soumis à une file d’attente asynchrone ajoute une complexité à votre système, par rapport à un processus de commande de processus qui retourne le résultat de l’opération après l’exécution de la transaction.</span><span class="sxs-lookup"><span data-stu-id="be73f-288">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="be73f-289">À l’aide de files d’attente, vous devrez peut-être renvoyer les résultats du processus de commande via d’autres messages de résultat d’opération, qui nécessite des composants supplémentaires et communication personnalisées dans votre système.</span><span class="sxs-lookup"><span data-stu-id="be73f-289">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="be73f-290">En outre, les commandes d’async sont les commandes unidirectionnels qui, dans de nombreux cas, peut ne pas être nécessaire, comme indiqué dans l’échange suivant intéressante entre Burtsev Alexey et Greg Young dans un [conversation en ligne](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="be73f-290">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="be73f-291">\[Burtsev Alexey\] rechercher une grande quantité de code où les personnes utilisent la gestion des commandes d’async ou une commande monodirectionnelle messagerie sans une raison quelconque pour ce faire (ils n’effectuent pas une opération longue, ils n’exécutent pas de code asynchrone externe, qu’elles ne traversent pas encore d’application limite à l’utilisation de bus de messages).</span><span class="sxs-lookup"><span data-stu-id="be73f-291">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="be73f-292">Pourquoi ils introduisent cette complexité inutile ?</span><span class="sxs-lookup"><span data-stu-id="be73f-292">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="be73f-293">Et en fait, je n’ai vu un exemple de code CQRS avec le blocage des gestionnaires de commandes jusqu'à présent, si elle fonctionne correctement dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="be73f-293">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="be73f-294">\[Greg Young\] \[... \] n’existe pas une commande asynchrone ; il s’agit en fait un autre événement.</span><span class="sxs-lookup"><span data-stu-id="be73f-294">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="be73f-295">Si je dois accepter ce que vous m’envoyez et déclencher un événement si je n’accepte pas, il n’est plus vous m’indiquant d’effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="be73f-295">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="be73f-296">Il est vous m’indiquant qu'un élément a été effectué.</span><span class="sxs-lookup"><span data-stu-id="be73f-296">It's you telling me something has been done.</span></span> <span data-ttu-id="be73f-297">Cela semble être une légère différence dans un premier temps, mais il a des implications en matière de nombre.</span><span class="sxs-lookup"><span data-stu-id="be73f-297">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="be73f-298">Commandes asynchrones augmentent considérablement la complexité d’un système, car il n’existe aucun moyen simple d’indiquent des échecs.</span><span class="sxs-lookup"><span data-stu-id="be73f-298">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="be73f-299">Par conséquent, commandes asynchrones sont déconseillées autre que lors de la mise à l’échelle est nécessaires ou dans des cas spéciaux lors de la communication du microservices interne via la messagerie.</span><span class="sxs-lookup"><span data-stu-id="be73f-299">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="be73f-300">Dans ce cas, vous devez concevoir un système de création de rapports et de récupération distinct pour les échecs.</span><span class="sxs-lookup"><span data-stu-id="be73f-300">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="be73f-301">Dans la version initiale d’eShopOnContainers, nous avons décidé d’utiliser le traitement des commandes synchrones, démarré à partir de requêtes HTTP et piloté par le modèle de médiateur.</span><span class="sxs-lookup"><span data-stu-id="be73f-301">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="be73f-302">Qui permet de facilement vous permet de retourner la réussite ou l’échec du processus, comme dans le [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="be73f-302">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="be73f-303">Dans tous les cas, cela doit être une décision basée sur les besoins de votre application ou une de microservice.</span><span class="sxs-lookup"><span data-stu-id="be73f-303">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="be73f-304">Mise en œuvre le pipeline de processus de commande avec un modèle de médiateur (MediatR)</span><span class="sxs-lookup"><span data-stu-id="be73f-304">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="be73f-305">Comme un exemple d’implémentation, ce guide propose à l’aide du pipeline de processus basée sur le modèle de médiateur de réception de commande de lecteur et le routage, dans la mémoire, les gestionnaires de commandes à droite.</span><span class="sxs-lookup"><span data-stu-id="be73f-305">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and routing them, in memory, to the right command handlers.</span></span> <span data-ttu-id="be73f-306">Le guide propose également l’application des éléments décoratifs ou [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) afin de séparer les problèmes transversaux.</span><span class="sxs-lookup"><span data-stu-id="be73f-306">The guide also proposes applying decorators or [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="be73f-307">Plusieurs bibliothèques d’open source disponibles qui implémentent le modèle de médiateur sont pour l’implémentation du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="be73f-307">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="be73f-308">La bibliothèque utilisée dans ce guide est le [MediatR](https://github.com/jbogard/MediatR) bibliothèque open source (créée par Jimmy Bogard), mais vous pouvez utiliser une autre approche.</span><span class="sxs-lookup"><span data-stu-id="be73f-308">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="be73f-309">MediatR est une bibliothèque de petite et simple qui permet de traiter les messages en mémoire comme une commande, lors de l’application des éléments décoratifs ou des comportements.</span><span class="sxs-lookup"><span data-stu-id="be73f-309">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="be73f-310">L’utilisation du modèle de médiateur vous aide à réduire le couplage et pour isoler les problèmes de la tâche demandée, lors de la connexion automatique au gestionnaire qui effectue ce travail, dans ce cas, aux gestionnaires de commandes.</span><span class="sxs-lookup"><span data-stu-id="be73f-310">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="be73f-311">Une autre bonne raison d’utiliser le modèle de médiateur a été expliquée par Jimmy Bogard lors de la consultation de ce guide :</span><span class="sxs-lookup"><span data-stu-id="be73f-311">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="be73f-312">Je pense qu’il peut être intéressant de mentionner test ici : il fournit une fenêtre de cohérente intéressante dans le comportement de votre système.</span><span class="sxs-lookup"><span data-stu-id="be73f-312">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="be73f-313">Demande, hors de la réponse. Nous avons trouvé cet aspect très utiles dans le bâtiment comporte toujours des tests.</span><span class="sxs-lookup"><span data-stu-id="be73f-313">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="be73f-314">Tout d’abord, nous examinons pour le code du contrôleur où vous pouvez réellement utiliser l’objet de médiateur.</span><span class="sxs-lookup"><span data-stu-id="be73f-314">First, let us take a look to the controller code where you actually would use the mediator object.</span></span> <span data-ttu-id="be73f-315">Si vous n’utilisiez pas l’objet de médiateur, vous devez insérer toutes les dépendances de ce contrôleur, un objet de l’enregistreur d’événements et des autres.</span><span class="sxs-lookup"><span data-stu-id="be73f-315">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="be73f-316">Par conséquent, le constructeur serait relativement complexe.</span><span class="sxs-lookup"><span data-stu-id="be73f-316">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="be73f-317">En revanche, si vous utilisez l’objet médiateur, le constructeur de votre contrôleur peut être beaucoup plus simple, avec seulement quelques dépendances plutôt que de nombreuses dépendances que vous devriez si vous aviez un par opération composites, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="be73f-317">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies that you would have if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

<span data-ttu-id="be73f-318">Vous pouvez voir que le médiateur fournit un constructeur de contrôleur Web API propre et lean.</span><span class="sxs-lookup"><span data-stu-id="be73f-318">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="be73f-319">En outre, dans les méthodes de contrôleur, le code d’envoyer une commande à l’objet médiateur est presque une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="be73f-319">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

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

<span data-ttu-id="be73f-320">Dans l’ordre pour MediatR connaître vos classes de gestionnaire de commandes, vous devez inscrire les classes de médiateur et les classes de gestionnaire de commande dans votre conteneur inversion de contrôle.</span><span class="sxs-lookup"><span data-stu-id="be73f-320">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="be73f-321">Par défaut, MediatR utilise Autofac comme conteneur d’inversion de contrôle, mais vous pouvez également utiliser le conteneur inversion de contrôle ASP.NET Core prédéfini ou tout autre conteneur pris en charge par MediatR.</span><span class="sxs-lookup"><span data-stu-id="be73f-321">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="be73f-322">Le code suivant montre comment inscrire les types et les commandes de médiateur lors de l’utilisation des modules de Autofac.</span><span class="sxs-lookup"><span data-stu-id="be73f-322">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

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

<span data-ttu-id="be73f-323">Étant donné que chaque gestionnaire de commandes implémente l’interface générique IAsyncRequestHandler&lt;T&gt; et puis inspecte le RegisteredAssemblyTypes de l’objet, le gestionnaire est en mesure de lier chaque commande avec son gestionnaire de commandes, car qui relation est indiquée dans la classe CommandHandler, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="be73f-323">Because each command handler implements the interface with generic IAsyncRequestHandler&lt;T&gt; and then inspects the RegisteredAssemblyTypes object, the handler is able to relate each command with its command handler, because that relationship is stated in the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="be73f-324">Voici le code qui met en corrélation les commandes avec les gestionnaires de commandes.</span><span class="sxs-lookup"><span data-stu-id="be73f-324">This is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="be73f-325">Le gestionnaire est simplement une classe simple, mais elle hérite RequestHandler&lt;T&gt;, et MediatR permet de s’assurer qu’il est appelé avec la charge utile correcte.</span><span class="sxs-lookup"><span data-stu-id="be73f-325">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it gets invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a><span data-ttu-id="be73f-326">Application des problèmes transversaux lors du traitement de commandes avec les modèles de médiateur et Decorator</span><span class="sxs-lookup"><span data-stu-id="be73f-326">Applying cross-cutting concerns when processing commands with the Mediator and Decorator patterns</span></span>

<span data-ttu-id="be73f-327">Il existe une dernière chose : d’appliquer des problèmes transversaux au pipeline médiateur.</span><span class="sxs-lookup"><span data-stu-id="be73f-327">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="be73f-328">Vous pouvez également afficher à la fin du code de module d’enregistrement Autofac comment il inscrit un décorateur de type, plus précisément, une classe LogDecorator personnalisée.</span><span class="sxs-lookup"><span data-stu-id="be73f-328">You can also see at the end of the Autofac registration module code how it is registering a decorator type, specifically, a custom LogDecorator class.</span></span>

<span data-ttu-id="be73f-329">Là encore, notez qu’une future version d’eShopOnContainers il migre vers [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) et déplacer vers [comportements](https://github.com/jbogard/MediatR/wiki/Behaviors) au lieu d’utiliser des éléments décoratifs.</span><span class="sxs-lookup"><span data-stu-id="be73f-329">Again, note that a future version of eShopOnContainers it will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

<span data-ttu-id="be73f-330">Que [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) classe peut être implémentée en tant que le code suivant, qui enregistre des informations sur le Gestionnaire de commandes en cours d’exécution et si elle a réussi ou non.</span><span class="sxs-lookup"><span data-stu-id="be73f-330">That [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

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

<span data-ttu-id="be73f-331">L’implémentation de cette classe decorator et en décorant le pipeline avec lui, toutes les commandes traitées via MediatR seront connecté plus d’informations sur l’exécution.</span><span class="sxs-lookup"><span data-stu-id="be73f-331">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="be73f-332">L’eShopOnContainers classement microservice s’applique également un deuxième decorator pour les validations de base, le [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) classe qui s’appuie sur le [FluentValidation](https://github.com/JeremySkinner/FluentValidation) bibliothèque, comme indiqué dans les code suivant :</span><span class="sxs-lookup"><span data-stu-id="be73f-332">The eShopOnContainers ordering microservice also applies a second decorator for basic validations, the [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="be73f-333">Ensuite, selon le [FluentValidation](https://github.com/JeremySkinner/FluentValidation) bibliothèque, nous avons créé la validation pour les données passées avec CreateOrderCommand, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="be73f-333">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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

<span data-ttu-id="be73f-334">Vous pouvez créer des validations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="be73f-334">You could create additional validations.</span></span> <span data-ttu-id="be73f-335">Il s’agit d’un moyen très propre et élégant pour implémenter vos validations de commande.</span><span class="sxs-lookup"><span data-stu-id="be73f-335">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="be73f-336">De la même façon, vous pouvez implémenter d’autres décorateurs pour des aspects supplémentaires ou des problèmes transversaux que vous souhaitez appliquer aux commandes lors de leur traitement.</span><span class="sxs-lookup"><span data-stu-id="be73f-336">In a similar way, you could implement other decorators for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="be73f-337">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="be73f-337">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="be73f-338">Le modèle de médiateur</span><span class="sxs-lookup"><span data-stu-id="be73f-338">The mediator pattern</span></span>

-   <span data-ttu-id="be73f-339">**Modèle de médiateur**
    [*https://en.wikipedia.org/wiki/Mediator\_modèle*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="be73f-339">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="be73f-340">Le modèle d’élément décoratif</span><span class="sxs-lookup"><span data-stu-id="be73f-340">The decorator pattern</span></span>

-   <span data-ttu-id="be73f-341">**Modèle d’élément décoratif**
    [*https://en.wikipedia.org/wiki/Decorator\_modèle*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="be73f-341">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="be73f-342">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="be73f-342">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="be73f-343">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="be73f-343">**MediatR.**</span></span> <span data-ttu-id="be73f-344">Référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="be73f-344">GitHub repo.</span></span>
    [<span data-ttu-id="be73f-345">*https://github.com/jbogard/MediatR*</span><span class="sxs-lookup"><span data-stu-id="be73f-345">*https://github.com/jbogard/MediatR*</span></span>](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="be73f-346">**CQRS avec MediatR et AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="be73f-346">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="be73f-347">**Placer vos contrôleurs un régime : publications et les commandes. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="be73f-347">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="be73f-348">**Résolution des problèmes transversaux avec un pipeline médiateur**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="be73f-348">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="be73f-349">**CQRS et reste : la solution idéale**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="be73f-349">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="be73f-350">**Exemples de Pipeline de MediatR**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="be73f-350">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="be73f-351">**Contextes de Test de tranche verticale pour MediatR et ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*</span><span class="sxs-lookup"><span data-stu-id="be73f-351">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="be73f-352">**Extensions MediatR pour l’Injection de dépendance de Microsoft publié**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="be73f-352">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="be73f-353">Validation Fluent</span><span class="sxs-lookup"><span data-stu-id="be73f-353">Fluent validation</span></span>

-   <span data-ttu-id="be73f-354">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="be73f-354">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="be73f-355">Référentiel GitHub.</span><span class="sxs-lookup"><span data-stu-id="be73f-355">GitHub repo.</span></span>
    [<span data-ttu-id="be73f-356">*https://github.com/JeremySkinner/FluentValidation*</span><span class="sxs-lookup"><span data-stu-id="be73f-356">*https://github.com/JeremySkinner/FluentValidation*</span></span>](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="be73f-357">[Précédente] (microservice-application-layer-web-api-design.md) [suivant] (.. /Implement-RESILIENT-applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="be73f-357">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>
