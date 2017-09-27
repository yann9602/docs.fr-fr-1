---
title: "Processus de développement des applications basées sur Docker"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Processus de développement des applications basées sur Docker"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: f4c241f463ff1270037c7d66ba39409ca5d9e728
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="development-process-for-docker-based-applications"></a>Processus de développement des applications basées sur Docker

*Développez des applications .NET en conteneur comme vous le souhaitez, soit dans un environnement de développement intégré (IDE) avec Visual Studio et Visual Studio Tools pour Docker, soit avec une interface CLI/un éditeur avec une interface CLI Docker et Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Environnement de développement pour les applications Docker

### <a name="development-tool-choices-ide-or-editor"></a>Choix des outils de développement : IDE ou éditeur

Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft propose des outils que vous pouvez utiliser pour développer des applications Docker.

**Visual Studio Tools pour Docker**. Si vous utilisez Visual Studio 2015, vous pouvez installer le complément [Visual Studio Tools pour Docker](https://marketplace.visualstudio.com/items?itemName=MicrosoftCloudExplorer.VisualStudioToolsforDocker-Preview). Si vous utilisez Visual Studio 2017, les outils pour Docker sont déjà intégrés. Dans les deux cas, les outils pour Docker vous permettent de développer, exécuter et valider vos applications directement dans l’environnement Docker cible. Vous pouvez appuyer sur F5 pour exécuter et déboguer votre application (conteneur unique ou plusieurs conteneurs) directement dans un hôte Docker, ou appuyer sur Ctrl+F5 pour modifier et actualiser votre application sans avoir à régénérer le conteneur. Ce choix est le plus simple et le plus robuste pour les développeurs Windows ciblant des conteneurs Docker pour Windows ou Linux.

**Visual Studio Code et interface CLI Docker**. Si vous préférez un éditeur léger et multiplateforme qui prend en charge n’importe quel langage de développement, vous pouvez utiliser Microsoft Visual Studio Code (VS Code) et l’interface CLI Docker. Il s’agit d’une approche de développement multiplateforme pour Mac, Linux et Windows.

Ces produits proposent une expérience simple mais robuste qui simplifie le flux de travail du développeur. En installant les outils [Docker Community Edition (CE)](https://www.docker.com/community-edition), vous pouvez utiliser une seule interface CLI Docker pour générer des applications pour Windows et Linux. De plus, Visual Studio Code prend en charge les extensions pour Docker comme IntelliSense pour les Dockerfiles et les tâches de raccourci afin d’exécuter des commandes Docker à partir de l’éditeur.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Visual Studio Tools pour Docker**
    [*https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4*](https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4)

-   **Visual Studio Code**. Site officiel.
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Docker Community Edition (CE) pour Mac et Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Langages et frameworks .NET pour conteneurs Docker

Comme indiqué dans les sections précédentes de ce guide, vous pouvez utiliser .NET Framework, .NET Core ou le projet Mono open source pour développer des applications .NET Docker en conteneur. Vous pouvez développer en C\#, F\# ou Visual Basic quand vous ciblez des conteneurs Linux ou Windows, selon le .NET Framework en cours d’utilisation. Pour plus d’informations sur les langages .NET, consultez le billet de blog [Stratégie de langage .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).


>[!div class="step-by-step"]
[Précédent] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)

