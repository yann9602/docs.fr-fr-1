---
title: "Architecture logique et l’architecture physique"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Architecture logique et l’architecture physique"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 635774a8fcd0cf1c0ede6a73c604071f538a37fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>Architecture logique et l’architecture physique

Il est utile à ce stade arrêter et traitent la distinction entre l’architecture logique et physique architecture, et comment cela s’applique à la conception d’applications microservice.

Pour commencer, génération microservices ne nécessite pas l’utilisation d’une technologie spécifique. Par exemple, les conteneurs Docker ne sont pas obligatoires pour créer une architecture basée sur un microservice. Ces microservices peut également être exécutées en tant que processus ordinaires. Microservices est une architecture logique.

En outre, même si un microservice peut être physiquement implémenté comme un service unique, un processus ou un conteneur (par souci de simplicité, qui est l’approche adoptée dans la version initiale de [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), cette parité entre microservice de l’entreprise et de service physique ou de conteneur n'est pas forcément dans tous les cas lorsque vous générez une application important et complexe composée de plusieurs dizaines ou même des centaines de services.

Il s’agit où il existe une différence entre l’architecture logique et physique d’une application. L’architecture logique et les limites de logiques d’un système ne correspondent pas nécessairement un à un à l’architecture physique ou de déploiement. Il peut se produire, mais il souvent pas.

Bien que vous avez peut-être identifié certaines microservices d’entreprise ou des contextes de délimitée, cela ne signifie pas que la meilleure façon de les implémenter est toujours en créant un seul service (par exemple, API Web ASP.NET) ou un seul conteneur Docker pour chaque microservice d’entreprise. Avoir une règle indiquant que chaque entreprise microservice a à être implémentées à l’aide d’un seul service ou conteneur est trop rigide.

Par conséquent, une entreprise microservice ou limitées est une architecture logique qui peut coïncident (ou non) avec l’architecture physique. Le point important est qu’une entreprise microservice ou délimitée doit être autonome en autorisant le code et l’état de version indépendamment, déployés et mis à l’échelle.

Comme le montre la Figure 4-8, le microservice business catalogue pourrait composé de plusieurs services ou processus. Il peut s’agir de plusieurs services d’API Web ASP.NET ou tout autre type de services à l’aide de HTTP ou un autre protocole. Plus important encore, les services pu partager les mêmes données, tant que ces services sont cohérente en ce qui concerne le même domaine d’entreprise.

![](./media/image8.png)

**Figure 4-8**. Microservice d’entreprise avec plusieurs services physiques

Les services dans l’exemple partagent le même modèle de données, car le service Web API cible les mêmes données que le service de recherche. Par conséquent, dans l’implémentation physique de l’entreprise microservice, vous fractionnez cette fonctionnalité afin d’adapter chacun de ces services internes vers le haut ou vers le bas en fonction des besoins. Peut-être que le service Web API généralement besoin plus instances que le service de recherche, ou vice versa.)

En bref, l’architecture logique de microservices n’a pas toujours coïncider avec l’architecture de déploiement physique. Dans ce guide, chaque fois que nous signaler un microservice, nous entendons une entreprise ou une logique microservice qui peut mapper à un ou plusieurs services. Dans la plupart des cas, il s’agit d’un service unique, mais il peut être plus.


>[!div class="step-by-step"]
[Précédente] (données-souveraineté-par-microservice.md) [suivant] (distributed-données-management.md)
