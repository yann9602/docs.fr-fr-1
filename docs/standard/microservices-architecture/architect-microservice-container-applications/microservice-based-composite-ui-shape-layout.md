---
title: "Création de l’interface utilisateur composite basée sur microservices, y compris visual forme de l’interface utilisateur et la disposition généré par plusieurs microservices"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Création de l’interface utilisateur composite basée sur microservices, y compris visual forme de l’interface utilisateur et la disposition généré par plusieurs microservices"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4b32fed5eb0de02b01665efa4368eb83e3fda08d
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2017
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Création de l’interface utilisateur composite basée sur microservices, y compris visual forme de l’interface utilisateur et la disposition généré par plusieurs microservices

Architecture de Microservices commence généralement par la gestion des données et la logique côté serveur. Toutefois, une approche plus avancée est de concevoir votre application en fonction de l’interface utilisateur de microservices ainsi. Qui implique l’existence d’une interface utilisateur composite de produits par le microservices, au lieu d’avoir microservices sur le serveur et simplement une application client monolithique consomme la microservices. Avec cette approche, le microservices que vous créez peut être complet avec la logique et représentation visuelle.

Figure 4-20 montre l’approche la plus simple d’utilisation juste des microservices à partir d’une application cliente monolithique. Bien sûr, vous pourriez avoir un service ASP.NET MVC entre production HTML et JavaScript. La figure est une version simplifiée qui met en évidence les que vous disposez d’un seul client (monolithique) l’interface utilisateur de la consommation de microservices, ce qui vous concentrer uniquement sur la logique et les données et non sur la forme d’interface utilisateur (HTML et JavaScript).

![](./media/image20.png)

**Figure 4-20**. Une application d’interface utilisateur monolithique consommation principal microservices

En revanche, une interface utilisateur composite est générée avec précision et composée par le microservices eux-mêmes. Parmi les microservices définissent la forme visual des zones spécifiques de l’interface utilisateur. La principale différence est que vous disposez des composants d’interface utilisateur client (classes TS, par exemple) basées sur des modèles et le ViewModel UI mise en forme des données de ces modèles proviennent de chaque microservice.

Au démarrage de l’application client, chacun des composants de l’interface utilisateur client (classes TypeScript, par exemple) s’inscrit avec une infrastructure microservice capable de fournir des ViewModel pour un scénario donné. Si le microservice modifie la forme, l’interface utilisateur change également.

Figure 4-21 présente une version de cette approche de l’interface utilisateur composite. Cela est simplifiée, car vous pouvez avoir d’autres microservices qui sont des parties précises basées sur les différentes techniques de groupement — il dépend de si vous générez une approche traditionnelle de web (ASP.NET MVC) ou un SPA (Application à Page unique).

![](./media/image21.png)

**Figure 4-21**. Exemple d’une application d’interface utilisateur composite mise en forme par le serveur principal microservices

Chacune de ces microservices de composition de l’interface utilisateur serait similaire à une passerelle API petit. Mais dans ce cas, chacun est responsable à une petite zone de l’interface utilisateur.

Une approche de l’interface utilisateur composite qui est pilotée par microservices peut être plus délicat ou moins ainsi, selon les technologies d’interface utilisateur que vous utilisez. Par exemple, vous n’utiliserez pas les mêmes techniques pour la création d’une application web classiques que vous utilisez pour la création d’un SPA ou pour des applications mobiles natives (comme lorsque vous développez des applications Xamarin, ce qui peuvent être plus difficile de cette approche).

Le [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) exemple d’application utilise l’approche de l’interface utilisateur monolithique pour plusieurs raisons. Tout d’abord, il est une présentation de microservices et de conteneurs. Une interface utilisateur composite est plus avancée, mais également requiert plus de complexité lors de la conception et développement de l’interface utilisateur. En second lieu, eShopOnContainers fournit également une application mobile native basée sur Xamarin, ce qui rendrait plus complexes sur le client C\# côté.

Toutefois, nous vous encourageons à utiliser les références suivantes pour en savoir plus sur l’interface utilisateur en fonction de microservices de composite.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Interface utilisateur composite à l’aide de ASP.NET (de notamment atelier)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Le serveur frontal monolithique de l’Architecture de Microservices**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Le secret de composition de l’interface utilisateur une meilleure**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **VIKTOR Farcic. Y compris les composants Web frontaux en Microservices**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **La gestion de serveur frontal dans l’Architecture de Microservices**\
    [*http://Allegro.Tech/2016/03/Managing-Frontend-in-the-microservices-architecture.HTML*](http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Précédente] (microservices-adressabilité-service-registry.md) [suivant] (résilient-haute-disponibilité-microservices.md)
