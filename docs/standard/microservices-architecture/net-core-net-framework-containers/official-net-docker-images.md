---
title: Images Docker de .NET officiels
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Images Docker de .NET officiels
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6f14bd0cf55a552f3881d755ebe7389f000975d8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="official-net-docker-images"></a>Images Docker de .NET officiels

Les images officiel .NET Docker sont Docker images créés et optimisés par Microsoft. Ils sont accessibles dans les référentiels de Microsoft sur [Hub Docker](https://hub.docker.com/u/microsoft/). Chaque référentiel peut contenir plusieurs images, en fonction des versions du .NET et le système d’exploitation et les versions (Debian de Linux, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).

La vision de Microsoft pour les référentiels de .NET est référentiels granulaires et ayant le focus, où un référentiel représente une charge de travail ou un scénario spécifique. Par exemple, le [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) images doivent être utilisés lors de l’à l’aide d’ASP.NET Core sur Docker, car ces images ASP.NET Core fournissent des optimisations supplémentaires conteneurs c’est le cas peut démarrer plus rapidement.

En revanche, les images de .NET Core (microsoft/dotnet) sont destinées à des applications de console basées sur .NET Core. Par exemple, les traitements par lots, les tâches Web Azure et autres scénarios de console doivent utiliser .NET Core. Ces images n’incluent pas la pile ASP.NET Core, ce qui entraîne une plus petite image de conteneur.

La plupart des référentiels d’image fournissent le balisage complet pour vous aider à sélectionner non seulement une version de framework spécifique, mais également de choisir un système d’exploitation (distribution de Linux ou de la version de Windows).

Pour plus d’informations sur les images Docker de .NET officiels fourni par Microsoft, consultez le [résumé de .NET Docker Images](https://aka.ms/dotnetdockerimages).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Optimisations image .NET core et Docker pour le développement par rapport à la production

Lors de la génération Docker images pour les développeurs, Microsoft est axé sur les principaux scénarios suivants :

-   Utilisé pour les images *développer* et générer des applications .NET Core.

-   Utilisé pour les images *exécuter* applications .NET Core.

Pourquoi plusieurs images ? Lorsque le développement, la création et exécution d’applications en conteneur, vous devez généralement des priorités différentes. En fournissant des images pour ces tâches distinctes, Microsoft permet d’optimiser les processus distincts de développement, la création et déploiement d’applications.

### <a name="during-development-and-build"></a>Pendant le développement et build

Pendant le développement, ce qui est important est la vitesse à laquelle vous pouvez parcourir les modifications et la possibilité de déboguer les modifications. La taille de l’image n’est pas aussi importante que la possibilité d’apporter des modifications à votre code et voir les modifications rapidement. Certains outils et les « conteneurs de l’agent de build », utiliser le développement de l’image ASP.NET Core (aspnetcore/microsoft-build) au cours du développement et générer des processus. Lorsque vous créez à l’intérieur d’un conteneur Docker, les aspects importants sont les éléments qui sont nécessaires pour compiler votre application. Cela inclut le compilateur, et toutes les autres dépendances .NET, ainsi que dépendances de développement web comme npm, Gulp, Bower.

Pourquoi est-ce type d’image de la build important ? Vous ne déployez pas cette image en production. Au lieu de cela, il est une image que vous utilisez pour générer le contenu que vous placez dans une image de production. Cette image doit être utilisée dans votre environnement d’intégration continue (CI) ou d’un environnement de génération. Par exemple, au lieu de l’installation manuelle de toutes les dépendances de votre application directement sur un agent de build hôte (un ordinateur virtuel, par exemple), l’agent de build instancier une image de génération .NET Core avec toutes les dépendances requises pour générer l’application. L’agent de build doit seulement savoir comment exécuter cette image Docker. Cela simplifie votre environnement de l’élément de configuration et le rend beaucoup plus prévisibles.

### <a name="in-production"></a>En production

Important en production est la vitesse à laquelle vous pouvez déployer et démarrer vos conteneurs basées sur une image .NET Core de production. Par conséquent, l’image de runtime uniquement basée sur [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) est petite afin qu’il peut se déplacent rapidement sur le réseau à partir de votre Registre Docker à vos hôtes Docker. Le contenu est prêt à être exécuté, l’activation du temps de démarrage du conteneur pour le traitement des résultats les plus rapides. Dans le modèle de Docker, il n’est pas nécessaire pour la compilation de C\# de code, comme il existe lorsque vous exécutez dotnet build ou dotnet publier quand utilise le conteneur de build.

Dans cette image optimisée, vous placez uniquement les fichiers binaires et tout autre contenu nécessaire pour exécuter l’application. Par exemple, le contenu créé par dotnet publier contient uniquement les fichiers binaires .NET compilés, images, .js et les fichiers .css. Au fil du temps, vous verrez des images qui contiennent des packages de pre-traités avec JIT.

Bien qu’il existe plusieurs versions des images .NET Core et ASP.NET Core, elles partagent toutes une ou plusieurs couches, y compris la couche de base. Par conséquent, la quantité d’espace disque nécessaire pour stocker une image est faible ; Il se compose uniquement de l’écart entre votre image personnalisée et son image de base. Le résultat est qu’elle est rapide à extraire l’image de votre Registre.

Quand vous explorez les référentiels d’image de .NET au Hub d’ancrage, vous trouverez plusieurs versions de l’image classées ou marqué avec balises. Ces balises permettent de déterminer celle à utiliser, selon la version que vous avez besoin, comme celles figurant dans le tableau suivant :

-   Microsoft /**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**aspnetcore-build : 2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Précédente] (net-conteneur-os-targets.md) [suivant] (.. /Architect-microservice-Container-applications/index.MD)
