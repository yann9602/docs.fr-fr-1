---
title: "Mise en œuvre de nouvelles tentatives avec interruption exponentielle"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Mise en œuvre de nouvelles tentatives avec interruption exponentielle"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8ad8c6363ddff59915efc076161fe6b76074bbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a><span data-ttu-id="6e647-104">Mise en œuvre de nouvelles tentatives avec interruption exponentielle</span><span class="sxs-lookup"><span data-stu-id="6e647-104">Implementing retries with exponential backoff</span></span>

<span data-ttu-id="6e647-105">[*Effectue une nouvelle tentative avec interruption exponentielle* ](https://docs.microsoft.com/azure/architecture/patterns/retry) est une technique qui effectue une nouvelle tentative d’une opération, avec un temps d’attente augmente de manière exponentielle, jusqu'à ce qu’un nombre maximal de tentatives a été atteint (le [interruption exponentielle](https://en.wikipedia.org/wiki/Exponential_backoff)).</span><span class="sxs-lookup"><span data-stu-id="6e647-105">[*Retries with exponential backoff*](https://docs.microsoft.com/azure/architecture/patterns/retry) is a technique that attempts to retry an operation, with an exponentially increasing wait time, until a maximum retry count has been reached (the [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff)).</span></span> <span data-ttu-id="6e647-106">Cette technique prend en compte le fait que les ressources de cloud par intermittence peut-être pas disponibles pendant plus de quelques secondes pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="6e647-106">This technique embraces the fact that cloud resources might intermittently be unavailable for more than a few seconds for any reason.</span></span> <span data-ttu-id="6e647-107">Par exemple, un orchestrator peut déplacer un conteneur vers un autre nœud dans un cluster pour l’équilibrage de charge.</span><span class="sxs-lookup"><span data-stu-id="6e647-107">For example, an orchestrator might be moving a container to another node in a cluster for load balancing.</span></span> <span data-ttu-id="6e647-108">Pendant ce temps, certaines demandes risquent d’échouer.</span><span class="sxs-lookup"><span data-stu-id="6e647-108">During that time, some requests might fail.</span></span> <span data-ttu-id="6e647-109">Un autre exemple pourrait être une base de données tels que SQL Azure, où une base de données peut être déplacé vers un autre serveur pour l’équilibrage de charge, à l’origine de la base de données de la charge sera indisponible pendant quelques secondes.</span><span class="sxs-lookup"><span data-stu-id="6e647-109">Another example could be a database like SQL Azure, where a database can be moved to another server for load balancing, causing the database to be unavailable for a few seconds.</span></span>

<span data-ttu-id="6e647-110">Il existe plusieurs approches pour implémenter la logique de nouvelle tentative avec interruption exponentielle.</span><span class="sxs-lookup"><span data-stu-id="6e647-110">There are many approaches to implement retries logic with exponential backoff.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6e647-111">[Précédente] (partielle-échec-strategies.md) [suivant] (implement-resilient-entity-framework-core-sql-connections.md)</span><span class="sxs-lookup"><span data-stu-id="6e647-111">[Previous] (partial-failure-strategies.md) [Next] (implement-resilient-entity-framework-core-sql-connections.md)</span></span>
