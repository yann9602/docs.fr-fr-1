---
title: "Implémentation d’applications résilientes"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Implémentation d’applications résilientes"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: a6fc2f4c963d857be06e194468e2f8514437dd1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-applications"></a>Implémentation d’applications résilientes

*Vos applications basées sur des microservices et le cloud devront faire face tôt ou tard à des défaillances partielles qui se produiront certainement. Vous devez concevoir votre application de façon à la rendre résiliente face à ces défaillances partielles.*

La résilience est la capacité à surmonter les défaillances et à continuer de fonctionner. Il ne s’agit pas d’éviter les défaillances, mais d’accepter le fait qu’il s’en produira et qu’il faudra y répondre pour éviter les temps d’arrêt ou des pertes de données. La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.

Il est assez difficile de concevoir et de déployer une application basée sur des microservices. Mais vous devez aussi veiller à ce votre application continue de s’exécuter dans un environnement qui subira à coup sûr une défaillance quelconque. Par conséquent, votre application doit être résiliente. Elle doit être conçue pour faire face à des défaillances partielles, qu’il s’agisse de pannes réseau ou d’incidents sur des nœuds ou des machines virtuelles dans le cloud. Même les microservices (conteneurs) qui sont déplacés sur un autre nœud de cluster peuvent occasionner de brèves défaillances intermittentes au sein de l’application.

Les divers composants qui constituent votre application doivent aussi intégrer des fonctionnalités de contrôle d’intégrité. En suivant les recommandations fournies dans ce chapitre, vous pouvez créer une application capable de fonctionner correctement en dépit des temps morts temporaires ou des interruptions normales qui se produisent dans les déploiements complexes et dans le cloud.


>[!div class="step-by-step"]
[Précédent] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Suivant] (handle-partial-failure.md)
