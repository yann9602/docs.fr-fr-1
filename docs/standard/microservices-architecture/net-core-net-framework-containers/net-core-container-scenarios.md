---
title: Pour choisir le .NET Core pour les conteneurs Docker
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Pour choisir le .NET Core pour les conteneurs Docker
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7e2322bab7937c41d4659fefef11c8937d5eae7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Pour choisir le .NET Core pour les conteneurs Docker

La nature de la modularité et légère du .NET Core fait l’outil idéal pour les conteneurs. Lorsque vous déployez et démarrez d’un conteneur, son image est beaucoup plus petit avec le .NET Core à avec .NET Framework. En revanche, pour utiliser .NET Framework pour un conteneur, vous devez baser votre image sur l’image de Windows Server Core, qui est beaucoup plus importante que le Windows Nano Server ou des images de Linux que vous utilisez pour .NET Core.

En outre, le .NET Core est inter-plateformes, afin de déployer des applications de serveur avec les images de conteneur Windows ou Linux. Toutefois, si vous utilisez le .NET Framework classiques, vous pouvez uniquement déployer images basées sur Windows Server Core.

Voici une explication plus détaillée de la raison pour laquelle choisir .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Développement et le déploiement cross-platform

Si votre objectif est d’avoir une application (application web ou service) pouvant s’exécuter sur plusieurs plateformes prises en charge par Docker (Linux et Windows), le choix est clairement .NET Core, car .NET Framework ne prend en charge de Windows.

.NET core prend également en charge macOS comme une plate-forme de développement. Toutefois, lorsque vous déployez des conteneurs à un hôte Docker, cet hôte doit (actuellement) basé sur Windows ou Linux. Par exemple, dans un environnement de développement, vous pouvez utiliser un VM Linux en cours d’exécution sur un Mac.

[Visual Studio](https://www.visualstudio.com/) fournit un environnement de développement intégré (IDE) de Windows et prend en charge le développement de Docker. 

[Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/) est un IDE, l’évolution de Xamarin Studio, en cours d’exécution dans macOS et prend en charge Docker depuis mid 2017.

Vous pouvez également utiliser [Visual Studio Code](https://code.visualstudio.com/) (VS Code) sur Windows, Linux et macOS. VS Code prend entièrement en charge le .NET Core, notamment IntelliSense et le débogage. VS Code étant un éditeur léger, vous pouvez l’utiliser pour développer des applications en conteneur sur le Mac, conjointement avec l’interface CLI Docker et le [outils de l’interface de ligne de commande (CLI) de .NET Core](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). Vous pouvez également cibler .NET Core des éditeurs tiers plus comme texte Sublime, Emacs, vi et le projet open source OmniSharp, qui fournit la prise en charge IntelliSense pour les langages .NET. En plus de l’IDE et les éditeurs, vous pouvez utiliser l’interface de ligne de base de .NET pour toutes les plateformes prises en charge.

## <a name="using-containers-for-new-green-field-projects"></a>L’utilisation de conteneurs pour les nouveaux projets (« vert-field »)

Conteneurs sont fréquemment utilisés conjointement avec une architecture microservices, bien qu’ils peuvent également être utilisés pour mettez en conteneur d’applications web ou les services qui suivent un modèle d’architecture. Vous pouvez utiliser le .NET Framework sur les conteneurs Windows, mais la modularité et la nature légère du .NET Core le rend idéal pour les architectures de conteneurs et microservices. Lorsque vous créez et déployez un conteneur, son image est beaucoup plus petit avec le .NET Core à avec .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Création et déploiement de microservices sur les conteneurs

Vous pouvez utiliser le .NET Framework traditionnelles pour la création d’applications microservices (sans les conteneurs) à l’aide de processus simples. De cette façon, étant donné que le .NET Framework est déjà installé et partagé entre plusieurs processus, les processus sont claires et rapidement pour démarrer. Toutefois, si vous utilisez des conteneurs, l’image pour le .NET Framework traditionnelles est également basée sur Windows Server Core et qui le rend trop importante pour une approche microservices-sur-conteneurs.

En revanche, le .NET Core est le meilleur candidat si l’adoption d’un système orienté de microservices qui est basé sur les conteneurs, étant donné que le .NET Core est léger. En outre, les images de conteneur associés, l’image de Linux ou l’image Windows Nano, sont lean et petites qui effectue la lumière de conteneurs et rapides pour démarrer.

Un microservice est destiné à être aussi petite que possible : soit clair lorsque révolution, d’avoir un faible encombrement mémoire, d’avoir un petit délimitée contexte, pour représenter une petite zone de problèmes et pour être en mesure de démarrer et arrêter d’accélérée. Pour ces configurations requises, vous devez utiliser des images de conteneur de petite et rapide à instancier à l’image de conteneur .NET Core.

Une architecture de microservices vous permet également de combiner les technologies au-delà des limites d’un service. Cela permet une migration progressive vers le .NET Core pour le nouveau microservices qui fonctionnent conjointement avec les autres microservices ou services développés avec Node.js, Python, Java, GoLang ou d’autres technologies.

## <a name="deploying-high-density-in-scalable-systems"></a>Déploiement de haute densité dans des systèmes évolutifs

Lorsque les besoins de votre système basé sur le conteneur de granularité, la meilleure densité possible et les performances, le .NET Core et ASP.NET Core sont les meilleures options. ASP.NET Core est jusqu'à dix fois plus rapide que ASP.NET dans le .NET Framework traditionnelles, et il existe d’autres technologies les plus courants pour microservices, telles que les servlets Java, Go et Node.js.

Cela est particulièrement pertinente pour les architectures de microservices, où vous pourriez avoir des centaines de microservices (conteneurs) en cours d’exécution. Avec des images ASP.NET Core (basés sur le runtime .NET Core) sur Linux ou Windows Nano, vous pouvez exécuter votre système avec un quantité nombre inférieur de serveurs ou ordinateurs virtuels, finalement l’enregistrement des coûts dans l’infrastructure et d’hébergement.


>[!div class="step-by-step"]
[Précédente] (général guidance.md) [suivant] (net-framework-conteneur-scenarios.md)
