---
title: Workflow DevOps pour les applications Docker avec les outils Microsoft
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft (workflow DevOps avec les outils Microsoft)
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8539e8c0a6d0c6c9d558b91e062184e7ef135856
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Workflow DevOps pour les applications Docker avec les outils Microsoft

Microsoft Visual Studio, Visual Studio Team Services, Team Foundation Server et Application Insights fournissent un écosystème complet pour le développement et les opérations informatiques. Votre équipe dispose de tous les outils nécessaires pour gérer des projets et générer, tester et déployer rapidement des applications en conteneur.

Avec Visual Studio et Visual Studio Team Services dans le cloud, et Team Foundation Server au niveau local, les équipes de développement peuvent efficacement générer, tester et publier des applications en conteneur ciblant n’importe quelle plateforme (Windows ou Linux).

Les outils Microsoft peuvent automatiser le pipeline pour des implémentations spécifiques d’applications en conteneur (Docker, .NET Core ou toute combinaison avec d’autres plateformes) : builds globales et intégration continue (CI), tests avec Visual Studio Team Services ou Team Foundation Server, déploiement continu (CD) dans les environnements Docker (développement, préproduction, production) et transmission de données analytiques sur les services à l’équipe de développement par le biais d’Application Insights. Chaque validation de code peut lancer une build (CI) et déployer automatiquement les services sur des environnements en conteneur spécifiques (CD).

Les développeurs et testeurs peuvent provisionner facilement et rapidement des environnements de développement et de test basés sur Docker similaires à des environnements de production au moyen de modèles dans Microsoft Azure.

La difficulté du développement d’applications en conteneur augmente de façon régulière en fonction de la complexité et des besoins en matière de scalabilité de l’entreprise. Les applications basées sur des architectures de microservices constituent un bon exemple. Pour réussir dans un tel environnement, votre projet doit automatiser le cycle de vie dans sa totalité : non seulement la build et le déploiement, mais aussi la gestion des versions et la collecte des données de télémétrie. Visual Studio Team Services et Azure offrent les fonctionnalités suivantes :

-   Gestion du code source Visual Studio Team Services/Team Foundation Server (basée sur Git ou Team Foundation Version Control), planification Agile (Agile, Scrum et CMMI sont pris en charge), intégration continue, gestion des versions et autres outils pour les équipes Agile.

-   Visual Studio Team Services et Team Foundation Server incluent un écosystème puissant et en plein essor d’extensions propriétaires et tierces à l’aide desquelles vous pouvez facilement construire un pipeline (intégration continue, build, test, remise et gestion des versions) pour les microservices.

-   Exécution de tests automatisés dans le cadre de votre pipeline de build dans Visual Studio Team Services.

-   Visual Studio Team Services peut renforcer le cycle de vie DevOps en effectuant des remises sur plusieurs environnements : non seulement les environnements de production, mais aussi à des fins de test (expérimentation A/B, [versions « canary »](http://martinfowler.com/bliki/CanaryRelease.html), etc.).

-   Les organisations peuvent facilement provisionner des conteneurs Docker à partir d’images privées stockées dans Azure Container Registry, ainsi que toute dépendance vis-à-vis de composants Azure (Data, PaaS, etc.) à l’aide de modèles Azure Resource Manager accessibles avec des outils familiers.


>[!div class="step-by-step"]
[Précédent] (../design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [Suivant] (docker-application-outer-loop-devops-workflow.md)
