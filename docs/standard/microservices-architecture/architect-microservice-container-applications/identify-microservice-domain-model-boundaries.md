---
title: "Identification des limites de modèle de domaine pour chaque microservice"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Identification des limites de modèle de domaine pour chaque microservice"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6fef11e5718706701abb29149c4c4a23ba39bde0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identifier les limites de modèle de domaine pour chaque microservice

Lors de l’identification des limites de modèle et de la taille de chaque microservice vise ne pas à accéder à la séparation plus granulaire possible, bien que vous devez ont tendance vers microservices small si possible. Au lieu de cela, votre objectif doit être pour accéder à la séparation plus significative guidée par votre connaissance du domaine. L’accent n’est pas sur la taille, mais plutôt sur les fonctions de l’entreprise. En outre, s’il existe clair cohésion nécessaire pour une certaine zone de l’application basée sur un grand nombre de dépendances, qui indique la nécessité d’un seul microservice, trop. Cohésion consiste à identifier comment dissocier ou microservices ensemble de groupe. Pour finir, alors que vous bénéficiez plus de connaissances sur le domaine, vous devez adapter la taille de votre microservice, itérative. Recherche la bonne taille n’est pas un processus Shot.

[SAM Newman](http://samnewman.io/), un promoteur reconnu de microservices et l’auteur du livre [Microservices de construction](http://samnewman.io/books/building_microservices/), met en évidence que vous devez concevoir votre microservices basée sur le modèle de contexte délimité (BC) (partie de conception domaine), introduit précédemment. Parfois, un BC peut être composée de plusieurs services physiques, mais pas vice versa.

Un modèle de domaine avec des entités de domaine spécifique s’applique dans un BC concrète ou microservice. Un BC délimite la mise en application d’un modèle de domaine et le développeur de fournit les membres de l’équipe une compréhension claire et partagée de ce qui doit être cohérent et ce qui peut être développé indépendamment. Ce sont les mêmes objectifs de microservices.

Est un autre outil pour informer vos choix de conception [la loi de Conway](https://en.wikipedia.org/wiki/Conway%27s_law), ce qui indique qu’une application reflètent les limites sociaux de l’organisation qui l’a produit. Mais parfois le contraire est vrai, organisation de l’entreprise est formée par le logiciel. Pour inverser la loi de Conway et générer les limites comme vous le souhaitez à être organisé, l’entreprise, vous devrez peut-être premiers pas dans la consultation des processus d’entreprise.

Afin d’identifier les contextes délimitées, est un modèle DDD qui peut être utilisé pour ce le [modèle de mappage de contexte](https://www.infoq.com/articles/ddd-contextmapping). Mappage de contexte, vous identifiez les différents contextes dans l’application et leurs limites. Il est courant d’avoir d’un contexte différent et les limites pour chaque sous-système petite, par exemple. Le mappage de contexte est un moyen de définir et de rendre explicite ces limites entre domaines. Un BC est autonome et inclut les détails d’un domaine unique : détails comme les entités de domaine et définit les contrats d’intégration avec d’autres BCs. Cela est similaire à la définition d’un microservice : il est autonome, il implémente certaines fonctionnalités de domaine et il doit fournir les interfaces. C’est pourquoi le mappage de contexte et le modèle de contexte de délimitée sont une bonne approche pour identifier les limites de modèle de domaine de votre microservices.

Lorsque vous concevez une application volumineuse, vous verrez comment son modèle de domaine peut être fragmenté, un expert du domaine du domaine de catalogue nommera entités différemment dans les domaines de catalogue et d’inventaire à un domaine d’expédition expert, pour l’instance. Ou l’entité de domaine utilisateur peut-être être différente de la taille et le nombre d’attributs lorsque vous traitez avec un expert CRM qui souhaitent stocker tous les détails sur le client que pour un tri expert de domaine qui a besoin uniquement des données partielles sur le client. Il est très difficile à lever l’ambiguïté de tous les termes de domaine dans tous les domaines liés à une application volumineuse. Mais le plus important est que vous ne devriez pas unifier les termes du contrat ; au lieu de cela, acceptez les différences et la richesse fournies par chaque domaine. Si vous essayez d’une base de données unifié pour l’application entière, tentatives d’un vocabulaire unifié seront difficiles et ne seront pas son droit à un des experts en plusieurs domaines. Par conséquent, BCs (implémentés en tant que microservices) vous aidera à clarifier où vous pouvez utiliser certains des termes de domaine, et où vous devez fractionner le système et de créer des BCs supplémentaires avec des domaines différents.

Vous savez que vous avez obtenu les limites de droite et les tailles de chaque BC et modèle de domaine si vous avez plusieurs relations fortes entre les modèles de domaine, et que vous ne sont généralement pas besoin fusionner les informations provenant de plusieurs modèles de domaine lors de l’exécution d’applications standard opérations.

Peut-être la meilleure réponse à la question de la taille que doit être un modèle de domaine pour chaque microservice est le suivant : elle doit avoir un BC autonome, comme isolé que possible, ce qui vous permet de travailler sans avoir à basculer constamment à d’autres contextes (autre modèles de microservice). Dans la Figure 4-10, vous pouvez voir comment plusieurs microservices (plusieurs BCs) chaque ont leur propre modèle et comment les entités peuvent être définies, selon les exigences spécifiques de chacun des domaines identifiés dans votre application.

![](./media/image10.png)

**Figure 4-10**. Identification des entités et des limites de microservice modèle

Figure 4-10 illustre un exemple de scénario lié à un système de gestion de conférence en ligne. Vous avez identifié plusieurs BCs qui pourrait être implémentés en tant que microservices, basé sur les domaines définis par des experts du domaine pour vous. Comme vous pouvez le voir, il existe des entités qui sont présentes uniquement dans un modèle de microservice unique, comme les paiements dans le paiement de microservice. Celles sera faciles à implémenter.

Toutefois, vous pouvez également disposer des entités qui ont une forme différente, mais partagent la même identité différents plusieurs modèles de domaine à partir de la microservices plusieurs. Par exemple, l’entité d’utilisateur est identifiée dans la gestion de conférences microservice. Ce même utilisateur, avec la même identité est celui nommé acheteurs dans le classement microservice, ou celui nommé Payer dans le paiement microservice et même l’un nommé client dans le Service clientèle de microservice. C’est pourquoi, en fonction de la [langage omniprésent](https://martinfowler.com/bliki/UbiquitousLanguage.html) qu’à l’aide de chaque expert du domaine, un utilisateur peut avoir une perspective différente, même avec des attributs différents. L’entité d’utilisateur dans le modèle de microservice nommé conférences Management peut-être la plupart de ses attributs de données personnelles. Toutefois, ce même utilisateur dans la forme de Payer dans le paiement de microservice ou dans la forme du client dans le Service clientèle de microservice devrez peut-être pas la même liste d’attributs.

Une approche similaire est illustrée dans la Figure 4-11.

![](./media/image11.png)

**Figure 4-11**. Décomposition des modèles de données traditionnelles en plusieurs modèles de domaine

Vous pouvez voir comment l’utilisateur est présent dans le modèle de microservice conférences gestion en tant que l’entité d’utilisateur et est également présent dans le formulaire de l’entité de l’acheteur dans le microservice de tarification, avec les autres attributs ou des détails relatifs à l’utilisateur lorsqu’il est en fait un acheteur. Chaque microservice ou la BC peut-être pas toutes les données relatives à une entité d’utilisateur, une partie seulement de celui-ci, selon le problème à résoudre ou le contexte. Par exemple, dans le modèle de microservice tarification, il est inutile l’adresse ou l’ID de l’utilisateur, simplement ID (en tant qu’identité) et l’état, ce qui aura un impact sur les remises lors de la tarification des sièges par acheteur.

L’entité siège a le même nom mais des attributs dans chaque modèle de domaine. Toutefois, les partages de siège identité basée sur le même ID, que se passe-t-il avec l’utilisateur et l’acheteur.

En fait, il est un concept partagé d’un utilisateur qui existe dans plusieurs services (domaines), qui partagent l’identité de cet utilisateur. Il existe cependant dans chaque modèle de domaine supplémentaires ou différents détails sur l’entité d’utilisateur. Par conséquent, il doit exister un moyen de mapper une entité d’utilisateur d’un domaine (microservice) à un autre.

Il existe plusieurs avantages à partage ne pas la même entité d’utilisateur avec le même nombre d’attributs entre les domaines. L’un des avantages sont pour réduire la duplication, afin que les modèles de microservice n’ont pas toutes les données qui n’a pas besoin. Un autre avantage rencontre un microservice maître qui possède un certain type de données par entité afin que les mises à jour et les requêtes pour ce type de données sont établies uniquement par ce microservice.


>[!div class="step-by-step"]
[Précédente] (distributed-données-management.md) [suivant] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
