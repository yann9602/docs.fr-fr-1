---
title: Choix entre .NET Core et .NET Framework pour les conteneurs Docker
description: Architecture des microservices .NET pour les applications .NET en conteneur | Choix entre .NET Core et .NET Framework pour les conteneurs Docker
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f7a5fee26f4d138ae22f3551a25a674b22a2f6d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="5dbe2-104">Choix entre .NET Core et .NET Framework pour les conteneurs Docker</span><span class="sxs-lookup"><span data-stu-id="5dbe2-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="5dbe2-105">Il existe deux implémentations prises en charge pour générer des applications Docker en conteneur côté serveur avec .NET : [.NET Framework](https://www.microsoft.com/net/download/framework) et [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="5dbe2-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="5dbe2-106">Elles partagent de nombreux composants .NET Standard et vous permettent de partager du code entre les deux.</span><span class="sxs-lookup"><span data-stu-id="5dbe2-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="5dbe2-107">Toutefois, il existe des différences fondamentales entre elles et votre choix dépend de ce que vous souhaitez accomplir.</span><span class="sxs-lookup"><span data-stu-id="5dbe2-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="5dbe2-108">Cette section fournit des instructions pour éclairer le choix de chaque implémentation.</span><span class="sxs-lookup"><span data-stu-id="5dbe2-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5dbe2-109">[Précédent] (../container-docker-introduction/docker-containers-images-registries.md) [Suivant] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="5dbe2-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
