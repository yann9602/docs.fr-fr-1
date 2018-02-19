---
title: "Présentation des conteneurs et de Docker"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 31260dc372f87305ad9d4556673a1cc94e24bfcc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="ee6bd-104">Présentation des conteneurs et de Docker</span><span class="sxs-lookup"><span data-stu-id="ee6bd-104">Introduction to containers and Docker</span></span>

<span data-ttu-id="ee6bd-105">La mise en conteneur est une approche de développement de logiciels qui consiste à empaqueter une application ou un service, ses dépendances et sa configuration (extraits sous forme de fichiers manifeste de déploiement) sous forme d’image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="ee6bd-106">Vous pouvez ensuite tester l’application en conteneur en tant qu’unité et la déployer sous forme d’instance d’image de conteneur sur le système d’exploitation hôte.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-106">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="ee6bd-107">De la même manière que l’industrie du transport utilise des conteneurs normalisés pour transporter des marchandises par bateau, train ou camion, et ce indépendamment de la nature de la cargaison, les conteneurs logiciels agissent comme une unité logicielle standard qui peut contenir du code et des dépendances différents.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-107">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="ee6bd-108">Le fait de placer des logiciels dans des conteneurs permet aux développeurs et informaticiens de déployer ces conteneurs dans les environnements avec peu ou pas de modifications.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-108">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="ee6bd-109">Les conteneurs isolent également les applications les unes des autres sur un système d’exploitation partagé.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-109">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="ee6bd-110">Les applications en conteneur s’exécutent sur un hôte de conteneurs qui à son tour s’exécute sur le système d’exploitation (Linux ou Windows).</span><span class="sxs-lookup"><span data-stu-id="ee6bd-110">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="ee6bd-111">Les conteneurs ont donc un encombrement bien moindre que les images de machine virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-111">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="ee6bd-112">Chaque conteneur peut exécuter un service ou une application web dans son intégralité, comme l’illustre la figure 1-1.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-112">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="ee6bd-113">Figure 1-1 : Plusieurs conteneurs s’exécutant sur un hôte de conteneurs</span><span class="sxs-lookup"><span data-stu-id="ee6bd-113">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="ee6bd-114">Dans cet exemple, l’hôte Docker est un hôte de conteneurs, et App1, App2, Svc 1 et Svc 2 sont des applications ou des services en conteneur.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-114">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="ee6bd-115">L’autre avantage qui dérive de la mise en conteneur est la scalabilité.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="ee6bd-116">Vous pouvez rapidement monter en charge en créant des conteneurs pour des tâches à court terme.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-116">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="ee6bd-117">Du point de vue de l’application, *instancier une image* (c.-à-d., créer un conteneur) revient à instancier un processus comme un service ou une application web.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-117">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="ee6bd-118">Cependant, dans un souci de fiabilité, quand il s’agit d’exécuter plusieurs instances d’une même image sur plusieurs serveurs hôtes, il est en principe préférable que chaque conteneur (instance d’image) s’exécute sur un serveur hôte différent ou sur une machine virtuelle dans différents domaines d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="ee6bd-119">Pour résumer, les conteneurs offrent les avantages de l’isolation, de la portabilité, de l’agilité, de l’extensibilité et du contrôle dans l’ensemble du flux de travail du cycle de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="ee6bd-120">L’avantage le plus important est l’isolation entre le développement et les opérations.</span><span class="sxs-lookup"><span data-stu-id="ee6bd-120">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ee6bd-121">[Suivant] (what-is-docker.md)</span><span class="sxs-lookup"><span data-stu-id="ee6bd-121">[Next] (what-is-docker.md)</span></span>
