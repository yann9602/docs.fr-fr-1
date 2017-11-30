---
title: "Défis et solutions pour la gestion des données distribuées"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Défis et solutions pour la gestion des données distribuées"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f961475b40c74bf448cff1aeae04ae4866360e52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Défis et solutions pour la gestion des données distribuées

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Défi \#1 : comment définir les limites de chaque microservice

Définir les limites de microservice est sans doute le premier test, que toute personne rencontre. Chaque microservice doit s’agir d’une partie de votre application et chaque microservice doit être autonome avec tous les avantages et les défis auxquels il transmet. Mais comment identifier ces limites ?

Tout d’abord, vous devez vous concentrer sur les modèles de domaine logique de l’application et les données associées. Vous devez essayer d’identifier découplées îlots de données et des contextes différents au sein de la même application. Chaque contexte peut avoir un langage différent (conditions commerciales). Les contextes doivent être définis et gérés indépendamment. Les entités utilisées dans ces contextes différents peuvent sembler identiques, mais vous pouvez découvrir que dans un contexte spécifique, un concept métier avec l’un est utilisé à des fins différentes dans un autre contexte et peut-être même un autre nom. Par exemple, un utilisateur peut être référencé en tant qu’utilisateur dans le contexte d’identité ou l’appartenance, en tant que client dans un contexte CRM, comme un acheteur dans un contexte de tri et ainsi de suite.

La façon de vous identifiez les limites entre plusieurs contextes d’application avec un domaine différent pour chaque contexte est exactement comment vous pouvez identifier les limites de chaque microservice de l’entreprise et ses données associées données et le modèle de domaine. Vous tentez de réduire le couplage entre ces microservices toujours. Ce guide passe en plus de détails sur cette conception de modèle d’identification et de domaine dans la section [identification des limites de modèle de domaine pour chaque microservice](#identifying-domain-model-boundaries-for-each-microservice) plus tard.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Défi \#2 : comment créer des requêtes qui extraient des données à partir de plusieurs microservices

Un deuxième consiste à implémenter des requêtes qui récupèrent des données à partir de plusieurs microservices, tout en évitant la communication bavarde à la microservices à partir d’applications de client à distance. Un exemple peut être un seul écran à partir d’une application mobile qui a besoin d’afficher les informations utilisateur qui sont détenues par le panier d’achat, le catalogue et microservices d’identité utilisateur. Un autre exemple consisterait à un rapport complex impliquant plusieurs tables situées dans plusieurs microservices. La solution dépend de la complexité des requêtes. Mais dans tous les cas, vous devrez un moyen pour regrouper les informations si vous souhaitez améliorer l’efficacité dans les communications de votre système. Les solutions les plus populaires sont les suivantes :

**Passerelle API**. Pour l’agrégation de données simple à partir de plusieurs microservices qui possèdent des bases de données différentes, l’approche recommandée est un microservice d’agrégation visé une passerelle API. Toutefois, vous devez faire attention à la mise en œuvre de ce modèle, car il peut être un point d’étranglement dans votre système, et il peut violer le principe d’autonomie de microservice. Pour atténuer ce risque, vous pouvez avoir plusieurs passerelles d’API précis pour chaque une en mettant l’accent sur une « tranche » à la verticale ou d’un secteur d’activité du système. Le modèle de la passerelle API est expliqué plus en détail dans la section de l’utilisation une passerelle API ultérieurement.

**CQRS avec des tables de la requête/lecture**. Une autre solution pour agréger les données à partir de plusieurs microservices est la [modèle de vue matérialisée](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). Dans cette approche, vous générez, à l’avance (préparer les données dénormalisées avant les requêtes réelles se produisent), une table en lecture seule avec les données appartenant à plusieurs microservices. La table a un format adapté aux besoins de l’application cliente.

Pensez à quelque chose comme l’écran pour une application mobile. Si vous avez une base de données, vous pourrez rassembler les données de cet écran à l’aide d’une requête SQL qui effectue une jointure complexe impliquant plusieurs tables. Toutefois, lorsque vous avez plusieurs bases de données, et chaque base de données est détenu par un autre microservice, vous ne peut pas interroger les bases de données et créer une jointure SQL. Votre requête complexe devient un défi. Vous pouvez traiter la demande à l’aide d’une approche CQRS, vous créez une table dénormalisée dans une autre base de données qui est utilisé pour les requêtes. La table permettre être conçue spécifiquement pour les données que vous avez besoin pour la requête complexe, avec une relation entre les champs requis par votre écran de l’application et les colonnes dans la table de requête. Il peut également servir à des fins de création de rapports.

Cette approche résout non seulement le problème d’origine (la façon de requêtes et de jointure entre microservices) ; Il améliore également les performances considérablement quand elle est comparée avec une jointure complexe, car vous avez déjà les données nécessaires à l’application dans la table de requête. Bien entendu, à l’aide de la commande et répartition de responsabilité de requête (CQRS) avec des tables de la requête/lecture signifie que le travail de développement supplémentaire, et vous devrez adopter la cohérence éventuelle. Néanmoins, les exigences de performances et haute évolutivité dans [scénarios collaboratifs](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (ou des scénarios de concurrence, en fonction du point de vue) est où vous devez appliquer CQRS avec plusieurs bases de données.

**« Données à froid » dans les bases de données centrales**. Pour des rapports complexes et les requêtes qui ne nécessitent pas de données en temps réel, une approche courante consiste à exporter votre » à chaud données » (données transactionnelles à partir de la microservices) en tant que « données à froid » dans les bases de données volumineuses qui sont utilisés uniquement pour le rapport. Ce système de base de données centrale peut être un système basé sur les données volumineuses, telles que Hadoop, un entrepôt de données comme une basée sur Azure SQL Data Warehouse, ou même une seule base de données SQL utilisée pour les rapports (si la taille ne sera pas un problème).

Gardez à l’esprit que cette base de données centralisée serait utilisée uniquement pour les requêtes et des rapports qui n’ont pas besoin de données en temps réel. Les mises à jour et les transactions, en tant que votre source de vérité, d’origine doivent être dans vos données microservices. La méthode que vous devez synchroniser les données serait à l’aide de communication pilotée par événements (traitée dans les sections suivantes) ou à l’aide d’autres outils d’importation/exportation d’infrastructure de base de données. Si vous utilisez pilotée par événements de communication, ce processus d’intégration serait similaire à la façon de que propager les données comme décrit précédemment pour les tables de requête CQRS.

Toutefois, si la conception de votre application implique l’agrégation en permanence des informations à partir de plusieurs microservices pour les requêtes complexes, il peut être le symptôme d’une conception médiocre, un microservice doit être isolé que possible à partir d’autres microservices. (Cela exclut les rapports/analytique qui doit toujours utiliser des bases de données centrales de données à froid). Ce problème persiste souvent peut être une raison de microservices de fusion. Vous devez équilibrer l’autonomie d’évolution et de déploiement de chaque microservice avec des dépendances fortes, cohésion et agrégation des données.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Défi \#3 : comment garantir la cohérence entre plusieurs microservices

Comme indiqué précédemment, les données appartienne à chaque microservice sont privées pour ce microservice et est accessible uniquement à l’aide de son API microservice. Par conséquent, un présentées consiste à implémenter des processus d’entreprise de bout en bout tout en conservant la cohérence entre plusieurs microservices.

Pour analyser ce problème, nous allons étudier un exemple de la [eShopOnContainers référencer l’application](http://aka.ms/eshoponcontainers). Le catalogue microservice conserve les informations sur les produits, y compris leur niveau de stock. Le classement microservice gère les commandes et devez vérifier qu’une commande ne dépasse pas le stock de produit du catalogue accessibles à le. (Ou le scénario peut impliquer une logique qui gère les autres produits.) Dans la version monolithique hypothétique de cette application, le sous-système de tri peut utiliser simplement de transaction ACID pour vérifier le stock disponible, créez la commande dans la table Orders et mettre à jour le stock disponible dans la table Products.

Toutefois, dans une application microservices-, les tables Order et produit appartiennent à leurs microservices respectifs. Aucun microservice ne doit inclure jamais de bases de données appartenant à un autre microservice dans ses propres transactions ou des requêtes, comme indiqué dans la Figure 4 à 9.

![](./media/image9.PNG)

**Figure 4-9**. Un microservice ne peut pas accéder directement à une table dans une autre microservice

Le classement microservice ne doit pas mettre la table Products directement, car la table Products est détenue par le catalogue microservice. Pour effectuer une mise à jour pour le catalogue microservice, le classement microservice doit uniquement utiliser des communications asynchrones tels que les événements d’intégration (message et la communication basée sur les événements). Voici comment la [eShopOnContainers](http://aka.ms/eshoponcontainers) référence application effectue ce type de mise à jour.

Comme indiqué par le [théorème de CAP](https://en.wikipedia.org/wiki/CAP_theorem), vous devez choisir entre la disponibilité et cohérence forte ACID. La plupart des scénarios basés sur microservice exigent une disponibilité et une haute évolutivité par opposition à forte cohérence. Les applications critiques doivent rester et en cours d’exécution et les développeurs peuvent contourner la cohérence forte à l’aide des techniques pour travailler avec la cohérence éventuelle ou faible. Il s’agit de l’approche adoptée par la plupart des architectures basée sur un microservice.

En outre, ACID de style ou de transactions de validation en deux phases ne sont pas simplement sur les principes de microservices ; la plupart des bases de données NoSQL (par exemple, la base de données Azure Cosmos, MongoDB, etc.) ne prennent pas en charge les transactions de validation en deux phases. Toutefois, en conservant les données cohérence pour les services et les bases de données est essentielle. Cette demande est également liée à la question de la façon de propager les modifications entre plusieurs microservices lorsque certaines données doivent être redondant, par exemple, lorsque vous devez avoir le nom du produit ou une description dans le catalogue microservice et le panier d’achat microservice.

Une bonne solution pour résoudre ce problème consiste à utiliser les cohérence éventuelle entre microservices articulé via pilotée par événements de communication et d’un système de publication et d’abonnement. Ces rubriques sont traitées dans la section [une communication asynchrone commandé par événement](#async_event_driven_communication) plus loin dans ce guide.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Défi \#4 : comment concevoir la communication au-delà des limites de microservice

La communication entre microservice limites est un véritable défi. Dans ce contexte, communication ne référence pas le protocole que vous devez utiliser (HTTP et REST, AMQP, messagerie, etc.). Au lieu de cela, il adresse le style de communication que vous devez utiliser, et en particulier comment couplée votre microservices doit être. Selon le niveau de couplage, en cas d’échec, l’impact de cette défaillance sur votre système varie considérablement.

Dans un système distribué comme une application basée sur des microservices, des artefacts autant de déplacement et avec des services distribués sur plusieurs serveurs ou ordinateurs hôtes, composants risque d’échouer. Échec partiel et interruptions supérieures seront produit, vous devez concevoir votre microservices et la communication entre eux en prenant en compte les risques courants dans ce type de système distribué.

Une approche courante consiste à implémenter HTTP (REST)-en fonction de microservices, en raison de leur simplicité. Une approche basée sur HTTP est parfaitement acceptable ; le problème ici est lié à l’utilisation. Si vous utilisez des requêtes et réponses HTTP simplement pour interagir avec votre microservices à partir d’applications clientes ou à partir des passerelles d’API, qui convient. Mais si vous créez des longues chaînes d’appels HTTP synchrones entre microservices, la communication entre leurs limites comme si les microservices des objets dans une application monolithique, votre application sera finalement rencontrent des problèmes.

Par exemple, supposons que votre application cliente effectue un appel de API HTTP pour un microservice individuelles telles que le classement de microservice. Si le classement microservice appelle à son tour supplémentaire à l’aide de HTTP au sein de la même demande/réponse de microservices cycle, vous créez une chaîne d’appels HTTP. Il peut sembler raisonnable initialement. Toutefois, il existe des points importants à prendre en compte lorsque vous passez ce chemin d’accès vers le bas :

-   Performances de blocage et faible. En raison de la nature synchrone de HTTP, la demande d’origine ne sera pas obtenir une réponse jusqu'à ce que tous les appels HTTP internes. Imaginez que si le nombre de ces appels augmente considérablement et en même temps qu’un des intermédiaire HTTP appelle à un microservice est bloqué. Le résultat est que les performances sont affectées et l’évolutivité globale concernée exponentielle en tant qu’augmentation de demandes HTTP supplémentaire.

-   COUPLAGE microservices avec HTTP. Entreprise microservices ne doivent pas être associés avec les autres microservices d’entreprise. Dans l’idéal, ils ne doivent pas » « connaît l’existence d’autres microservices. Si votre application dépend de couplage microservices comme dans l’exemple, pour parvenir à autonomie par microservice sera pratiquement impossible.

-   Échec de tout un microservice. Si vous avez implémenté une chaîne de microservices liée par les appels HTTP, lorsque de la microservices échoue (et finalement ne pourront pas) la chaîne entière de microservices échoue. Un système basé sur les microservice doit être conçu pour continuer à utiliser, ainsi que possible lors de défaillances partielles. Même si vous implémentez la logique du client qui utilise les nouvelles tentatives avec interruption exponentielle ou de mécanismes de disjoncteur, les chaînes d’appel plus complexe HTTP sont, le plus complexe, il est d’implémenter une stratégie de défaillance basée sur HTTP.

En fait, si votre microservices internes communiquent en créant des chaînes de requêtes HTTP, comme décrit, il peut être avancé que vous disposez d’une application monolithique, mais une basée sur HTTP entre des processus au lieu de mécanismes de communication intraprocess.

Par conséquent, pour appliquer l’autonomie de microservice et avoir une meilleure résilience, vous devez réduire l’utilisation de chaînes de communication de demande/réponse sur microservices. Il est recommandé d’utiliser interaction asynchrone uniquement pour la communication de microservice entre réseaux virtuels, à l’aide de la communication asynchrone basée sur message et d’événement, ou à l’aide d’interrogation HTTP indépendamment du cycle de demande/réponse HTTP d’origine.

L’utilisation de la communication asynchrone est expliquée avec des détails supplémentaires plus loin dans ce guide dans les sections [microservice asynchrone applique l’autonomie de microservice](#asynchronous-microservice-integration-enforce-microservices-autonomy) et [asynchrone communication basée sur le message](#asynchronous-message-based-communication).

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Théorème de CAP**
    [*https://en.wikipedia.org/wiki/CAP\_théorème*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Cohérence éventuelle**
    [*https://en.wikipedia.org/wiki/Eventual\_la cohérence*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Manuel de la cohérence des données**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Martin Fowler. CQRS (commande et répartition de responsabilité de requête)**
    [*http://martinfowler.com/bliki/CQRS.html*](http://martinfowler.com/bliki/CQRS.html)

-   **Vue matérialisée**
    [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

-   **Ligne de Charles. Vs ACID. De BASE : Le DEPHASAGE pH de traitement des transactions de base de données**
    [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

-   **Transactions de compensation**
    [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

-   **UDI Dahan. Composition d’orientée**
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)


>[!div class="step-by-step"]
[Précédente] (logique-et-physique-architecture.md) [suivant] (identifier-microservice-domaine-modèle-boundaries.md)
