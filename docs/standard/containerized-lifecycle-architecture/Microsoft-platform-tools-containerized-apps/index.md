---
title: "Présentation de la plateforme et des outils Microsoft pour les applications en conteneur"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a24f57216130a42eb11ef44abe462d4955601fdb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-the-microsoft-platform-and-tools-for-containerized-apps"></a>Présentation de la plateforme et des outils Microsoft pour les applications en conteneur


La figure 3-1 illustre les principaux piliers du cycle de vie des applications Docker, classés selon le type de travail fourni par plusieurs équipes (développement d’applications, processus d’infrastructure DevOps, gestion et opérations informatiques). Dans l’entreprise, les profils du « persona » en charge de chaque zone sont généralement différents. Ses compétences varient aussi.

![](./media/image1.png)

Figure 3-1 : Principaux piliers du cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft

Un workflow de cycle de vie Docker en conteneur peut être initialement normalisé selon les « choix des produits par défaut », ce qui facilite et accélère le démarrage des développeurs. Toutefois, sous le capot, l’existence d’une infrastructure ouverte est fondamentale pour garantir un workflow flexible capable de s’adapter aux différents contextes de chaque organisation ou entreprise. L’infrastructure de workflow (composants et produits) doit être suffisamment flexible pour prendre en charge le futur environnement de chaque entreprise. Elle doit notamment permettre le remplacement de produits de développement ou DevOps par d’autres. Ces caractéristiques, à savoir la flexibilité, l’ouverture et le vaste choix de technologies d’infrastructure et de plateforme, sont précisément les priorités de Microsoft pour les applications Docker en conteneur, comme l’expliquent les chapitres qui suivent.

Comme le montre le tableau 3-1, l’intention de Microsoft DevOps pour les applications Docker en conteneur est de fournir un workflow DevOps ouvert qui permet de choisir les produits à utiliser pour chaque phase (Microsoft ou tiers) tout en bénéficiant d’un workflow simplifié avec des « produits par défaut » déjà connectés. Vous pouvez donc vous lancer rapidement dans votre workflow DevOps au niveau de l’entreprise pour les applications Docker.

Tableau 3-1 : Workflow DevOps ouvert à n’importe quelle technologie

| Hôte | Technologies Microsoft | Technologies tierces, enfichables dans Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Plateforme pour applications Docker   | • Microsoft Visual Studio et Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Container Service<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • N’importe quel éditeur de code (par exemple, Sublime)<br /> • N’importe quel langage (Node.js, Java, Go, etc.)<br /> • N’importe quel orchestrateur/planificateur<br /> • N’importe quel registre Docker<br /> |
| DevOps pour applications Docker     | • Visual Studio Team Services<br /> • Microsoft Team Foundation Server<br /> • Azure Container Service<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • Centre de données Docker local, Docker Swarm, Mesos DC/OS, Kubernetes, etc.<br /> |
| Gestion et surveillance  | • Operations Management Suite<br /> • Applications Insights<br /> | • Marathon, Chronos, etc.<br />

La plateforme et les outils Microsoft pour les applications Docker en conteneur, tels que définis dans le tableau 3-1, comprennent les composants suivants :

-   **Plateforme pour le développement d’applications Docker** Développement d’un service ou d’une collection de services constituant une « application ». La plateforme de développement permet aux développeurs d’effectuer tout le travail nécessaire avant d’envoyer (push) leur code dans un dépôt de code partagé. Le processus de développement de services déployés comme conteneurs est très similaire à celui d’applications ou de services sans Docker. Vous pouvez continuer d’utiliser votre langage par défaut (.NET, Node.js, Go, etc.) et votre éditeur ou IDE préféré comme Visual Studio ou Visual Studio Code. Toutefois, plutôt que de considérer Docker comme destination du déploiement, vous développez vos services dans l’environnement Docker. Vous générez, exécutez, testez et déboguez votre code dans des conteneurs au niveau local, et vous indiquez l’environnement de destination au moment du développement. L’environnement de destination étant fourni au niveau local, les conteneurs Docker mettent en place ce qu’il faut pour améliorer considérablement votre cycle de vie DevOps. Visual Studio et Visual Studio Code offrent des extensions permettant d’intégrer les conteneurs Docker à votre processus de développement.

-   **DevOps pour les applications Docker** Les développeurs qui créent des applications Docker peuvent utiliser Visual Studio Team Services (VSTS) ou tout autre produit tiers, tel que Jenkins, pour générer une solution ALM (Application Lifecycle Management) automatisée complète.

Les développeurs peuvent utiliser VSTS pour créer une solution DevOps axée sur les conteneurs en vue d’établir un processus itératif rapide qui couvre le contrôle de code source, quelle que soit son origine (VSTS-Git, GitHub, dépôt Git distant quelconque ou Subversion), l’intégration continue (CI), les tests unitaires internes, les tests d’intégration interconteneur/interservice, la livraison continue (CD) et la gestion des versions (RM). Les développeurs peuvent également automatiser les versions de leurs applications Docker dans Azure Container Service (du développement à la production en passant par la préproduction).

-   Gestion et surveillance de la production informatique.

**Gestion** Le service informatique peut gérer les applications et services de production de plusieurs façons :

-   **Portail Azure** Si vous avez recours à des orchestrateurs open source, utilisez Azure Container Service (ACS) et des outils de gestion de cluster comme Docker Datacenter et Mesosphere Marathon pour faciliter la configuration et la gestion de vos environnements Docker. Si vous utilisez Azure Service Fabric, l’outil Service Fabric Explorer vous permet de visualiser et de configurer votre cluster.

-   **Outils Docker** Vous pouvez gérer vos applications conteneur à l’aide d’outils familiers. Il est inutile de changer vos méthodes de gestion Docker existantes pour déplacer les charges de travail de conteneur dans le cloud. Utilisez les outils de gestion d’application que vous connaissez déjà et connectez-vous par le biais des points de terminaison d’API standards de l’orchestrateur de votre choix. Vous pouvez également utiliser d’autres outils tiers pour gérer vos applications Docker, notamment Docker Datacenter ou même les outils CLI Docker.

-   **Outils Open source** ACS exposant les points de terminaison de l’API standard pour le moteur d’orchestration, les outils les plus populaires sont compatibles avec ACS et, dans la plupart des cas, fonctionnent dans leur configuration par défaut (comme les visualiseurs, les moniteurs, les outils en ligne de commande ainsi que les outils disponibles à l’avenir).

**Surveillance** Quand vous travaillez dans des environnements de production, vous pouvez surveiller chaque angle comme suit :

-   **Operations Management Suite (OMS)** La « solution conteneur OMS » permet de gérer et de surveiller les hôtes et conteneurs Docker. Pour cela, elle affiche des informations sur l’emplacement de vos conteneurs et hôtes de conteneur, les conteneurs en cours d’exécution ou ayant échoué, ainsi que les journaux des démons et conteneurs Docker. Elle montre également les métriques de performances, notamment celles liées au processeur, à la mémoire, au réseau et au stockage pour le conteneur et les hôtes pour vous aider à résoudre et à trouver les conteneurs voisins bruyants.

-   **Application Insights** Vous pouvez surveiller les applications Docker de production en configurant simplement le SDK dans vos services de manière à récupérer les données de télémétrie des applications.

Microsoft offre donc une base complète pour un cycle de vie d’application Docker en conteneur de bout en bout. Toutefois, il s’agit d’une *collection de produits et de technologies qui vous permettent de sélectionner et d’intégrer des outils et processus existants*. La flexibilité d’une approche large et la profondeur des fonctionnalités offertes confèrent à Microsoft un positionnement avantageux dans le domaine du développement d’applications Docker en conteneur.

>[!div class="step-by-step"]
[Précédent] (../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md) [Suivant] (../design-develop-containerized-apps/index.md)
