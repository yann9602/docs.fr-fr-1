---
title: "Communication client à microservice directe et le modèle de la passerelle API"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Communication client à microservice directe et le modèle de la passerelle API"
keywords: Docker, Microservices, ASP.NET, conteneur, passerelle API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8227ec47888c7cf361f34c4c85a09c0666f886e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>Communication client à microservice directe et le modèle de la passerelle API

Dans une architecture microservices, chaque microservice expose un ensemble de points de terminaison fine‑grained (généralement). Cela peut affecter la communication client‑to‑microservice, comme expliqué dans cette section.

## <a name="direct-client-to-microservice-communication"></a>Communication client à microservice directe

Une approche possible consiste à utiliser une architecture de communication client à microservice directe. Dans cette approche, une application cliente peut envoyer des demandes directement à certaines le microservices, comme indiqué dans la Figure 4-12.

![](./media/image12.png)

**Figure 4-12**. À l’aide d’une architecture de communication client à microservice directe

Dans cette approche. chaque microservice possède un point de terminaison public, parfois avec un port TCP différent pour chaque microservice. Un exemple d’URL pour un service particulier peut être l’URL suivante dans Azure :

<http://eshoponcontainers.westus.cloudapp.Azure.com:88 />

Dans un environnement de production basé sur un cluster, l’URL serait mapper à l’équilibrage de charge utilisé dans le cluster, qui distribue ensuite les demandes entre le microservices. Dans les environnements de production, vous pourriez avoir un contrôleur de remise d’Application (ADC) comme [passerelle d’Application Azure](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) entre votre microservices et Internet. Il agit comme une couche transparente qui non seulement effectue l’équilibrage de charge, mais permet de sécuriser vos services en offrant la terminaison SSL. Cela améliore la charge de vos ordinateurs hôtes en déchargeant la terminaison SSL de gourmande en ressources processeur et autres droits de routage pour la passerelle d’Application Azure. Dans tous les cas, un équilibreur de charge et le connecteur Active Directory sont transparent à partir d’un point de vue de logique d’application architecture.

Une architecture de communication client à microservice directe peut être suffisante pour une petite application microservice, surtout si l’application cliente est une application web côté serveur comme une application ASP.NET MVC. Toutefois, lorsque vous générez important et complexes des applications basées sur les microservice (par exemple, lors de la gestion des dizaines de types de microservice), et en particulier lorsque les applications clientes sont des applications mobiles à distance ou des applications web SPA, cette approche est confronté à quelques problèmes.

Lors du développement d’une application volumineuse en fonction de microservices, tenez compte des questions suivantes :

-   *Comment les applications clientes peuvent réduire le nombre de demandes au serveur principal et réduire la communication bavarde à plusieurs microservices ?*

Interagir avec plusieurs microservices pour générer un seul écran de l’interface utilisateur d’augmente le nombre d’allers-retours sur Internet. Cela augmente la latence et la complexité du côté de l’interface utilisateur. Dans l’idéal, les réponses doivent être agrégées efficacement côté serveur, cela réduit la latence, étant donné que plusieurs éléments de données sont revenir en parallèle et une interface utilisateur peut afficher les données dès qu’il est prêt.

-   *Comment peut gérer des problèmes transversaux comme d’autorisation, les transformations de données et la distribution de requête dynamique ?*

Implémentation de sécurité et problèmes transversaux comme la sécurité et l’autorisation sur chaque microservice peuvent nécessiter des efforts de développement significatifs. Une approche possible consiste à ces services au sein de l’hôte Docker ou internes du cluster, afin de restreindre l’accès direct à partir de l’extérieur et pour implémenter ces problèmes transversaux dans un emplacement centralisé, comme une passerelle API.

-   *Comment les applications clientes peuvent communiquer avec les services qui utilisent des protocoles non adaptée à Internet ?*

Protocoles utilisés sur le côté serveur (par exemple, le protocole AMQP ou protocoles binaires) ne sont généralement pas prises en charge dans les applications clientes. Par conséquent, les requêtes doivent être exécutées via des protocoles tels que HTTP/HTTPS et traduits par la suite pour les autres protocoles. A *man in the middle* approche peut aider dans cette situation.

-   *Comment en forme une façade apportée en particulier pour les applications mobiles ?*

L’API de microservices plusieurs ne peut pas être également conçu pour les besoins des différentes applications clientes. Par exemple, les besoins d’une application mobile peuvent être différents de celui des besoins d’une application web. Pour les applications mobiles, vous devrez peut-être optimiser davantage afin que les réponses de données peuvent être plus efficaces. Ce faire, vous pouvez agréger des données à partir de plusieurs microservices et retourner un jeu unique de données et parfois en éliminant toutes les données dans la réponse n’est pas requis par l’application mobile. Et, bien entendu, vous pourrez compresser les données. Là encore, une façade ou une API entre l’application mobile et le microservices peut être pratique pour ce scénario.

## <a name="using-an-api-gateway"></a>À l’aide d’une passerelle d’API

Lorsque vous concevez et créez des applications volumineuses ou complexes microservice des applications avec plusieurs clients, une bonne approche à prendre en compte peut être un [passerelle API](http://microservices.io/patterns/apigateway.html). Il s’agit d’un service qui fournit un point d’entrée unique pour certains groupes de microservices. Il est similaire à la [modèle de contenu](https://en.wikipedia.org/wiki/Facade_pattern) à partir de la conception d’object‑oriented, mais dans ce cas, il fait partie d’un système distribué. Le modèle de la passerelle API est également parfois appelé « principal » pour le serveur frontal » [(BFF)](http://samnewman.io/patterns/architectural/bff/) car vous le générez lors de la réflexion sur les besoins de l’application cliente.

Figure 4-13 montre comment une passerelle API personnalisées peuvent tenir dans une architecture basée sur un microservice.
Il est important de souligner que dans ce diagramme, que vous utilisiez un seul service de passerelle API personnalisé faisant face à multiples et les applications clientes différente. Que fait est un risque important, car votre service de passerelle API sera augmente et évolue basée sur les nombreuses exigences différentes à partir des applications client. Finalement, il sera trop importants en raison de ces différents besoins et efficacement, il peut être très similaire à une application monolithique ou le service monolithique. C’est pourquoi il est recommandé de beaucoup de fractionner la passerelle API dans plusieurs services ou de plusieurs passerelles API plus petite, une par type de facteur de forme, par exemple.

![](./media/image13.png)

**Figure 4-13**. À l’aide d’une passerelle API implémenté comme service Web API personnalisée

Dans cet exemple, la passerelle API serait être implémentée comme un service Web API personnalisé en cours d’exécution en tant que conteneur.

Comme mentionné, vous devez implémenter plusieurs passerelles API afin que vous pouvez avoir une façade différents pour les besoins de chaque application cliente. Chaque passerelle API peut fournir une autre API adaptés pour chaque application cliente, voire même selon le facteur de forme client en implémentant le code de l’adaptateur spécifique qui en dessous appelle plusieurs microservices interne.

Une passerelle API personnalisée étant généralement une agrégation de données, vous devez être prudent avec elle. Elle ne pose généralement pas judicieux d’avoir une seule passerelle API l’agrégation de tous les microservices internes de votre application. Dans ce cas, il se comporte comme une agrégation monolithique ou l’orchestrator et viole microservice autonomie en associant tous les microservices. Par conséquent, les passerelles API doivent être séparés en fonction des limites de l’entreprise et act pas comme une agrégation de l’application entière.

Parfois, une passerelle API granulaire peut également être un microservice par lui-même et même a un domaine ou nom de l’entreprise et des données connexes. Ayant des limites de la passerelle API dictées par l’entreprise ou d’un domaine vous aidera à obtenir une meilleure conception.

Granularité au niveau de la passerelle API peut être particulièrement utile pour les applications d’interface utilisateur composites plus avancées en fonction de microservices, étant donné que le concept d’une passerelle API affinée est similaire à un service de composition de l’interface utilisateur. Nous aborderons cela plus tard dans le [création de l’interface utilisateur composite basée sur microservices](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

Par conséquent, pour de nombreuses applications et grand-taille moyenne, à l’aide d’une passerelle API personnalisée est généralement une bonne approche, mais pas comme un aggregator monolithique unique ou une unique passerelle centrale des API personnalisées.

Une autre approche consiste à utiliser un produit tel que [gestion des API Azure](https://azure.microsoft.com/services/api-management/) comme indiqué dans la Figure 4-14. Cette approche résout les besoins de votre passerelle API mais fournit des fonctionnalités telles que la collecte des informations à partir de votre API. Si vous utilisez une solution de gestion des API, une passerelle API est uniquement un composant au sein de cette solution de gestion des API complète.

![](./media/image14.png)

**Figure 4-14**. À l’aide de la gestion des API Azure pour votre passerelle API

Dans ce cas, quand à l’aide d’un produit, tels que la gestion des API Azure, le fait que vous pouvez avoir une seule passerelle API n’est pas donc risqué, car ces types de passerelles API sont « plus étroit », ce qui signifie que vous n’implémentez pas personnalisé code c# qui peut évoluer vers un monolithique composant. 

Ce type de produit agit plus comme un proxy inverse pour la communication en entrée, où vous pouvez également filtrer les API de la microservices interne plus appliquer l’autorisation à l’API publiées de ce niveau unique.

Les informations disponibles à partir d’un aide de système de gestion des API vous découvrez comment vos API est utilisées et comment ils fonctionnent. Ils ce faire, ce qui vous permet d’afficher près analytique en temps réel des rapports et d’identifier les tendances qui peuvent avoir un impact sur votre entreprise. De plus, vous pouvez avoir des journaux sur l’activité de demande et de réponse pour une analyse plus approfondie en ligne et hors connexion.

Avec la gestion des API Azure, vous pouvez sécuriser votre API à l’aide d’une clé, un jeton et le filtrage IP. Ces fonctionnalités vous permettent d’appliquer des quotas souples et affinées limites du taux de modifier la forme et le comportement de votre API à l’aide de stratégies et, améliorer les performances avec la réponse mise en cache.

Dans l’exemple d’application référence (eShopOnContainers) et de ce guide, nous limitons l’architecture à une architecture en conteneur plus simple et personnalisée afin de vous concentrer sur les conteneurs bruts sans utiliser PaaS des produits tels que la gestion des API Azure. Mais pour les grandes microservice applications déployées dans Microsoft Azure, nous vous encourageons à consulter et adopter la gestion des API Azure comme base pour vos passerelles API.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Le modèle de la passerelle API présente deux inconvénients :

-   L’inconvénient plus important est que, lorsque vous implémentez une passerelle d’API, vous sont couplage ce niveau avec le microservices interne. COUPLAGE à ceci peut introduire des difficultés graves pour votre application. Fait référence Clemens Vaster, architecte de l’équipe Azure Service Bus, à cette difficulté potentielle en tant que « la nouvelle ESB » dans son «[Microservices et messagerie](https://www.youtube.com/watch?v=rXi5CLjIQ9k)« session à GOTO 2016.

-   À l’aide d’une passerelle API microservices crée un point de défaillance unique possible supplémentaire.

-   Une passerelle API peuvent introduire des temps de réponse accru en raison de l’appel de réseau supplémentaire. Toutefois, cet appel supplémentaire a généralement moins d’impact qu’un client de l’interface qui est trop bavarde appeler directement la microservices interne.

-   Si ne pas monté en charge correctement, la passerelle API peut devenir un goulot d’étranglement.

-   Une passerelle API nécessite le coût de développement supplémentaires et une maintenance ultérieure si elle inclut une logique personnalisée et l’agrégation de données. Les développeurs doivent mettre à jour la passerelle API pour exposer des points de terminaison de chaque microservice. En outre, les modifications d’implémentation dans le microservices interne peuvent entraîner des modifications du code au niveau de la passerelle API. Toutefois, si la passerelle API applique simplement le contrôle de version, la journalisation et la sécurité (comme lorsque vous utilisez la gestion des API Azure), ce coût de développement supplémentaires ne peut-être pas s’appliquer.

-   Si la passerelle API est développée par une équipe unique, il peut y avoir un goulot d’étranglement de développement. Il s’agit d’une autre raison pourquoi il est préférable d’avoir plusieurs précis passerelles API qui répondent aux besoins de différents clients. Vous pourriez également séparer la passerelle API en interne en plusieurs parties ou couches qui sont détenus par les différentes équipes de travailler sur le microservices interne.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Charles Richardson. Modèle : Passerelle API / serveur principal de frontal**
    [*http://microservices.io/patterns/apigateway.html*](http://microservices.io/patterns/apigateway.html)

-   **Gestion des API Azure**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **UDI Dahan. Composition orientée services**\
    [*http://UdiDahan.com/2014/07/30/Service-Oriented-composition-with-Video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters. Microservices à GOTO 2016 et messagerie** (vidéo) [ *https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Précédente] (identifier-microservice-domaine-modèle-boundaries.md) [suivant] (communication de microservice architecture.md)
