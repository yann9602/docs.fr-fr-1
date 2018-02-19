---
title: "Surveiller les services d’application en conteneur"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 58bf96dfa06a78892563698200e6f4df5f371346
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="monitor-containerized-application-services"></a>Surveiller les services d’application en conteneur

Il est essentiel pour les applications de fractionner en plusieurs conteneurs et microservices un moyen de surveiller et d’analyser le comportement de l’application.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) est un service d’analytique extensible qui surveille votre application en temps réel. Il vous aide à détecter et diagnostiquer les problèmes de performances et de comprendre ce que les utilisateurs effectuent avec votre application. Il est conçu pour les développeurs, avec l’intention de vous aider à améliorer en permanence les performances et la facilité d’utilisation de vos services ou applications. Application Insights fonctionne avec les services web/et autonome des applications sur un large éventail de plateformes, comme .NET, Java, Node.js et nombreuses autres plateformes, hébergé localement ou dans le cloud.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analyse des applications de Docker dans les environnements de questions et réponses à l’aide d’Application Insights

En ce qui concerne les Docker, vous pouvez représenter des événements de cycle de vie et les compteurs de performances à partir des conteneurs Docker sur Application Insights. Vous devez simplement exécuter la [image Application Insights Docker](https://hub.docker.com/r/microsoft/applicationinsights/) comme un conteneur dans votre hôte et il affiche les compteurs de performance pour l’hôte, ainsi que pour les autres images Docker. Cette image de l’Application Insights Docker (Figure 6 - 1) vous aide à surveiller vos applications en conteneur en collectant les données de télémétrie sur les performances et l’activité de l’hôte Docker (autrement dit, vos ordinateurs virtuels Linux), les conteneurs Docker et les applications en cours d’exécution au sein de celles-ci.

![exemple](./media/image1.png)

Figure 6-1 : Application Insights analyse les conteneurs et les hôtes de Docker

Lorsque vous exécutez le [image Application Insights Docker](https://hub.docker.com/r/microsoft/applicationinsights/) sur l’hôte Docker, vous pouvez :

-   Cycle de vie des données de télémétrie sur tous les conteneurs en cours d’exécution sur l’ordinateur hôte, Démarrer, arrêter et ainsi de suite.

-   Compteurs de performances pour tous les conteneurs : processeur, mémoire, l’utilisation du réseau et bien plus encore.

-   Si vous avez installé également [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) dans les applications en cours d’exécution dans les conteneurs, toutes les données de télémétrie de ces applications ont des propriétés supplémentaires identifier l’ordinateur hôte et de conteneur. Ainsi, par exemple, si vous avez des instances d’une application en cours d’exécution dans plusieurs hôtes, vous facilement pourrez filtrer la télémétrie de votre application par hôte.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Configuration d’Application Insights pour analyser les applications Docker et les hôtes de Docker

Pour créer une ressource Application Insights, suivez les instructions fournies dans les articles présentés dans la liste qui suit. Portail Azure créera le script nécessaire pour vous.

-   **Analyser les applications Docker dans Application Insights :**[https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Image d’application Insights Docker Hub Docker et Github :**  
[https://Hub.docker.com/r/Microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) et <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Vous pouvez configurer Application Insights pour ASP.NET :**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Application Insights pour les pages web :**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](http://microsoft.com/oms) est une solution de gestion informatique simplifiée qui fournit l’analytique de journal, d’automatisation, sauvegarde et récupération de site. En fonction de [requêtes](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) dans Operations Management Suite, vous pouvez augmenter [alertes](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) et définir la mise à jour via [Azure Automation](https://docs.microsoft.com/azure/automation/). Il intègre également en toute transparence vos solutions de gestion existant pour fournir une vue du volet verre-unique. Operations Management Suite vous aide à gérer et protéger vos locaux et d’infrastructure de cloud computing.

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](http://microsoft.com/oms) Solution conteneur Docker

En plus de fournir des services précieux sur son propre, la Solution de conteneur Operations Management Suite pouvez gérer et surveiller des hôtes Docker et les conteneurs en affichant des informations sur l’emplacement vos conteneurs et les hôtes de conteneur, les conteneurs en cours d’exécution ou ayant échoué et les journaux de conteneur et le démon Docker envoyés à *stdout* et *stderr*. Elle montre également les métriques de performances, notamment celles liées au processeur, à la mémoire, au réseau et au stockage pour le conteneur et les hôtes pour vous aider à résoudre et à trouver les conteneurs voisins bruyants.

![](./media/image2.png)

Figure 6-2 : les informations sur les conteneurs Docker indiqué par Operations Management Suite

Application Insights et Operations Management Suite se concentrent sur la surveillance des activités ; Toutefois, Application Insights se concentre plus sur les applications elles-mêmes grâce à son kit de développement logiciel en cours d’exécution dans l’application d’analyse. Toutefois, Operations Management Suite se concentre davantage sur l’infrastructure sur les ordinateurs hôtes, il offre en outre une analyse approfondie sur les journaux à l’échelle tout en fournissant un système très flexible piloté par les données/requête de recherche.

Comme Operations Management Suite est implémenté comme un service basé sur le cloud, il peut être en cours d’exécution rapidement avec un investissement minimal dans les services d’infrastructure. Nouvelles fonctionnalités sont fournies automatiquement, qui vous évite de maintenance continue et les coûts de mise à niveau.

Solution de conteneur Operations Management Suite, vous pouvez effectuer les opérations suivantes :

-   Centraliser et mettre en corrélation des millions de journaux à partir des conteneurs Docker à l’échelle

-   Afficher des informations sur tous les hôtes de conteneur dans un emplacement unique

-   Connaître les conteneurs sont en cours d’exécution, image qu’ils s’exécutent, et où ils s’exécutent

-   Diagnostiquer rapidement les conteneurs de « voisin bruyant » qui peuvent entraîner des problèmes sur les ordinateurs hôtes de conteneur

-   Consultez une piste d’audit pour les actions sur les conteneurs

-   Résoudre les problèmes en affichant et en recherche de journaux centralisées sans la communication à distance aux ordinateurs hôtes Docker

-   Rechercher des conteneurs qui peuvent être « voisin bruyant » et consomme des ressources excessives sur un ordinateur hôte

-   Afficher centralisée de l’UC, mémoire, stockage et les informations de performances et d’utilisation réseau pour les conteneurs

-   Générer des tests des conteneurs Docker avec Azure Automation

Vous pouvez voir des informations sur les performances en exécutant des requêtes comme Type = Perf, comme indiqué dans la Figure 6-3.

![DockerPerfMetricsView](./media/image3.png){width="5.78625in" height="3.25in"}

Figure 6-3 : les métriques de performances des hôtes Docker indiquées par Operations Management Suite

L’enregistrement des requêtes est également une fonctionnalité standard dans Operations Management Suite et peuvent vous aider à conserver des requêtes que vous avez trouvé utile et découvrez des tendances dans votre système.

**Plus d’informations** pour trouver des solutions de conteneur dans plus d’informations sur l’installation et la configuration du Docker [Operations Management Suite](http://microsoft.com/oms), accédez à <https://docs.microsoft.com/azure/log-analytics /log-Analytics-Containers>.

>[!div class="step-by-step"]
[Précédente] (gérer-production-docker-environments.md) [suivant] (.. /Key-takeaways/index.MD)
