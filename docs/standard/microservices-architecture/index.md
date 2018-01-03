---
title: Microservices .NET. Architecture pour les applications .NET en conteneur
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Avant-propos"
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
ms.openlocfilehash: 87a4b9f2bb076eccfa79e2951e509a35461ff257
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="f3890-105">Microservices .NET.</span><span class="sxs-lookup"><span data-stu-id="f3890-105">.NET Microservices.</span></span> <span data-ttu-id="f3890-106">Architecture pour les applications .NET en conteneur</span><span class="sxs-lookup"><span data-stu-id="f3890-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="f3890-107">TÉLÉCHARGEMENT disponible à l’adresse : <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="f3890-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="f3890-108">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="f3890-108">PUBLISHED BY</span></span>

<span data-ttu-id="f3890-109">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3890-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="f3890-110">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f3890-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="f3890-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="f3890-111">One Microsoft Way</span></span>

<span data-ttu-id="f3890-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="f3890-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="f3890-113">Copyright © 2017 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="f3890-113">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="f3890-114">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="f3890-114">All rights reserved.</span></span> <span data-ttu-id="f3890-115">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="f3890-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="f3890-116">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="f3890-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="f3890-117">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="f3890-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="f3890-118">Certains exemples décrits dans ce document ne sont fournis qu’à titre d’illustration et sont purement fictifs.</span><span class="sxs-lookup"><span data-stu-id="f3890-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="f3890-119">Toute ressemblance ou tout lien avec le monde réel sont purement fortuits et involontaires.</span><span class="sxs-lookup"><span data-stu-id="f3890-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="f3890-120">Microsoft et les marques commerciales mentionnées dans la page web « Marques » de http://www.microsoft.com sont des marques du groupe de sociétés Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f3890-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="f3890-121">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="f3890-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="f3890-122">Le logo de Docker représentant une baleine est une marque déposée de Docker, Inc. Utilisé sous autorisation.</span><span class="sxs-lookup"><span data-stu-id="f3890-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="f3890-123">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="f3890-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="f3890-124">Coauteurs :</span><span class="sxs-lookup"><span data-stu-id="f3890-124">Co-Authors:</span></span>

> <span data-ttu-id="f3890-125">**Cesar de la Torre**, chef de projet senior, équipe produit .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="f3890-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="f3890-126">**Bill Wagner**, développeur de contenu senior, C+E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="f3890-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="f3890-127">**Mike Rousos**, ingénieur logiciel principal, équipe DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="f3890-128">Rédacteurs :</span><span class="sxs-lookup"><span data-stu-id="f3890-128">Editors:</span></span>

> <span data-ttu-id="f3890-129">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="f3890-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="f3890-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="f3890-130">**Steve Hoag**</span></span>

<span data-ttu-id="f3890-131">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="f3890-131">Participants and reviewers:</span></span>

> <span data-ttu-id="f3890-132">**Jeffrey Ritcher**, ingénieur logiciel partenaire, équipe Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-132">**Jeffrey Ritcher**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="f3890-133">**Jimmy Bogard**, architecte en chef chez Headspring</span><span class="sxs-lookup"><span data-stu-id="f3890-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="f3890-134">**Udi Dahan**, fondateur et PDG, Particular Software</span><span class="sxs-lookup"><span data-stu-id="f3890-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="f3890-135">**Jimmy Nilsson**, co-fondateur et PDG de Factor10</span><span class="sxs-lookup"><span data-stu-id="f3890-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="f3890-136">**Glenn Condron**, responsable de programme senior, équipe ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f3890-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="f3890-137">**Mark Fussell**, responsable principal de la gestion de projets, équipe Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="f3890-138">**Diego Vega**, responsable de la gestion de projets, équipe Entity Framework, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="f3890-139">**Barry Dorrans**, responsable de programme de sécurité senior</span><span class="sxs-lookup"><span data-stu-id="f3890-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="f3890-140">**Rowan Miller**, responsable de programme senior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="f3890-141">**Ankit Asthana**, responsable principal de la gestion de projets, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f3890-142">**Scott Hunter**, chef de projet directeur partenaire, équipe .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="f3890-143">**Dylan Reisenberger**, architecte et responsable de développement chez Polly</span><span class="sxs-lookup"><span data-stu-id="f3890-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="f3890-144">**Steve Smith**, artisan logiciel et formateur chez ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="f3890-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="f3890-145">**Ian Cooper**, architecte développement chez Brighter</span><span class="sxs-lookup"><span data-stu-id="f3890-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="f3890-146">**Unai Zorrilla**, architecte et responsable de développement chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="f3890-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="f3890-147">**Eduard Tomas**, responsable de développement chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="f3890-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="f3890-148">**Ramon Tomas**, développeur chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="f3890-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="f3890-149">**David Sanz**, développeur chez Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="f3890-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="f3890-150">**Javier Valero**, chef des opérations chez Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="f3890-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="f3890-151">**Pierre Millet**, consultant senior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="f3890-152">**Michael Friis**, chef de produit, Docker Inc.</span><span class="sxs-lookup"><span data-stu-id="f3890-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="f3890-153">**Charles Lowell**, ingénieur logiciel, équipe VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="f3890-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="f3890-154">Introduction</span><span class="sxs-lookup"><span data-stu-id="f3890-154">Introduction</span></span>

<span data-ttu-id="f3890-155">Les entreprises cherchent de plus en plus à réaliser des économies, à résoudre les problèmes de déploiement et à améliorer les opérations DevOps et de production en utilisant des conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f3890-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="f3890-156">Microsoft a fait preuve d’innovation dans le domaine des conteneurs pour Windows et Linux en créant des produits comme Azure Container Service et Azure Service Fabric et en formant des partenariats avec des acteurs phares du secteur tels que Docker, Mesosphere et Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="f3890-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="f3890-157">Ces produits offrent aux entreprises des solutions de conteneur qui leur permettent de créer et déployer des applications à la vitesse et à l’échelle du cloud, indépendamment de la plateforme ou des outils qu’elles ont choisi d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="f3890-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="f3890-158">Docker est en passe de devenir de facto le standard dans le domaine du conteneur, recueillant l’adhésion des éditeurs les plus en vue dans les écosystèmes Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="f3890-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="f3890-159">(Microsoft est l’un des principaux fournisseurs de cloud à se ranger du côté de Docker.) Dans l’avenir, Docker sera probablement omniprésent dans les centres de données cloud ou locaux.</span><span class="sxs-lookup"><span data-stu-id="f3890-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="f3890-160">Par ailleurs, l’architecture de [microservices](https://martinfowler.com/articles/microservices.html) est une approche qui devient importante pour les applications stratégiques distribuées.</span><span class="sxs-lookup"><span data-stu-id="f3890-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="f3890-161">Dans une architecture basée sur les microservices, l’application repose sur un ensemble de services qui peuvent être développés, testés, déployés et versionnés de manière indépendante.</span><span class="sxs-lookup"><span data-stu-id="f3890-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="f3890-162">À propos de ce guide</span><span class="sxs-lookup"><span data-stu-id="f3890-162">About this guide</span></span>

<span data-ttu-id="f3890-163">Ce guide est une introduction au développement d’applications basées sur les microservices et à la gestion de celles-ci au moyen de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="f3890-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="f3890-164">Il traite de la conception architecturale et des approches d’implémentation utilisant .NET Core et les conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="f3890-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="f3890-165">Pour faciliter la prise en main des conteneurs et des microservices, ce guide met en lumière une application de référence en conteneur basée sur des microservices que vous pouvez explorer.</span><span class="sxs-lookup"><span data-stu-id="f3890-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="f3890-166">L’exemple d’application est disponible sur le dépôt GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span><span class="sxs-lookup"><span data-stu-id="f3890-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="f3890-167">Ce guide livre des conseils de base en matière de développement et d’architecture au niveau de l’environnement de développement avec deux technologies mises en avant : Docker et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f3890-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="f3890-168">Notre objectif est que vous lisiez ce guide en pensant à la conception de votre application sans vous polariser sur l’infrastructure (cloud ou locale) de votre environnement de production.</span><span class="sxs-lookup"><span data-stu-id="f3890-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="f3890-169">Vous prendrez vos décisions concernant l’infrastructure plus tard, au moment de créer vos applications pour la production.</span><span class="sxs-lookup"><span data-stu-id="f3890-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="f3890-170">Par conséquent, ce guide se veut neutre concernant l’infrastructure et davantage centré sur l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="f3890-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="f3890-171">Après avoir examiné ce guide, votre prochaine étape consistera à vous familiariser avec les microservices prêts pour la production dans Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f3890-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="f3890-172">Sujets non abordés dans ce guide</span><span class="sxs-lookup"><span data-stu-id="f3890-172">What this guide does not cover</span></span>

<span data-ttu-id="f3890-173">Ce guide ne traite pas du cycle de vie des applications, de DevOps, des pipelines CI/CD, ni du travail d’équipe.</span><span class="sxs-lookup"><span data-stu-id="f3890-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="f3890-174">Le guide complémentaire intitulé [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft) porte essentiellement sur ce sujet.</span><span class="sxs-lookup"><span data-stu-id="f3890-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="f3890-175">Le présent guide ne fournit pas non plus de détails sur l’implémentation de l’infrastructure Azure, notamment sur les orchestrateurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f3890-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f3890-176">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f3890-176">Additional resources</span></span>

-   <span data-ttu-id="f3890-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (livre électronique téléchargeable) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="f3890-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="f3890-178">Public visé par ce guide</span><span class="sxs-lookup"><span data-stu-id="f3890-178">Who should use this guide</span></span>

<span data-ttu-id="f3890-179">Nous avons rédigé ce guide à l’intention des développeurs et des architectes de solutions qui n’ont pas d’expérience en matière développement d’applications Docker et d’architecture basée sur les microservices.</span><span class="sxs-lookup"><span data-stu-id="f3890-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="f3890-180">Ce guide s’adresse à vous si votre intention est d’apprendre à architecturer, concevoir et implémenter des applications de type preuve de concept avec les technologies de développement Microsoft (plus particulièrement .NET Core) et des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="f3890-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="f3890-181">Ce guide saura aussi vous intéresser si vous êtes un décideur technique, tel qu’un architecte d’entreprise, désireux d’avoir une vue d’ensemble de l’architecture et des technologies avant d’opter pour telle ou telle approche d’application distribuée nouvelle et moderne.</span><span class="sxs-lookup"><span data-stu-id="f3890-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="f3890-182">Comment utiliser ce guide</span><span class="sxs-lookup"><span data-stu-id="f3890-182">How to use this guide</span></span>

<span data-ttu-id="f3890-183">La première partie de ce guide offre une présentation des conteneurs Docker, explique comment choisir entre .NET Core et le .NET Framework comme framework de développement et propose une vue d’ensemble des microservices.</span><span class="sxs-lookup"><span data-stu-id="f3890-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="f3890-184">Ce contenu s’adresse aux architectes et aux décideurs techniques qui souhaitent obtenir une vue d’ensemble, mais qui n’ont pas besoin de s’attarder sur les détails d’implémentation de code.</span><span class="sxs-lookup"><span data-stu-id="f3890-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="f3890-185">La deuxième partie du guide commence par la section [Processus de développement des applications basées sur Docker](#ch_dev_process_for_docker_based_apps).</span><span class="sxs-lookup"><span data-stu-id="f3890-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="f3890-186">Elle porte essentiellement sur les modèles de développement et de microservices pour l’implémentation d’applications utilisant .NET Core et Docker.</span><span class="sxs-lookup"><span data-stu-id="f3890-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="f3890-187">Cette section intéressera plus particulièrement les développeurs et les architectes qui souhaitent se concentrer sur le code et les détails concernant les modèles et l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="f3890-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="f3890-188">Application de référence basée sur des conteneurs et des microservices : eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="f3890-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="f3890-189">L’application eShopOnContainers est une application de référence pour .NET Core et les microservices qui a été conçue pour être déployée en utilisant des conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="f3890-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="f3890-190">L’application est constituée de divers sous-systèmes, notamment de plusieurs frontends d’interface utilisateur d’e-store (une application web et une application mobile native).</span><span class="sxs-lookup"><span data-stu-id="f3890-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="f3890-191">Elle inclut aussi les microservices et les conteneurs backend pour toutes les opérations côté serveur nécessaires.</span><span class="sxs-lookup"><span data-stu-id="f3890-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="f3890-192">Le code source de cette application basée sur des microservices et des conteneurs est open source et disponible sur le dépôt GitHub [eShopOnContainers](http://aka.ms/MicroservicesArchitecture).</span><span class="sxs-lookup"><span data-stu-id="f3890-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="f3890-193">Envoyez-nous vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="f3890-193">Send us your feedback!</span></span>

<span data-ttu-id="f3890-194">Nous avons rédigé ce guide pour vous aider à comprendre l’architecture des applications en conteneur et des microservices dans .NET.</span><span class="sxs-lookup"><span data-stu-id="f3890-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="f3890-195">Le guide et l’application de référence associée étant voués à évoluer, nous faisons bon accueil à vos commentaires !</span><span class="sxs-lookup"><span data-stu-id="f3890-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="f3890-196">Si vous avez des commentaires à formuler sur la façon dont ce guide peut être amélioré, communiquez-les nous à l’adresse :</span><span class="sxs-lookup"><span data-stu-id="f3890-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="f3890-197">[Suivant] (conteneur-docker-introduction/index.md)</span><span class="sxs-lookup"><span data-stu-id="f3890-197">[Next] (container-docker-introduction/index.md)</span></span>
