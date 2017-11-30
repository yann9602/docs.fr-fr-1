---
title: "Conseils généraux"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conseils généraux"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a><span data-ttu-id="5b662-104">Conseils généraux</span><span class="sxs-lookup"><span data-stu-id="5b662-104">General guidance</span></span>

<span data-ttu-id="5b662-105">Cette section fournit un résumé des choix .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b662-105">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="5b662-106">Nous fournir plus de détails sur ces options dans les sections qui suivent.</span><span class="sxs-lookup"><span data-stu-id="5b662-106">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="5b662-107">Vous devez utiliser .NET Core, avec les conteneurs Windows ou Linux pour votre application de serveur Docker en conteneur lorsque :</span><span class="sxs-lookup"><span data-stu-id="5b662-107">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="5b662-108">vous avez des besoins multiplateformes ;</span><span class="sxs-lookup"><span data-stu-id="5b662-108">You have cross-platform needs.</span></span> <span data-ttu-id="5b662-109">Par exemple, vous souhaitez utiliser les conteneurs Linux et Windows.</span><span class="sxs-lookup"><span data-stu-id="5b662-109">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="5b662-110">Architecture de votre application repose sur microservices.</span><span class="sxs-lookup"><span data-stu-id="5b662-110">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="5b662-111">Vous devez démarrer rapide des conteneurs et un faible encombrement mémoire par atteindre une meilleure densité ou les conteneurs plus par unité de matériel afin de réduire les coûts.</span><span class="sxs-lookup"><span data-stu-id="5b662-111">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="5b662-112">En bref, lorsque vous créez des applications .NET en conteneur, vous devez considérer .NET Core comme l’option par défaut.</span><span class="sxs-lookup"><span data-stu-id="5b662-112">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="5b662-113">Il présente de nombreux avantages et répond le mieux à la philosophie de conteneurs et le style de travail.</span><span class="sxs-lookup"><span data-stu-id="5b662-113">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="5b662-114">Un autre avantage de l’utilisation de .NET Core est que vous pouvez exécuter des versions côte à côte du .NET pour les applications dans le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5b662-114">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="5b662-115">Cet avantage est plus important pour les serveurs ou ordinateurs virtuels qui n’utilisent pas de conteneurs, étant donné que les conteneurs d’isoler les versions de .NET dont l’application a besoin.</span><span class="sxs-lookup"><span data-stu-id="5b662-115">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="5b662-116">(Tant qu’ils sont compatibles avec le système d’exploitation sous-jacent.)</span><span class="sxs-lookup"><span data-stu-id="5b662-116">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="5b662-117">Vous devez utiliser .NET Framework, les conteneurs Windows pour votre application de serveur Docker en conteneur lorsque :</span><span class="sxs-lookup"><span data-stu-id="5b662-117">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="5b662-118">Actuellement, votre application utilise le .NET Framework et a des dépendances fortes sur Windows.</span><span class="sxs-lookup"><span data-stu-id="5b662-118">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="5b662-119">Vous devez utiliser les API Windows qui ne sont pas pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b662-119">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="5b662-120">Vous devez utiliser les bibliothèques .NET de tiers ou les packages NuGet qui ne sont pas disponibles pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b662-120">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="5b662-121">À l’aide de .NET Framework sur Docker peut améliorer votre expérience de déploiement en réduisant les problèmes de déploiement.</span><span class="sxs-lookup"><span data-stu-id="5b662-121">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="5b662-122">Cela [ *scénario « de courbes d’élévation et MAJ »* ](https://aka.ms/liftandshiftwithcontainersebook) est important pour containerizing les applications héritées qui ont été développées à l’origine avec le .NET Framework classiques, telles que ASP.NET WebForms, MVC web apps ou WCF ( Services Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="5b662-122">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5b662-123">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5b662-123">Additional resources</span></span>

-   <span data-ttu-id="5b662-124">**livres : moderniser des applications .NET Framework existantes avec Azure et les conteneurs Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="5b662-124">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="5b662-125">**Exemples d’applications : modernisation des applications web ASP.NET héritées à l’aide de conteneurs Windows**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="5b662-125">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5b662-126">[Précédente] (index.md) [suivant] (net-core-conteneur-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="5b662-126">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>
