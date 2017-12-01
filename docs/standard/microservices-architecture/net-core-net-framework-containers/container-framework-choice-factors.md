---
title: "Table de décision. .NET Framework à utiliser pour Docker"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Table de décision, .NET Framework à utiliser pour Docker"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Table de décision : .NET Framework à utiliser pour Docker

Voici un résumé s’il faut utiliser des conteneurs de .NET Framework ou .NET Core et Windows ou Linux. N’oubliez pas que pour les conteneurs Linux, vous devez les hôtes basés sur Linux de Docker (machines virtuelles ou serveurs) que pour les conteneurs Windows, vous devez Windows Server en fonction des hôtes Docker (machines virtuelles ou serveurs).

Il existe plusieurs fonctionnalités qui affectent votre décision de votre application. Vous devez peser l’importance de ces fonctionnalités lors de votre décision.

> [!IMPORTANT]
> Vos ordinateurs de développement seront exécute à un hôte Docker, Linux ou Windows. Microservices connexes que vous souhaitez exécuter et tester ensemble dans une solution devrez toutes exécutées sur la même plateforme de conteneur.

* Choix d’architecture de votre application est **Microservices sur les conteneurs**.
    - Votre choix d’implémentation .NET doit être *.NET Core*.
    - Votre choix de la plateforme conteneur peut être *les conteneurs Linux* ou *les conteneurs Windows*.
* Choix d’architecture de votre application est un **application monolithique**.
    - Votre choix d’implémentation .NET peut être *.NET Core* ou *.NET Framework*.
    - Si vous avez choisi *.NET Core*, votre choix de la plateforme conteneur peut être *les conteneurs Linux* ou *les conteneurs Windows*.
    - Si vous avez choisi *.NET Framework*, votre choix de la plateforme conteneur doit être *les conteneurs Windows*.
* Votre application est un **nouveau développement basé sur le conteneur (« vert-field »)**.
    - Votre choix d’implémentation .NET doit être *.NET Core*.
    - Votre choix de la plateforme conteneur peut être *les conteneurs Linux* ou *les conteneurs Windows*.
* Votre application est un **migration d’application hérité (« brown-field ») de Windows Server aux conteneurs**
    - Votre choix d’implémentation .NET est *.NET Framework* selon la dépendance d’infrastructure.
    - Choix de la plateforme de conteneur doit être *les conteneurs Windows* en raison de la dépendance de .NET Framework.
* Objectif de conception de votre application est **pair meilleures performances et évolutivité**.
    - Votre choix d’implémentation .NET doit être *.NET Core*.
    - Votre choix de la plateforme conteneur peut être *les conteneurs Linux* ou *les conteneurs Windows*.
* Vous avez créé votre application à l’aide de **ASP.NET Core**.
    - Votre choix d’implémentation .NET doit être *.NET Core*.
    - Vous pouvez utiliser la *.NET Framework* implémentation, si vous avez d’autres dépendances d’infrastructure.
    - Si vous avez choisi *.NET Core*, votre choix de la plateforme conteneur peut être *les conteneurs Linux* ou *les conteneurs Windows*.
    - Si vous avez choisi *.NET Framework*, votre choix de la plateforme conteneur doit être *les conteneurs Windows*.
* Vous avez créé votre application à l’aide de **4 d’ASP.NET (MVC 5, API Web 2 et Web Forms)**.
    - Votre choix d’implémentation .NET est *.NET Framework* selon la dépendance d’infrastructure.
    - Choix de la plateforme de conteneur doit être *les conteneurs Windows* en raison de la dépendance de .NET Framework.
* Votre application utilise **les services SignalR**.
    - Votre choix d’implémentation .NET peut être *.NET Framework*, ou *.NET Core 2.1 (lorsqu’il est publié) ou version ultérieure*.
    - Choix de la plateforme de conteneur doit être *les conteneurs Windows* si vous avez choisi l’implémentation SignalR dans .NET Framework.
    - Votre choix de la plateforme conteneur peut être Linux conteneurs ou les conteneurs Windows si vous avez choisi l’implémentation SignalR dans .NET Core 2.1 ou version ultérieure (quand il est publié).  
    - Lorsque **les services SignalR** s’exécutent sur *.NET Core*, vous pouvez utiliser *Linux conteneurs ou conteneurs Windows*.
* Votre application utilise **WCF, WF et autres infrastructures existantes**.
    - Votre choix d’implémentation .NET est *.NET Framework*, ou *.NET Core (dans la feuille de route pour une version ultérieure)*.
    - Choix de la plateforme de conteneur doit être *les conteneurs Windows* en raison de la dépendance de .NET Framework.
* Votre application implique **les services de la consommation de Azure**.
    - Votre choix d’implémentation .NET est *.NET Framework*, ou *.NET Core (services finalement tout Azure fournira client SDK pour .NET Core)*.
    - Choix de la plateforme de conteneur doit être *les conteneurs Windows* si vous utilisez des API clientes .NET Framework.
    - Si vous utilisez le client API disponibles pour *.NET Core*, vous pouvez également choisir entre *Linux conteneurs et les conteneurs Windows*.

>[!div class="step-by-step"]
[Précédente] (net-framework-conteneur-scenarios.md) [suivant] (net-conteneur-os-targets.md)
