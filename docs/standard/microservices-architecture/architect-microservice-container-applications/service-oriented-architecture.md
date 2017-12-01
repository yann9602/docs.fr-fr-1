---
title: "Architecture orientée services"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Architecture orientée services"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a>Architecture orientée services 

Architecture orientée services (SOA) a été un utilisation excessive du terme et a vocation de différentes choses pour différentes personnes. Mais comme dénominateur commun, SOA signifie la structure de votre application en décomposant il dans plusieurs services (généralement en tant que les services HTTP) qui peuvent être classées en tant que différents types tels que les sous-systèmes ou les niveaux.

Ces services peuvent désormais être déployés en tant que conteneurs Docker, qui résout les problèmes de déploiement, car toutes les dépendances sont incluses dans l’image de conteneur. Toutefois, lorsque vous avez besoin faire évoluer des applications SOA, vous pouvez avoir l’évolutivité et défis de disponibilité si vous déployez basé sur des hôtes Docker uniques. Il s’agit où Docker clustering logiciel ou une orchestrator vous aideront, comme expliqué dans les sections suivantes, nous permet de décrire les approches de déploiement pour microservices.

Conteneurs docker sont utiles (mais n’est pas obligatoire) pour les architectures orientées service traditionnelles et les architectures de microservices plus avancées.

Microservices dérivent SOA, mais SOA est différent de l’architecture de microservices. Fonctionnalités comme les courtiers centrales big, orchestrators central au niveau de l’organisation et le [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) typiques dans SOA. Mais dans la plupart des cas, il s’agit des modèles dans la Communauté de microservice. En fait, certaines personnes dire que « l’architecture de microservice est SOA bien ».

Ce guide se concentre sur microservices, car une approche SOA est moins normative que la configuration requise et les techniques utilisées dans une architecture de microservice. Si vous savez comment créer une application basée sur un microservice, vous savez également comment générer une application orientée plus simple.




>[!div class="step-by-step"]
[Précédente] (docker-application-état-data.md) [suivant] (microservices-architecture.md)
