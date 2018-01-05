---
title: "Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS"
description: "Architecture des Microservices .NET pour les applications .NET en conteneur | Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 45f29a8d19e49685f864b7ca83e466ceb1f73a62
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="4423a-104">Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS</span><span class="sxs-lookup"><span data-stu-id="4423a-104">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="4423a-105">*Concevoir un modèle de domaine pour chaque microservice ou contexte délimité qui reflète la compréhension du domaine d’entreprise.*</span><span class="sxs-lookup"><span data-stu-id="4423a-105">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="4423a-106">Cette section s’intéresse à des microservices plus avancés que vous implémentez quand vous avez besoin de vous attaquer à des sous-systèmes ou microservices complexes relevant de la connaissance d’experts du domaine avec des règles d’entreprise en constante évolution.</span><span class="sxs-lookup"><span data-stu-id="4423a-106">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="4423a-107">Les modèles d’architecture utilisés dans cette section sont basés sur les approches de la conception pilotée par domaine (DDD, Domain-Driven Design) et de la séparation des responsabilités dans les commandes et requêtes (CQRS, Command and Query Responsibility Segregation), comme illustré dans la figure 9-1.</span><span class="sxs-lookup"><span data-stu-id="4423a-107">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="4423a-108">**Figure 9-1**.</span><span class="sxs-lookup"><span data-stu-id="4423a-108">**Figure 9-1**.</span></span> <span data-ttu-id="4423a-109">Modèles d’architecture de microservice externe ou interne pour chaque microservice</span><span class="sxs-lookup"><span data-stu-id="4423a-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="4423a-110">Toutefois, la plupart des techniques liées aux microservices pilotés par des données, comme la manière d’implémenter un service API Web ASP.NET Core ou d’exposer des métadonnées Swagger avec Swashbuckle, sont également applicables aux microservices plus avancés implémentés en interne avec des modèles DDD.</span><span class="sxs-lookup"><span data-stu-id="4423a-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="4423a-111">Cette section est une extension des sections précédentes, car la plupart des pratiques expliquées précédemment s’appliquent également ici ou à tout type de microservice.</span><span class="sxs-lookup"><span data-stu-id="4423a-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="4423a-112">Tout d’abord, cette section fournit des détails sur les modèles CQRS simplifiés utilisés dans l’application de référence eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4423a-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="4423a-113">Ensuite, vous obtiendrez une vue d’ensemble des techniques DDD qui vous permettent de rechercher des modèles courants que vous pouvez réutiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="4423a-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="4423a-114">DDD est un large sujet avec un ensemble complet de ressources d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="4423a-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="4423a-115">Vous pouvez commencer avec des ouvrages comme [Domain-Driven Design](https://domainlanguage.com/ddd/) d’Eric Evans et d’autres documents de Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard et de nombreux autres experts en DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="4423a-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="4423a-116">Mais avant tout, vous devez essayer d’apprendre à appliquer des techniques DDD à partir des conversations, tableaux blancs et sessions de modélisation que vous tenez avec des experts de votre domaine d’entreprise concret.</span><span class="sxs-lookup"><span data-stu-id="4423a-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="4423a-117">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4423a-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="4423a-118">DDD (Domain-Driven Design)</span><span class="sxs-lookup"><span data-stu-id="4423a-118">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="4423a-119">**Eric Evans. Domain Language**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="4423a-119">**Eric Evans. Domain Language**
[*http://domainlanguage.com/*](http://domainlanguage.com/)</span></span>

-   <span data-ttu-id="4423a-120">**Martin Fowler. Domain-Driven Design**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="4423a-120">**Martin Fowler. Domain-Driven Design**
[*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="4423a-121">**Jimmy Bogard. Strengthening your domain: a primer**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="4423a-121">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="4423a-122">Ouvrages DDD</span><span class="sxs-lookup"><span data-stu-id="4423a-122">DDD books</span></span>

-   <span data-ttu-id="4423a-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="4423a-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="4423a-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="4423a-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="4423a-125">**Vaughn Vernon. Implementing Domain-Driven Design**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="4423a-125">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="4423a-126">**Vaughn Vernon. Domain-Driven Design Distilled**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="4423a-126">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="4423a-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="4423a-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="4423a-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="4423a-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="4423a-129">**Abel Avram et Floyd Marinescu. Domain-Driven Design Quickly**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="4423a-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="4423a-130">Formation DDD</span><span class="sxs-lookup"><span data-stu-id="4423a-130">DDD training</span></span>

-   <span data-ttu-id="4423a-131">**Julie Lerman et Steve Smith. Domain-Driven Design Fundamentals**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="4423a-131">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4423a-132">[Précédent] (../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [Suivant] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="4423a-132">[Previous] (../multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
