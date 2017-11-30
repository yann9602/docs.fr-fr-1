---
title: "Conception d’un microservice DDD et orienté"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conception d’un microservice DDD et orienté"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: df45441089fd59d5e0e52b4bcec409adcc11fb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-a-ddd-oriented-microservice"></a>Conception d’un microservice DDD et orienté

Conception domaine (DDD) éducateurs modélisation selon la réalité de l’entreprise comme pertinentes pour votre usage. Dans le contexte de la création d’applications, DDD parle des problèmes en tant que domaines. Elle décrit les zones à problème indépendants en tant que limitées de contextes (chaque contexte délimité en corrélation avec un microservice) et met l’accent sur un langage commun pour communiquer avec ces problèmes. Il suggère également de nombreux concepts techniques et des modèles, comme des entités de domaine avec des modèles riches (aucun [anemic-domaine modèle](https://martinfowler.com/bliki/AnemicDomainModel.html)), valeur objets, les agrégats et racine d’agrégation (ou entité racine) des règles pour prendre en charge l’implémentation interne. Cette section présente la conception et l’implémentation de ces modèles internes.

Parfois, ces règles de techniques DDD et les modèles de considérés comme des obstacles qui ont un apprentissage important pour implémenter les approches DDD. Mais la partie importante n’est pas les modèles eux-mêmes, mais organiser le code afin qu’il est aligné à des problèmes professionnels et à l’aide des même (langage omniprésent) des termes professionnels. En outre, les approches DDD doivent être appliqués uniquement si vous implémentez microservices complexes avec des règles d’entreprise importantes. Responsabilités plus simples, comme un service CRUD, peuvent être gérées avec une approche plus simple.

Où dessiner les limites est la tâche clée lorsque vous concevez et définition d’un microservice. Les modèles DDD vous aident à comprendre la complexité dans le domaine. Pour le modèle de domaine pour chaque contexte délimité, vous identifiez et définissez les entités, les objets de valeur et les agrégats que votre domaine de modèle. Pour générer et affiner un modèle de domaine qui est contenu dans une limite qui définit votre contexte. Et c’est très explicite sous la forme d’un microservice. Les composants au sein de ces limites finissent par votre microservices, bien que dans certains cas, une BC ou microservices d’entreprise peuvent être composées de plusieurs services physiques. DDD est sur les limites et sont donc microservices.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Conserver les limites du contexte du microservice relativement faible

Déterminer où placer les limites entre les contextes de délimitée équilibre deux objectifs concurrents. Tout d’abord, vous souhaitez créer initialement la plus petite microservices possibles, mais qui ne doit pas être le pilote principal ; Vous devez créer une limite autour des choses cohésion. En second lieu, vous devez éviter de communication bavarde entre microservices. Ces objectifs peuvent contredisent. Vous devriez équilibrer les en décomposant le système dans des microservices small autant que possible jusqu'à ce que vous voyiez croît rapidement avec chaque nouvelle tentative pour séparer un nouveau contexte limité des limites de communication. Cohésion est la clé dans un contexte de limite unique.

Il est similaire à la [odeur de code intimité inappropriée](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) lors de l’implémentation de classes. Si deux microservices devez collaborer beaucoup entre eux, ils doivent être probablement la même microservice.

Une autre façon d’examiner ce est autonomie. Si un microservice doit s’appuyer sur un autre service à une demande de service directement, il n’est pas réellement autonome.

## <a name="layers-in-ddd-microservices"></a>Couches dans DDD microservices

La plupart des applications d’entreprise avec importants de l’activité et de complexité technique sont définies par plusieurs couches. Les couches sont un artefact de logique et ne sont pas liées au déploiement du service. Ils existent pour aider les développeurs de gérer la complexité dans le code. Différentes couches (par exemple, la couche de modèle de domaine par rapport à la couche de présentation, etc.) peuvent avoir différents types, qui impose des conversions entre ces types.

Par exemple, une entité peut être chargée à partir de la base de données. Puis la partie de ces informations ou d’un regroupement d’informations, y compris les données supplémentaires à partir d’autres entités, peut être envoyé à l’interface utilisateur via une API REST de Web client. Le point ici est que l’entité de domaine est contenue dans la couche de modèle de domaine et qu’il ne doit pas être propagée à d’autres zones il n’appartient pas à, comme pour la couche de présentation.

En outre, vous devez disposer des entités toujours valide (consultez la [conception validations dans la couche de modèle de domaine](#designing-validations-in-the-domain-model-layer) section) contrôlé par les racines d’agrégat (entités racine). Par conséquent, les entités ne doivent pas liées aux vues du client, car le niveau de l’interface utilisateur des données peuvent toujours pas possible de valider. C’est ce que le ViewModel pour. Ce dernier est un modèle de données exclusivement pour les besoins de couche de présentation. Les entités de domaine n’appartiennent pas directement à ce dernier. Au lieu de cela, vous devez traduire entre des entités ViewModel et le domaine et vice versa.

Lorsque la complexité abordant le problème, il est important de disposer d’un modèle de domaine contrôlé par les racines d’agrégat (rentrer dans cela plus en détail plus loin) qui vous assurer que les invariants et les règles associées à ce groupe d’entités (regroupement) sont effectuées via une seule entrée point ou le portail, la racine d’agrégation.

Figure 9-5 illustre comment une conception multicouche est implémentée dans l’application eShopOnContainers.

![](./media/image6.png)

**Figure 9-5**. Couches DDD dans l’ordre de tri microservice dans eShopOnContainers

Vous souhaitez concevoir le système afin que chaque couche communique uniquement avec certains autres couches. Qui peut être plus facile à appliquer si les couches sont implémentées comme des bibliothèques de classes différentes, car vous pouvez identifier clairement les dépendances sont définies entre les bibliothèques. Par exemple, la couche de modèle de domaine ne nécessite pas une dépendance sur toutes les autres couches (les classes de modèle de domaine doivent être Plain Old CLR Objects ou [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), classes). Comme indiqué dans la Figure 9-6, le **Ordering.Domain** bibliothèque de couche a des dépendances uniquement sur les bibliothèques .NET Core mais pas sur toute autre bibliothèque personnalisée (bibliothèque de données, la bibliothèque de persistance, etc.).

![](./media/image7.PNG)

**Figure 9-6**. Implémenté comme bibliothèques permettent de mieux contrôler les dépendances entre les couches de couches

### <a name="the-domain-model-layer"></a>La couche de modèle de domaine

Carnet d’excellentes de Eric Evans [Domain Driven Design](http://domainlanguage.com/ddd/) à propos de la couche de modèle de domaine et de la couche application.

**Couche de modèle de domaine**: responsable représentant les concepts de l’entreprise, des informations sur la situation de l’entreprise et les règles d’entreprise. État qui reflète la situation de l’entreprise est contrôlé et utilisé ici, même si les détails techniques de stockage sont déléguées à l’infrastructure. Cette couche est au cœur des logiciels d’entreprise.

La couche de modèle de domaine est où l’entreprise est exprimée. Lorsque vous implémentez une couche de modèle de domaine microservice dans .NET, qui s’appuient est encodé comme une bibliothèque de classes avec les entités de domaine qui capturent des données ainsi que le comportement (méthodes avec une logique).

Suivant le [ignorant la persistance](http://deviq.com/persistence-ignorance/) et [Ignorance de l’Infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance) principes, cette couche doivent ignorer complètement les détails de persistance des données. Ces tâches de persistance doivent être effectuées par la couche d’infrastructure. Par conséquent, cette couche ne nécessite pas de dépendances directes sur l’infrastructure, ce qui signifie qu’une règle importante est que vos classes d’entité de modèle domaine doivent être [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entités de domaine ne doivent pas avoir de toute dépendance directe (par exemple, en dérivant une classe de base) sur n’importe quelle infrastructure d’infrastructure d’accès aux données comme Entity Framework ou NHibernate. Dans l’idéal, vos entités de domaine ne doivent pas dériver d’ou implémenter n’importe quel type défini dans n’importe quelle infrastructure de l’infrastructure.

Les infrastructures ORM plus modernes comme Entity Framework Core autorisent cette approche, afin que vos classes de modèle de domaine ne sont pas associés à l’infrastructure. Toutefois, avec les entités POCO n’est pas toujours possible lorsque vous utilisez certaines bases de données NoSQL et les infrastructures, comme les acteurs et des Collections fiable dans Azure Service Fabric.

Même lorsqu’il est important de suivre le principe ignorant la persistance pour votre modèle de domaine, vous ne devez pas ignorer les problèmes de persistance. Il est toujours très important de comprendre le modèle de données physique et comment il est mappé à votre modèle d’objet entité. Dans le cas contraire, vous pouvez créer des conceptions impossibles.

En outre, cela ne signifie pas prendre un modèle conçu pour une base de données relationnelle et les déplacer directement vers un NoSQL orienté document base de données ou. Dans certains modèles d’entité, le modèle peut correspondre, mais en général il n’existe pas. Il existe toujours des contraintes de votre modèle d’entité doit respecter, basée sur les technologies de stockage et ORM.

### <a name="the-application-layer"></a>La couche application

Passer à la couche application, nous pouvons citer à nouveau les livres de Eric Evans [Domain Driven Design](http://domainlanguage.com/ddd/):

**Couche d’application :** définit les travaux, le logiciel est supposée pour faire et dirige les objets de domaine expressives pour déterminer les problèmes. Les tâches de que cette couche est responsable sont significatives pour l’entreprise ou nécessaire pour l’interaction avec les couches d’application d’autres systèmes. Cette couche est conservée dynamique. Il ne contient pas de règles d’entreprise ou de la base de connaissances, mais uniquement les tâches de coordonnées et les délégués de travail pour les collaborations d’objets de domaine de la couche suivante vers le bas. Il n’a pas d’état reflétant la situation de l’entreprise, mais elle peut avoir d’état qui reflète la progression d’une tâche pour l’utilisateur ou le programme.

Couche d’application d’un microservice dans .NET est généralement encodé comme un projet de l’API Web ASP.NET principale. Le projet implémente interaction de la microservice, accès réseau à distance et les API Web externe utilisé dans les applications client ou de l’interface utilisateur. Il inclut les requêtes s’approche d’à l’aide d’un CQRS, commandes acceptées par le microservice et même la communication pilotée par événements entre microservices (événements d’intégration). L’API de Web ASP.NET Core qui représente la couche d’application ne doit pas contenir des règles d’entreprise ou de la connaissance de domaine (notamment règles de domaine pour les transactions ou les mises à jour) ; Il doivent être possédé par la bibliothèque de classes de modèle de domaine. La coordonnée d’uniquement doit de couche application tâches et ne doive pas contenir ou définir n’importe quel état de domaine (modèle de domaine). Elle délègue l’exécution des règles d’entreprise pour les classes de modèle domaine eux-mêmes (racines d’agrégat et entités de domaine), qui seront finalement jour des données au sein de ces entités de domaine.

En fait, la logique d’application est où vous implémentez tous les cas d’utilisation qui dépendent d’un serveur frontal donné. Par exemple, l’implémentation relatifs à un service Web API.

L’objectif est que la logique de domaine dans la couche de modèle de domaine, son invariants, le modèle de données et des règles d’entreprise associées doit être complètement indépendante des couches de présentation et d’application. Surtout, la couche de modèle de domaine doit dépendre pas directement de n’importe quelle infrastructure de l’infrastructure.

### <a name="the-infrastructure-layer"></a>La couche d’infrastructure

La couche d’infrastructure est la façon dont les données qui sont maintenues initialement dans les entités de domaine (en mémoire) sont conservées dans les bases de données ou un autre magasin persistant. Un exemple est à l’aide de code d’Entity Framework Core pour implémenter les classes de modèle de référentiel qui utilisent un DBContext pour conserver les données dans une base de données relationnelle.

Conformément aux mentionnées précédemment [ignorant la persistance](http://deviq.com/persistence-ignorance/) et [Ignorance de l’Infrastructure](https://ayende.com/blog/3137/infrastructure-ignorance) principes, la couche d’infrastructure ne doivent pas « contaminer » la couche de modèle de domaine. Vous devez conserver l’indépendantes de classes de domaine modèle entité à partir de l’infrastructure qui vous permet de rendre persistantes des données (EF ou toute autre infrastructure) en les dépendances dures ne pas sur des infrastructures. Votre bibliothèque de classes de couche de modèle domaine doit avoir uniquement votre code de domaine, simplement [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) entité classes qui implémentent le cœur de votre logiciel et complètement découplées à partir des technologies d’infrastructure.

Par conséquent, des couches ou des bibliothèques de classes et des projets doivent finalement s’appuyer sur votre couche de modèle de domaine (bibliothèque), pas l’inverse, comme indiqué dans la Figure 9-7.

![](./media/image8.png)

**Figure 9-7**. Dépendances entre les couches dans DDD

Cette conception de la couche doit être indépendante pour chaque microservice. Comme indiqué précédemment, vous pouvez implémenter le microservices plus complexe suivant des modèles DDD, lors de l’implémentation la plus simple piloté par les données microservices (CRUD simple dans une couche unique) dans une méthode plus simple.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **DevIQ. Principe d’Ignorance de persistance**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Ou en Eini. Ignorance de l’infrastructure**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **Angel Lopez. Architecture de conception domaine multicouches**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[Précédente] (cqrs-microservice-reads.md) [suivant] (microservice-domaine-model.md)
