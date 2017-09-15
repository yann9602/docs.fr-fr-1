---
title: "Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS"
description: "Architecture des Microservices .NET pour les applications .NET en conteneur | Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: d81091bf09d690f5d57ad9a30b5f16de1358ede6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Lutte contre la complexité d’entreprise dans un microservice disposant des modèles DDD et CQRS

*Concevoir un modèle de domaine pour chaque microservice ou contexte délimité qui reflète la compréhension du domaine d’entreprise.*

Cette section s’intéresse à des microservices plus avancés que vous implémentez quand vous avez besoin de vous attaquer à des sous-systèmes ou microservices complexes relevant de la connaissance d’experts du domaine avec des règles d’entreprise en constante évolution. Les modèles d’architecture utilisés dans cette section sont basés sur les approches de la conception pilotée par domaine (DDD, Domain-Driven Design) et de la séparation des responsabilités dans les commandes et requêtes (CQRS, Command and Query Responsibility Segregation), comme illustré dans la figure 9-1.

![](./media/image1.png)

**Figure 9-1**. Modèles d’architecture de microservice externe ou interne pour chaque microservice

Toutefois, la plupart des techniques liées aux microservices pilotés par des données, comme la manière d’implémenter un service API Web ASP.NET Core ou d’exposer des métadonnées Swagger avec Swashbuckle, sont également applicables aux microservices plus avancés implémentés en interne avec des modèles DDD. Cette section est une extension des sections précédentes, car la plupart des pratiques expliquées précédemment s’appliquent également ici ou à tout type de microservice.

Tout d’abord, cette section fournit des détails sur les modèles CQRS simplifiés utilisés dans l’application de référence eShopOnContainers. Ensuite, vous obtiendrez une vue d’ensemble des techniques DDD qui vous permettent de rechercher des modèles courants que vous pouvez réutiliser dans vos applications.

DDD est un large sujet avec un ensemble complet de ressources d’apprentissage. Vous pouvez commencer avec des ouvrages comme [Domain-Driven Design](https://domainlanguage.com/ddd/) d’Eric Evans et d’autres documents de Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard et de nombreux autres experts en DDD/CQRS. Mais avant tout, vous devez essayer d’apprendre à appliquer des techniques DDD à partir des conversations, tableaux blancs et sessions de modélisation que vous tenez avec des experts de votre domaine d’entreprise concret.

#### <a name="additional-resources"></a>Ressources supplémentaires

##### <a name="ddd-domain-driven-design"></a>DDD (Domain-Driven Design)

-   **Eric Evans. Domain Language**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)

-   **Martin Fowler. Domain-Driven Design**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Strengthening your domain: a primer**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>Ouvrages DDD

-   **Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Implementing Domain-Driven Design**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Domain-Driven Design Distilled**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Abel Avram et Floyd Marinescu. Domain-Driven Design Quickly**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

Formation DDD

-   **Julie Lerman et Steve Smith. Domain-Driven Design Fundamentals**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Précédent] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)

