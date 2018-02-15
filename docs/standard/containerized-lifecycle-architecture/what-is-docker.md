---
title: "Qu’est-ce que Docker ?"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c75b2fa87e5aad93693c76c3bbd135044b36525f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="what-is-docker"></a>Qu’est-ce que Docker ?

[Docker](https://www.docker.com/) est un [projet open source](https://github.com/docker/docker) pour automatiser le déploiement d’applications en tant que conteneurs portables, autonomes qui peuvent s’exécuter dans le cloud ou localement (voir Figure 1 - 2). Docker est également un [société](https://www.docker.com/) qui promeut et développe cette technologie, travailler en collaboration avec le cloud, Linux et les fournisseurs de Windows, notamment Microsoft.

![](./media/image2.png)

Figure 1-2 : Docker déploie des conteneurs à toutes les couches du cloud hybride

Conteneurs d’image docker peuvent s’exécuter en mode natif sur Linux et Windows. Toutefois, les images de Windows peuvent s’exécuter uniquement sur les hôtes Windows et Linux images peuvent s’exécuter uniquement sur les hôtes Linux, ce qui signifie un serveur hôte ou une machine virtuelle.

Les développeurs peuvent utiliser des environnements de développement sur Windows, Linux ou macOS. Sur l’ordinateur de développement, le développeur exécute un hôte Docker dans le Docker images sont déployés, y compris l’application et ses dépendances. Les développeurs qui travaillent sur Linux ou sur le Mac, utilisent un hôte Docker Linux basée, et ils peuvent créer des images mais uniquement pour les conteneurs Linux. (Les développeurs qui travaillent sur le Mac peuvent modifier le code ou exécuter l’interface de ligne de commande Docker \[CLI\] du macOS, mais, à ce jour, les conteneurs n’exécutez pas directement sur macOS.) Les développeurs qui travaillent sur Windows peuvent créer des images pour les conteneurs Windows ou Linux.

Pour héberger des conteneurs dans des environnements de développement et fournissent d’autres outils de développement, est fourni Docker [Docker Community Edition (CE)](https://www.docker.com/community-edition) pour Windows ou Mac OS. Ces produits installent VM nécessaire (hôte Docker) pour héberger les conteneurs. Docker est également disponible [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), qui est conçu pour le développement de l’entreprise et est utilisé par les équipes informatiques qui créent, expédier et exécuter des applications critiques volumineuses en production.

Pour exécuter [les conteneurs Windows](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), il existe deux types de runtime :

-   **Conteneur Windows Server** ce runtime fournit l’isolation des applications via une technologie d’isolation des processus et l’espace de noms. Un conteneur Windows Server partage un noyau avec l’hôte de conteneur et tous les conteneurs en cours d’exécution sur l’ordinateur hôte.

-   **Conteneur Hyper-V** cette action développe l’isolation fournie par les conteneurs Windows Server en exécutant chaque conteneur dans une machine virtuelle hautement optimisée. Dans cette configuration, le noyau de l’hôte de conteneur n’est pas partagé avec les conteneurs Hyper-V, qui fournit une meilleure isolation.

Les images de ces conteneurs sont créés de la même façon et fonctionnent de la même. La différence réside dans la manière dont le conteneur est créé à partir de l’image, l’exécution d’un conteneur Hyper-V requiert un paramètre supplémentaire. Pour plus d’informations, consultez [conteneurs Hyper-V](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-vms"></a>Comparaison des conteneurs Docker avec des machines virtuelles

Figure 1-3 indique une comparaison entre les machines virtuelles et Docker conteneurs.

Étant donné que les conteneurs nécessitent beaucoup moins de ressources (par exemple, il est inutile un système d’exploitation complet), ils sont faciles à déployer et à leur démarrage rapide. Cela rend possible d’avoir une densité plus élevée, ce qui signifie que que vous pouvez exécuter plusieurs services sur la même unité de matériel, ce qui réduit les coûts.

En tant qu’effet secondaire de l’exécution sur le même noyau, vous obtenir moins d’isolation que les machines virtuelles.

L’objectif principal d’une image est qu’elle rend l’environnement (dépendances) identique entre les différents déploiements. Cela signifie que vous pouvez le déboguer sur votre ordinateur et puis le déployer sur un autre ordinateur avec le même environnement garanti.

Une image de conteneur est un moyen pour empaqueter une application ou un service et le déployer de manière fiable et reproductible. À cet égard, Docker n’est pas uniquement une technologie, il est également une philosophie et un processus.

Lorsque vous utilisez Docker, les développeurs s’entendre pas dire, « Il fonctionne sur mon ordinateur, pourquoi ne pas en production ? » Ils peuvent simplement par exemple, « Il s’exécute sur Docker, », car l’application empaquetée Docker peut être exécutée sur n’importe quel environnement Docker pris en charge, et il s’exécutera la manière qu’il a été prévue pour sur toutes les destinations de déploiement (développement, assurance qualité, de mise en lots, production, etc..).

![](./media/image3.png)

Figure 1-3 : comparaison entre traditionnels machines virtuelles dans des conteneurs Docker


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (docker-terminology.md)
