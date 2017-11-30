---
title: Conteneurs comme base pour une collaboration DevOps
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 24aad577fca0fd540d66f9e037b58f53583d8fbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Conteneurs comme base pour une collaboration DevOps

La nature de la technologie de Docker et de conteneurs, les développeurs peuvent partager leurs logiciels et les dépendances facilement avec les environnements de production et les opérations informatiques tout en éliminant la classique prétend « il fonctionne sur mon ordinateur ». Conteneurs de résoudre les conflits d’application entre différents environnements. Indirectement, conteneurs et Docker, réunissez les développeurs et les opérateurs informatiques sont plus proches, ce qui facilite leur permettent de collaborer efficacement. La continuité des activités DevOps leur avez recherché mais précédemment mettre en œuvre via une configuration plus complexe pour la mise en production et générer des pipelines adopter le flux de travail conteneur fournit de nombreux clients. Conteneurs de simplifient les pipelines génération/test/déploiement DevOps.

![](./media/image1.png)

Charges de travail principal figure 2-1 : par « personas » dans le cycle de vie pour les applications en conteneur Docker

Avec des conteneurs Docker, les développeurs propres Nouveautés dans le conteneur (application et service et les dépendances pour les infrastructures et des composants) et comment les conteneurs et les services se comportent en tant qu’une application composée d’une collection de services. Les interdépendances des conteneurs plusieurs sont définies dans un fichier compose.yml de docker, ou ce qui peut être appelé une *manifeste de déploiement*. Pendant ce temps, les équipes d’exploitation informatique (professionnels de l’informatique et gestion) peuvent se concentrer sur la gestion des environnements de production ; infrastructure ; évolutivité ; analyse ; et, enfin, vous être assuré que les applications offrent correctement pour les utilisateurs finaux, sans avoir à connaître le contenu des conteneurs différents. Par conséquent, le nom « conteneur, « rappelant l’analogie aux conteneurs d’expédition du monde réel. Par conséquent, les propriétaires de contenu d’un conteneur ne pas concerner eux-mêmes avec la façon dont le conteneur est livré et les transports de société d’expédition un conteneur à partir de son point d’origine vers sa destination sans connaître ou de sur le contenu. De la même manière, les développeurs peuvent créer et possède le contenu dans un conteneur Docker sans devoir se préoccuper les mécanismes de « transport ».

Dans la base sur le côté gauche de la Figure 2-1, les développeurs écrivent et exécutent localement le code dans des conteneurs Docker à l’aide de Docker pour Windows ou Mac. Ils définissent l’environnement d’exploitation pour le code à l’aide d’un fichier Dockerfile qui spécifie le système d’exploitation de base à l’exécution ainsi que les étapes de génération pour la création de leur code dans une image Docker. Les développeurs de définissent comment l’une ou plusieurs images seront interagissent à l’aide de la susmentionnés *docker-compose.yml* manifeste de déploiement de fichiers. Comme elles terminent leur développement local, push leur code d’application ainsi que les fichiers de configuration de Docker dans le référentiel de code de leur choix (autrement dit, le référentiel Git).

Le montant de DevOps définit les pipelines d’intégration (CI) – continu de build à l’aide du fichier Dockerfile fourni dans le référentiel de code. Le système CI extrait les images de conteneur de base à partir du Registre Docker sélectionné et génère les images Docker personnalisées pour l’application. Puis les images sont validées et envoyées au Registre Docker utilisé pour les déploiements à plusieurs environnements.

Dans le fondement sur la droite, les équipes gérer les opérations déploiement applications et l’infrastructure de production lors de la surveillance de l’environnement et les applications afin qu’ils puissent fournir des commentaires et des informations à l’équipe de développement sur la manière dont l’application peut améliorées. Applications de conteneur sont généralement exécutées en production à l’aide d’orchestrators de conteneur.

Les deux équipes collaborent via une plate-forme (conteneurs Docker) qui fournit une séparation des préoccupations en tant qu’un contrat, tout en améliorant considérablement la collaboration les deux équipes dans le cycle de vie d’application. Les développeurs possèdent les interdépendances de conteneur, le contenu du conteneur et son environnement d’exploitation, tandis que les équipes d’exploitation prennent les images de génération, ainsi que le manifeste et les exécute dans son système d’orchestration.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Introduction à un workflow de cycle de vie bout en bout Docker application générique

Figure 2-2 présente un flux de travail plus détaillée pour un cycle de vie application Docker, en mettant l’accent dans cette instance de ressources et des activités spécifiques DevOps.

![](./media/image2.png)

Figure 2-2 : les flux de haut niveau pour le cycle de vie d’une application en conteneur Docker

Tout commence par le développeur, qui commence à écrire du code dans le flux de travail de la boucle interne. L’étape de la boucle interne est où les développeurs définissent tout ce qui se produit avant d’installer le code dans le référentiel de code (par exemple, un système de contrôle source tels que Git). Il est validé, le référentiel est déclenché après intégration continue (CI) et le reste du flux de travail.

La boucle interne est constituée fondamentalement d’étapes classiques tels que « code », « run », « test » et « debug », ainsi que des étapes supplémentaires directement avant l’exécution de l’application localement. Il s’agit lorsque le développeur s’exécute et teste l’application comme un conteneur Docker. Le flux de travail de la boucle interne est expliquée dans les sections qui suivent.

Reprise en une étape d’examiner le workflow de fin à la fin, le flux de travail DevOps est plus d’une technologie ou d’un ensemble d’outils : il s’agit d’un état d’esprit qui nécessite une évolution culturelle. Il s’agit des personnes, les processus et les outils appropriés pour rendre votre cycle de vie d’application plus rapide et prévisible. Les entreprises qui adoptent un flux de travail en conteneur généralement restructurer leurs organisations pour représenter les personnes et les processus qui correspondent à des flux de travail.

Qui emploient DevOps permet aux équipes de répondre plus rapidement conjointement à la pression de la concurrence en remplaçant des processus manuels sujets aux erreurs avec automation, ce qui entraîne la traçabilité améliorée et des workflows reproductibles. Les organisations peuvent également gérer plus efficacement des environnements et réaliser des économies en combinant locaux et des ressources de cloud, ainsi que des outils étroitement intégrés.

Lors de l’implémentation de votre flux de travail DevOps pour les applications de Docker, vous verrez que les technologies de Docker sont présents dans presque chaque étape du flux de travail, à partir de votre boîte de dialogue de développement tout en travaillant dans la boucle interne (code, exécuter, déboguer), à la phase de génération-test-l’élément de configuration et, Bien entendu, à la production et l’environnement intermédiaire et lors du déploiement de vos conteneurs à ces environnements.

Amélioration des pratiques de qualité permet d’identifier les défauts au début du cycle de développement, ce qui réduit le coût de leur résolution. En incluant l’environnement et les dépendances dans l’image et en adoptant une philosophie de déploiement de la même image sur plusieurs environnements, de promouvoir une discipline d’extraire les configurations spécifiques à l’environnement qui effectue les déploiements plus fiable.

Données enrichies obtenues via l’instrumentation efficace (analyse et aux diagnostics) permet de connaître les problèmes de performances et le comportement de l’utilisateur pour guider les investissements et les priorités futures.

DevOps considéré un parcours, pas une destination. Il doit être implémentée progressivement via projets correctement étendues à partir de laquelle vous pouvez illustrer la réussite, en savoir plus et évoluent.

## <a name="benefits-of-devops-for-containerized-applications"></a>Avantages de DevOps pour des applications en conteneur

Voici quelques-uns des principaux avantages fournis par un flux de travail plein DevOps :

-   Fournir des logiciels de meilleure qualité, plus rapidement et avec une meilleure compatibilité

-   Lecteur ajustements et amélioration permanente plus tôt et plus économique

-   Augmenter la transparence et collaboration entre les parties prenantes impliquées dans la livraison et de logiciel

-   Contrôler les coûts et utiliser plus efficacement les ressources configurées tout en réduisant les risques de sécurité

-   Plug-and-play correctement avec la plupart de vos investissements DevOps existants, y compris les investissements dans open source

>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (.. /Microsoft-Platform-Tools-containerized-Apps/index.MD)
