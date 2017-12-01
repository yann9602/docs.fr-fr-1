---
title: "Présentation de .NET et Docker"
description: "Présentation des Docker et .NET Core"
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
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a>Présentation de .NET et Docker

 Cet article fournit une introduction et l’arrière-plan conceptuel à l’utilisation de .NET sur Docker. 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker : Empaquetage de vos applications pour déployer et exécuter n’importe quel endroit

[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) est une plateforme ouverte qui permet aux développeurs et aux administrateurs de build [images](https://docs.docker.com/glossary/?term=image), expédier et d’exécuter des applications distribuées dans un environnement faiblement isolé, appelé un [conteneur](https://www.docker.com/what-container). Cette approche permet la gestion du cycle de vie application efficace entre le développement, les questions et réponses et les environnements de production.
 
Le [plateforme Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) utilise le [moteur Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) pour rapidement générer et empaqueter des applications en tant que [Docker images](https://docs.docker.com/glossary/?term=image) créé à l’aide des fichiers écrits le [Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) format puis déployé et exécuté un [en couche du conteneur](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Vous pouvez créer votre propre [en couches d’images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) en tant que fichiers dockerfile ou utiliser celles qui existent déjà dans un [Registre](https://docs.docker.com/glossary/?term=registry), comme [Hub Docker](https://docs.docker.com/glossary/?term=Docker%20Hub).

Le [relation entre les registres, des images et des conteneurs Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) est un concept important lorsque [création et architecture placées dans des conteneurs applications ou microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/). Cette approche réduit considérablement le temps entre le développement et le déploiement.

### <a name="further-reading-and-watching"></a>Informations supplémentaires (et la surveillance)

* [Conteneurs Windows : développement d’applications modernes avec contrôle de niveau entreprise.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Vue d’ensemble de docker](https://docs.docker.com/engine/docker-overview/)
* [Informations sur les conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Meilleures pratiques pour l’écriture de fichiers Dockerfile](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Génération Docker Images pour les applications .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Mise en route du .NET Docker Images

Les images officiel .NET Docker sont créés et optimisés par Microsoft. Ils sont accessibles dans les référentiels de Microsoft sur le Hub d’ancrage. Chaque référentiel peut contenir plusieurs images, selon les versions de .NET et sur les versions de système d’exploitation. La plupart des référentiels d’image fournissent le balisage complet pour vous aider à sélectionner une version de framework spécifique et d’un système d’exploitation (distribution de Linux ou de la version de Windows).

## <a name="scenario-based-guidance"></a>Scénario en fonction des instructions

Intention de Microsoft pour les référentiels de .NET est d’avoir des référentiels granulaires et précis, qui représentent une charge de travail ou un scénario spécifique.

Le `microsoft/aspnetcore` images sont optimisés pour les applications ASP.NET Core sur Docker, afin de démarrage plus rapide des conteneurs.

Les images de .NET Core (`microsoft/dotnet`) sont conçus pour les applications console basées sur .NET Core. Par exemple, les traitements par lots, les tâches Web Azure et autres scénarios de la console doivent utiliser des images .NET Core optimisées.

Le scénario plus évident horizontal pour l’utilisation des applications .NET et de Docker est pour le déploiement de production et l’hébergement. Il s’avère que la production est le seul scénario et les autres sont également utiles. Ces scénarios ne sont pas spécifiques à .NET, mais il doivent s’appliquer à la plupart des plateformes de développeur.

* **Faible friction installer** — vous pouvez essayer .NET sans une installation locale. Téléchargez une image Docker avec .NET qu’il contient.

* **Développer dans un conteneur** , vous pouvez développer dans un environnement cohérent, qui effectue les environnements de développement et de production similaires (en évitant les problèmes, tels que l’état global sur les ordinateurs de développement). Visual Studio Tools pour Docker même permettent de démarrer un conteneur directement à partir de Visual Studio.

* **Dans un conteneur de test** — vous pouvez tester dans un conteneur, ce qui réduit les défaillances dues à des environnements mal configurés ou à d’autres modifications à partir du dernier test.

* **Build dans un conteneur** , vous pouvez générer du code dans un conteneur, ce qui évite de devoir configurer correctement les ordinateurs de build partagé pour plusieurs environnements, mais au lieu de déplacer vers un « BYOC » (apportez votre propre conteneur) approche.

* **Déploiement dans les environnements** , vous pouvez déployer une image via l’ensemble de vos environnements. Cette approche réduit les échecs en raison de différences de configuration, en général, modifier le comportement de l’image via la configuration externe (par exemple, les variables d’environnement injecté).

[Conseils généraux](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) pour choisir entre .NET Core et .NET Framework pour le développement de conteneur Docker.

### <a name="common-docker-development-scenarios"></a>Scénarios de développement courants Docker

#### <a name="net-core"></a>.NET Core

**Ressources de .NET core**

 Choisissez les exemples de .NET Core selon vos scénarios d’intérêt. Toutes les instructions de l’exemple décrivent comment cibler Windows ou Linux Docker images à partir d’ordinateurs hôtes Windows, Linux ou macOS.

Les exemples utilisent la base de .NET 2.0. Ils utilisent Docker [en plusieurs étapes build](https://github.com/dotnet/announcements/issues/18) et [arch plusieurs balises](https://github.com/dotnet/announcements/issues/14) le cas échéant.

* [Images de .NET core sur docker Hub](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockerize d’une application .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* Cet exemple .NET Core Docker montre comment [utiliser Docker dans votre processus de développement .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). L’exemple fonctionne avec les conteneurs Linux et Windows.

* Cet exemple de .NET Core Docker montre un modèle pratique meilleures pour [génération Docker images pour les applications .NET Core pour la production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) L’exemple fonctionne avec les conteneurs Linux et Windows.

* Cela [exemple de .NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) illustre un modèle pratique meilleures pour créer des images de Docker pour [des applications .NET Core autonomes](https://docs.microsoft.com/dotnet/core/deploying/). Utilisé pour le plus petit conteneur de production sans un avantage de [partage d’images de base entre les conteneurs](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). Toutefois, les couches inférieures de Docker peut être partagés.

#### <a name="arm32--raspberry-pi"></a>ARM32 / framboises Pi

* [Annonce de builds ARM32 de Runtime .NET core](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / framboises Pi .NET Core images sur docker Hub](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Pi Raspberry .NET Core Docker Samples sur GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Images de .NET framework sur docker Hub](https://hub.docker.com/r/microsoft/dotnet-framework/) ce référentiel contient des exemples qui illustrent différentes configurations de .NET Framework Docker. Vous pouvez utiliser ces images en tant que la base de vos propres images Docker.

**.NET framework 4.7**

[Le [dotnet-exemple d’infrastructure : 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) illustre l’utilisation « hello world » de base de la [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47). Il vous montre comment vous pouvez générer et déployer l’application de partie de confiance sur le [image docker de .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**.NET framework 4.6.2**

Le [dotnet-exemple d’infrastructure : 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) illustre l’utilisation « hello world » de base de la [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462). Il vous montre comment vous pouvez générer et déployer l’application de partie de confiance sur le [image docker de .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**.NET framework 3.5**

 Le [dotnet-exemple d’infrastructure : 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) illustre l’utilisation « hello world » de base de [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Il vous montre comment vous pouvez générer et déployer un projet de s’appuyer sur .NET Framework 3.5 dans Docker.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Cet exemple ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) illustre un modèle pratique meilleures pour générer des images Docker pour ASP.NET Core des applications de production. L’exemple fonctionne avec les conteneurs Linux et Windows.

* [Images ASP.NET Core sur docker Hub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Images ASP.NET Core sur GitHub](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>Infrastructure ASP.NET 

* [Images de l’infrastructure ASP.NET sur docker Hub](https://hub.docker.com/r/microsoft/aspnet/)

* [Application de Web Forms ASP.NET sur l’exemple de .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Foundation (WCF)

* [Images de Windows Communication Framework (WCF) sur docker Hub](https://hub.docker.com/r/microsoft/wcf/)

* [Images de Windows Communication Framework (WCF) sur GitHub](https://github.com/microsoft/iis-docker)

* [Exemples de Docker Windows Communication Framework (WCF) à l’aide complète de .NET Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Images de Internet Information Server (IIS) sur docker Hub](https://hub.docker.com/r/microsoft/iis/)

* [Images de Internet Information Server (IIS) sur GitHub](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Interagir avec d’autres images de conteneur de pile Microsoft

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Exécutez Microsoft SQL Server pour l’image de conteneur Linux 2017 avec démarrage rapide de Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server pour les images Linux sur docker Hub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Images de Microsoft SQL Server pour les conteneurs Windows sur docker Hub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Images de Microsoft SQL Server Express Edition pour les conteneurs Windows sur docker Hub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Images de Microsoft SQL Server Developer Edition pour les conteneurs Windows sur docker Hub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Agent de Visual Studio Team Services (VSTS)

* [Images de l’agent Visual Studio Team Services (VSTS) sur docker Hub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Images de l’agent Visual Studio Team Services (VSTS) sur GitHub](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agent de Operations Management Suite (OMS) Linux

* [Présentation de l’agent Operations Management Suite (OMS) Linux](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Images Operations Management Suite (OMS) sur docker Hub](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [Images Operations Management Suite (OMS) sur GitHub](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Interface de ligne de commande (CLI) Microsoft Azure

* [Images docker hub Microsoft Azure Interface de ligne de commande (CLI)](Docker image for Microsoft Azure Command Line Interface) 

* [Images de Microsoft Azure Interface de ligne de commande (CLI) sur GitHub](https://github.com/Microsoft/OMS-docker)

> [!Note]
> Si vous n’avez pas d’un abonnement Azure, [Inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour un compte gratuit de 30 jours et un get 200 $ de crédits Azure permettant de tester n’importe quelle combinaison de services Azure.
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB émulateur (uniquement pour les conteneurs Windows)

* [Images d’émulateur de base de données Microsoft Azure Cosmos sur docker Hub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Utiliser l’émulateur de base de données Azure Cosmos pour développement local et le test](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Exploration de l’écosystème de développement riche Docker

Maintenant que vous avez appris sur la plateforme Docker et les images Docker différentes, l’étape suivante consiste à Explorer l’écosystème Docker enrichi. Les liens suivants vous montrent comment les outils Microsoft complètent le développement du conteneur.

* [L’utilisation conjointe de .NET et Docker](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [Conception et développement d’Applications .NET multi conteneur et en fonction de Microservice](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [Extension de Visual Studio Code Docker](https://code.visualstudio.com/docs/languages/dockerfile) 
* [Découvrez comment utiliser Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/) 
* [Exemple de service Fabric prise en main](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Avantages des conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [Utilisation des outils de Visual Studio Docker](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Déploiement d’Images Docker à partir du Registre de conteneur Azure pour les Instances du conteneur Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Débogage avec Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Prise en mains avec Visual Studio pour Mac, les conteneurs et sans code dans le cloud](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Prise en main Docker et Visual Studio pour Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Étapes suivantes

* [Principes fondamentaux de Docker avec le .NET Core](../docker/docker-basics-dotnet-core.md)
* [Création d’Images de Docker .NET Core](../docker/building-net-docker-images)