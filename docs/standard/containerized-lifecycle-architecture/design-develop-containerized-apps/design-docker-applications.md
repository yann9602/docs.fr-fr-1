---
title: Concevoir des applications de Docker
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aeddd3a4b7ebd3c917fba46e048fbab5a77dda19
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="design-docker-applications"></a><span data-ttu-id="1988a-104">Concevoir des applications de Docker</span><span class="sxs-lookup"><span data-stu-id="1988a-104">Design Docker applications</span></span>

<span data-ttu-id="1988a-105">Chapitre 1 a introduit les concepts fondamentaux concernant les conteneurs et Docker.</span><span class="sxs-lookup"><span data-stu-id="1988a-105">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="1988a-106">Cette information est le niveau de base des informations que vous avez besoin pour commencer.</span><span class="sxs-lookup"><span data-stu-id="1988a-106">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="1988a-107">Toutefois, les applications d’entreprise peuvent être complexes et composé de plusieurs services au lieu d’un seul service ou le conteneur.</span><span class="sxs-lookup"><span data-stu-id="1988a-107">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="1988a-108">Pour les cas d’utilisation facultative, vous devez connaître les autres approches de conception, telles que les Architecture orientée services (SOA) et les concepts de microservices plus avancées et conteneur concepts d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="1988a-108">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="1988a-109">La portée de ce document n’est pas limitée à microservices mais un cycle de vie application Docker, par conséquent, il ne pas Explorer architecture microservices en profondeur, car vous également pourrez utiliser des conteneurs et Docker avec São régulière, les tâches en arrière-plan ou les tâches, ou même avec les approches de déploiement d’application monolithique.</span><span class="sxs-lookup"><span data-stu-id="1988a-109">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="1988a-110">Toutefois, avant d’entrer dans le cycle de vie d’application et DevOps, il est important de connaître la façon dont vous vous apprêtez à la conception et construire votre application et quels sont vos choix de conception.</span><span class="sxs-lookup"><span data-stu-id="1988a-110">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1988a-111">[Précédente] (index.md) [suivant] (commun-conteneur-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="1988a-111">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
