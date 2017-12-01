---
title: "Moderniser vos applications avec la surveillance et télémétrie"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Moderniser vos applications avec la surveillance et télémétrie"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 03a6f2be9dc6c020cfe93a2597d1288943e527c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Moderniser vos applications avec la surveillance et télémétrie

Lorsque vous exécutez une application en production, il est essentiel que vous disposez des informations sur les performances de votre application. Il effectue un haut niveau ? Utilisateurs obtenez des erreurs ou l’application n’est stable et fiable ? Vous avez besoin de l’analyse des performances riche, puissant alertes et tableaux de bord pour vous assurer que votre application est disponible et les performances comme prévu. Vous devez également être en mesure de voir rapidement s’il existe un problème, déterminer le nombre de clients est affecté et effectuer une analyse des causes pour rechercher et corriger le problème.

## <a name="monitor-your-application-with-application-insights"></a>Analyser votre application avec Application Insights

Application Insights est un service de gestion des performances des applications (APM) extensible pour les développeurs web qui fonctionnent sur plusieurs plateformes. Il permet d’analyser votre application web dynamique. Application Insights détecte automatiquement les anomalies de performance. Il inclut des outils puissants analytique pour vous aider à diagnostiquer les problèmes et pour vous aider à comprendre ce que les utilisateurs effectuent avec votre application. Application Insights est conçu pour vous aider à améliorer en permanence les performances et la convivialité. Il fonctionne pour les applications sur un large éventail de plateformes, y compris .NET, Node.js et J2EE, si hébergé localement ou dans le cloud. Application Insights s’intègre à vos processus DevOps et a des points de connexion à une variété d’outils de développement.

Figure 4-10 illustre un exemple de comment Application Insights surveille votre application et comment il expose ces analyses au tableau de bord.

![Tableau de bord de surveillance application Insights](./media/image10.png)

> **Figure 4-10.** Tableau de bord de surveillance application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Surveiller votre infrastructure de Docker avec Analytique de journal et de sa solution d’analyse de conteneur

[Azure Analytique de journal](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) fait partie de la [globale de solution de surveillance de Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Il est également un service [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Analytique de journal surveille le cloud et les environnements locaux (OMS pour local) pour aider à assurer la disponibilité et les performances. Il collecte les données générées par les ressources dans vos environnements locaux et cloud et d’autres outils de surveillance pour fournir une analyse à plusieurs sources.

Par rapport aux journaux d’infrastructure Azure, Analytique de journal, comme un service Azure, résultants journal et mesure des données à partir d’autres services Azure (via [moniteur Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), machines virtuelles Azure, les conteneurs Docker et en local ou autres infrastructures de cloud. Analytique de journal offre de recherche de journal flexible et analytique hors de la zone au-dessus de ces données. Il fournit des outils que vous pouvez utiliser pour analyser les données dans toutes les sources, il permet des requêtes complexes sur tous les journaux et peut informer proactive en fonction des conditions spécifiées. Vous pouvez même collecter des données personnalisées dans le référentiel central Analytique de journal, où vous pouvez interroger et visualiser. Vous pouvez également tirer parti des solutions intégrées Analytique de journal pour obtenir des informations détaillées dans la sécurité et les fonctionnalités de votre infrastructure.

Vous pouvez accéder Analytique de journal par le biais du portail OMS ou le portail Azure, qui s’exécutent dans n’importe quel navigateur, et fournir d’accéder aux paramètres de configuration et des plusieurs outils pour analyser et agir sur les données collectées.

Le [solution d’analyse de conteneur](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) dans Analytique de journal permet de consulter et de gérer vos hôtes Docker et conteneur Windows dans un emplacement unique. La solution montre les conteneurs sont en cours d’exécution, image de conteneur qu’ils s’exécutent et exécutant des conteneurs. Vous pouvez afficher des informations d’audit détaillées, y compris les commandes qui sont utilisés avec des conteneurs. Vous pouvez également résoudre les conteneurs en affichant et en recherche de journaux centralisées, sans avoir à afficher à distance des ordinateurs hôtes Docker ou Windows. Vous pouvez rechercher des conteneurs qui peuvent être bruyants et beaucoup de ressources en excès sur un ordinateur hôte. En outre, vous pouvez afficher centralisée de l’UC, mémoire, stockage, l’utilisation du réseau et des informations sur les performances, pour les conteneurs. Sur les ordinateurs exécutant Windows, vous pouvez centraliser et comparer les journaux à partir de Windows Server, Hyper-V et des conteneurs Docker. La solution prend en charge les orchestrators conteneur suivant :

-   Docker essaim

-   CONTRÔLEUR DE DOMAINE/SYSTÈME D’EXPLOITATION

-   Kubernetes

-   Infrastructure de service

-   Red Hat OpenShift

Figure 4-11 montre les relations entre les différents hôtes de conteneurs et les agents et OMS.

![Solution de surveillance de conteneur Analytique de journal](./media/image11.png)

> **Figure 4-11.** Solution de surveillance de conteneur Analytique de journal

Vous pouvez utiliser la solution d’analyse de journal Analytique conteneur à :

-   Afficher des informations sur tous les hôtes de conteneur dans un emplacement unique.

-   Connaître les conteneurs sont en cours d’exécution, image qu’ils s’exécutent, et où ils s’exécutent.

-   Consultez une piste d’audit pour les actions sur les conteneurs.

-   Résoudre les problèmes en affichant et en recherche de journaux centralisées sans connexion à distance aux ordinateurs hôtes Docker.

-   Rechercher des conteneurs qui peuvent être « voisin bruyant » et consomme des ressources supplémentaires sur un ordinateur hôte.

-   Afficher centralisée de l’UC, mémoire, stockage, l’utilisation du réseau et des informations sur les performances, pour les conteneurs.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Vue d’ensemble de l’analyse dans Microsoft Azure**

[https://docs.Microsoft.com/Azure/Monitoring-and-Diagnostics/Monitoring-Overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **Nouveautés d’Application Insights ?**

[https://docs.Microsoft.com/Azure/application-Insights/App-Insights-Overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **Quel est le journal Analytique ?**

[https://docs.Microsoft.com/Azure/log-Analytics/log-Analytics-Overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   **Solution de surveillance de conteneur dans le journal Analytique**

[https://docs.Microsoft.com/Azure/log-Analytics/log-Analytics-Containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Vue d’ensemble du moniteur de Azure**

[https://docs.Microsoft.com/Azure/Monitoring-and-Diagnostics/Monitoring-Overview-Azure-Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **Nouveautés d’Operations Management Suite (OMS) ?**

[https://docs.Microsoft.com/Azure/Operations-Management-Suite/Operations-Management-Suite-Overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **Analyse des conteneurs Windows Server dans l’infrastructure de Service auprès d’OMS**

[https://docs.Microsoft.com/Azure/service-Fabric/service-Fabric-Diagnostics-Containers-WindowsServer](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[Précédent](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Suivant](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
