---
title: "Raisons de courbes d’élévation et MAJ existante des applications .NET pour les applications DevOps prête pour le Cloud"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Raisons de courbes d’élévation et MAJ existante des applications .NET pour les applications DevOps prête pour le Cloud"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4f09ec8f5aa041057ac1256eb564e197793c8a2b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications"></a>Raisons de courbes d’élévation et MAJ existante des applications .NET pour les applications DevOps prête pour le Cloud

Avec une application DevOps prête pour le Cloud, vous pouvez rapidement et à plusieurs reprises livrer des applications fiables à vos clients. Vous bénéficiez agilité essentielle et la fiabilité en différant la complexité opérationnelle de votre application à la plateforme.

Si vous ne parvenez pas vos applications sur le marché rapidement, au moment où que vous expédiez votre application, le marché que vous ciblait sera ont évolué. Vous pouvez être trop tard, quel que soit l’application a été mise en œuvre ou conçue. Vous pouvez être échouent ou ne pas atteindre votre potentiel, car vous ne peut pas synchroniser la remise d’application avec les besoins du marché.

La nécessité d’innovation de continuité d’activité envoie les équipes de développement et les opérations à la limite. La seule façon d’atteindre l’agilité que vous avez besoin dans l’innovation continue est par rénovation vos applications des technologies telles que les conteneurs et les principes d’application prête pour le Cloud DevOps spécifiques.

L’essentiel est que lorsqu’une organisation génère et gère les applications qui sont DevOps prête pour le Cloud, il peut placer des solutions plus tôt entre les mains des clients et mettre de nouvelles idées sur le marché quand ils sont pertinents.

## <a name="cloud-devops-ready-application-principles-and-tenets"></a>Principes d’applications DevOps prêt et principes de cloud computing 

Améliorations dans le cloud portent principalement sur deux objectifs : réduire les coûts et améliorer la croissance de l’entreprise en améliorant la réactivité. Ces objectifs sont obtenus en ce qui simplifie le processus et de réduire la friction lorsque vous relâchez et livrer des applications.

Votre application est prête pour le Cloud DevOps si vous pouvez d’agile manière-développer votre application de façon autonome à partir d’autres applications locales et relâchez, déployer, à l’échelle automatique, surveiller et résoudre les problèmes de votre application dans le cloud.

La clé est *agilité*. Vous ne peut pas être commercialisé avec souplesse réduit au strict minimum tout déploiement de production problèmes et les problèmes d’environnement de développement et de test. Conteneurs (plus précisément, Docker, comme une norme) et services gérés ont été conçus spécialement dans ce but.

Pour obtenir une souplesse, vous devez également les processus automatisés DevOps sont basées sur les pipelines de l’élément de configuration/CD de version pour les plates-formes évolutives dans le cloud. Plateformes CI/CD (tels que Visual Studio Team Services ou Jenkins) que vous déploiement sur une plateforme cloud évolutive et robuste (comme Azure Service Fabric ou Kubernetes) sont des technologies clés pour atteindre une souplesse dans le cloud.

La liste suivante décrit les principaux principes ou pratiques pour les applications de DevOps prête pour le Cloud. Notez que vous pouvez adopter tout ou seulement une partie de ces principes, dans une approche progressive ou incrémentielle :

-   **Conteneurs**. Conteneurs de vous donnent la possibilité d’inclure des dépendances des applications avec l’application elle-même. CONTENEURISATION des données réduisant sensiblement le nombre de problèmes que vous pouvez rencontrer lorsque vous déployez sur les environnements de production ou testez dans l’environnement intermédiaire. Pour finir, conteneurs améliorent la souplesse de remise de l’application.

-   **Cloud résilient et évolutif**. Le cloud offre une plateforme qui est géré, élastique, évolutive et fiable. Ces caractéristiques sont fondamentaux pour obtenir des améliorations de coût et de livrer des applications fiables et disponibles hautement dans une livraison continue. Services gérés comme des bases de données managés, gérées mettre en cache comme un service (CaaS) et stockage géré sont des éléments fondamentaux de ce qui réduit les coûts de maintenance de votre application.

-   **Analyse**. Vous ne pouvez avoir une application fiable sans avoir un bon moyen de détecter et diagnostiquer les problèmes de performances des applications et les exceptions. Vous devez obtenir des informations exploitables par l’intermédiaire de gestion de performances des applications et des instantanés analytique.

-   **DevOps culture et livraison continue**. Adoption de pratiques de DevOps prête pour le Cloud nécessite un changement culturel dans lequel les équipes cesseront de fonctionner dans des silos indépendants. L’élément de configuration/CD pipelines sont possibles uniquement s’il existe une collaboration accrue entre le développement et les équipes d’exploitation informatique, pris en charge par les conteneurs et les outils de l’élément de configuration/CD.

Figure 4-2 montre les principaux piliers facultatif d’une application DevOps prête pour le Cloud. Les piliers plus que vous implémentez, la meilleure votre application sera réussisse satisfaire les attentes de vos clients.

> ![Axes principaux d’une application DevOps prête pour le Cloud](./media/image2.png)
>
> **Figure 4-2.** Axes principaux d’une application DevOps prête pour le Cloud

Pour résumer, une application DevOps prête pour le Cloud est une approche pour la création et la gestion des applications qui tire parti du cloud computing de modèle, tout en utilisant une combinaison de conteneurs, l’infrastructure de cloud géré, techniques de l’application robuste, surveillance, livraison continue et DevOps, tous sans avoir à redéfinir l’architecture et de réécrire vos applications existantes.

Votre organisation peut adopter ces technologies et les approches progressivement. Vous n’êtes pas obligé d’adopter tous, tous en même temps. Vous pouvez adopter les progressivement, en fonction de priorités de l’entreprise et les besoins des utilisateurs.

## <a name="benefits-of-a-cloud-devops-ready-application"></a>Avantages d’une application DevOps prête pour le Cloud

Vous pouvez obtenir les avantages suivants en les convertissant en une application existante vers une application Cloud DevOps (sans modification de l’architecture ou de codage) :

-   **Réduire les coûts, car l’infrastructure managée est géré par le fournisseur de cloud**. Les applications cloud DevOps prêt obtiennent les avantages du cloud à l’aide de l’élasticité du cloud out of box, mise à l’échelle et haute disponibilité. Avantages liés non seulement pour les fonctionnalités de calcul (machines virtuelles et conteneurs), mais dépendent également de ressources dans le cloud, une application peut nécessaire, DBaaS, CaaS et n’importe quelle infrastructure.

-   **Application résistante et l’infrastructure**. Lorsque vous migrez vers le cloud, vous devez adopter les erreurs temporaires ; erreurs se produisent dans le cloud. En outre, matériel et l’infrastructure de cloud est « remplaçable, « ce qui augmente les opportunités d’interruption temporaire. En même temps, des capacités du cloud interne et certaines techniques de développement d’application qui implémentent la résilience et d’automatisent la récupération rendent beaucoup plus facile de récupérer à partir de défaillances inattendues dans le cloud.

-   **Une compréhension plus approfondie des performances des applications**. Outils d’analyse, comme Azure Application Insights fournissent la visualisation pour la gestion de l’intégrité, la journalisation et les notifications de cloud computing. Rendre les applications facile à déboguer et auditer les journaux d’audit. Cela est essentiel pour une application cloud fiable.

-   **La portabilité des applications, avec les déploiements agiles**. Les conteneurs (conteneurs Linux ou Windows basés sur le moteur Docker) offrent la meilleure solution pour éviter une application verrouillé de cloud. À l’aide de conteneurs, les hôtes de Docker et orchestrators de clouds multiples, vous pouvez facilement déplacer d’un environnement ou de cloud computing à l’autre. Conteneurs éliminer la friction qui se produit généralement dans les déploiements à n’importe quel environnement (étape/test/production).

Tous ces avantages finalement fournissent des réductions des coûts de clé pour le cycle de vie de votre application de bout en bout.

Dans les sections suivantes, les avantages sont expliquées plus en détail et sont liés à des technologies spécifiques.

>[!div class="step-by-step"]
[Précédent](index.md)
[Suivant](microsoft-technologies-in-cloud-devops-ready-applications.md)
