---
title: "Application simplifiée des modèles CQRS et DDD dans un microservice."
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Application simplifiée des modèles CQRS et DDD dans un microservice."
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 99fd7ce32039742e23f8e01aa4c33cddd7a9f698
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Application simplifiée des modèles CQRS et DDD dans un microservice.

CQRS est un modèle d’architecture qui sépare les modèles pour lire et écrire des données. Le terme connexe [séparation de requête de commande (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) a été initialement définie par Bertrand Meyer dans son livre *Construction de logiciel orienté objet*. L’idée est que vous pouvez diviser les opérations d’un système en deux catégories nettement séparées :

-   Requêtes. Ces retournent un résultat et que vous ne modifiez pas l’état du système, et ils ne contiennent pas d’effets secondaires.

-   Commandes. Ces modifications de l’état d’un système.

CQS est un concept simple : il s’agit de méthodes dans le même objet en cours de requêtes ou commandes. Chaque méthode retourne l’état ou mute, état, mais pas les deux. Même un objet de modèle de référentiel unique peut respecter CQS. CQS peut être considéré comme un principe fondamental pour CQRS.

[Commande et répartition de responsabilité de requête (CQRS)](https://martinfowler.com/bliki/CQRS.html) a été introduite par Greg Young et fortement promue par Udi Dahan et d’autres. Il est basé sur le principe CQS, bien qu’il est plus détaillée. Il peut être considéré comme un modèle basé sur les commandes et les événements et éventuellement de messages asynchrones. Dans de nombreux cas, CQRS est lié à des scénarios plus avancés, comme une base de données physique pour les lectures (requêtes) que pour les écritures (mises à jour). En outre, un système CQRS plus ont évolué peut implémenter [(ES) événement rurale](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) pour votre base de données mises à jour, par conséquent, vous serez uniquement stocker les événements dans le modèle de domaine au lieu de stocker les données d’état actuel. Toutefois, cela n’est pas l’approche utilisée dans ce guide ; Nous utilisons l’approche la plus simple de la CQRS, qui se compose uniquement de séparer les requêtes à partir des commandes.

L’aspect de séparation de CQRS est obtenue en regroupant les opérations de requête dans une couche et les commandes dans une autre couche. Chaque couche possède son propre modèle de données (Notez que nous dire le modèle, pas nécessairement une base de données) et est construit à l’aide de sa propre combinaison de technologies et de modèles. Plus important encore, les deux couches peuvent être dans le même niveau ou microservice, comme dans l’exemple (classement microservice) utilisé dans ce guide. Ou peut être implémentés sur microservices différents ou des processus afin de pouvoir être optimisés et monté en charge séparément sans affecter les unes des autres.

CQRS implique deux objets pour une opération de lecture/écriture où dans d’autres contextes existe. Il existe des raisons d’avoir une base de données dénormalisées lectures, vous pouvez en savoir plus sur dans la documentation CQRS plus avancée. Mais nous n’utilisons pas cette approche ici, où l’objectif est d’avoir plus de souplesse dans les requêtes au lieu de limiter les requêtes avec des contraintes à partir de modèles DDD comme agrégats.

Un exemple de ce type de service est le tri microservice à partir de l’application de référence eShopOnContainers. Ce service implémente un microservice basé sur une approche CQRS simplifiée. Il utilise une source de données ou base de données, mais deux modèles logiques plus les modèles DDD pour le domaine transactionnels, comme illustré dans la Figure 9-2.

![](./media/image2.png)

**Figure 9-2**. Simplifiée CQRS et DDD basés sur un microservice

La couche application peut être l’API Web elle-même. L’aspect de conception importante ici est que le microservice a fractionne les requêtes et les ViewModel (modèles de données créés spécialement pour les applications clientes) à partir des commandes, de modèle de domaine et de transactions suivant le modèle CQRS. Cette approche permet de conserver les requêtes indépendante de restrictions et les contraintes provenant des modèles DDD qui ne sont pertinentes pour les transactions et les mises à jour, comme expliqué dans les sections suivantes.


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (eshoponcontainers-cqrs-ddd-microservice.md)
