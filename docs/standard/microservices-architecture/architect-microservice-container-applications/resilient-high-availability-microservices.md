---
title: "Résilience et la haute disponibilité dans microservices"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Résilience et la haute disponibilité dans microservices"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 149e28ac7bd7383e4e960ed8a226943e2b9bdaa1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="resiliency-and-high-availability-in-microservices"></a>Résilience et la haute disponibilité dans microservices

Traitement des erreurs inattendues est un des problèmes plus difficiles à résoudre, en particulier dans un système distribué. Une grande partie du code que les développeurs écrivent implique la gestion des exceptions, et il s’agit également où la plupart du temps est passé dans le test. Le problème est plus complexe que l’écriture de code pour gérer les erreurs. Que se passe-t-il en cas d’échec de l’ordinateur sur lequel s’exécute le microservice ? Non seulement vous devez détecter cet échec microservice (un problème sur son propre), mais vous devez également quelque chose pour redémarrer votre microservice.

Un microservice doit résister aux défaillances et à pouvoir redémarrer souvent sur un autre ordinateur pour la disponibilité. Cette souplesse comprend également vers le bas à l’état qui a été enregistré pour le compte de le microservice, où le microservice peut récupérer cet état à partir de, et si le microservice redémarre. En d’autres termes, il doit être résilience de la capacité de calcul (le processus peut redémarrer à tout moment), ainsi que la résilience dans l’état ou les données (sans perte de données et les données restent cohérentes).

Les problèmes de résilience sont aggravés durant les autres scénarios, tels que lorsque les échecs se produisent pendant une mise à niveau de l’application. Le microservice, utilisation avec le système de déploiement doit déterminer si elle peut continuer à accéder à une version plus récente ou à la place de restaurer une version antérieure pour maintenir un état cohérent. Des questions telles que si suffisamment d’ordinateurs est disponibles pour conserver le déplacement vers l’avant et comment récupérer des versions précédentes de la microservice doivent être considérés. Cela nécessite la microservice pour émettre des informations de contrôle d’intégrité afin que l’application globale et orchestrator peuvent prendre ces décisions.

En outre, la résilience est liée à des systèmes basés sur les cloud doit se comporter. Comme mentionné, un système basé sur le cloud doit adopter les échecs et doit essayer de récupérer automatiquement à partir de celles-ci. Par exemple, en cas de défaillances réseau ou un conteneur, les applications clientes ou les services client faut une stratégie de nouvelle tentative d’envoi de messages ou nouvelles tentatives de demandes, car dans de nombreux cas, les défaillances dans le cloud sont partielles. Le [mise en œuvre des Applications résilientes](#implementing_resilient_apps) section de ce guide explique comment gérer une défaillance partielle. Elle décrit les techniques telles que de nouvelles tentatives avec interruption exponentielle ou le modèle de disjoncteur dans .NET Core à l’aide des bibliothèques telles que [Polly](https://github.com/App-vNext/Polly), qui offre une grande variété de stratégies pour gérer ce sujet.

## <a name="health-management-and-diagnostics-in-microservices"></a>Gestion de la santé et diagnostics dans microservices

Cela peut paraître évident et il est souvent négligé, mais un microservice doit signaler son intégrité et les diagnostics. Sinon, il est peu d’informations à partir d’un point de vue des opérations. Mise en corrélation des événements de diagnostic sur un ensemble de services indépendants et que vous traitez des décalages d’horloge machine sens de l’ordre des événements sont difficile. Dans la même façon que vous interagissez avec un microservice sur convenu de protocoles et formats de données, il est nécessaire de normalisation quant à l’intégrité et les événements de diagnostic qui finissent dans un magasin d’événements pour l’interrogation et affichage de journal. Dans une approche microservices, il s’agit de clé que différentes équipes s’accorder sur un format de journal unique. Il doit être une approche cohérente à l’affichage des événements de diagnostic de l’application.

### <a name="health-checks"></a>Contrôles d’intégrité

Contrôle d’intégrité est différent de diagnostics. Contrôle d’intégrité est sur le microservice reporting son état actuel à prendre les mesures appropriées. Un bon exemple fonctionne avec les mécanismes de mise à niveau et de déploiement pour maintenir la disponibilité. Bien qu’un service peut actuellement être défectueux en raison d’un arrêt de processus ou redémarrage de l’ordinateur, le service peut toujours être opérationnels. La dernière chose est à faire pire en effectuant une mise à niveau. La meilleure approche consiste à faire en premier une enquête ou attendez que le microservice à récupérer. Événements de contrôle d’intégrité à partir d’un microservice nous aider à prendre des décisions avisées et, en effet, aider à créer des services de réparation automatique.

Dans l’implémentation de contrôles d’intégrité dans la section de services ASP.NET Core de ce guide, nous expliquons comment utiliser une nouvelle bibliothèque de vérifications d’ASP.NET dans votre microservices afin qu’ils peuvent leur état à un service de surveillance pour prendre les mesures appropriées.

### <a name="using-diagnostics-and-logs-event-streams"></a>À l’aide de flux d’événements de journaux et de diagnostic

Journaux fournissent des informations sur la façon dont une application ou un service est en cours d’exécution, y compris les exceptions, les avertissements et messages d’information simples. En règle générale, chaque journal est au format texte avec une ligne par événement, bien que les exceptions montrent également souvent la trace de pile sur plusieurs lignes.

Dans les applications serveur monolithiques, vous pouvez simplement écrire les journaux dans un fichier sur disque (un fichier journal) et puis les analyser avec n’importe quel outil. Étant donné que l’exécution de l’application est limitée à un serveur fixe ou la machine virtuelle, il est généralement pas trop complexe pour analyser le flux d’événements. Toutefois, dans une application distribuée où plusieurs services sont exécutées sur plusieurs nœuds d’un cluster d’orchestrator, qui est en mesure de mettre en corrélation les événements distribuées est un défi.

Une application basée sur les microservice doit pas tenter de stocker le flux de sortie des événements ou des fichiers journaux par lui-même et même pas que vous essayez de gérer le routage des événements à un emplacement central. Il doit être transparent, ce qui signifie que que chaque processus doit écrire juste de son flux d’événements vers une sortie standard qui, en dessous, est collectée par l’infrastructure de l’environnement d’exécution où il est en cours d’exécution. Est un exemple de ces routeurs de flux de données d’événement [Microsoft.Diagnostic.EventFlow](https://github.com/Azure/diagnostics-eventflow), qui collecte des flux d’événements provenant de plusieurs sources et le publie aux systèmes de sortie. Celles-ci peuvent inclure la sortie standard simple pour un environnement de développement ou de systèmes de cloud comme [Application Insights](https://azure.microsoft.com/services/application-insights/), [OMS](https://github.com/Azure/diagnostics-eventflow#oms-operations-management-suite) (pour les applications sur site), et [lesDiagnosticsAzure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/azure-diagnostics). Il existe également plateformes d’analyse de journal complet de tiers et des outils qui permettent de rechercher, alerte, état, et les journaux d’analyse, même en temps réel, telles que [Splunk](http://www.splunk.com/goto/Splunk_Log_Management?ac=ga_usa_log_analysis_phrase_Mar17&_kk=logs%20analysis&gclid=CNzkzIrex9MCFYGHfgodW5YOtA).

### <a name="orchestrators-managing-health-and-diagnostics-information"></a>Orchestrators la gestion des informations d’intégrité et diagnostics

Lorsque vous créez une application basée sur un microservice, vous devez gérer la complexité. Bien entendu, un seul microservice est simple à gérer, mais des dizaines ou des centaines de types et des milliers d’instances de microservices est un problème complex. Il n’est pas créé à votre architecture microservice, vous devez également une disponibilité élevée, adressabilité, de résilience, intégrité et diagnostics si vous voulez disposer d’un système stable et cohérent.

![](./media/image22.png)

**Figure 4-22**. Une plateforme Microservice est essentielle pour la gestion de l’intégrité d’une application

Les problèmes complexes indiqués dans la Figure 4-22 sont très difficiles à résoudre par vous-même. Les équipes de développement doivent se concentrer sur la résolution des problèmes et de création d’applications personnalisées avec des approches basées sur un microservice. Ils ne doivent pas se concentrer sur la résolution des problèmes d’infrastructure complexe ; dans l’affirmative, le coût de n’importe quelle application microservice serait énorme. Par conséquent, il existe des plateformes orientée de microservice, appelées orchestrators ou microservice clusters, qui tentent de résoudre des problèmes de génération et exécution d’un service et l’utilisation efficace des ressources d’infrastructure. Cela réduit la complexité de la création d’applications qui utilisent une approche microservices.

Orchestrators différents peuvent sembler identiques, mais les vérifications d’intégrité offertes par chacun d’eux et diagnostic diffèrent dans les fonctionnalités et l’état de maturité, parfois en fonction de la plateforme du système d’exploitation, comme expliqué dans la section suivante.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Le facteur de douze l’application. XI. Journaux : Traiter les journaux sous forme de flux d’événements**
    [*https://12factor.net/logs*](https://12factor.net/logs)

-   **Bibliothèque de EventFlow de Diagnostic de Microsoft.** Référentiel GitHub.

    [*https://github.com/Azure/Diagnostics-eventflow*](https://github.com/Azure/diagnostics-eventflow)

-   **Nouveautés de Azure Diagnostics**
    [*https://docs.microsoft.com/azure/azure-diagnostics*](https://docs.microsoft.com/azure/azure-diagnostics)

-   **Connecter des ordinateurs Windows et le service de journal Analytique dans Azure**
    [*https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents*](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents)

-   **Ce que vous journalisation moyenne : Le bloc d’Application de journalisation sémantique à l’aide de**
    [*https://msdn.microsoft.com/library/dn440729 (v=pandp.60).aspx*](https://msdn.microsoft.com/library/dn440729(v=pandp.60).aspx)

-   **Splunk.** Site officiel.
    [*http://www.splunk.com*](http://www.splunk.com)

-   **EventSource, classe**. API pour les événements de suivi pour Windows (ETW) [ *https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource*](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing.eventsource)




>[!div class="step-by-step"]
[Précédente] (microservice-based-composite-ui-shape-layout.md) [suivant] (scalable-available-multi-container-microservice-applications.md)
