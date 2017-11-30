---
title: "Common architectures d’application web"
description: "Architecture des applications web avec ASP.NET Core et Microsoft Azure | Common architectures d’application web"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: b6236cfab290211f930d6a1987075abeade4fd6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
#<a name="common-web-application-architectures"></a>Common Architectures d’Application Web

> « Si vous pensez que la bonne architecture est coûteuse, essayez une architecture incorrecte. »  
> _-Brian pi et Joseph Yoder_

## <a name="summary"></a>Résumé

.NET traditionnels sont déployées sous la forme d’unités correspondant à un fichier exécutable ou une seule application web qui s’exécutent dans un appdomain IIS unique. Cela est le modèle de déploiement plus simple et sert de nombreuses applications internes et publics plus petites très bien. Toutefois, même si cette unité de déploiement unique, la plupart des applications métier non trivial bénéficient certaine séparation logique en plusieurs couches.

## <a name="what-is-a-monolithic-application"></a>Qu’est une application monolithique ?

Une application monolithique n’est complète, en termes de son comportement. Il peut interagir avec d’autres banques de données ou des services au cours de ses opérations, mais la base de son comportement s’exécute dans son propre processus et l’ensemble de l’application est généralement déployé comme une unité unique. Si une telle application doit pouvoir évoluer horizontalement, en général, l’application entière est dupliquée sur plusieurs serveurs ou ordinateurs virtuels.

## <a name="all-in-one-applications"></a>Applications de tout-en-un

Le plus petit nombre possible de projets pour une architecture d’application est un. Dans cette architecture, l’intégralité de la logique de l’application est contenue dans un seul projet compilé dans un assembly unique et déployé comme une unité unique.

Un nouveau projet ASP.NET Core, si créée dans Visual Studio ou à partir de la ligne de commande démarre comme un simple monolithique de « tout-en-un ». Il contient l’ensemble du comportement de l’application, y compris la logique de présentation, métier et données d’accès. Figure 5-1 montre la structure des fichiers d’une application de projet unique.

**Figure 5-1.** Un seul projet ASP.NET Core application

![](./media/image5-1.png)

Dans un scénario de projet unique, la séparation des problèmes est obtenue grâce à l’utilisation des dossiers. Le modèle par défaut inclut des dossiers distincts pour les responsabilités du modèle MVC de modèles, des vues et des contrôleurs, ainsi que des dossiers supplémentaires pour les Services et les données. Dans cette configuration, les détails de présentation doivent être limitées autant que possible dans le dossier Views et détails d’implémentation d’un accès aux données doivent être limités aux classes conservés dans le dossier de données. Logique métier doit résider dans les classes dans le dossier de modèles et de services.

Bien que simple, la solution monolithique de projet unique présente des inconvénients. Comme la taille et la complexité du projet augmente, le nombre de fichiers et dossiers continueront à croître également. Problèmes d’interface utilisateur (modèles, vues, contrôleurs) se trouvent dans plusieurs dossiers qui ne sont pas regroupés par ordre alphabétique. Ce problème seulement s’aggrave lorsque des constructions supplémentaires au niveau de l’interface utilisateur, telles que les filtres ou ModelBinders, sont ajoutées dans leurs propres dossiers. Logique métier est répartie entre les dossiers de modèles et des Services, et il n’existe aucun signe évident dont les classes dans les dossiers qui doivent s’appuyer sur d’autres. Ce manque de l’organisation au niveau du projet se traduit généralement par [code spaghetti](http://deviq.com/spaghetti-code/).

Pour résoudre ces problèmes, applications deviennent souvent des solutions à projets multiples, où chaque projet est considéré comme résidant dans un particulier *couche* de l’application.

## <a name="what-are-layers"></a>Quelles sont les couches ?

Comme les applications de croître en complexité, une méthode pour gérer cette complexité consiste à décomposer l’application en fonction de ses responsabilités ou les problèmes. Suit la séparation du principe de problèmes, il peut aider à conserver une base de code croissante organisée afin que les développeurs peuvent facilement rechercher où certaines fonctionnalités sont implémentées. Architecture multiniveau offre plusieurs avantages au-delà de l’organisation de code uniquement, cependant.

En organisant code en couches, des fonctionnalités communes de bas niveau peuvent être réutilisées dans l’ensemble de l’application. Cette réutilisation est bénéfique, car il a donc que besoin de moins de code à écrire et car elle permet à l’application afin de normaliser sur une implémentation unique, selon le principe sec.

Avec une architecture en couches, les applications peuvent appliquer des restrictions sur lequel les couches peuvent communiquer avec les autres couches. Cela permet d’améliorer l’encapsulation. Lorsqu’une couche est modifiée ou remplacée, seuls ces couches qui fonctionnent avec lui doivent être affectées. En limitant qui couches varient sur lequel les autres couches, l’impact de modifications peuvent être atténuées afin qu’une seule modification n’affecte pas l’application entière.

Couches (et encapsulation) rendent beaucoup plus facile de remplacer la fonctionnalité de l’application. Par exemple, une application peut utiliser initialement sa propre base de données SQL Server pour la persistance, mais plus tard peut choisir d’utiliser une stratégie basée sur le cloud de persistance, ou un derrière une API web. Si l’application a encapsulé correctement son implémentation de persistance au sein d’une couche logique, cette couche spécifique de SQL Server a remplacé par une implémentation de la même interface publique.

Outre la possibilité de permutation des implémentations en réponse aux modifications futures dans la configuration requise, les couches application également facilitent permuter des implémentations à des fins de test. Au lieu d’écrire des tests qui fonctionnent sur la couche de données réelles ou l’interface utilisateur de l’application, ces couches peuvent être remplacés au moment de test avec des implémentations factices qui fournissent des réponses aux demandes connus. En règle générale, cela fait tests beaucoup plus facile à écrire et beaucoup plus rapides à exécuter par rapport à exécuter les tests à nouveau infrastructure réelle de l’application.

En couches logiques est une technique courante pour l’amélioration de l’organisation de code dans les applications d’entreprise, et il existe plusieurs façons dans lequel le code peut être organisé en couches.

> [!NOTE]
> *Couches* représentent une séparation logique dans l’application. Dans le cas où la logique de l’application est distribuée physiquement pour séparer les serveurs ou des processus, ces cibles de déploiement physique distincte sont appelés *niveaux*. Il est possible et qu’il est assez courant d’avoir une application de couche N est déployée sur un même niveau.

## <a name="traditional-n-layer-architecture-applications"></a>Applications d’architecture traditionnelles couche « N »

L’organisation courante de logique d’application en couches il montre la Figure 5-2.

**Figure 5-2.** Couches d’application standard.

![](./media/image5-2.png)

Ces couches sont souvent abrégés en tant que l’interface utilisateur, BLL (Business Logic Layer) et DAL (couche d’accès aux données). À l’aide de cette architecture, les utilisateurs font des demandes via la couche d’interface utilisateur qui interagit uniquement avec la couche BLL. La couche BLL, à son tour, peut appeler la couche DAL pour les demandes d’accès aux données. La couche d’interface utilisateur ne devez pas apporter toutes les demandes à la couche DAL directement, ni doit interagir avec la persistance par d’autres moyens. De même, la couche BLL interagissez uniquement persistance en passant par la couche DAL. De cette manière, chaque couche possède sa propre responsabilité bien connue.

L’un des inconvénients de cette approche en couches traditionnel sont que les dépendances de compilation s’exécuter à partir du haut vers le bas. Autrement dit, la couche d’interface utilisateur dépend de la couche BLL, ce qui dépend de la couche DAL. Cela signifie que la couche BLL, qui contient généralement la logique la plus importante dans l’application, est dépendante sur les détails d’implémentation d’un accès aux données (et souvent de l’existence d’une base de données). Il est souvent difficile, nécessitant une base de données de test de logique métier de test dans une telle architecture. Le principe d’inversion de dépendance peut être utilisé pour résoudre ce problème, comme vous le verrez dans la section suivante.

Figure 5-3 montre un exemple de solution, arrêt de l’application dans trois projets par responsabilité (ou couche).

**Figure 5-3.** Une simple application monolithique avec trois projets.

![](./media/image5-3.png)

Bien que cette application utilise plusieurs projets à des fins d’organisation, il est toujours déployé comme une unité unique et ses clients interagissent avec lui comme une application web unique. Cela permet à un processus de déploiement très simple. Figure 5-4 montre comment une telle application peut être hébergé à l’aide de Windows Azure.

![](./media/image5-4.png)

**Figure 5-4.** Déploiement simple de l’application Web Azure

Comme l’application doit augmenter, les solutions de déploiement plus complexe et robuste peuvent être nécessaire. Figure 5-5 montre un exemple d’un plan de déploiement plus complexe qui prend en charge des fonctionnalités supplémentaires.

![](./media/image5-5.png)

**Figure 5-5.** Déploiement d’une application web à un Service d’application Azure

En interne, une organisation de ce projet en plusieurs projets en fonction de la responsabilité améliore la facilité de maintenance de l’application.

Cette unité peut être monté en haut ou out pour tirer parti de l’évolutivité de la demande sur le cloud. L’évolution verticale signifie l’ajout d’UC supplémentaires, mémoire, espace disque ou autres ressources pour l’ou les serveurs hébergeant votre application. Montée en puissance parallèle signifie que l’ajout d’instances supplémentaires de ces serveurs, si ce sont des serveurs physiques ou virtuels. Lorsque votre application est hébergée sur plusieurs instances, un équilibreur de charge est utilisé pour assigner les requêtes à des instances d’application individuels.

L’approche la plus simple à l’échelle d’une application web dans Azure consiste à configurer la mise à l’échelle manuellement dans du Plan l’application App Service. Figure 5-6 afficher l’écran du tableau de bord Azure approprié pour configurer le nombre d’occurrences servent à une application.

![](./media/image5-6.png)

**Figure 5-6.** Plan App Service mise à l’échelle dans Azure.

## <a name="clean-architecture"></a>Nouvelle architecture

Les applications qui suivent le principe d’Inversion de dépendance, ainsi que les principes de la conception orientée ont tendance à arriver à une architecture similaire. Cette architecture est passé par le nombre de noms au fil des années. Un des noms des première a été Architecture Hexagonal, suivi par les adaptateurs et des Ports. Plus récemment, il est citée en tant que le [en cercles concentriques Architecture](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) ou [propre Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Il est de ce nom, nouvelle Architecture, qui est utilisé comme base pour la description de l’architecture dans ce livre électronique.

> [!NOTE]
> Le terme que propre Architecture peut être appliqué aux applications qui sont générées à l’aide des principes DDD ainsi qu’à ceux qui ne sont pas générées à l’aide de DDD. Dans le cas de la première, cette combinaison peut être appelée en tant que « Nouvelle Architecture de DDD ».

Nouvelle architecture place le modèle logique et les applications d’entreprise dans le centre de l’application. Au lieu de logique métier dépendent de l’accès aux données ou d’autres problèmes d’infrastructure, cette dépendance est inversée : détails de l’infrastructure et de l’implémentation varient selon le cœur de l’Application. Cela est possible en définissant des abstractions ou des interfaces, dans le noyau de l’Application, puis implémentées par les types définis dans la couche d’Infrastructure. Une méthode courante de visualisation de cette architecture est d’utiliser une série de cercles concentriques, similaires à une en cercles concentriques. Figure 5-X montre un exemple de ce style de représentation de l’architecture.

![](./media/image5-7.png)

**Figure 5-7.** Nouvelle Architecture ; vue d’en cercles concentriques

Dans ce diagramme de flux de dépendances vers le cercle plus profond. Par conséquent, vous pouvez voir que le cœur de l’Application (qui tire son nom à partir de sa position au cœur de ce diagramme) ne dispose d’aucune dépendance sur d’autres couches application. Dans le centre de très sont des entités et les interfaces de l’application. À l’extérieur, mais dans le cœur de l’Application, sont des services de domaine, qui implémentent généralement des interfaces définies dans le cercle interne. En dehors de l’Application Core, l’Interface utilisateur et les couches d’Infrastructure varient sur le cœur de l’Application, mais pas sur un autre (nécessairement).

Figure 5-X affiche un diagramme de couche horizontal plus classique qui reflète mieux la dépendance entre l’interface utilisateur et d’autres couches.

![](./media/image5-8.png)

**Figure 5-8.** Nouvelle Architecture ; vue de la couche horizontale

Notez que les flèches solides représentent les dépendances de compilation, tandis que la flèche en pointillé représente une dépendance de runtime. À l’aide de la nouvelle architecture, la couche d’interface utilisateur fonctionne avec les interfaces définies dans le cœur de l’Application au moment de la compilation, et dans l’idéal, ne doivent pas avoir des connaissances sur les types d’implémentation définie dans la couche d’Infrastructure. Lors de l’exécution, toutefois, ces types de mise en œuvre seront requis pour l’application à exécuter, donc ils devront être présent et câblé jusqu'à les interfaces de base d’Application via l’injection de dépendances.

Figure 5-9 illustre une vue plus détaillée de l’architecture d’une application ASP.NET Core lors de la génération en suivant ces recommandations.

![Architecture de base ASPNET](./media/image5-9.png)

**Figure 5-9.** Diagramme d’architecture ASP.NET Core suivant la nouvelle Architecture.

Étant donné que le cœur de l’Application ne dépend d’Infrastructure, il est très facile d’écrire des tests unitaires automatisés pour cette couche. Figures 5 à 10 et 11-5 montrent comment les tests s’adaptent à cette architecture.

![UnitTestCore](./media/image5-10.png)

**Figure 5-10.** Test unitaire de base d’Application dans d’isolation.

![IntegrationTests](./media/image5-11.png)

**Figure 5-11.** Intégration de test des implémentations d’Infrastructure avec des dépendances externes.

Puisque la couche d’interface utilisateur n’a pas une dépendance directe sur les types définis dans le projet d’Infrastructure, il est également très facile à échanger des implémentations, soit pour faciliter le test ou en réponse à l’évolution des besoins de l’application. D’ASP.NET Core utilisation intégrée d’et prise en charge pour l’injection de dépendance rend cette architecture de la manière la plus appropriée aux applications monolithique de structure non trivial.

Pour les applications monolithiques les projets de base de l’Application, l’Infrastructure et l’Interface utilisateur sont exécutés en tant qu’une seule application. L’architecture d’application runtime peut ressembler à la Figure 5-12.

![Architecture de ASPNET 2](./media/image5-12.png)

**Figure 5-12.** Architecture d’exécution d’une application exemple ASP.NET Core.

### <a name="organizing-code-in-clean-architecture"></a>Organisation du Code dans la nouvelle Architecture

Dans une solution nouvelle Architecture, chaque projet est claire des responsabilités. Par conséquent, certains types appartiendra dans chaque projet et vous trouverez souvent les dossiers correspondant à ces types dans le projet approprié.

Le cœur de l’Application contient le modèle d’entreprise, ce qui inclut les entités, les services et les interfaces. Ces interfaces incluent des abstractions pour les opérations qui seront effectuées à l’aide de l’Infrastructure, tels que l’accès aux données, les accès au système de fichiers, les appels réseau, etc.. Parfois, services ou des interfaces définies au niveau de cette couche devrez travailler avec les types d’entité non qui n’ont aucune dépendance sur l’interface utilisateur ou d’Infrastructure. Il peuvent être définis comme simple transférer des objets de données (DTO).

> ### <a name="application-core-types"></a>Types de base d’application
> -   Entités (entreprise classes de modèle qui sont conservées)
> -   Interfaces
> -   Services
> -   DTO

Le projet d’Infrastructure inclut généralement des implémentations d’accès aux données. Dans une application web ASP.NET Core classique, cela inclut l’Entity Framework DbContext, les Migrations de noyaux EF qui ont été définies et classes d’implémentation d’un accès aux données. La méthode la plus courante d’abstraire le code d’implémentation d’un accès aux données est à l’aide de la [modèle de conception de référentiel](http://deviq.com/repository-pattern/).

En plus des implémentations d’accès aux données, le projet de l’Infrastructure doit contenir des implémentations de services qui doivent interagir avec des problèmes d’infrastructure. Ces services doivent implémenter les interfaces définies dans le cœur de l’Application et Infrastructure doit avoir une référence au projet de base de l’Application.

> ### <a name="infrastructure-types"></a>Types d’infrastructure
> -   Types de principaux EF (DbContext, Migrations)
> -   Types d’implémentation (référentiels) d’accès aux données
> -   Services d’infrastructure spécifique (FileLogger, SmtpNotifier, etc.).

La couche d’interface utilisateur dans une application ASP.NET MVC de base sera le point d’entrée pour l’application et sera un projet ASP.NET MVC de base. Ce projet doit référencer le projet de base de l’Application et ses types doivent interagir avec l’infrastructure strictement via les interfaces définies dans la base de l’Application. Aucun l’instanciation directe de (ou les appels statiques) types de couche d’Infrastructure doivent être autorisées dans la couche d’interface utilisateur.

> ### <a name="ui-layer-types"></a>Types de couche d’interface utilisateur
> -   Contrôleurs
> -   Filtres
> -   Affichages
> -   ViewModel
> -   Démarrage

La classe de démarrage est chargée pour la configuration de l’application et pour la création de types d’implémentation pour les interfaces, ce qui permet d’injection de dépendances fonctionne correctement au moment de l’exécution.

> [!NOTE]
> Pour associer l’injection de dépendances dans ConfigureServices dans le fichier Startup.cs du projet de l’interface utilisateur, le projet devrez peut-être fait référence au projet d’Infrastructure. Cette dépendance peut être éliminée plus facilement à l’aide d’un conteneur DI personnalisé. Dans le cadre de cet exemple, l’approche la plus simple doit autoriser l’interface utilisateur project référencer le projet d’Infrastructure.

## <a name="monolithic-applications-and-containers"></a>Conteneurs et les Applications monolithiques 

Vous pouvez générer un Service ou une unique et monolithique déploiement Application Web basée sur et le déployer en tant que conteneur. Dans l’application, il peut être monolithique mais sont organisés en plusieurs bibliothèques, composants ou couches. En externe, il est un conteneur unique comme un processus unique, la seule application web ou le service unique.

Pour gérer ce modèle, vous déployez un conteneur unique pour représenter l’application. Pour mettre à l’échelle, ajoutez simplement des copies supplémentaires avec un équilibrage de charge à l’avant. La simplicité provient de la gestion d’un déploiement unique dans un seul conteneur ou d’une machine virtuelle.

![](./media/image5-13.png)

Vous pouvez inclure plusieurs composants/bibliothèques ou couches internes dans chaque conteneur, comme illustré dans la Figure 5-X. Mais, suivant le principal du conteneur de *» un conteneur fait une chose et qu’il le fait dans un processus*», le modèle monolithique peut être un conflit.

L’inconvénient de cette approche est fournie si/quand l’application atteint, nécessitant une mise à l’échelle. Si la mise à l’échelle de l’application entière, il n’est pas réellement un problème. Toutefois, dans la plupart des cas, certaines parties de l’application sont les points d’étranglement nécessitant une mise à l’échelle, tandis que les autres composants sont moins utilisé.

À l’aide de l’exemple classique de commerce électronique ; Vous devez probablement à l’échelle est le composant d’informations de produit. De nombreux clients plus parcourir les produits que les acheter. Davantage de clients utilisent leur panier d’achat que d’utiliser le pipeline de paiement. Les clients moins ajouter des commentaires ou afficher leur historique d’achat. Il vous suffit probablement le quelques employés, dans une région unique, qui ont besoin de gérer le contenu et les campagnes marketing. Par la mise à l’échelle de la conception monolithique, tout le code est déployé plusieurs fois.

En plus de l’échelle tout problème, modifications apportées à un seul composant nécessitent un nouveau test complet de l’application entière et un redéploiement complet de toutes les instances.

L’approche monolithique est courant, et de nombreuses organisations développez avec cette approche architecturale. Nombreux sont ayant une bonne nombre insuffisant de résultats, alors que d’autres sont en appuyant sur les limites. La plupart conçus leurs applications dans ce modèle, car l’infrastructure et les outils ont été trop difficiles à générer des architectures orientées service (SOA), et il n’a pas été voit la nécessité - jusqu'à ce que l’application a fait l’objet. Si vous trouvez que vous rencontrez les limites de l’approche monolithique, la division de l’application pour lui permettre de mieux tirer parti des conteneurs et microservices peut être la prochaine étape logique.

![](./media/image5-14.png)

Déploiement d’applications monolithiques dans Microsoft Azure peut être obtenue à l’aide de machines virtuelles dédiées pour chaque instance. À l’aide de [jeux de mise à l’échelle de machine virtuelle Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), vous pouvez adapter facilement les machines virtuelles. [Services d’application Azure](https://azure.microsoft.com/services/app-service/) peuvent exécuter des applications monolithiques et gérer facilement des instances sans avoir à gérer les machines virtuelles. Services d’application Azure peut exécuter des instances uniques des conteneurs Docker, ce qui simplifie le déploiement. À l’aide de Docker, vous pouvez déployer une seule machine virtuelle comme un hôte Docker et exécuter plusieurs instances. À l’aide de l’équilibrage de Azure, comme indiqué dans la Figure 5-14, vous pouvez gérer la mise à l’échelle.

Le déploiement sur les ordinateurs hôtes différents peut être géré avec les techniques de déploiement traditionnelles. Les hôtes Docker peuvent être gérés avec les commandes telles que **docker exécuter** effectuée manuellement ou via l’automatisation, telles que les pipelines de livraison continue (CD).

### <a name="monolithic-application-deployed-as-a-container"></a>Application monolithique déployée comme un conteneur

Il existe des avantages de l’utilisation de conteneurs pour gérer les déploiements d’applications monolithique. Mise à l’échelle les instances de conteneurs est beaucoup plus rapide et plus facile que le déploiement de machines virtuelles supplémentaires. Même si vous utilisez des jeux de mise à l’échelle de machine virtuelle à l’échelle de machines virtuelles, elles de temps à l’instance. Lors du déploiement en tant qu’instances de l’application, la configuration de l’application est gérée dans le cadre de la machine virtuelle.

Déploiement des mises à jour comme images Docker est beaucoup plus rapide et efficace du réseau. Docker Images démarrent généralement en secondes, ce qui accélère les déploiements. Destruction d’une instance de Docker est aussi simple que l’émission d’un **stop de docker** commande, généralement à la fin dans moins d’une seconde.

Comme les conteneurs sont par nature immuables par sa conception, vous devez jamais à vous soucier des machines virtuelles d’endommagés, tandis que les scripts de mise à jour peuvent oublier pour prendre en compte une configuration spécifique ou d’un fichier restant sur le disque.

Alors que les applications monolithiques peuvent tirer parti de Docker, en fractionnant l’application monolithique aux systèmes sub qui peut être mis à l’échelle, développés et déployés de manière individuelle peut être votre point d’entrée dans le domaine de microservices.

> ### <a name="references--common-web-architectures"></a>Références – Architectures Web courantes
> - **La nouvelle Architecture**  
> <https://8thlight.com/blog/Uncle-Bob/2012/08/13/the-Clean-architecture.HTML>
> - **L’Architecture en cercles concentriques**  
> <http://jeffreypalermo.com/blog/the-Onion-architecture-part-1/>
> - **Le modèle de référentiel**  
> <http://deviq.com/repository-Pattern/>
> - **Nettoyer l’exemple de Solution d’Architecture**  
> <https://github.com/ardalis/cleanarchitecture>
> - **Architecture des livres Microservices** <http://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
[Précédente] (architecture principles.md) [suivant] (commun-client-côté-web-technologies.md)
