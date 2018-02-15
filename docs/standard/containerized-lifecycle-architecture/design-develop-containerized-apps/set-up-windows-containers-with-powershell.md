---
title: "À l’aide des commandes Windows PowerShell dans un fichier DockerFile pour configurer les conteneurs Windows (Docker standard en fonction)"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3c9a4bec4f48d988ecf8c75ff340300b83a1faef
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
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
