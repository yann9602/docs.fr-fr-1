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
# <a name="service-oriented-architecture"></a><span data-ttu-id="fd94a-104">Architecture orientée services</span><span class="sxs-lookup"><span data-stu-id="fd94a-104">Service-oriented architecture</span></span> 

<span data-ttu-id="fd94a-105">Architecture orientée services (SOA) a été un utilisation excessive du terme et a vocation de différentes choses pour différentes personnes.</span><span class="sxs-lookup"><span data-stu-id="fd94a-105">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="fd94a-106">Mais comme dénominateur commun, SOA signifie la structure de votre application en décomposant il dans plusieurs services (généralement en tant que les services HTTP) qui peuvent être classées en tant que différents types tels que les sous-systèmes ou les niveaux.</span><span class="sxs-lookup"><span data-stu-id="fd94a-106">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="fd94a-107">Ces services peuvent désormais être déployés en tant que conteneurs Docker, qui résout les problèmes de déploiement, car toutes les dépendances sont incluses dans l’image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="fd94a-107">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="fd94a-108">Toutefois, lorsque vous avez besoin faire évoluer des applications SOA, vous pouvez avoir l’évolutivité et défis de disponibilité si vous déployez basé sur des hôtes Docker uniques.</span><span class="sxs-lookup"><span data-stu-id="fd94a-108">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you are deploying based on single Docker hosts.</span></span> <span data-ttu-id="fd94a-109">Il s’agit où Docker clustering logiciel ou une orchestrator vous aideront, comme expliqué dans les sections suivantes, nous permet de décrire les approches de déploiement pour microservices.</span><span class="sxs-lookup"><span data-stu-id="fd94a-109">This is where Docker clustering software or an orchestrator will help you out, as explained in later sections where we describe deployment approaches for microservices.</span></span>

<span data-ttu-id="fd94a-110">Conteneurs docker sont utiles (mais n’est pas obligatoire) pour les architectures orientées service traditionnelles et les architectures de microservices plus avancées.</span><span class="sxs-lookup"><span data-stu-id="fd94a-110">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="fd94a-111">Microservices dérivent SOA, mais SOA est différent de l’architecture de microservices.</span><span class="sxs-lookup"><span data-stu-id="fd94a-111">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="fd94a-112">Fonctionnalités comme les courtiers centrales big, orchestrators central au niveau de l’organisation et le [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) typiques dans SOA.</span><span class="sxs-lookup"><span data-stu-id="fd94a-112">Features like big central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="fd94a-113">Mais dans la plupart des cas, il s’agit des modèles dans la Communauté de microservice.</span><span class="sxs-lookup"><span data-stu-id="fd94a-113">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="fd94a-114">En fait, certaines personnes dire que « l’architecture de microservice est SOA bien ».</span><span class="sxs-lookup"><span data-stu-id="fd94a-114">In fact, some people argue that “The microservice architecture is SOA done right.”</span></span>

<span data-ttu-id="fd94a-115">Ce guide se concentre sur microservices, car une approche SOA est moins normative que la configuration requise et les techniques utilisées dans une architecture de microservice.</span><span class="sxs-lookup"><span data-stu-id="fd94a-115">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="fd94a-116">Si vous savez comment créer une application basée sur un microservice, vous savez également comment générer une application orientée plus simple.</span><span class="sxs-lookup"><span data-stu-id="fd94a-116">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="fd94a-117">[Précédente] (docker-application-état-data.md) [suivant] (microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="fd94a-117">[Previous] (docker-application-state-data.md) [Next] (microservices-architecture.md)</span></span>
