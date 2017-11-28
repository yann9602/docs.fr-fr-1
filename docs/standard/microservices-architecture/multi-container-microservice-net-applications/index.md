---
title: "Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices"
description: "Architecture des Microservices .NET pour les applications .NET en conteneur | Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 46d2859fa3b739b1a2a8b1502d4e418fab204648
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="754f2-104">Conception et développement d’applications .NET à plusieurs conteneurs et basées sur des microservices</span><span class="sxs-lookup"><span data-stu-id="754f2-104">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="754f2-105">*Le développement d’applications de microservice en conteneur signifie que vous générez des applications à plusieurs conteneurs. Toutefois, une application à plusieurs conteneurs pourrait aussi être plus simple, (par exemple, une application à trois niveaux) et non générée à l’aide d’une architecture de microservice.*</span><span class="sxs-lookup"><span data-stu-id="754f2-105">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="754f2-106">Précédemment, nous avons posé la question : « Docker est-il nécessaire pour générer une architecture de microservice ? »</span><span class="sxs-lookup"><span data-stu-id="754f2-106">Earlier we raised the question “Is Docker necessary when building a microservice architecture?”</span></span> <span data-ttu-id="754f2-107">La réponse est clairement non.</span><span class="sxs-lookup"><span data-stu-id="754f2-107">The answer is a clear no.</span></span> <span data-ttu-id="754f2-108">Docker est un activateur qui peut fournir des avantages significatifs, mais les conteneurs et Docker ne sont pas obligatoires pour les microservices.</span><span class="sxs-lookup"><span data-stu-id="754f2-108">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="754f2-109">Par exemple, vous pouvez créer une application basée sur des microservices avec ou sans Docker en utilisant Azure Service Fabric, qui prend en charge des microservices exécutés en tant que processus simples ou en tant que conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="754f2-109">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="754f2-110">Toutefois, si vous savez comment concevoir et développer une application basée sur des microservices qui est également basée sur des conteneurs Docker, vous serez en mesure de concevoir et développer n’importe quel modèle d’application plus simple.</span><span class="sxs-lookup"><span data-stu-id="754f2-110">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="754f2-111">Par exemple, vous pouvez concevoir une application à trois niveaux qui requiert également une approche de plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="754f2-111">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="754f2-112">Par conséquent, et parce que les architectures de microservice sont une tendance majeure dans le milieu des conteneurs, cette section se concentre sur une implémentation d’architecture de microservice qui utilise des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="754f2-112">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="754f2-113">[Précédent] (../containerize-net-framework-applications/index.md) [Next] (microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="754f2-113">[Previous] (../containerize-net-framework-applications/index.md) [Next] (microservice-application-design.md)</span></span>
