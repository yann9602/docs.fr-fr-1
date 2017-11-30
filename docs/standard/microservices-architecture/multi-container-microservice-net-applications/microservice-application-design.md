---
title: "Conception d’une application orientée de microservice"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conception d’une application orientée de microservice"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1e1dc919c7e35580576c86b4cf9872b4f8cea2c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="designing-a-microservice-oriented-application"></a>Conception d’une application orientée de microservice

Cette section se concentre sur le développement d’une application hypothétique côté serveur enterprise.

## <a name="application-specifications"></a>Spécifications de l’application

L’application hypothétique gère les requêtes par l’exécution de la logique métier, l’accès aux bases de données, puis de retourner les réponses XML, JSON ou HTML. Disons que l’application doit prendre en charge un éventail de clients, y compris les navigateurs de bureau exécutant des Applications à Page unique (ZPS), les applications web classiques, les applications web mobiles et des applications mobiles natives. L’application peut exposer également une API à des tiers à consommer. Il doit également être en mesure d’intégrer de façon asynchrone, de son microservices ou les applications externes afin que la méthode permet de résilience de la microservices en cas de défaillance partielle.

L’application se compose de ces types de composants :

-   Composants de la présentation. Ceux-ci sont responsables de la gestion de l’interface utilisateur et la consommation de services à distance.

-   Logique de domaine ou d’entreprise. Il s’agit d’une logique de domaine de l’application.

-   Logique d’accès de base de données. Il s’agit de composants d’accès aux données responsable de l’accès aux bases de données (SQL ou NoSQL).

-   Logique de l’intégration d’application. Cela inclut un canal de messagerie, principalement en fonction de brokers de message.

L’application demandera une haute évolutivité, tout en autorisant son sous-systèmes verticales montée en puissance parallèle de manière autonome, car certains sous-systèmes nécessitera plus grande que d’autres.

L’application doit pouvoir être déployée dans plusieurs environnements d’infrastructure (plusieurs clouds publics et locaux) et doit idéalement être inter-plateformes, la possibilité de déplacer facilement à partir de Linux vers Windows (ou vice versa).

## <a name="development-team-context"></a>Contexte d’équipe de développement

Nous supposons également les éléments suivants concernant le processus de développement de l’application :

-   Vous avez plusieurs équipes de développement en mettant l’accent sur différents domaines d’activité de l’application.

-   Membres de l’équipe doivent être plus productifs rapidement, et l’application doit être facile à comprendre et à modifier.

-   L’application aura une évolution à long terme et l’évolution des règles d’entreprise.

-   Vous avez besoin d’une bonne maintenabilité à long terme, qui implique l’agilité lors de l’implémentation de nouvelles modifications à l’avenir tout en étant en mesure de mettre à jour plusieurs sous-systèmes avec un impact minimal sur les autres sous-systèmes.

-   Vous souhaitez intégration continue de pratique et de déploiement continu de l’application.

-   Vous souhaitez tirer parti des nouvelles technologies (infrastructures, langages de programmation, etc.) lors de l’évolution de l’application. Vous ne souhaitez pas effectuer une migration complète de l’application lors du déplacement vers de nouvelles technologies, car qui serait entraîner des coûts élevés et avoir un impact sur la prévisibilité et la stabilité de l’application.

## <a name="choosing-an-architecture"></a>Choix d’une architecture

Quelle doit être l’architecture de déploiement d’application ? Les spécifications de l’application, ainsi que le contexte de développement, recommandons vivement que vous devez organiser l’application en décomposant en sous-systèmes autonomes sous la forme de microservices de collaboration et de conteneurs, où un microservice. est un conteneur.

Dans cette approche, chaque service (conteneur) implémente un ensemble de fonctions connexes avec précision et en cohésion. Par exemple, une application peut consister en des services tels que le service de catalogue, ordre de service, service de panier d’achat, service de profil utilisateur, etc..

Microservices communiquer à l’aide de protocoles tels que HTTP (REST), mais également de façon asynchrone (c'est-à-dire AMQP) dès que possible, en particulier lorsque propagation des mises à jour avec les événements d’intégration.

Microservices sont développés et déployés en tant que conteneurs indépendamment les unes des autres. Cela signifie qu’une équipe de développement peut être développement et le déploiement d’un certain microservice sans affecter d’autres sous-systèmes.

Chaque microservice possède sa propre base de données, ce qui permet de découpler complètement à partir d’autres microservices. Lorsque cela est nécessaire, la cohérence entre les bases de données à partir de différents microservices est obtenue à l’aide d’événements d’intégration au niveau de l’application (via un bus d’événements logique), comme géré dans la commande et de répartition de responsabilité de requête (CQRS). Par conséquent, les contraintes de l’entreprise doivent adopter la cohérence éventuelle entre le microservices plusieurs et bases de données associées.

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers : une application de référence pour le .NET Core et microservices déployé à l’aide de conteneurs

Afin de pouvoir vous concentrer sur l’architecture et les technologies au lieu de réfléchir à un domaine d’entreprise hypothetic que vous ne savez ne peut-être pas, nous avons sélectionné un domaine d’entreprise connue, à savoir, une application de commerce électronique simplifiée (Boutique) qui présente un catalogue de les produits, prend des commandes à partir de clients, vérifie le stock et effectue d’autres fonctions d’entreprise. Ce code de la source d’application basée sur le conteneur est disponible dans le [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) référentiel GitHub.

L’application se compose de plusieurs sous-systèmes, y compris plusieurs magasin UI frontaux (une application Web et une application mobile native), ainsi que les principaux microservices et les conteneurs pour toutes les opérations côté serveur requises. Figure 8-1 montre l’architecture de l’application de référence.

![](./media/image1.png)

**Figure 8-1**. Les eShopOnContainers référencer l’application, en indiquant une communication client à microservice directe et le bus d’événements

**Environnement d’hébergement**. Figure 8-1, vous voyez plusieurs conteneurs sont déployés au sein d’un seul hôte Docker. Qui peut être le cas lors du déploiement sur un seul hôte Docker avec la docker-composer des commandes. Toutefois, si vous êtes à l’aide d’un orchestrator ou cluster de conteneur, chaque conteneur peut être en cours d’exécution dans un autre ordinateur hôte (nœud), et n’importe quel nœud pouvant s’exécuter n’importe quel nombre de conteneurs, comme expliqué précédemment dans la section architecture.

**Architecture de communication**. L’application eShopOnContainers utilise deux types de communication, en fonction du type de l’action fonctionnel (requêtes par rapport aux mises à jour et de transactions) :

-   Communications client à microservice directe. Cela est utilisé pour les requêtes et lors de l’acceptation des mises à jour ou des commandes transactionnelles à partir des applications client.

-   Communication asynchrone basé sur des événements. Cela se produit via un bus d’événements se propager les mises à jour sur microservices ou pour intégrer des applications externes. Le bus d’événements peut être implémenté avec les technologies d’infrastructure de service broker de messagerie comme RabbitMQ ou à l’aide du bus de service de niveau supérieur tels que Azure Service Bus, NServiceBus, MassTransit ou Brighter.

L’application est déployée en tant qu’ensemble de microservices sous la forme de conteneurs. Les applications clientes peuvent communiquer avec ces conteneurs ainsi que communiquer entre microservices. Comme mentionné, cette architecture initiale utilise une architecture de communication client à microservice directe, ce qui signifie qu’une application cliente peut envoyer des demandes à chacune de la microservices, de façon directement. Chaque microservice possède un point de terminaison public comme https://servicename.applicationname.companyname. Si nécessaire, chaque microservice peut utiliser un port TCP différent. En production, permettant d’associer URL à équilibrage de charge du microservices, qui répartit les demandes entre les instances disponibles de microservice.

**Remarque importante sur la passerelle API vs. Communication directe dans eShopOnContainers.** Comme expliqué dans la section de l’architecture de ce guide, l’architecture de communication client à microservice directe peut avoir des inconvénients lorsque vous générez une application important et complexe microservice. Mais il peut être suffisant pour une petite application, par exemple, dans l’eShopOnContainers démarrage de l’application, où l’objectif est de vous concentrer sur l’obtention d’une simple application basée sur un conteneur sur Docker et nous ne vouliez créer une passerelle API monolithique unique peut avoir un impact sur le autonomie des microservices développement.

Toutefois, si vous souhaitez concevoir une grande application microservice avec des dizaines de microservices, nous recommandons vivement que vous envisagez du modèle de la passerelle API, comme expliqué dans la section architecture.
Cette décision architecture pourrait être refactorisée une fois que vous réfléchissez concernant les applications de l’environnement de production et de façades de spécialement à cet effet pour les clients distants. Avoir plusieurs passerelles API personnalisées en fonction du facteur de forme applications client peut offrir des avantages en ce qui concerne l’agrégation des données différentes par l’application cliente, plus vous pouvez masquer des microservices internes ou des API pour les applications client et autoriser dans ce niveau unique. 

Toutefois et comme indiqué, soyez attentif aux contre volumineux et monolithique passerelles API qui peut arrêter l’autonomie du développement des votre microservices.

### <a name="data-sovereignty-per-microservice"></a>Souveraineté de données par microservice

Dans l’exemple d’application, chaque microservice possède sa propre base de données ou source de données et chaque base de données ou source de données est déployée en tant qu’un autre conteneur. Cette décision de conception a été effectuée uniquement pour faciliter le travail à un développeur d’obtenir le code à partir de GitHub, cloner et ouvrez-le dans Visual Studio ou Visual Studio Code. Ou, sinon, il facilite la tâche compiler les images Docker personnalisés à l’aide de .NET Core CLI et le Docker et de déployer et de les exécuter dans un environnement de développement de Docker. Dans les deux cas, l’utilisation de conteneurs pour les données sources permet aux développeurs générer et déploiement en quelques minutes, sans avoir à configurer une base de données externe ou toute autre source de données avec des dépendances de disque durs sur l’infrastructure (cloud ou localement).

Dans un environnement de production réel, pour la haute disponibilité et l’évolutivité, les bases de données doivent être basées sur les serveurs de base de données dans le nuage ou sur site, mais pas dans les conteneurs.

Par conséquent, les unités de déploiement pour microservices (et même pour les bases de données de cette application) sont des conteneurs Docker, et l’application de référence est une application conteneur multiples qui prend en compte les principes de microservices.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **eShopOnContainers référentiel GitHub. Code source pour l’application de référence**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>Avantages d’une solution basée sur les microservice

Une solution en fonction de microservice présente de nombreux avantages :

**Chaque microservice est relativement faible, facile à gérer et faire évoluer**. Plus précisément :

-   Il est facile pour un développeur de comprendre et de prise en main rapidement une bonne productivité.

-   Démarrage des conteneurs rapide, ce qui permet aux développeurs plus productif.

-   Un IDE tel que Visual Studio peut charger des projets plus petits rapides, qui effectue les développeurs productifs.

-   Chaque microservice permettre être conçu, développé et déployé indépendamment des autres microservices, qui fournit l’agilité, car il est plus facile de déployer de nouvelles versions de microservices fréquemment.

**Il est possible de montée en charge les zones individuelles de l’application**. Par exemple, vous devrez peut-être le service de catalogue ou le service du panier d’achat à l’échelle, mais pas le processus de commande. Une infrastructure de microservices sera beaucoup plus efficace en ce qui concerne les ressources utilisées lors de la montée en puissance parallèle à celle une architecture monolithique.

**Vous pouvez diviser le travail de développement entre plusieurs équipes**. Chaque service peut être détenue par une équipe de développement unique. Chaque équipe peut gérer, développer, déployer et mettre à l’échelle de leur service, indépendamment du reste des équipes.

**Les problèmes sont plus isolés**. S’il existe un problème dans un service, seulement ce service est affecté initialement (sauf lorsque la conception incorrecte est utilisée avec des dépendances directes entre microservices) et autres services peuvent continuer à traiter les demandes. En revanche, un composant défectueux dans une architecture de déploiement monolithique peut arrêter l’ensemble du système, notamment si elle implique des ressources, comme une fuite de mémoire. En outre, lorsqu’un problème dans un microservice est résolu, vous pouvez déployer simplement la microservice affecté sans affecter le reste de l’application.

**Vous pouvez utiliser les dernières technologies**. Étant donné que vous pouvez commencer à développer des services de manière indépendante et les exécuter côte à côte (grâce aux conteneurs et .NET Core), commencer à utiliser les dernières technologies et infrastructures échelonnées au lieu de blocage sur une pile ou une infrastructure pour l’ensemble plus anciens application.

## <a name="downsides-of-a-microservice-based-solution"></a>Inconvénients d’une solution basée sur les microservice

Une solution en fonction de microservice a également des inconvénients :

**Application distribuée**. Distribution de l’application ajoute une complexité pour les développeurs lorsqu’ils sont de conception et de création des services. Par exemple, les développeurs doivent implémenter communication interservices à l’aide des protocoles tels que HTTP ou AMPQ, ce qui augmente la complexité pour les tests et la gestion des exceptions. Il ajoute également une latence dans le système.

**La complexité du déploiement**. Une application qui a des dizaines de types de microservices et a besoin d’une haute évolutivité (il doit être en mesure de créer des instances par service et équilibrer les services sur plusieurs hôtes) signifie un degré élevé de complexité de déploiement pour la gestion et des opérations informatiques. Si vous n’utilisez pas une infrastructure orientée de microservice (comme un orchestrator et du Planificateur), que la complexité supplémentaire peut nécessiter beaucoup plus d’efforts de développement à l’application d’entreprise lui-même.

**Les transactions atomiques**. Les transactions atomiques entre plusieurs microservices généralement ne sont pas possibles. Les exigences métier doivent adopter la cohérence éventuelle entre plusieurs microservices.

**Augmente les besoins en ressources globales** (total de mémoire, des disques et des ressources réseau pour tous les serveurs ou les ordinateurs hôtes). Dans de nombreux cas, lorsque vous remplacez une application monolithique avec une approche microservices, la quantité de ressources globales requises par l’application microservice sera supérieure aux besoins de l’infrastructure de l’application monolithique d’origine. Il s’agit, car le niveau plus élevé de granularité et de services distribués nécessite des ressources plus globales. Toutefois, étant donné le faible coût des ressources en général et l’avantage de permettre la montée en puissance parallèle uniquement certaines zones de l’application par rapport aux coûts à long terme lors de l’évolution des applications monolithiques, l’utilisation accrue de ressources est généralement un bon compromis pour volumineux, applications à long terme.

**Problèmes de communication de direct client‑to‑microservice**. Si l’application est élevée, avec des dizaines de microservices, problèmes et limitations sont si l’application requiert des communications client à microservice directe. Un problème est une incompatibilité possible entre les besoins du client et les API exposées par chacun du microservices. Dans certains cas, l’application cliente deviez apporter de nombreuses demandes distinctes pour composer l’interface utilisateur, ce qui peut être inefficace sur Internet et ne conviendrait pas sur un réseau mobile. Par conséquent, les demandes à partir de l’application cliente pour le système principal doivent être réduites.

Un autre problème avec les communications client à microservice directs est que certains microservices peut utiliser les protocoles qui ne sont pas compatibles avec le Web. Un service peut utiliser un protocole binaire, lors d’un autre service peut utiliser la messagerie AMQP. Ces protocoles ne sont pas firewall‑friendly et sont mieux utilisées en interne. En règle générale, une application doit utiliser des protocoles tels que HTTP et WebSockets pour communiquer en dehors du pare-feu.

Encore un autre inconvénient avec cette approche client‑to‑service direct est qu’elle rend difficile à refactoriser les contrats pour ces microservices. Au fil du temps les développeurs souhaitent modifier la façon dont le système est partitionné dans les services. Par exemple, ils peuvent fusionner les deux services ou fractionner un service en deux ou plusieurs services. Toutefois, si les clients communiquent directement avec les services, exécution de ce type de refactorisation peut empêcher la compatibilité avec les applications clientes.

Comme mentionné dans la section architecture, lors de la conception et création d’une application complexe basée sur microservices, vous pouvez envisager l’utilisation de plusieurs passerelles API affinées au lieu de l’approche de communication directe client‑to‑microservice plus simple.

**Partitionnement de la microservices**. Enfin, quel que soit l’approche que vous prenez pour votre architecture microservice, un autre défi consiste à décider comment partitionner une application de bout en bout dans plusieurs microservices. Comme indiqué dans la section de l’architecture du guide, il existe plusieurs techniques et les approches. En fait, vous devez identifier les zones de l’application qui sont découplées à partir des autres domaines, et qui ont un nombre faible de dépendances dures. Dans de nombreux cas, il est aligné au partitionnement des services en cas d’utilisation. Par exemple, dans notre application de la Boutique, nous avons un service de tri qui est responsable de toute la logique métier liée au processus de commande. Nous avons également le service de catalogue et le service du panier d’achat qui implémentent les autres fonctions. Dans l’idéal, chaque service doit avoir uniquement un petit ensemble de responsabilités. Cela est similaire au principe de responsabilité unique (SRP) appliqué aux classes, qui stipule qu’une classe doit avoir uniquement une raison à modifier. Mais dans ce cas, il est microservices, pour que l’étendue soit supérieure à une seule classe. Surtout, un microservice doit être complètement autonome, de bout en bout, y compris la responsabilité de ses propres sources de données.

## <a name="external-versus-internal-architecture-and-design-patterns"></a>Externe par rapport à des modèles de conception et l’architecture internes

L’architecture externe est l’architecture de microservice composée par plusieurs services, suivant les principes décrits dans la section de l’architecture de ce guide. Toutefois, selon la nature de chaque microservice, indépendamment d’architecture de haut niveau de microservice vous choisissez, il est commun et parfois conseillé de posséder différentes architectures internes, chacun basé sur des modèles différents pour différents microservices. Le microservices pouvez même utiliser les différentes technologies et les langages de programmation. Figure 8-2 illustre cette diversité.

![](./media/image2.png)

**Figure 8-2**. Externe par rapport à la conception et l’architecture interne

Par exemple, dans notre *eShopOnContainers* microservices de profil exemple, le catalogue, du panier d’achat et utilisateur sont simples (en fait, les sous-systèmes CRUD). Par conséquent, leur conception et architecture interne est simple. Toutefois, vous pouvez avoir d’autres microservices, telles que le tri microservice, qui est plus complexe et représente l’évolution des règles d’entreprise avec un haut degré de complexité du domaine. Dans ce cas, vous souhaiterez implémenter des modèles plus avancés dans un microservice particulier, telles que celles définies avec les approches de conception domaine (DDD), comme nous le faisons les *eShopOnContainers* classement microservice. (Nous allons examiner ces modèles DDD dans la section qui explique l’implémentation de la *eShopOnContainers* classement microservice.)

Une autre raison d’une technologie différente par microservice peut être la nature de chaque microservice. Par exemple, il peut être préférable d’utiliser un langage de programmation fonctionnels comme F\#, ou même un langage tel que R si vous ciblez AI et l’apprentissage de domaines, au lieu d’un langage de programmation plus orientée objet tels que C\#.

Le point important est que chaque microservice peut avoir une architecture interne différente en fonction des modèles de conception. Microservices pas toutes doivent être implémentées à l’aide des modèles avancés DDD, car qui serait être trop d’ingénierie les. De même, microservices complexes avec une logique métier évolution ne doit pas être implémenté en tant que composants CRUD, ou vous pouvez se retrouver avec code de basse qualité.



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>Le nouveau monde : plusieurs modèles d’architecture et microservices polyglot

Il existe de nombreux modèles d’architecture utilisées par les développeurs et aux architectes logiciels. Voici quelques exemples (combinant les styles de l’architecture et les modèles d’architecture) :

-   Simple CRUD, niveau unique, simple couche.

-   [Traditionnel N couches](https://msdn.microsoft.com/en-us/library/ee658109.aspx#Layers).

-   [Domaine-Driven Design N couches](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/).

-   [Nettoyer l’Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html) (tel qu’utilisé avec [eShopOnWeb](http://aka.ms/WebAppArchitecture))

-   [Commande et de répartition de responsabilité de la requête](https://martinfowler.com/bliki/CQRS.html) (CQRS).

-   [Pilotée par événements Architecture](https://en.wikipedia.org/wiki/Event-driven_architecture) (EDA).

Vous pouvez également générer des microservices avec de nombreuses technologies et les langages, tels que des API Web ASP.NET Core, NancyFx, ASP.NET Core SignalR (disponible avec .NET Core 2), F\#, Node.js, Python, Java, C++, GoLang et bien plus encore.

Le point important est qu’aucun modèle d’architecture particulière ou style, ni une technologie particulière, est adaptée à toutes les situations. Figure 8-3 illustre certaines approches et des technologies (mais pas dans un ordre particulier) qui peuvent être utilisés dans différentes microservices.

![](./media/image3.png)

**Figure 8-3**. Modèles architecturaux multiples et le monde microservices polyglot

Comme indiqué dans la Figure 8-3, dans les applications composé de nombreuses microservices (délimitée contextes dans la terminologie de conception domaine, ou simplement « sous-systèmes » en tant que microservices autonome), vous pouvez implémenter chaque microservice d’une manière différente. Chacun peut ont un modèle d’architecture différente et utiliser différentes langues et les bases de données en fonction de la nature de l’application, les besoins de l’entreprise et les priorités. Dans certains cas, le microservices peut être similaire. Mais qui n’est pas généralement le cas, étant donné que la limite de contexte et les exigences de chaque sous-système sont généralement différents.

Par exemple, pour une application de gestion CRUD simple, il peut être pas judicieux de concevoir et implémenter des modèles DDD. Mais pour votre domaine de base ou d’un cœur de métier, vous devrez peut-être appliquer des modèles plus avancés pour attaquer la complexité d’entreprise avec l’évolution des règles d’entreprise.

En particulier lorsque vous travaillez avec grandes applications composées par plusieurs sous-systèmes, vous ne devez pas appliquer une architecture de niveau supérieur unique basée sur un modèle d’architecture unique. Par exemple, CQRS ne doit pas être appliquée comme une architecture de niveau supérieur pour un ensemble de l’application, mais il peut être utile pour un ensemble spécifique de services.

Aucune puce silver ou un modèle d’architecture adéquate pour tous les cas donné existe. Vous ne pouvez pas « un modèle d’architecture pour toutes les règles. » Selon les priorités de chaque microservice, vous devez choisir une approche différente pour chacune, comme expliqué dans les sections suivantes.


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (données-driven-crud-microservice.md)
