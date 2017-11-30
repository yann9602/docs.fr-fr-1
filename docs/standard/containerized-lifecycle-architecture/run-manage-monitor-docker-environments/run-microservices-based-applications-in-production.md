---
title: "Exécuter les applications composées et microservices dans les environnements de production"
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e7a2788098aa731699cbb201c7177e7578907673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Exécuter les applications composées et microservices dans les environnements de production

Les applications composées par plusieurs microservices n’avez pas besoin être déployée dans des clusters orchestrator afin de simplifier la complexité du déploiement et de rendre viable du point de vue d’informatique. Sans un cluster orchestrator, il serait très difficile de déployer et d’une application complexe microservices montée en puissance parallèle.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Introduction à orchestrators, les planificateurs et les clusters de conteneur

Plus haut dans ce livre électronique, nous avons présenté *clusters* et *planificateurs* dans le cadre de la discussion sur l’architecture logicielle et de développement. Docker Swarm et système d’exploitation de centre de données mésosphère (contrôleur de domaine/système d’exploitation) sont des exemples de clusters de Docker. Ces deux éléments peuvent fonctionner comme une partie de l’infrastructure fournie par le Service de conteneur Microsoft Azure.

Lorsque les applications sont montés sur plusieurs systèmes hôtes, la possibilité de gérer chaque système hôte et d’abstraire la complexité de la plateforme sous-jacente devient intéressante. C’est précisément ce que fournissent orchestrators et des planificateurs. Examinons une brève les ici :

-   **Planificateurs*** *« Planification » désigne la capacité d’un administrateur pour charger un fichier de service sur un système hôte qui établit la façon d’exécuter un conteneur spécifique. Lancement des conteneurs dans un cluster de Docker a tendance à être appelée à la planification. Bien que la planification fait référence à l’acte spécifique du chargement de la définition de service, dans un sens plus général, les planificateurs sont responsables de se connecter à un système de l’hôte init pour gérer les services de la capacité nécessaire.

Un planificateur de cluster a plusieurs objectifs : utilisation efficace des ressources du cluster, l’utilisation des contraintes de placement de fourni par l’utilisateur, applications rapidement à ne pas les laisser dans un état d’attente, ayant un degré de « respect, « en cours fiables pour les erreurs, de planification et être toujours disponibles.

-   **Orchestration*** *plateformes étendent les capacités de gestion du cycle de vie des charges de travail complexes, multicontainer déployées sur un cluster d’hôtes. En faisant abstraction de l’infrastructure de l’hôte, outils d’orchestration de permettent aux utilisateurs de traiter l’intégralité du cluster comme cible de déploiement unique.

Le processus d’orchestration implique des outils et une plateforme qui automatise tous les aspects de la gestion des applications à partir de la sélection élective initiale ou de déploiement par conteneur ; déplacement de conteneurs sur différents hôtes selon l’intégrité de son hôte ou des performances ; le contrôle de version et enchaînée mises à jour et l’intégrité de la surveillance des fonctions qui prennent en charge la mise à l’échelle et basculement ; et bien plus encore.

Orchestration est un terme général qui fait référence à la planification du conteneur gestion du cluster et éventuellement la configuration des hôtes supplémentaires.

Les capacités offertes par orchestrators et des planificateurs sont très complexes à développer et créer à partir de zéro, et par conséquent vous souhaite apporter utilisation des solutions d’orchestration offertes par les fournisseurs.


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (gérer-production-docker-environments.md)
