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
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="bf108-104">À l’aide des commandes Windows PowerShell dans un fichier DockerFile pour configurer les conteneurs Windows (Docker standard en fonction)</span><span class="sxs-lookup"><span data-stu-id="bf108-104">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="bf108-105">Avec [les conteneurs Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), vous pouvez convertir vos applications Windows pour les images Docker et les déployer avec les mêmes outils que le reste de l’écosystème Docker.</span><span class="sxs-lookup"><span data-stu-id="bf108-105">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="bf108-106">Pour utiliser les conteneurs Windows, vous devez simplement écrire des commandes Windows PowerShell dans le fichier DockerFile, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bf108-106">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="bf108-107">Dans ce cas, nous utilisons Windows PowerShell pour installer une image de base Windows Server Core, ainsi qu’IIS.</span><span class="sxs-lookup"><span data-stu-id="bf108-107">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="bf108-108">De la même façon, vous pouvez également utiliser des commandes Windows PowerShell pour configurer des composants supplémentaires comme ASP.NET traditionnel 4.x et .NET 4.6 ou tout autre logiciel Windows, comme indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="bf108-108">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="bf108-109">[Précédente] (visual-studio-outils-de-docker.md) [suivant] (.. /docker-DevOps-workflow/index.MD)</span><span class="sxs-lookup"><span data-stu-id="bf108-109">[Previous] (visual-studio-tools-for-docker.md) [Next] (../docker-devops-workflow/index.md)</span></span>
