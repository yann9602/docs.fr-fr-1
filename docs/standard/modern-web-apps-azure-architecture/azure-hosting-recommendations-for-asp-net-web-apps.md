---
title: "Azure hébergeant des recommandations pour les applications web ASP.NET Core"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | Azure hébergeant des recommandations pour les applications web ASP.NET"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: c361a28321ec9dcbfee1db8036757632a5d81f7c
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Azure hébergeant des recommandations pour les applications Web ASP.NET Core

> « Line-of-business leaders everywhere sont en ignorant les services informatiques pour obtenir des applications à partir du cloud (également appelé SaaS) et de paiement pour les comme s’il s’agissait d’un abonnement de magazine. Et lorsque le service n’est plus nécessaire, ils peuvent annuler l’abonnement avec aucun matériel pas utilisé dans le coin. »  
> _\-Daryl Plummer, analyste de Gartner_

## <a name="summary"></a>Résumé

Tout ce qui doit et l’architecture de votre application, Windows Azure peut prendre en charge il. Vos besoins d’hébergements peuvent être aussi simples que d’un site web statique à une application extrêmement sophistiqué constituée de dizaines de services. Des applications ASP.NET Core monolithique et les services de prise en charge, il existe plusieurs configurations connues qui sont recommandées. Les recommandations ci-dessous sont regroupées selon le type de ressource pour être hébergé, complet si des applications, des processus individuels ou des données.

## <a name="web-applications"></a>Applications Web

Les applications Web peuvent être hébergées avec :

-   Applications de Service d’applications Web

-   Conteneurs

-   Azure Service Fabric

-   Machines virtuelles (VM)

Parmi ceux-ci, les applications Web App Service sont l’approche recommandée pour la plupart des scénarios. Pour les architectures de microservice, envisagez une approche basée sur le conteneur ou l’infrastructure de service. Si vous avez besoin de davantage de contrôle sur les ordinateurs qui exécutent votre application, envisagez les Machines virtuelles Azure.

### <a name="app-service-web-apps"></a>Applications de Service d’applications Web

Applications de Service d’applications Web offre une plateforme d’entièrement gérée optimisée pour l’hébergement d’applications web. Il s’agit d’un platform-as-a-service(PaaS) offre que vous pouvez vous concentrer sur votre logique métier, tandis que Azure prend en charge l’infrastructure nécessaire pour exécuter et mettre à l’échelle de l’application. Certaines fonctionnalités clés de l’application de Service Web Apps :

-   Optimisation de DevOps (intégration continue et remise, plusieurs environnements, A / B tests, le script de prise en charge)

-   Haute disponibilité et à l’échelle mondiale

-   Connexions pour les plateformes SaaS et de vos données locales

-   Sécurité et conformité

-   Visual Studio, intégration

Azure App Service est le meilleur choix pour la plupart des applications web. Déploiement et gestion sont intégrées à la plate-forme, sites peuvent évoluer rapidement pour gérer des charges de trafic élevé, et le Gestionnaire de trafic et de l’équilibrage de charge intégrés fournir une haute disponibilité. Vous pouvez déplacer les sites existants dans Azure App Service facilement avec un outil de migration en ligne, utiliser une application open source à partir de la galerie d’applications Web, ou créer un nouveau site à l’aide du framework et outils de votre choix. La fonctionnalité WebJobs facilite l’ajouter la tâche en arrière-plan à votre application web de Service d’applications de traitement.

### <a name="containers-and-azure-container-service"></a>Conteneurs et le Service de conteneur Azure

Service de conteneur Azure facilite la créer, configurer et gérer un cluster d’ordinateurs virtuels qui sont préconfigurés pour exécuter des applications en conteneur. Il utilise une configuration optimisée des outils de planification et d’orchestration open source populaires. Cela vous permet d’utiliser vos compétences ou appuyer sur un corps important et croissant d’expertise de Communauté, déployer et gérer les applications basées sur le conteneur sur Microsoft Azure.

Service de conteneur Azure facilite la créer, configurer et gérer un cluster d’ordinateurs virtuels qui sont préconfigurés pour exécuter des applications en conteneur. Il utilise une configuration optimisée des outils de planification et d’orchestration open source populaires. Cela vous permet d’utiliser vos compétences ou appuyer sur un corps important et croissant d’expertise de Communauté, déployer et gérer les applications basées sur le conteneur sur Microsoft Azure.

Un Service de conteneur Azure vise à fournir un environnement d’hébergement conteneur à l’aide des outils d’open source et les technologies qui sont courants parmi les clients de Microsoft dès aujourd'hui. À cette fin, Service de conteneur Azure expose les points de terminaison API standards pour votre orchestrator choisie (contrôleur de domaine/système d’exploitation, Docker Swarm ou Kubernetes). À l’aide de ces points de terminaison, vous pouvez exploiter tout logiciel qui est capable de communiquer avec ces points de terminaison. Par exemple, dans le cas le point de terminaison Docker Swarm, vous pouvez choisir d’utiliser l’interface de ligne de commande Docker (CLI). Pour le contrôleur de domaine/système d’exploitation, vous pouvez choisir le DCOS CLI. Pour Kubernetes, vous pouvez choisir kubectl. Figure 11-1 montre comment utiliser ces points de terminaison pour gérer vos clusters de conteneur.

![](./media/image11-1.png)

**Figure 11-1.** Gestion du Service de conteneur Azure avec Docker, Kubernetes ou contrôleur de domaine/système d’exploitation des points de terminaison.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Service Fabric est un bon choix si vous créez une nouvelle application ou réécrire une application existante pour utiliser une architecture de microservice. Les applications qui s’exécutent sur un pool de machines, peuvent commencer petites et croître à grande échelle avec des centaines, voire des milliers d’ordinateurs en fonction des besoins. Services avec état permettent de manière cohérente et fiable stocker l’état de l’application, et l’infrastructure de Service gère automatiquement la partition du service, la mise à l’échelle et la disponibilité pour vous. Service Fabric prend également en charge les WebAPI avec l’Interface Web ouverte pour .NET (OWIN) et ASP.NET Core. Par rapport au Service d’application, l’infrastructure de Service fournit également plus contrôler, ou un accès direct à l’infrastructure sous-jacente. Vous pouvez à distance sur vos serveurs ou que vous configurez des tâches de démarrage du serveur.

### <a name="azure-virtual-machines"></a>Machines virtuelles Azure

Si vous avez une application existante qui nécessite des modifications substantielles pour s’exécuter dans le Service d’applications ou de l’infrastructure de Service, vous pouvez choisir les Machines virtuelles afin de simplifier la migration vers le cloud. Toutefois, correctement configuration, la sécurisation et les machines virtuelles de mise à jour nécessite beaucoup plus de temps et de ressources informatiques par rapport au Service d’applications Azure et Service Fabric. Si vous envisagez de Machines virtuelles Azure, veillez à que prendre en compte l’effort de maintenance continue pour les corriger, de mettre à jour et de gérer votre environnement de machine virtuelle. Machines virtuelles est Infrastructure-as-a-Service (IaaS), du Service d’applications et l’infrastructure de Service sont Platform-as-a-Service (Paas).

#### <a name="feature-comparison"></a>Comparaison des fonctionnalités

| Fonctionnalité du Service d’applications | Infrastructure de service | Machine virtuelle |
|---------|----------|----------|
| Déploiement quasi-instantané | X | X | |
| L’échelle pour les ordinateurs plus importants sans redéploiement | X | X | |
| Instances de partagent du contenu et configuration ; pas nécessaire de redéployer ou reconfigure lors de la mise à l’échelle | X | X | |
| Plusieurs environnements de déploiement (production et intermédiaire) | X | X | |
| Gestion automatique de mise à jour du système d’exploitation | X | | |
| Transparente de commutation entre les plateformes 32/64 bits | X | | |
| Déployer le code avec Git, FTP | X | | X |
| Déployer le code avec WebDeploy | X | | X |
| Déployer le code avec TFS | X | X | X |
| Site web hôte ou le niveau de service web d’architecture multiniveau | X | X | X |
| Accéder aux services Azure comme Service Bus, stockage, base de données SQL | X | X | X |
| Installez les MSI personnalisé | | X | X |

## <a name="logical-processes"></a>Processus logiques

Processus logiques individuels qui peuvent être dissociés du reste de l’application peuvent être déployés indépendamment à des fonctions de Azure de manière « sans serveur ». Fonctions Azure vous permet simplement écrire le code que vous avez besoin d’un problème donné, sans se préoccuper de l’infrastructure ou d’une application pour l’exécuter. Vous pouvez choisir parmi une variété de langages de programmation, y compris C\#, F\#, Node.js, Python et PHP, ce qui vous permet de choisir le langage le plus productif pour la tâche en cours. Comme la plupart des solutions de cloud computing, vous payez uniquement pour la durée de votre utilisation, et vous pouvez faire confiance à des fonctions de Azure pour faire évoluer en fonction des besoins.

## <a name="data"></a>Données

Azure propose un large éventail d’options de stockage de données, afin que votre application peut utiliser le fournisseur de données approprié pour les données en question.

Pour les données transactionnelles, relationnelles, bases de données SQL Azure constituent la meilleure option. Pour les données de lecture principalement du hautes performances, un cache Redis soutenu par une base de données SQL Azure est une bonne solution.

De différentes façons pour DocumentDB, à partir de colonnes de base de données SQL pour les objets BLOB ou des Tables dans le stockage Azure, peuvent contenir des données JSON non structurées. Parmi ceux-ci, DocumentDB offre les meilleures fonctionnalités d’interrogation et est l’option recommandée pour un grand nombre de documents basée sur JSON qui doivent prendre en charge l’interrogation.

Transitoire commande - ou -données d’événements permet d’orchestrer le comportement de l’application peuvent utiliser Azure Service Bus ou des files d’attente de stockage Azure. Bus de stockage Azure offre davantage de souplesse et le service recommandé pour la messagerie non triviale dans et entre les applications.

## <a name="architecture-recommendations"></a>Recommandations concernant l’architecture

Exigences de votre application doivent dicter son architecture. De nombreux services Azure différents sont disponibles, en choisissant que celui qui convient est une décision importante. Microsoft propose une galerie d’architectures de référence pour aider à identifier les architectures classiques optimisés pour les scénarios courants. Vous pouvez lier une architecture de référence que maps étroitement aux exigences de votre application, ou au offre moins un point de départ.

Figure 11-2 illustre une architecture de référence d’exemple. Ce diagramme décrit une approche de l’architecture recommandée pour un site Web système de gestion de contenu Sitecore optimisé pour le département marketing.

![](./media/image11-2.png)

**Figure 11-2.** Architecture de référence Sitecore marketing du site Web.

**Références : recommandations d’hébergement Azure**

-   Solution Azure Architectures\
    <https://Azure.Microsoft.com/solutions/architecture/>

-   Développeur Azure Guide\
    <https://Azure.Microsoft.com/campaigns/Developer-Guide/>

-   Nouveautés du Service d’applications Azure ? \
    <https://docs.Microsoft.com/Azure/app-service/app-service-Value-Prop-What-is>

-   Azure App Service, les Machines virtuelles, Service Fabric et Comparison\ de Services de Cloud
    <https://docs.Microsoft.com/Azure/app-service-Web/Choose-Web-site-cloud-service-VM>

>[!div class="step-by-step"]
[Précédente] (développement-processus-de-azure.md)
