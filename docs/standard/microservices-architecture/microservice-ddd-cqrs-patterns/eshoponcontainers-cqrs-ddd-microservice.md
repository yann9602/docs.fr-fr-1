---
title: Application CQRS et CQS approches dans un microservice DDD dans eShopOnContainers
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Application CQRS et CQS approches dans un microservice DDD dans eShopOnContainers
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a2c4429a75ca47d4fbcde868b95e76bc65ea2bef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Application CQRS et CQS approches dans un microservice DDD dans eShopOnContainers

La conception de la commande microservice à l’application de référence eShopOnContainers est basée sur les principes CQRS. Toutefois, il utilise l’approche la plus simple, qui est simplement séparant les requêtes à partir des commandes et à l’aide de la même base de données pour les actions.

L’essence de ces modèles et le point important ici, est que les requêtes sont idempotents : quel que soit le nombre de fois où vous interrogez un système, l’état de ce système ne change pas, vous pouvez même utiliser un modèle de données de différents « lecture » à la logique transactionnelle « écriture » modèle de domaine, bien que le tri microservices à l’aide de la même base de données. Par conséquent, il s’agit d’une approche CQRS simplifiée.

En revanche, des commandes qui déclenchent des transactions et les mises à jour de données, changent état du système. Avec les commandes, vous devez être prudent lorsque relatifs à la complexité et l’évolution des règles d’entreprise. Ceci est l’emplacement où vous souhaitez appliquer des techniques DDD pour avoir un système basé sur un modèle le mieux.

Les modèles DDD présentées dans ce guide ne doivent pas être appliqués globalement. Ils introduisent des contraintes de votre conception. Ces contraintes fournissent les avantages, notamment une meilleure qualité au fil du temps, en particulier dans les commandes et tout autre code qui modifie l’état du système. Toutefois, ces contraintes renforce la complexité avec moins d’avantages pour la lecture et l’interrogation des données.

Un modèle de ce type est le modèle d’agrégation, ce qui nous examiner plus dans les sections suivantes. Brièvement, dans le modèle d’agrégation, vous pouvez considérer qu’il existe plusieurs objets de domaine comme une unité unique à la suite de leur relation dans le domaine. Vous ne pourrez pas obtenir toujours avantages à partir de ce modèle dans les requêtes ; Cela peut augmenter la complexité de la logique de requête. Pour les requêtes en lecture seule, vous n’obtenez pas les avantages de traitement de plusieurs objets comme un agrégat unique. Vous n’obtenez que la complexité.

Comme indiqué dans la Figure 9-2, ce guide propose à l’aide de modèles de DDD uniquement dans la zone transactionnelle/mises à jour de votre microservice (autrement dit, comme déclenchée par des commandes). Les requêtes peuvent suivre une approche plus simple et doivent être séparées des commandes, suivant une approche CQRS.

Pour implémenter le côté « requêtes », vous pouvez choisir entre plusieurs méthodes, à partir de votre ORM complet comme EF Core, AutoMapper projections, des procédures stockées, vues, les vues matérialisées ou un micro ORM.

Dans ce guide et dans eShopOnContainers (en particulier le microservice tri), nous avons choisi d’implémenter des requêtes de droites à l’aide d’un micro ORM comme [Dapper](https://github.com/StackExchange/dapper-dot-net). Cela vous permet d’implémenter toute requête en fonction des instructions SQL pour obtenir des performances optimales, grâce à une infrastructure claire avec très peu de surcharge.

Notez que lorsque vous utilisez cette approche, toutes les mises à jour à votre modèle qui affectent le mode de conservation des entités à une base de données SQL doivent également les mises à jour distinctes pour les requêtes SQL utilisées par Dapper ou toutes les autres approches (non-EF) distincts à l’interrogation.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Modèles CQRS et DDD ne sont pas des architectures de niveau supérieur

Il est important de comprendre que CQRS et la plupart des modèles DDD (comme les couches DDD ou un modèle de domaine avec les agrégats) ne sont pas styles architecturaux, mais uniquement les modèles d’architecture. Microservices, SOA et pilotée par événements architecture (EDA) sont des exemples de styles de l’architecture. Elles décrivent un système de nombreux composants, tels que de nombreux microservices. CQRS et DDD décrivent un élément à l’intérieur d’un système unique ou un composant ; Dans ce cas, un problème à l’intérieur d’un microservice.

Délimitée contextes (BCs) utiliser différents modèles. Ils disposent de responsabilités différentes, et qui conduit à différentes solutions. Il est important de souligner que forcer le même modèle qu'everywhere entraîne la défaillance. N’utilisez pas de modèles CQRS et DDD partout. Plusieurs sous-systèmes, BCs ou microservices sont plus simples et peut être implémenté plus facilement à l’aide des services CRUD simples ou une autre approche.

Architecture d’une seule application : l’architecture de l’application système ou de bout en bout que vous créez (par exemple, l’architecture de microservices). Toutefois, la conception de chaque limitées de contexte ou de microservice au sein de cette application reflète son propre compromis et les décisions de conception interne à un niveau de modèles d’architecture. N’essayez pas d’appliquer les mêmes modèles d’architecture CQRS ou DDD partout.

####  <a name="additional-resources"></a>Ressources supplémentaires

-   **Martin Fowler. CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Greg Young. CQS vs. CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Greg Young. Les Documents CQRS**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Greg Young. CQRS, de tâches en fonction des interfaces et événements approvisionnement**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **UDI Dahan. Clarification CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **(ES) événement rurale**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[Précédente] (apply-simplified-microservice-cqrs-ddd-patterns.md) [suivant] (cqrs-microservice-reads.md)
