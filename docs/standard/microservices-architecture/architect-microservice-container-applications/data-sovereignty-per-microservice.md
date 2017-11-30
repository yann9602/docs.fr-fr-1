---
title: "Souveraineté de données par microservice"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Souveraineté de données par microservice"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c51daae04215cfa6f5b5b8d2158a8ed1a8949652
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="data-sovereignty-per-microservice"></a>Souveraineté de données par microservice

Une règle importante pour l’architecture de microservices est que chaque microservice doit posséder ses données de domaine et de la logique. Tout comme une application complète possède sa logique et les données, par conséquent, doit chaque microservice posséder sa logique et les données sous un cycle de vie autonome, avec un déploiement indépendant par microservice.

Cela signifie que le modèle conceptuel du domaine varient entre les sous-systèmes ou microservices. Envisagez d’applications d’entreprise, où la relation (CRM) de gestion des applications client transactionnelles acheter sous-systèmes et client prise en charge de chaque appel sur les attributs d’entité client unique et des données et chacune utilise un autre Limite de contexte (BC).

Ce principe est similaire dans [conception domaine (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design), où chaque [limitées de contexte](https://martinfowler.com/bliki/BoundedContext.html) ou sous-système autonome ou un service doit être propriétaire de son modèle de domaine (données plus logique et le comportement). Chaque contexte de délimitée DDD correspond à une entreprise microservice (un ou plusieurs services). (Nous développer sur ce point sur le modèle limitées de contexte dans la section suivante).

En revanche, l’approche traditionnelle (données monolithique) utilisé dans de nombreuses applications est ayant quelques bases de données ou d’une base de données centralisée. Il s’agit souvent une base de données SQL normalisée qui est utilisé pour l’ensemble de l’application et de ses sous-systèmes internes, comme indiqué dans la Figure 4-7.

![](./media/image7.png)

**Figure 4-7**. Comparaison de données souveraineté : base de données monolithique pour microservices

Initialement, l’approche de la base de données centralisée semble plus simple et semble pour permettre la réutilisation des entités dans les différents sous-systèmes pour rendre tous les éléments cohérent. Mais la réalité est que vous vous retrouvez avec grandes tables qui font Office de nombreux différents sous-systèmes et qui incluent des attributs et des colonnes qui ne sont pas nécessaires dans la plupart des cas. C’est comme une tentative d’utilisation de la même carte physique pour une piste courte de randonnée, en prenant un voyage de voiture de la journée et apprendre geography.

Une application monolithique généralement une base de données relationnelles présente deux avantages essentiels : [les transactions ACID](https://en.wikipedia.org/wiki/ACID) et le langage SQL, les deux travaille avec toutes les tables et les données relatives à votre application. Cette approche vous permet d’écrire facilement une requête qui combine les données provenant de plusieurs tables.

Cependant, l’accès aux données devient beaucoup plus complexe lorsque vous déplacez vers une architecture microservices. Mais même lorsque les transactions ACID peuvent ou doivent être utilisées dans un contexte de limitées ou de microservice, les données appartenant à chaque microservice sont privées pour ce microservice et sont accessibles via son API microservice. En encapsulant les données garantit que les microservices sont faiblement couplés et peuvent évoluer indépendamment les unes des autres. Si plusieurs services ont été l’accès aux mêmes données, mises à jour de schéma nécessiterait la coordination des mises à jour à tous les services. Cela compromettrait l’autonomie de cycle de vie de microservice. Mais les structures de données distribuées signifient que vous ne pouvez effectuer une seule transaction ACID sur microservices. À son tour, cela signifie que lorsqu’un processus d’entreprise s’étend sur plusieurs microservices, vous devez utiliser la cohérence éventuelle. Cela est beaucoup plus difficile à implémenter que les jointures SQL simples ; de même, de nombreuses autres fonctionnalités de base de données relationnelle ne sont pas disponibles sur plusieurs microservices.

Même aller microservices différents utilisent souvent différents *types* des bases de données. Magasin d’applications modernes et processus différents types de données et une base de données relationnelle n’est pas toujours le meilleur choix. Pour certains cas d’usage, d’une base de données NoSQL comme Azure DocumentDB ou MongoDB peut disposer d’un modèle de données plus pratique et offrent de meilleures performances et évolutivité à une base de données SQL telle que SQL Server ou de la base de données SQL Azure. Dans d’autres cas, une base de données relationnelle est toujours la meilleure approche. Par conséquent, les applications basées sur des microservices utilisent souvent un mélange de bases de données SQL et NoSQL, qui est parfois appelé le [polyglot persistance](http://martinfowler.com/bliki/PolyglotPersistence.html) approche.

Une architecture partitionnée, polyglot persistant pour le stockage de données présente de nombreux avantages. Notamment les services faiblement couplés et de meilleures performances, l’évolutivité, les coûts et facilité de gestion. Toutefois, il peut introduire des défis de gestion des données distribuées, comme nous allons expliquer dans «[identification des limites de domaine en mode](#identifying-domain-model-boundaries-for-each-microservice)» plus loin dans ce chapitre.

## <a name="the-relationship-between-microservices-and-the-bounded-context-pattern"></a>La relation entre microservices et le modèle limitées de contexte

Le concept de microservice dérive le [modèle de contexte délimité (BC)](http://martinfowler.com/bliki/BoundedContext.html) dans [conception domaine (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design). DDD porte sur les modèles volumineux en distinguant plusieurs BCs et soient explicites sur leurs limites. Chaque BC doit avoir son propre modèle et la base de données ; de même, chaque microservice possède ses données associées. En outre, chaque BC généralement possède son propre [langage omniprésent](http://martinfowler.com/bliki/UbiquitousLanguage.html) permettant la communication entre les développeurs de logiciels et des experts du domaine.

Ces termes (principalement les entités de domaine) dans le langage omniprésent peuvent avoir différents noms dans différents contextes limitées, même lorsque l’autre domaine entités partagent la même identité (autrement dit, l’ID unique est utilisé pour lire l’entité à partir du stockage). Par exemple, dans un contexte délimité de profil utilisateur, l’entité de domaine d’utilisateur susceptibles de partager identité avec l’entité de domaine de l’acheteur dans le contexte délimité tri.

Un microservice est par conséquent similaire à un contexte délimité, mais il indique également qu’il est un service distribué. Il est construit comme un processus séparé pour chaque contexte délimité, et il doit utiliser les protocoles distribuées indiquées précédemment, tels que HTTP/HTTPS, WebSockets, ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Le modèle limitées de contexte, toutefois, ne spécifie pas si le contexte délimité est un service distribué ou s’il est simplement une limite logique (par exemple, un sous-système générique) dans une application de déploiement monolithique.

Il est important de souligner que la définition d’un service pour chaque contexte délimité est un bon point de départ. Mais il est inutile limiter votre conception à celui-ci. Parfois, vous devez concevoir un contexte délimité ou business microservice composé de plusieurs services physiques. Mais en fin de compte, les deux modèles : limitées de contexte et microservice — sont étroitement liés.

DDD bénéficie des microservices en obtenant les limites réelles sous la forme de microservices distribuée. Mais les idées à ne pas partager le modèle entre microservices sont ce que vous souhaitez également dans un contexte délimité.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Chris Richardson. Modèle : La base de données par le service**
    [*http://microservices.io/patterns/data/database-per-service.html*](http://microservices.io/patterns/data/database-per-service.html)

-   **Martin Fowler. BoundedContext**
    [*http://martinfowler.com/bliki/BoundedContext.html*](http://martinfowler.com/bliki/BoundedContext.html)

-   **Martin Fowler. PolyglotPersistence**
    [*http://martinfowler.com/bliki/PolyglotPersistence.html*](http://martinfowler.com/bliki/PolyglotPersistence.html)

-   **Blog d’Alberto Brandolini. Stratégique Domain Driven Design avec le mappage de contexte**
    [*https://www.infoq.com/articles/ddd-contextmapping*](https://www.infoq.com/articles/ddd-contextmapping)


>[!div class="step-by-step"]
[Précédente] (microservices-architecture.md) [suivant] (logique-et-physique-architecture.md)
