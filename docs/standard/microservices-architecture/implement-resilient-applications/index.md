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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93e5435b402cc1a8ff049f25465de0f719516f31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="7a8ac-104">Implémentation d’applications résilientes</span><span class="sxs-lookup"><span data-stu-id="7a8ac-104">Implementing Resilient Applications</span></span>

<span data-ttu-id="7a8ac-105">*Vos applications basées sur des microservices et le cloud devront faire face tôt ou tard à des défaillances partielles qui se produiront certainement. Vous devez concevoir votre application de façon à la rendre résiliente face à ces défaillances partielles.*</span><span class="sxs-lookup"><span data-stu-id="7a8ac-105">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="7a8ac-106">La résilience est la capacité à surmonter les défaillances et à continuer de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="7a8ac-107">Il ne s’agit pas d’éviter les défaillances, mais d’accepter le fait qu’il s’en produira et qu’il faudra y répondre pour éviter les temps d’arrêt ou des pertes de données.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-107">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="7a8ac-108">La résilience vise à remettre l’application dans un état entièrement fonctionnel après une défaillance.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="7a8ac-109">Il est assez difficile de concevoir et de déployer une application basée sur des microservices.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-109">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="7a8ac-110">Mais vous devez aussi veiller à ce votre application continue de s’exécuter dans un environnement qui subira à coup sûr une défaillance quelconque.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="7a8ac-111">Par conséquent, votre application doit être résiliente.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="7a8ac-112">Elle doit être conçue pour faire face à des défaillances partielles, qu’il s’agisse de pannes réseau ou d’incidents sur des nœuds ou des machines virtuelles dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="7a8ac-113">Même les microservices (conteneurs) qui sont déplacés sur un autre nœud de cluster peuvent occasionner de brèves défaillances intermittentes au sein de l’application.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="7a8ac-114">Les divers composants qui constituent votre application doivent aussi intégrer des fonctionnalités de contrôle d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="7a8ac-115">En suivant les recommandations fournies dans ce chapitre, vous pouvez créer une application capable de fonctionner correctement en dépit des temps morts temporaires ou des interruptions normales qui se produisent dans les déploiements complexes et dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="7a8ac-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7a8ac-116">[Précédent] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Suivant] (handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="7a8ac-116">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
