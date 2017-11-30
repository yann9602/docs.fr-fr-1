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
# <a name="implementing-retries-with-exponential-backoff"></a>Mise en œuvre de nouvelles tentatives avec interruption exponentielle

[*Effectue une nouvelle tentative avec interruption exponentielle* ](https://docs.microsoft.com/azure/architecture/patterns/retry) est une technique qui effectue une nouvelle tentative d’une opération, avec un temps d’attente augmente de manière exponentielle, jusqu'à ce qu’un nombre maximal de tentatives a été atteint (le [interruption exponentielle](https://en.wikipedia.org/wiki/Exponential_backoff)). Cette technique prend en compte le fait que les ressources de cloud par intermittence peut-être pas disponibles pendant plus de quelques secondes pour une raison quelconque. Par exemple, un orchestrator peut déplacer un conteneur vers un autre nœud dans un cluster pour l’équilibrage de charge. Pendant ce temps, certaines demandes risquent d’échouer. Un autre exemple pourrait être une base de données tels que SQL Azure, où une base de données peut être déplacé vers un autre serveur pour l’équilibrage de charge, à l’origine de la base de données de la charge sera indisponible pendant quelques secondes.

Il existe plusieurs approches pour implémenter la logique de nouvelle tentative avec interruption exponentielle.


>[!div class="step-by-step"]
[Précédente] (partielle-échec-strategies.md) [suivant] (implement-resilient-entity-framework-core-sql-connections.md)
