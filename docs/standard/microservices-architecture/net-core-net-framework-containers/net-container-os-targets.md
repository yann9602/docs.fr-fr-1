---
title: "Le système d’exploitation à cibler avec les conteneurs .NET"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Le système d’exploitation à cibler avec les conteneurs .NET"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a>Le système d’exploitation à cibler avec les conteneurs .NET

Étant donné la diversité des systèmes d’exploitation pris en charge par Docker et les différences entre .NET Framework et .NET Core, vous devez cibler un système d’exploitation spécifique et des versions spécifiques en fonction de l’infrastructure que vous utilisez. 

Pour Windows, vous pouvez utiliser Windows Server Core ou Nano Server de Windows. Ces versions de Windows fournissent des caractéristiques différentes (IIS dans Windows Server Core par rapport à un serveur web auto-hébergé comme Kestrel dans Nano Server) qui peuvent être nécessaires par .NET Framework ou .NET Core, respectivement. 

Pour Linux, plusieurs versions sont disponibles et pris en charge dans les images Docker de .NET officiels (par exemple, Debian).

Dans la Figure 3-1, vous pouvez voir la version du système d’exploitation possible selon les .NET framework.

![](./media/image1.png)

**Figure 3-1.** Systèmes d’exploitation pour cibler selon les versions du .NET framework

Vous pouvez également créer votre propre image Docker dans les cas où vous souhaitez utiliser un autre distributeur de Linux ou où vous voulez une image avec les versions non fournies par Microsoft. Par exemple, vous pouvez créer une image avec ASP.NET Core en cours d’exécution sur le .NET Framework et Windows Server Core, qui est un scénario non-fréquents pour Docker traditionnel.

Lorsque vous ajoutez le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version en fonction de la balise que vous utilisez, comme dans les exemples suivants :

-   Microsoft /**dotnet:2.0.0-runtime-Jessica**

        .NET Core 2.0 runtime-only on Linux

-   Microsoft /**dotnet:2.0.0-exécution-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   Microsoft /**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[Précédente] (conteneur-framework-choix-factors.md) [suivant] (officielle-net-docker-images.md)
