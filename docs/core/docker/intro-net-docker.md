---
title: "Introduction à .NET et à Docker"
description: "Présentation de Docker et de .NET Core"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload: dotnetcore
ms.openlocfilehash: 8c6daabb3040998d3376ad022790c16b9629233f
ms.sourcegitcommit: bf8a3ba647252010bdce86dd914ac6c61b5ba89d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2018
---
# <a name="introduction-to-net-and-docker"></a>Introduction à .NET et à Docker

Cet article fournit une introduction et un contexte conceptuel à l’utilisation de .NET sur Docker.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker : empaquetage d’applications pour leur déploiement et leur exécution partout

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) est une plateforme ouverte qui permet aux développeurs et aux administrateurs de créer des [images](https://docs.docker.com/glossary/?term=image), de livrer et d’exécuter des applications distribuées dans un environnement peu isolé appelé un [conteneur](https://www.docker.com/what-container). Cette approche permet une gestion efficace du cycle de vie des applications entre les environnements de développement, d’assurance qualité et de production.
 
La [plateforme Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) utilise le [moteur Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) pour générer et empaqueter rapidement des applications sous forme d’[images Docker](https://docs.docker.com/glossary/?term=image) créées à l’aide de fichiers écrits au format [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) qui est ensuite déployé et exécuté dans un [conteneur en couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Vous pouvez créer vos propres [images en couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) en tant que fichiers Dockerfile ou utiliser des images existant déjà dans un [Registre](https://docs.docker.com/glossary/?term=registry), comme [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).

La [relation entre les conteneurs, les images et les Registres Docker](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) est un concept important pour la [conception et création d’applications ou de microservices en conteneur](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Cette approche réduit considérablement le temps nécessaire entre le développement et le déploiement.

### <a name="further-reading-and-watching"></a>Informations (et vidéos) supplémentaires

* [Conteneurs Windows : développement d’applications modernes avec un contrôle d’entreprise.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Vue d’ensemble de Docker](https://docs.docker.com/engine/docker-overview/)
* [Dockerfile sur les conteneurs Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile.md)
* [Meilleures pratiques pour l’écriture de fichiers Dockerfile](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Création d’images Docker pour les applications .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Obtention d’images .NET Docker

Les images officielles .NET Docker sont créées et optimisées par Microsoft. Elles sont accessibles dans les référentiels de Microsoft sur Docker Hub. Chaque référentiel peut contenir plusieurs images, selon les versions de .NET et les versions du système d’exploitation. La plupart des référentiels d’images fournissent un balisage complet pour vous aider à sélectionner à la fois une version de Framework spécifique et un système d’exploitation (distribution de Linux ou version de Windows).

## <a name="scenario-based-guidance"></a>Recommandations basées sur des scénarios

L’intention de Microsoft en termes de référentiels .NET est de disposer de référentiels granulaires et précis, qui représentent une charge de travail ou un scénario spécifique.

Les images `microsoft/aspnetcore` sont optimisées pour les applications ASP.NET Core sur Docker, ce qui permet un démarrage plus rapide des conteneurs.

Les images .NET Core (`microsoft/dotnet`) sont conçues pour les applications console basées sur .NET Core. Par exemple, les traitements par lots, Azure WebJobs et d’autres scénarios de console devraient utiliser des images .NET Core optimisées.

Le scénario horizontal le plus évident pour l’utilisation de Docker et d’applications .NET est celui du déploiement et de l’hébergement de la production. Notons toutefois que la production est seulement un scénario parmi d’autres qui s’avèrent tout aussi utiles. Bien que ces scénarios ne soient pas spécifiques de .NET, ils devraient s’appliquer à la plupart des plateformes de développeurs.

* **Installation à faible friction** : vous pouvez essayer .NET sans installation locale. Téléchargez simplement une image Docker contenant .NET.

* **Développement dans un conteneur** : vous pouvez développer dans un environnement cohérent, en utilisant des environnements de développement et de production similaires (pour éviter des problèmes tels que l’état global sur les machines de développeurs). Visual Studio Tools pour Docker permet même de démarrer un conteneur directement à partir de Visual Studio.

* **Tests dans un conteneur** : vous pouvez tester dans un conteneur, ce qui permet de réduire les défaillances dues à des environnements mal configurés ou à d’autres modifications apportées depuis le dernier test.

* **Génération dans un conteneur** : vous pouvez générer du code dans un conteneur, ce qui évite d’avoir à configurer correctement les ordinateurs de build partagés pour plusieurs environnements, en adoptant à la place une approche « BYOC » (apportez votre propre conteneur).

* **Déploiement dans tous les environnements** : vous pouvez déployer une image sur l’ensemble de vos environnements. Cette approche permet de réduire les défaillances dues à des différences de configuration, en modifiant généralement le comportement de l’image via la configuration externe (par exemple, variables d’environnement injectées).

[Recommandations générales](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) pour choisir entre .NET Core et .NET Framework pour le développement de conteneurs Docker.

### <a name="common-docker-development-scenarios"></a>Scénarios de développement Docker courants

#### <a name="net-core"></a>.NET Core

**Ressources .NET Core**

 Choisissez les exemples de .NET Core en fonction des scénarios qui vous intéressent. Toutes les instructions des exemples décrivent comment cibler des images Docker Windows ou Linux à partir d’ordinateurs hôtes Windows, Linux ou macOS.

Les exemples utilisent .NET Core 2.0. Ils utilisent une [build Docker en plusieurs étapes ](https://github.com/dotnet/announcements/issues/18) et des [balises Docker multi-arch](https://github.com/dotnet/announcements/issues/14) lorsque nécessaire.

* [Images .NET Core sur DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockeriser une application .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* Cet exemple de Docker .NET Core montre comment [utiliser Docker dans votre processus de développement .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). L’exemple s’applique aux conteneurs Linux et Windows.

* Cet exemple de Docker .NET Core montre un modèle des meilleures pratiques pour la [création d’images Docker pour les applications .NET Core pour la production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) L’exemple s’applique aux conteneurs Linux et Windows.

* Cet [exemple de Docker .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) montre un modèle des meilleures pratiques pour la création d’images Docker pour les [applications .NET Core autonomes](../deploying/index.md). Il sert pour le plus petit conteneur de production, sans tirer avantage du [partage d’images de base entre les conteneurs](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Les couches inférieures de Docker peuvent néanmoins être partagées.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [Annonce de builds ARM32 de Runtime .NET Core](https://github.com/dotnet/announcements/issues/29)

* [Images .NET Core pour ARM32 / Raspberry Pi sur DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Exemples de .NET Core Docker pour ARM32 / Pi Raspberry sur GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Images .NET Framework sur DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)

Ce référentiel contient des exemples qui illustrent différentes configurations de .NET Framework Docker. Vous pouvez utiliser ces images comme base pour vos propres images Docker.

**.NET Framework 4.7**

[L’exemple dotnet-framework:4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) illustre l’utilisation de base de « hello world » de [.NET Framework 4.7](../../framework/whats-new/index.md#v47). Il vous montre comment vous pouvez générer et déployer l’application en vous basant sur l’[image Docker du .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**.NET Framework 4.6.2**

L’[exemple dotnet-framework:4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) illustre l’utilisation de base de « hello world » du [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462). Il vous montre comment vous pouvez générer et déployer l’application en vous basant sur l’[image Docker du .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**.NET Framework 3.5**

 L’[exemple dotnet-framework:3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) illustre l’utilisation de base de « hello world » du [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Il vous montre comment vous pouvez générer et déployer un projet en vous basant sur .NET Framework 3.5 dans Docker.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Cet exemple d’ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) montre un modèle des meilleures pratiques pour la création d’images Docker pour les applications ASP.NET Core pour la production. L’exemple s’applique aux conteneurs Linux et Windows.

* [Images ASP.NET Core sur DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Images ASP.NET Core sur GitHub](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET Framework

* [Images ASP.NET Framework sur DockerHub](https://hub.docker.com/r/microsoft/aspnet/)

* [Application de Web Forms ASP.NET sur l’exemple de .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Images Windows Communication Framework (WCF) sur DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [Images Windows Communication Framework (WCF) sur GitHub](https://github.com/microsoft/iis-docker)

* [Exemples de Docker Windows Communication Framework (WCF) utilisant .NET Full Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Images Internet Information Server (IIS) sur DockerHub](https://hub.docker.com/r/microsoft/iis/)

* [Images Internet Information Server (IIS) sur GitHub](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Interagir avec d’autres images de conteneur de pile Microsoft

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Exécuter l’image de conteneur de Microsoft SQL Server pour Linux 2017 avec Docker Quickstart](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server pour les images Linux sur DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server pour les images de conteneur Windows sur DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Images de Microsoft SQL Server Express Edition pour les conteneurs Windows sur DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Images de Microsoft SQL Server Developer Edition pour les conteneurs Windows sur DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Agent Visual Studio Team Services (VSTS)

* [Images de l’agent Visual Studio Team Services (VSTS) sur DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Images de l’agent Visual Studio Team Services (VSTS) sur GitHub](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agent Linux Operations Management Suite (OMS)

* [Vue d’ensemble de l’agent Linux Operations Management Suite (OMS)](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Images Operations Management Suite (OMS) sur DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Images Operations Management Suite (OMS) sur GitHub](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Interface de ligne de commande (CLI) Microsoft Azure

* [Images de l’interface de ligne de commande (CLI) Microsoft Azure sur DockerHub](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Images de l’interface de ligne de commande (CLI) Microsoft Azure sur GitHub](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> Si vous ne disposez pas d’abonnement Azure, [inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour obtenir un compte gratuit pendant 30 jours et 200 dollars US en crédits Azure pour essayer une combinaison quelconque de services Azure.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Émulateur Microsoft Azure Cosmos DB (uniquement pour les conteneurs Windows)

* [Images de l’émulateur Microsoft Azure Cosmos DB sur DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Utiliser l’émulateur Azure Cosmos DB pour le développement et le test locaux](/azure/cosmos-db/local-emulator.md#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Exploration du riche écosystème de développement Docker

Maintenant que vous en avez appris plus sur la plateforme Docker et les différentes images Docker, l’étape suivante consiste à explorer le riche écosystème Docker. Les liens suivants vous montrent comment les outils Microsoft complètent le développement de conteneurs.

* [Utilisation conjointe de .NET et Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Extension Docker dans Visual Studio Code](https://code.visualstudio.com/docs/languages/dockerfile)
* [Découvrez comment utiliser Azure Service Fabric](/azure/service-fabric/index.md)
* [Exemple pour bien démarrer avec Service Fabric](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Avantages des conteneurs Windows](/virtualization/windowscontainers/about/index.md#video-overview)
* [Utilisation des outils Docker dans Visual Studio](/aspnet/core/publishing/visual-studio-tools-for-docker/index.md)
* [Déploiement d’images Docker à partir du Registre de conteneurs Azure dans Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Débogage avec Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Prise en main de Visual Studio pour Mac, les conteneurs et le code serverless dans le cloud](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Bien démarrer avec Docker et Visual Studio pour Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Étapes suivantes

* [Découvrir les concepts de base de Docker avec .NET Core](docker-basics-dotnet-core.md)
* [Création d’images Docker .NET Core](building-net-docker-images.md)
