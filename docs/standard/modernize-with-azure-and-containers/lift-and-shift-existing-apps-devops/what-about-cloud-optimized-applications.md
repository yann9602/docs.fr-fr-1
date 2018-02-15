---
title: "Qu’en est-il optimisée pour le cloud des applications ?"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Qu’en est-il optimisée pour le Cloud des applications ?"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4cb85c9dbcc7586510db9947d0151e3856964ef4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="what-about-cloud-optimized-applications"></a>Qu’en est-il optimisée pour le cloud des applications ?

Bien qu’optimisée pour le Cloud et [natif cloud](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) applications ne sont pas le principal objectif de ce guide, il est utile de comprendre ce niveau de maturité modernisation et pour le distinguer de DevOps prête pour le Cloud.

Figure 4-3 positionne optimisée pour le Cloud des applications dans les niveaux de maturité modernisation application :

![Positionnement des applications optimisée pour le Cloud](./media/image3.png)

> **Figure 4-3.** Positionnement des applications optimisée pour le Cloud

Le niveau de maturité optimisée pour le Cloud de modernisation nécessite généralement de nouveaux investissements de développement. Déplacement au niveau des tables optimisées en nuage généralement est piloté par la nécessité de moderniser des applications autant que possibles réduire les coûts et accroître la souplesse et sont en concurrence parti. Ces objectifs sont accomplies en optimisant l’utilisation du cloud PaaS. Cela signifie non seulement à l’aide des services PaaS comme DBaaS, CaaS et le stockage en tant que service (STaaS), mais également par la migration de vos applications et les services vers un PaaS plateforme comme Azure App Service de calcul, ou à l’aide d’orchestrators.

Ce type de modernisation requiert généralement refactorisation ou écrivez un nouveau code est optimisé pour les plateformes de PaaS (comme pour Azure App Service) de cloud computing. Il peut même nécessiter une architecture spécifiquement pour l’environnement du cloud, en particulier si vous déplacez vers les modèles d’application de cloud en mode natif qui sont basées sur microservices. Il s’agit d’une clé par rapport aux DevOps prête pour le Cloud, ce qui ne nécessite aucune modification de l’architecture et aucun nouveau code de facteur de différenciation.

Dans certains cas plus avancés, vous pouvez créer [natif cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) applications basées sur les architectures de microservices, ce qui peuvent évoluer avec souplesse et de répondre aux limites qui seraient difficiles à réaliser une architecture monolithique déployée dans un environnement local.

Figure 4-4 indique le type d’application que vous pouvez déployer lorsque vous utilisez le modèle optimisée pour le Cloud. Vous avez deux applications de base web moderne de choix et les applications cloud en mode natif.

> ![Types d’application au niveau optimisée pour le Cloud](./media/image4.png)
>
> **Figure 4-4.** Types d’application au niveau optimisée pour le Cloud

Vous pouvez étendre les applications web modernes de base et les applications cloud en mode natif en ajoutant d’autres services, tels que l’intelligence artificielle (AI), apprentissage (ML) et IoT. Vous pouvez utiliser un de ces services pour étendre une des approches possibles optimisée pour le Cloud.

La différence fondamentale dans les applications du niveau optimisée pour le Cloud est dans l’architecture d’application. [Cloud natif](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) applications sont, par définition, les applications qui reposent sur microservices. Les applications de cloud en mode natif nécessitent des architectures spéciales, technologies et plateformes, par rapport à une application web de monolithique ou d’une application multicouche classique.

Création d’applications qui n’utilisent pas microservices peut s’avérer utile. Il existe de nombreux scénarios de nouveau et toujours modernes dans lequel une approche basée sur des microservices peut-être dépasser vos besoins. Dans certains cas, vous souhaiterez simplement créer une application web monolithique plus simple, ou ajouter des services à granularité grossière à une application multicouche. Dans ces cas, vous pouvez toujours effectuer pleinement parti du cloud PaaS des fonctionnalités telles que celles offertes par le Service d’applications Azure. Vous réduisez toujours votre travail de maintenance à la limite.

En outre, étant donné que vous développez le nouveau code dans les scénarios optimisée pour le Cloud (pour une application complète ou partielles sous-systèmes), lorsque vous créez le nouveau code, vous devez utiliser les versions plus récentes de .NET ([.NET Core](https://docs.microsoft.com/dotnet/core/) et [ASP.NET Core](https://docs.microsoft.com/aspnet/core/), en particulier). Cela est particulièrement vrai si vous créez des microservices et des conteneurs, car .NET Core est une infrastructure lean et rapide. Vous obtenez un faible encombrement mémoire et le démarrage rapide dans des conteneurs, et vos applications seront hautes performances. Cette approche s’intègre parfaitement aux exigences de microservices et de conteneurs, et vous bénéficiez d’un inter-plateformes framework-être en mesure d’exécuter la même application sur Mac (Mac pour les environnements de développement), Windows Server et Linux.

## <a name="cloud-native-applications-with-cloud-optimized-applications"></a>Applications cloud en mode natif avec les applications optimisée pour le Cloud

[Cloud natif](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) est un état plus avancé ou mature pour les applications critiques volumineux. Les applications cloud en mode natif nécessitent généralement l’architecture et conception qui sont créés à partir de zéro à la place de par rénovation des applications existantes. La principale différence entre une application cloud en mode natif et une application web Cloud optimisés plus simple déployée sur PaaS est la recommandation d’utiliser des architectures de microservices dans une approche de cloud en mode natif. Optimisée pour le cloud des applications peuvent également être des applications web monolithique ou des applications multicouches déployées dans un cloud service PaaS comme Azure App Service.

Le [douze-facteur application](https://12factor.net/) (il s’agit d’une collection de modèles qui sont étroitement liés aux approches de microservices) également est considéré comme une condition requise pour [natif cloud](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) architectures d’application.

Le [Foundation de calcul natif Cloud (CNCF)](https://www.cncf.io/) est un principal promoteur des principes de cloud en mode natif. Microsoft est un [membre de la CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Pour un exemple de définition et pour plus d’informations sur les caractéristiques des applications de cloud en mode natif, consultez l’article de Gartner [comment structurer et concevoir des applications de cloud natif](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Pour obtenir des instructions spécifiques à partir de Microsoft sur l’implémentation d’une application cloud en mode natif, consultez [.NET microservices : Architecture pour les applications .NET en conteneur](https://aka.ms/microservicesebook).

Le facteur le plus important à prendre en compte les si vous migrez une application complète pour la [natif cloud](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modèle est que vous devez redéfinir l’architecture pour une architecture basée sur des microservices. Clairement, cela nécessite un investissement important dans le développement en raison du grand processus de refactorisation impliqué. Cette option est généralement choisie pour les applications critiques qui ont besoin de nouveaux niveaux d’évolutivité et de souplesse à long terme. Mais, vous pouvez démarrer un déplacement vers le cloud en mode natif en ajoutant des microservices de quelques nouveaux scénarios et finalement refactoriser l’application entièrement comme microservices. Il s’agit d’une approche progressive qui est la meilleure option pour certains scénarios.

## <a name="what-about-microservices"></a>Qu’en est-il des microservices ? 

Si vous envisagez des applications cloud en mode natif pour votre organisation, il est important de comprendre microservices et leur fonctionnement.

L’architecture de microservices est une approche avancée que vous pouvez utiliser pour les applications qui sont créées à partir de zéro ou lorsque vous développez des applications existantes (locale ou prêt DevOps applications cloud) vers les applications cloud en mode natif. Vous pouvez commencer par ajouter quelques microservices aux applications existantes pour en savoir plus sur les nouveaux modèles de microservices. Mais clairement, vous devez architecte et le code, en particulier pour ce type d’approche architecturale.

Toutefois, les microservices ne sont pas obligatoires pour toutes les applications nouvelles ou modernes. Microservices ne sont pas un « magique », et ils ne sont pas le seul, meilleures permet de créer chaque application. Comment et quand vous utilisez microservices dépend du type d’application que vous souhaitez générer.

L’architecture de microservices devient la meilleure approche pour les applications critiques distribuées et volumineux ou complexes qui sont basées sur des sous-systèmes indépendantes multiples, sous la forme de services autonomes. Dans une architecture basée sur des microservices, une application est générée comme une collection de services qui peuvent être développées indépendamment, testée et une version déployée et à l’échelle. Cela peut inclure une base de données connexe, autonome par microservice.

Pour une présentation détaillée sur une architecture de microservices que vous pouvez implémenter à l’aide de .NET Core, consultez l’e-livre PDF téléchargeable [.NET microservices : Architecture pour les applications .NET en conteneur](https://aka.ms/microservicesebook). Le guide est également disponible [online](https://docs.microsoft.com/dotnet/standard/microservices-architecture/).

Mais même dans les scénarios dans lesquels microservices offrent des puissantes fonctionnalités indépendant du déploiement, les limites de sous-système fort et diversité technologique-ils déclenchent également de nombreux défis de nouveau. Les défis liés au développement d’applications distribuées, tels que les modèles de données fragmentés et indépendante ; Pour parvenir à communication résiliente entre microservices ; le besoin de cohérence éventuelle ; et la complexité opérationnelle. Microservices présentent un niveau supérieur de complexité par rapport aux applications monolithiques traditionnelles.

En raison de la complexité d’une architecture de microservices, uniquement les scénarios spécifiques et certains types d’applications conviennent pour les applications microservice. Ceux-ci incluent des applications volumineuses et complexes qui ont plusieurs évolution sous-systèmes. Dans ces cas, il convient d’investir dans une architecture plus complexe de logiciel, pour une souplesse accrue à long terme et la maintenance des applications plus efficace. Mais pour les scénarios moins complexes, il peut être préférable continuer avec une approche application monolithique ou multicouches plus simple est proche.

En tant qu’une note finale, même au risque d’être répétitive sur ce concept, vous ne doivent pas consulter à l’aide de microservices dans vos applications en tant que « tout dedans tout ou rien du tout*.*» Vous pouvez étendre et faire évoluer des applications monolithiques existantes en ajoutant de nouveaux, petits scénarios basés sur microservices. Vous n’avez pas besoin de démarrer à partir de zéro pour commencer à utiliser avec une approche d’architecture microservices. En fait, nous recommandons que vous développez à l’aide d’une application monolithique ou multicouches existant en ajoutant de nouveaux scénarios. Par la suite, vous pouvez décomposer l’application en composants autonomes ou microservices. Vous pouvez démarrer l’évolution de vos applications monolithiques dans une direction microservices, étape par étape.

## <a name="when-to-use-azure-app-service-for-modernizing-existing-net-apps"></a>Quand utiliser le Service d’applications Azure de rénovation des applications .NET existantes

Lorsque vous modernisez des applications web ASP.NET existantes au niveau de maturité d’optimisée pour le Cloud, étant donné que vos applications web ont été développées à l’aide de .NET Framework, les dépendances principales sont sur Windows et, très probablement, Internet Information Server (IIS). Vous pouvez utiliser et déployer des applications Windows et IIS soit en déployant directement à [Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is) ou d’abord containerizing votre application à l’aide de conteneurs Windows. Si containerizing, déployez les applications, soit les conteneurs Windows des ordinateurs hôtes (basé sur une machine virtuelle) ou vers un Service Azure Fabric cluster qui prend en charge les conteneurs Windows.

Lorsque vous utilisez des conteneurs Windows, vous obtenez tous les avantages de la mise en conteneur. Augmenter l’agilité de livraison et de déploiement de votre application et de réduire la friction pour les problèmes d’environnement (mise en lots, développement/test, production). Dans les sections suivantes, nous aller plus en détail les avantages que vous obtenez de l’utilisation de conteneurs.

Au moment de la rédaction de ce guide, Azure App Service ne prend pas en charge les conteneurs Windows. Il prend en charge des conteneurs pour Linux. Par conséquent, peut être votre question suivante, « Comment choisir entre les conteneurs Windows et Azure App Service ? »

En fait, si le Service d’applications Azure fonctionne pour votre application et ne contient pas de tout serveur ou les dépendances personnalisées bloque le chemin d’accès pour utiliser le Service d’applications, migrer votre application de web de .NET existante pour le Service d’applications. Il s’agit de la méthode plus simple et plus efficace pour gérer votre application. Dans Azure, votre application également a un chemin d’accès de maintenance plus simple en raison des avantages d’infrastructure PaaS, telles que DBaaS, CaaS et STaaS.

Toutefois, si votre application a de serveur ou dépendances personnalisées qui ne sont pas pris en charge dans Azure App Service, vous devrez peut-être envisager les options qui sont basées sur les conteneurs Windows. Les logiciels tiers ou un fichier .msi qui doit être installé sur le serveur, mais qui n’est pas pris en charge dans Azure App Service sont des exemples de serveur ou de dépendances personnalisées. Un autre exemple est une autre configuration de serveur qui n’est pas pris en charge dans Azure App Service, comme l’utilisation d’assemblys dans le Global Assembly Cache (GAC) ou COM / composants COM +. Grâce aux images de conteneur Windows, vous pouvez inclure vos dépendances personnalisées dans la même « unité de déploiement. »

Ou bien, vous pourriez refactoriser les zones de votre application qui ne sont pas pris en charge par le Service d’applications Azure. Selon le volume de travail de refactorisation nécessiterait, vous devez évaluer avec soin si la valeur de cette opération.

### <a name="benefits-of-moving-to-azure-app-service"></a>Avantages de la migration vers Azure App Service

Azure App Service est un PaaS entièrement géré qui offre permet de facilement créer des applications web qui sont sauvegardées par des processus d’entreprise. Lorsque vous utilisez le Service d’applications, vous évitez les coûts de gestion d’infrastructure associés à la mise à niveau et de gestion web applications locales. Plus précisément, vous coupez le matériel et les coûts des licences de web applications locales en cours d’exécution.

Si votre application web est appropriée pour la migration vers Azure App Service, le principal avantage est la quantité de courte durée que nécessaire au déplacement de l’application. Service d’applications offre un environnement très simple dans lequel commencer.

Azure App Service est le meilleur choix pour la plupart des applications web, car il est le plus simple PaaS dans Azure, vous pouvez utiliser pour exécuter des applications web. Déploiement et gestion sont intégrées à la plate-forme, sites évoluent rapidement pour gérer des charges de trafic élevé, et le Gestionnaire de trafic et de l’équilibrage de charge intégrés fournir une haute disponibilité.

Même analyse vos applications web est simple, via l’Application Azure Insights. Application Insights est intégrée à un Service d’applications et ne nécessitent pas écrire de code spécial dans votre application. Juste exécuter votre application web dans le Service d’applications, et vous aurez un système de surveillance attrayante, sans aucun travail supplémentaire.

Avec le Service d’application, vous pouvez utiliser également directement de nombreuses applications open source à partir de la galerie d’applications Web Azure (comme WordPress ou Umbraco), ou vous pouvez créer un nouveau site en utilisant le framework et les outils de votre choix, comme ASP.NET. La fonctionnalité WebJobs de Service d’application rend facile d’ajouter la tâche en arrière-plan à votre application web de Service d’applications de traitement.

Les avantages clés de migration de vos applications web à l’aide de la fonctionnalité d’applications Web de Service d’applications Azure sont les suivants :

-   Échelle automatique pour répondre à la demande pendant les heures de disponibilité et de réduire les coûts pendant les périodes creuses.

-   Sauvegarde automatique de site pour protéger les données et les modifications.

-   Haute disponibilité et résilience sur la plateforme Azure PaaS.

-   Emplacements de déploiement pour le développement et l’environnement intermédiaire et plusieurs conceptions de site de test.

-   L’équilibrage de charge et la protection de déni de Service distribué (DDoS).

-   Gestion du trafic pour diriger les utilisateurs au déploiement géographique le plus proche.

Bien que le Service d’applications peut être le meilleur choix pour les nouvelles applications web, toutefois, pour les applications existantes, du Service d’applications peut être le meilleur choix uniquement si les dépendances de votre application sont prises en charge dans le Service d’applications.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Analyse de compatibilité pour le Service d’applications Azure**  
[https://www.migratetoazure.net/Resources](https://www.migratetoazure.net/Resources)


### <a name="benefits-of-moving-to-windows-containers"></a>Avantages du passage aux conteneurs Windows

Le principal avantage de l’utilisation de conteneurs Windows est que vous obtenez une expérience de déploiement plus fiable et améliorées par rapport aux applications de conteneur-non géré. En outre, votre application modernisé efficacement avec des conteneurs, votre application prête pour d’autres plateformes et les clouds qui prennent en charge des conteneurs Windows. Les avantages de passer aux conteneurs Windows sont décrites plus en détail dans les sections suivantes.

Les environnements de calcul principal dans Azure (en disponibilité générale, à compter de mid 2017) qui prennent en charge des conteneurs Windows sont Azure Service Fabric et les hôtes de conteneurs Windows base (Windows Server 2016 de machines virtuelles). Ces environnements sont les scénarios d’infrastructure principale traités dans ce guide.

Vous pouvez également déployer des conteneurs Windows à d’autres orchestrators, comme Kubernetes, Docker Swarm ou contrôleur de domaine/système d’exploitation. Actuellement (tôt se situent 2017), ces plateformes sont en version préliminaire dans le conteneur de Service Azure pour l’utilisation de conteneurs Windows.

>[!div class="step-by-step"]
[Précédent](microsoft-technologies-in-cloud-devops-ready-applications.md)
[Suivant](how-to-deploy-existing-net-apps-to-azure-app-service.md)
