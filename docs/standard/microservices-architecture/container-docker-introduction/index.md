---
title: "Introduction aux conteneurs et à Docker"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Introduction aux conteneurs et à Docker"
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
ms.openlocfilehash: 8809ae41609ff0e2d2fc969d412cb5edc8939653
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="25cfc-104">Introduction aux conteneurs et à Docker</span><span class="sxs-lookup"><span data-stu-id="25cfc-104">Introduction to Containers and Docker</span></span>

<span data-ttu-id="25cfc-105">La mise en conteneur est une approche de développement de logiciels qui consiste à empaqueter une application ou un service, ses dépendances et sa configuration (extraits sous forme de fichiers manifeste de déploiement) sous forme d’image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="25cfc-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="25cfc-106">L’application en conteneur peut être testée en tant qu’unité et déployée sous forme d’instance d’image de conteneur sur le système d’exploitation (SE) hôte.</span><span class="sxs-lookup"><span data-stu-id="25cfc-106">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="25cfc-107">De la même manière que les conteneurs de transport permettent de transporter des marchandises par bateau, par train ou par camion indépendamment de la nature de la cargaison, les conteneurs logiciels agissent comme une unité logicielle standard qui peut contenir du code et des dépendances différents.</span><span class="sxs-lookup"><span data-stu-id="25cfc-107">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="25cfc-108">Cette façon de mettre les logiciels en conteneur permet aux développeurs et aux informaticiens de les déployer dans les environnements avec peu ou pas de modifications.</span><span class="sxs-lookup"><span data-stu-id="25cfc-108">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="25cfc-109">Par ailleurs, les conteneurs isolent les applications les unes des autres sur un SE partagé.</span><span class="sxs-lookup"><span data-stu-id="25cfc-109">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="25cfc-110">Les applications en conteneur s’exécutent sur un hôte de conteneurs qui à son tour s’exécute sur le SE (Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="25cfc-110">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="25cfc-111">Par conséquent, les conteneurs ont un encombrement bien moindre que les images de machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="25cfc-111">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="25cfc-112">Chaque conteneur peut exécuter une application web ou un service dans son intégralité, comme l’illustre la figure 2-1.</span><span class="sxs-lookup"><span data-stu-id="25cfc-112">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="25cfc-113">Dans cet exemple, l’hôte Docker est un hôte de conteneurs, et App1, App2, Svc 1 et Svc 2 sont des applications ou des services en conteneur.</span><span class="sxs-lookup"><span data-stu-id="25cfc-113">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![](./media/image1.png)

<span data-ttu-id="25cfc-114">**Figure 2-1** :</span><span class="sxs-lookup"><span data-stu-id="25cfc-114">**Figure 2-1**.</span></span> <span data-ttu-id="25cfc-115">plusieurs conteneurs s’exécutant sur un hôte de conteneurs</span><span class="sxs-lookup"><span data-stu-id="25cfc-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="25cfc-116">L’autre avantage de la mise en conteneur est l’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="25cfc-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="25cfc-117">Vous pouvez rapidement monter en charge en créant des conteneurs pour des tâches à court terme.</span><span class="sxs-lookup"><span data-stu-id="25cfc-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="25cfc-118">Du point de vue de l’application, instancier une image (c.-à-d., créer un conteneur) revient à instancier un processus comme un service ou une application web.</span><span class="sxs-lookup"><span data-stu-id="25cfc-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="25cfc-119">Cependant, dans un souci de fiabilité, quand il s’agit d’exécuter plusieurs instances d’une même image sur plusieurs serveurs hôtes, il est en principe préférable que chaque conteneur (instance d’image) s’exécute sur un serveur hôte différent ou sur une machine virtuelle dans différents domaines d’erreur.</span><span class="sxs-lookup"><span data-stu-id="25cfc-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="25cfc-120">Pour résumer, les conteneurs offrent les avantages de l’isolation, de la portabilité, de l’agilité, de l’extensibilité et du contrôle dans l’ensemble du flux de travail du cycle de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="25cfc-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="25cfc-121">L’avantage le plus important est l’isolation entre le développement et les opérations.</span><span class="sxs-lookup"><span data-stu-id="25cfc-121">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="25cfc-122">[Précédent] (../index.md) [Suivant] (docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="25cfc-122">[Previous] (../index.md) [Next] (docker-defined.md)</span></span>
