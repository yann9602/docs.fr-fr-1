---
title: "Environnement de développement pour les applications Docker"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad1a6e4cb0974ebb067cf1a7be987d696e8bc82a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="development-environment-for-docker-apps"></a>Environnement de développement pour les applications Docker

## <a name="development-tools-choices-ide-or-editor"></a>Choix d’outils de développement : IDE ou éditeur

Sans que si vous préférez un IDE complet et puissant ou un éditeur léger et agile, Microsoft a vous couvert en matière de développement d’applications de Docker.

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code et Docker CLI (les outils multiplateformes pour Mac, Linux et Windows)

Si vous préférez un éditeur léger, inter-plateformes prenant en charge de n’importe quel langage de développement, vous pouvez utiliser le Code de Visual Studio et l’interface CLI de Docker. Ces produits fournissent une expérience simple et robuste, qui est essentielle pour rationaliser le flux de travail du développeur. En installant « Docker pour Mac » ou « Docker pour Windows » (environnement de développement), les développeurs de Docker peuvent utiliser des CLI Docker unique pour créer des applications pour Windows ou Linux (environnement d’exécution). De plus, Visual Studio Code prend en charge les extensions de Docker avec IntelliSense pour les fichiers Dockerfile et tâches de raccourci exécuter des commandes Docker à partir de l’éditeur.

> [!NOTE]
> Pour télécharger le Code de Visual Studio, accédez à <https://code.visualstudio.com/download>.

Pour télécharger Docker pour Mac et Windows, accédez à <http://www.docker.com/products/docker>.

### <a name="visual-studio-with-docker-tools"></a>Visual Studio avec des outils de Docker

Lorsque vous utilisez Visual Studio 2015, vous pouvez installer les outils complémentaires « Docker des outils pour Visual Studio ». Pour Visual Studio 2017, outils Docker sont intégrés déjà. Dans les deux cas, vous pouvez développer, exécuter et valider vos applications directement dans l’environnement Docker choisi. F5 (unique ou plusieurs conteneurs) de votre application directement dans une Docker héberger avec débogage ou appuyez sur Ctrl + F5 pour actualiser votre application sans avoir à reconstruire le conteneur et les modifier. Il s’agit du choix de la plus simple et plus puissant pour les développeurs Windows en créant des conteneurs Docker pour Windows ou Linux.

> [!NOTE]
> Pour télécharger les outils Docker pour Visual Studio, accédez à <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.

## <a name="language-and-framework-choices"></a>Choix de langue et le framework

Vous pouvez développer des applications de Docker et les outils de Microsoft avec les langues les plus récents. Voici une liste initiale, mais vous n’êtes pas limité à celui-ci :

-   .NET core et ASP.NET Core

-   Node.js

-   Golang

-   Java

-   Ruby

-   Python

En fait, vous pouvez utiliser n’importe quel langage moderne pris en charge par Docker sur Windows ou Linux.


>[!div class="step-by-step"]
[Précédente] (orchestrer-haute-évolutivité-availability.md) [suivant] (docker-applications-interne-boucle-workflow.md)
