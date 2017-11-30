---
title: "À l’aide des commandes Windows PowerShell dans un fichier DockerFile pour configurer les conteneurs Windows (Docker standard en fonction)"
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: f7e92b0f1c749e2c00e3afc4ffcfc2fc88d7628f
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2017
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>À l’aide des commandes Windows PowerShell dans un fichier DockerFile pour configurer les conteneurs Windows (Docker standard en fonction)

Avec [les conteneurs Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), vous pouvez convertir vos applications Windows pour les images Docker et les déployer avec les mêmes outils que le reste de l’écosystème Docker.

Pour utiliser les conteneurs Windows, vous devez simplement écrire des commandes Windows PowerShell dans le fichier DockerFile, comme illustré dans l’exemple suivant :

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Dans ce cas, nous utilisons Windows PowerShell pour installer une image de base Windows Server Core, ainsi qu’IIS.

De la même façon, vous pouvez également utiliser des commandes Windows PowerShell pour configurer des composants supplémentaires comme ASP.NET traditionnel 4.x et .NET 4.6 ou tout autre logiciel Windows, comme indiqué ici :

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
[Précédente] (visual-studio-outils-de-docker.md) [suivant] (.. /docker-DevOps-workflow/index.MD)
