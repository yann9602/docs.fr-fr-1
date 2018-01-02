---
title: Moderniser des applications .NET existantes avec le cloud Azure et des conteneurs Windows
description: "Découvrir comment effectuer un lift-and-shift des applications existantes dans le cloud Azure en utilisant des conteneurs"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: b7ef8c0e68eee3b2b4247454929e92fb175cae0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-v10"></a>Moderniser des applications .NET existantes avec le cloud Azure et des conteneurs Windows (v1.0)  

![image de couverture](./media/cover.png)

PUBLIÉ PAR  
Microsoft Press et Microsoft DevDiv  
Divisions de Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2017 Microsoft Corporation  

Tous droits réservés. Aucune partie du contenu de ce document ne peut être reproduite sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.

Cet ouvrage est disponible gratuitement sous forme de livre électronique via plusieurs canaux Microsoft, comme <http://dot.net/architecture>

Si vous avez des questions liées à cet ouvrage, envoyez un e-mail à [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur. Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.

Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs. Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.

Microsoft et les marques commerciales mentionnées dans la page web « Marques » de http://www.microsoft.com sont des marques du groupe de sociétés Microsoft. Toutes les autres marques sont la propriété de leurs propriétaires respectifs.

Auteur :
> **Cesar de la Torre**, chef de projet sénior, équipe produit .NET, Microsoft Corp.

Participants et réviseurs :
> **Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft  
> **Paul Yuknewicz**, chef de projet responsable principal, équipe Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, chef de projet sénior, équipe Visual Studio Tools, Microsoft  
> **Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft  
> **Unai Zorrilla**, développeur en chef, Plain Concepts  
> **Javier Valero**, chef des opérations chez Grupo Solutio  

## <a name="introduction"></a>Introduction

Quand vous décidez de moderniser vos applications web et de les faire passer dans le cloud, vous ne devez pas nécessairement refondre entièrement l’architecture de vos applications. La refonte de l’architecture d’une application avec une approche avancée comme celle des microservices n’est pas toujours une option en raison de restrictions de coûts et de temps. Selon le type de l’application, la refonte de son architecture peut ne pas être pas nécessaire. Pour optimiser la rentabilité de la stratégie de migration vers le cloud de votre organisation, il est important de prendre en compte les besoins de votre activité et les exigences de vos applications. Vous devez déterminer :

-   Les applications qui nécessitent une transformation ou une nouvelle architecture.

-   Les applications qui doivent être modernisées seulement en partie.

-   Les applications pouvant faire l’objet d’un lift-and-shift directement dans le cloud.

## <a name="about-this-guide"></a>À propos de ce guide

Ce guide se focalise essentiellement sur les scénarios de lift-and-shift dans le cloud et la modernisation initiale des applications Microsoft .NET Framework orientées web ou service. Une opération lift-and-shift est l’action de déplacer une charge de travail vers un environnement plus récent ou plus moderne, sans modification du code et de l’architecture de base de l’application.

Ce guide décrit comment faire passer vos applications serveur .NET Framework existantes directement dans le cloud en en modernisant certains aspects spécifiques, mais sans refondre l’architecture ni recoder des applications entières.

Ce guide présente également les avantages du passage de vos applications dans le cloud et de la modernisation partielle des applications, avec un ensemble spécifique de nouvelles technologies et approches, comme les conteneurs Windows et les orchestrateurs dans Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Déplacement vers le cloud des applications .NET existantes

En règle générale, les organisations choisissent de passer au cloud pour apporter souplesse et rapidité à leurs applications. Vous pouvez configurer des milliers de serveurs (des machines virtuelles) dans le cloud en quelques minutes, en comparaison aux semaines généralement nécessaires pour configurer des serveurs locaux.

Il n’existe pas de stratégie unique et universelle pour migrer des applications dans le cloud. La bonne stratégie de migration pour vous dépend des besoins et des priorités de votre organisation, ainsi que du type des applications que vous migrez. Les applications ne justifient pas toutes l’investissement nécessaire pour passer à un modèle Paas ([plateforme en tant que service](https://azure.microsoft.com/overview/what-is-paas/)) ou pour développer un modèle d’application [natif pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Dans de nombreux cas, vous pouvez adopter une approche progressive ou incrémentielle quand vous investissez dans le déplacement de vos ressources sur le cloud, en fonction des besoins de votre entreprise.

Pour les applications modernes avec la meilleure agilité et la meilleure valeur à long terme pour l’organisation, vous pouvez tirer profit d’un investissement dans des architectures d’application *optimisées pour le cloud* et *natives pour le cloud*. Cependant, pour les applications qui sont des ressources existantes ou héritées, le plus important est de consacrer le moins de temps et d’argent possible (pas de refonte de l’architecture ni de modifications du code) lors de leur passage dans le cloud, de façon à en tirer des profits significatifs.

La figure 1-1 montre les voies possibles utilisables quand vous faites passer progressivement des applications .NET existantes dans le cloud.

 ![Voies de modernisation pour les applications et les services .NET existants](./media/image1-1.png)

> **Figure 1-1**. Voies de modernisation pour les applications et les services .NET existants

Chaque approche de la migration présente des avantages différents et est utilisée pour des raisons différentes. Vous pouvez choisir une même approche quand vous migrez des applications vers le cloud, ou choisir certains composants provenant de plusieurs approches. Les applications individuelles ne sont pas limitées à une seule approche ou à un seul état de maturité. Par exemple, une approche hybride courante consiste à avoir certains des composants en local et d’autres composants dans le cloud.

Au deux premiers niveaux de migration, vous pouvez simplement effectuer un lift-and-shift de vos applications dans le cloud :

**Niveau 1 : Prêt pour l’infrastructure cloud** : dans cette approche de la migration, vous pouvez simplement réhéberger ou déplacer vos applications locales actuelles vers une plateforme IaaS ([Infrastructure en tant que service](https://azure.microsoft.com/overview/what-is-iaas/)). Vos applications ont pratiquement la même composition qu’avant, mais vous les déployez désormais sur des machines virtuelles dans le cloud.

**Niveau 2 : Prêt pour le DevOps cloud** : à ce niveau, après une première opération de lift-and-shift, mais toujours sans refondre l’architecture ni modifier le code, vous pouvez même tirer davantage profit de l’exécution de votre application dans le cloud. Vous améliorez l’agilité de vos applications pour les livrer plus rapidement, en affinant les processus de fonctionnement du développement (DevOps) dans votre entreprise. C’est possible en utilisant une technologie comme les conteneurs Windows, qui est basée sur le moteur Docker. Les conteneurs suppriment les freins liés aux dépendances des applications quand vous déployez en plusieurs étapes. Les conteneurs utilisent également d’autres services cloud gérés liés aux données, à la surveillance et aux pipelines d’intégration continue/déploiement continu.

Le troisième niveau de maturité est l’objectif ultime dans le cloud, mais il est facultatif pour de nombreuses applications et ne constitue pas l’objet principal de ce guide :

**Niveau 3 : Optimisé pour le cloud** : cette approche de la migration est généralement pilotée par les besoins métier et cible la modernisation de vos applications critiques. À ce niveau, vous utilisez des services PaaS pour passer vos applications sur des plateformes informatiques PaaS. Vous implémentez des applications et une architecture de microservices [natives pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) pour faire évoluer les applications avec une agilité à long terme et pour les adapter à de nouvelles limites. Ce type de modernisation nécessite généralement une architecture spécifique pour le cloud. Du nouveau code doit souvent être écrit, en particulier quand vous passez à des modèles d’application natifs pour le cloud et basés sur des microservices. Cette approche peut vous aider à profiter d’avantages difficiles à obtenir dans votre environnement applicatif monolithique et local.

Le tableau 1-1 décrit les principaux avantages et les raisons de choisir chaque approche de migration ou de modernisation.

> | **Prêt pour l’infrastructure cloud** <br /> *Lift-and-shift* | **Prêt pour le DevOps cloud** <br /> *Lift-and-shift* | **Optimisé pour le cloud** *Moderniser/refactoriser/réécrire* |
> |---|---|---|
> | **Cible informatique de l’application** |
> | Applications déployées sur des machines virtuelles dans Azure | Applications en conteneur monolithiques ou multiniveaux déployées sur des machines virtuelles, sur Azure Service Fabric ou sur Azure Container Service (Kubernetes) | Microservices en conteneur ou applications standard PaaS sur Azure App Service, sur Azure Service Fabric, sur Azure Container Service (Kubernetes) |
> | **Cible de données** |
> | SQL ou n’importe quelle base de données relationnelle sur une machine virtuelle | Azure SQL Database Managed Instance | Azure SQL Database, Azure Cosmos DB ou une autre base de données NoSQL |
> | **Avantages**|
> | <li>Pas de refondation de l’architecture, pas de nouveau code <li> Moins de travail pour une migration rapide <li> Plus petit dénominateur commun pris en charge dans Azure <li> Garanties de disponibilité de base <li> Après être passé au cloud, il est plus facile de moderniser encore plus | <li>Pas de refondation de l’architecture, pas de nouveau code <li> Les conteneurs nécessitent un petit peu plus de travail que les machines virtuelles <li> Déploiement amélioré et meilleure agilité de DevOps pour la production de nouvelles versions grâce aux conteneurs <li> Densité accrue et coûts de déploiement inférieurs <li> Portabilité des applications et des dépendances <li> Avec Azure Container Service (ou Kubernetes) et Azure Service Fabric, fournit une haute disponibilité et l’orchestration <li> Mise à jour corrective des nœuds/machines virtuelles dans Service Fabric <li> Flexibilité des cibles d’hôte : machines virtuelles ou groupes de machines virtuelles identiques Azure, Azure Container Service (ou Kubernetes), Service Fabric et d’autres choix à venir basés sur les conteneurs | <li>Nouvelle architecture pour le cloud, refactorisation, nouveau code nécessaire <li> Approches natives pour le cloud avec des microservices <li> Nouvelles applications web, monolithiques, multiniveaux, résilientes sur le cloud et optimisée pour le cloud <li> Services entièrement gérés <li> Mise à jour corrective automatique <li> Optimisé pour la mise à l’échelle <li> Optimisé pour une agilité autonome par sous-système <li> S’appuyant sur le déploiement et sur DevOps <li> DevOps amélioré, comme les connecteurs et les stratégies de déploiement <li> PaaS et cibles d’orchestrateur : Azure App Service, Azure Container Service (ou Kubernetes), Azure Service Fabric et les PaaS futures basées sur des conteneurs |
> | **Difficultés éventuelles** |
> | <li> Valeur cloud inférieure, autre que la variation des dépenses d’exploitation ou la fermeture de centres de données <li> Très peu d’aspects sont gérés : pas de mise à jour corrective du système d’exploitation ou du middleware ; solutions d’infrastructure possibles, comme Terraform, Spinnaker ou Puppet | <li> La mise en conteneur est une étape supplémentaire dans le processus d’apprentissage | <li> Une refactorisation ou une réécriture significative peut être nécessaire (temps et budget accrus) |
>> **Tableau 1-1.** Avantages et difficultés éventuelles des parcours de modernisation pour les applications et les services .NET existants

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Technologies et architectures principales par niveau de maturité

Au départ, les applications .NET Framework démarraient avec le .NET Framework version 1.0, qui a été publié fin 2001. Ensuite, les entreprises sont passées à des versions plus récentes (comme 2.0, 3.5 et .NET 4.x). La plupart de ces applications s’exécutaient sur Windows Server et IIS (Internet Information Server), et utilisaient une base de données relationnelle, comme SQL Server, Oracle, MySQL ou n’importe quel autre SGBDR.

La plupart des applications .NET existantes sont probablement basées sur le .NET Framework 4.x, ou même sur le .NET Framework 3.5, et elles utilisent des frameworks web, comme ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, WCF (Windows Communication Foundation), ASP.NET SignalR et ASP.NET Web Pages. Ces technologies .NET Framework répandues dépendent de Windows. Cette dépendance est importante à prendre en compte si vous effectuez simplement une migration d’applications héritées et que vous voulez apporter le moins de modifications possible à votre infrastructure d’application.

La figure 1-2 montre les technologies et les styles d’architecture principaux utilisés pour chacun des trois niveaux de maturité cloud :

![Technologies principales pour chaque niveau de maturité pour la modernisation d’applications web .NET existantes](./media/image1-2.png)

> **Figure 1-2.** Technologies principales pour chaque niveau de maturité pour la modernisation d’applications web .NET existantes

La figure 1-2 met en évidence les scénarios les plus courants, mais de nombreuses variations hybrides et mixtes sont possibles concernant l’architecture. Par exemple, les modèles de maturité s’appliquent non seulement aux architectures monolithiques dans les applications web existantes, mais aussi à l’orientation service, au multiniveau et à d’autres variations du style d’architecture.

Chaque niveau de maturité du processus de modernisation est associé aux technologies et aux approches principales suivantes :

-   **Prêt pour l’infrastructure cloud** (réhébergement ou lift-and-shift de base) : dans un premier temps, de nombreuses organisations veulent seulement exécuter rapidement une stratégie de migration cloud. Dans ce cas, les applications sont simplement réhébergées. La plus grande partie du réhébergement peut être automatisée avec [Azure Migrate](https://aka.ms/azuremigrate), service qui fournit de l’aide, des insights et les mécanismes nécessaires pour vous aider à migrer vers Azure, basé sur des outils cloud comme [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) et [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Vous pouvez également configurer manuellement le réhébergement, ce qui vous permet de découvrir des détails d’infrastructure sur vos ressources quand vous déplacez des applications héritées dans le cloud. Par exemple, vous pouvez déplacer vos applications vers des machines virtuelles dans Azure avec très peu de modifications, probablement avec seulement des modifications de configuration mineures. La mise en réseau est dans ce cas similaire à un environnement local, en particulier si vous créez des réseaux virtuels dans Azure.

-   **Prêt pour le DevOps cloud** (lift-and-shift amélioré) : ce modèle implique d’effectuer quelques optimisations importantes du déploiement pour obtenir du cloud certains bénéfices significatifs, sans modifier l’architecture principale de l’application. Le principal est ici d’ajouter la prise en charge des [conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) à vos applications .NET Framework existantes. Cette étape importante (mise en conteneur) ne nécessite pas de toucher au code : le travail global de lift-and-shift est très peu important. Vous pouvez utiliser des outils comme [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ou Visual Studio, avec ses outils pour [Docker](https://www.docker.com/). Visual Studio choisit automatiquement des valeurs par défaut adaptées pour les applications ASP.NET et les images de conteneurs Windows. Ces outils permettent à la fois une boucle interne rapide et une voie rapide pour placer les conteneurs dans Azure. Votre agilité est améliorée quand vous déployez sur plusieurs environnements. Ensuite, en passant en production, vous pouvez déployer vos conteneurs Windows sur des orchestrateurs, comme [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) ou [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS ou Swarm). Au cours de cette modernisation initiale, vous pouvez également ajouter des ressources provenant du cloud, comme la surveillance avec des outils comme [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview), des pipelines d’intégration continue/de déploiement continu pour les cycles de vie de votre application avec [Visual Studio Team Services](https://www.visualstudio.com/team-services/), et de nombreux autres services de ressources de données qui sont disponibles dans Azure. Par exemple, vous pouvez modifier une application web monolithique qui a été développée à l’origine avec les composants classiques [ASP.NET Web Forms](https://www.asp.net/web-forms) ou [ASP.NET MVC](https://www.asp.net/mvc), mais vous la déployez maintenant en utilisant des conteneurs Windows. Quand vous utilisez des conteneurs Windows, vous devez également migrer vos données vers une base de données qui se trouve dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/), le tout sans modifier l’architecture principale de votre application.

-   **Optimisé pour le cloud** : comme indiqué précédemment, l’objectif ultime quand vous modernisez des applications dans le cloud est de baser votre système sur des plateformes PaaS, comme [Azure App Service](https://azure.microsoft.com/services/app-service/). Les plateformes PaaS sont principalement destinées aux applications web modernes, et étendent vos applications avec de nouveaux services basés sur [l’informatique serverless](https://azure.microsoft.com/overview/serverless-computing/) et des plateformes comme [Azure Functions](https://azure.microsoft.com/services/functions/). Le deuxième scénario, plus avancé, de ce modèle de maturité concerne les architectures de microservices et les applications [natives pour le cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications), qui utilisent généralement des orchestrateurs comme [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) ou [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS ou Swarm). Ces orchestrateurs sont destinés spécifiquement aux microservices et aux applications multiconteneurs. Toutes ces approches (comme les microservices et PaaS) nécessitent l’écriture d’un nouveau code adapté à des plateformes PaaS spécifiques, ou de code qui s’aligne sur des architectures spécifiques, comme les microservices.

La figure 1-3 montre les technologies internes que vous pouvez utiliser pour chaque niveau de maturité :

![Technologies internes pour chaque niveau de maturité de modernisation](./media/image1-3.png)

> **Figure 1-3.** Technologies internes pour chaque niveau de maturité de modernisation

## <a name="lift-and-shift-scenarios"></a>Scénarios de lift-and-shift

Pour les migrations de type lift-and-shift, gardez à l’esprit que vous pouvez utiliser de nombreuses variations de lift-and-shift différentes dans vos scénarios d’application. Si vous réhébergez seulement votre application, vous pouvez avoir un scénario semblable à celui illustré dans la Figure 1-4, où vous utilisez des machines virtuelles dans le cloud seulement pour votre application et pour votre serveur de base de données.

![Exemple de scénario IaaS pur dans le cloud](./media/image1-4.png)

> **Figure 1-4**. Exemple de scénario IaaS pur dans le cloud

Pour aller plus loin, vous pouvez avoir une application prête pour le DevOps cloud pur, qui utilise seulement des éléments de ce niveau de maturité. Vous pouvez aussi avoir une application dans un état intermédiaire avec quelques éléments au niveau Prêt pour l’infrastructure cloud et d’autres éléments au niveau Prêt pour le DevOps cloud (un modèle par sélection ou mixte), comme dans la figure 1-5.

![Exemple de scénario « par sélection », avec une base de données sur IaaS, DevOps et des ressources de mise en conteneur](./media/image1-5.png)

> **Figure 1-5.** Exemple de scénario « par sélection », avec une base de données sur IaaS, DevOps et des ressources de mise en conteneur

Ensuite, comme scénario idéal pour de nombreuses applications .NET Framework existantes à migrer, vous pouvez migrer vers une application Prête pour le DevOps cloud, pour obtenir des bénéfices importants avec peu de travail. Cette approche vous permet aussi d’être prêt pour une éventuelle optimisation cloud dans le futur. La figure 1-6 en montre un exemple.

![Exemple de scénario Prêt pour le DevOps cloud, avec des conteneurs Windows et des services gérés](./media/image1-6.png)

> **Figure 1-6.** Exemple de scénario Prêt pour le DevOps cloud, avec des conteneurs Windows et des services gérés

Pour aller encore plus loin, vous pouvez étendre votre application Prête pour le DevOps cloud en ajoutant quelques microservices pour des scénarios spécifiques. Ceci vous placerait partiellement au niveau du natif pour le cloud dans le modèle optimisé pour le cloud, qui n’est pas le sujet central de cette aide.


## <a name="what-this-guide-does-not-cover"></a>Sujets non abordés dans ce guide

Ce guide couvre un sous-ensemble spécifique des exemples de scénarios, comme le montre la figure 1-7. Il est centré sur les scénarios de lift-and-shift et traite pour terminer du modèle Prêt pour le DevOps cloud. Dans le modèle Prêt pour le DevOps cloud, une application .NET Framework est modernisée avec des conteneurs Windows, plus d’autres composants comme la surveillance et les pipelines d’intégration continue/de déploiement continu. Chaque composant est fondamental pour permettre un déploiement plus rapide et agile des applications dans le cloud.

![Lift-and-shift et modernisation initiale pour des applications Prêtes pour le DevOps cloud](./media/image1-7.png)

> **Figure 1-7.** Lift-and-shift et modernisation initiale pour des applications Prêtes pour le DevOps cloud

L’objet principal de ce guide est spécifique. Nous vous montrons le cheminement à suivre pour effectuer un lift-and-shift de vos applications .NET existantes, sans refonte de l’architecture ni modification du code. Nous vous montrons au final comment rendre votre application Prête pour le DevOps cloud.

Ce guide ne vous montre pas comment travailler avec des applications natives pour le cloud, par exemple comment évoluer vers une architecture de microservices. Pour refondre l’architecture de vos applications ou pour créer de nouvelles applications basées sur des microservices, consultez le livre électronique [.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (livre électronique téléchargeable) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

-   **.NET Microservices: Architecture for containerized .NET applications** (livre électronique téléchargeable) : [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

-   **Architecting modern web applications with ASP.NET Core and Azure** (livre électronique téléchargeable) : [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Public visé par ce guide

Ce guide est destiné aux développeurs et aux architectes de solutions qui veulent moderniser des applications ASP.NET existantes basées sur le .NET Framework, de façon à obtenir une meilleure agilité dans la livraison des applications.

Ce guide peut être utile également si vous êtes décideur informatique, par exemple architecte d’entreprise ou responsable du développement, et souhaitez seulement une vue d’ensemble des bénéfices que vous pouvez obtenir en utilisant des conteneurs Windows et en déployant sur le cloud si vous utilisez Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Comment utiliser ce guide

Ce guide répond à la question « pourquoi » : pourquoi il peut être souhaitable de moderniser vos applications existantes. Il explique aussi quels sont les bénéfices procurés par l’utilisation des conteneurs Windows quand vous déplacez vos applications dans le cloud. Le contenu des premiers chapitres du guide est conçu pour les architectes et les décideurs informatiques qui veulent une vue d’ensemble, mais qui n’ont pas besoin d’informations techniques détaillées sur le processus d’implémentation.

Le dernier chapitre de ce guide contient plusieurs procédures pas à pas centrées sur des scénarios de déploiement spécifiques. Dans ce guide, nous présentons des versions plus courtes des procédures pas à pas, qui résument les scénarios et mettent évidence leurs avantages. Les procédures pas à pas complètes détaillent la configuration et l’implémentation. Elles sont publiées sous la forme d’un ensemble de [billets wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) dans le [dépôt GitHub](https://github.com/dotnet-architecture/eShopModernizing) où vous trouvez aussi des exemples d’applications associées (présentées dans la section suivante). Le dernier chapitre et les procédures pas à pas du wiki sur GitHub sont plus intéressants pour les développeurs et les architectes qui veulent connaître les détails d’implémentation.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Exemples d’applications pour la modernisation d’applications héritées : eShopModernizing

Le dépôt [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) sur GitHub contient deux exemples d’applications qui simulent des applications web monolithiques héritées. Une des applications web est développée avec ASP.NET MVC, tandis que l’autre est développée avec ASP.NET Web Forms. Les deux applications web sont basées sur le .NET Framework classique. Ces exemples d’applications n’utilisent pas .NET Core ou ASP.NET Core, car elles sont supposées être des applications .NET Framework existantes/héritées à moderniser.

Les deux exemples d’applications ont une seconde version, avec le code modernisé, et sont assez simples. La différence la plus importante entre les versions des applications est que leur seconde version utilise les conteneurs Windows comme choix de déploiement. Quelques ajouts ont été apportés aux secondes versions, comme des objets blob Stockage Azure pour la gestion des images, Azure Active Directory pour la gestion de la sécurité et Azure Application Insights pour la surveillance et l’audit des applications.

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

Nous avons écrit ce guide pour vous aider à comprendre les options dont vous disposez pour améliorer et moderniser des applications web .NET existantes. Le guide et les exemples d’applications associés sont en constante évolution. Vos commentaires sont bienvenus ! Si vous avez des commentaires à formuler sur la façon dont ce guide peut être amélioré, envoyez-les à l’adresse : [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
