---
title: "Migrer vers les scénarios de cloud hybride"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Migrer vers les scénarios de cloud hybride"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.openlocfilehash: 7394d0fd208e131b4e683298f6ca31a9eddade28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="2c14f-103">Migrer vers les scénarios de cloud hybride</span><span class="sxs-lookup"><span data-stu-id="2c14f-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="2c14f-104">Certaines organisations et les entreprises ne peut pas migrer certaines de leurs applications vers les clouds publics tels que Microsoft Azure, ou n’importe quel autre cloud public en raison des réglementations ou leurs propres stratégies.</span><span class="sxs-lookup"><span data-stu-id="2c14f-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="2c14f-105">Toutefois, il est probable que toute organisation peut bénéficier de l’utilisation de certaines de leurs applications dans le cloud public et autres applications locales.</span><span class="sxs-lookup"><span data-stu-id="2c14f-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="2c14f-106">Mais l’excès de complexité dans les environnements en raison des différentes plateformes et technologies utilisées dans des clouds publics et les environnements sur site risque d’un environnement mixte.</span><span class="sxs-lookup"><span data-stu-id="2c14f-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="2c14f-107">Microsoft fournit la meilleure solution de cloud hybride, une dans laquelle vous pouvez optimiser vos ressources existantes sur site et dans le cloud public, alors que vous vous assurez que dans un cloud hybride Azure.</span><span class="sxs-lookup"><span data-stu-id="2c14f-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="2c14f-108">Vous pouvez optimiser les compétences et obtenir une approche unifiée flexible pour la création d’applications qui peuvent s’exécuter dans le cloud ou localement, grâce à Azure pile (local) et Azure (nuage public).</span><span class="sxs-lookup"><span data-stu-id="2c14f-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="2c14f-109">Lorsqu’il s’agit de sécurité, vous pouvez centraliser la gestion et sécurité sur votre cloud hybride.</span><span class="sxs-lookup"><span data-stu-id="2c14f-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="2c14f-110">Vous pouvez contrôler tous les éléments multimédias, à partir de votre centre de données dans le cloud, en fournissant une authentification unique sur local et des applications de cloud.</span><span class="sxs-lookup"><span data-stu-id="2c14f-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="2c14f-111">Pour cela en étendant Active Directory à un cloud hybride et à l’aide de la gestion d’identité.</span><span class="sxs-lookup"><span data-stu-id="2c14f-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="2c14f-112">Enfin, vous pouvez distribuer et analyser les données en toute transparence, utiliser les mêmes langages de requête pour les ressources de cloud et locales et appliquer analytique et la profondeur d’apprentissage dans Azure pour enrichir vos données, quelle que soit sa source.</span><span class="sxs-lookup"><span data-stu-id="2c14f-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="2c14f-113">Pile Azure</span><span class="sxs-lookup"><span data-stu-id="2c14f-113">Azure Stack</span></span>

<span data-ttu-id="2c14f-114">Pile Azure est une plateforme de cloud hybride qui vous permet de fournir des services Azure à partir du centre de données de votre organisation.</span><span class="sxs-lookup"><span data-stu-id="2c14f-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="2c14f-115">Pile Azure est conçu pour prendre en charge de nouvelles options pour vos applications modernes dans des scénarios clés, telles que le bord et des environnements non connectées ou des exigences de conformité et de sécurité spécifiques de réunion.</span><span class="sxs-lookup"><span data-stu-id="2c14f-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="2c14f-116">Figure 4-13 montre une vue d’ensemble de la plateforme de cloud hybride true offertes par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2c14f-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Plateforme de cloud hybride de Microsoft avec la pile d’Azure et Azure](./media/image13.jpg)

> <span data-ttu-id="2c14f-118">**Figure 4-13.**</span><span class="sxs-lookup"><span data-stu-id="2c14f-118">**Figure 4-13.**</span></span> <span data-ttu-id="2c14f-119">Plateforme de cloud hybride de Microsoft avec la pile d’Azure et Azure</span><span class="sxs-lookup"><span data-stu-id="2c14f-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="2c14f-120">Pile Azure est proposé dans les deux options de déploiement pour répondre à vos besoins :</span><span class="sxs-lookup"><span data-stu-id="2c14f-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="2c14f-121">Pile Azure les systèmes intégrés</span><span class="sxs-lookup"><span data-stu-id="2c14f-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="2c14f-122">Kit de développement de pile Azure</span><span class="sxs-lookup"><span data-stu-id="2c14f-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="2c14f-123">Pile Azure les systèmes intégrés</span><span class="sxs-lookup"><span data-stu-id="2c14f-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="2c14f-124">Systèmes de pile intégré Azure sont offerts par un partenariat de partenaires Microsoft et de matériel.</span><span class="sxs-lookup"><span data-stu-id="2c14f-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="2c14f-125">Le partenariat crée une solution qui offre à rythme cloud innovation qui est équilibrée avec simplicité de gestion.</span><span class="sxs-lookup"><span data-stu-id="2c14f-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="2c14f-126">Car Azure pile est proposé comme un système intégré de matériel et logiciel, vous obtenez la quantité exacte de flexibilité et de contrôle, lors de l’adoption toujours de l’innovation à partir du cloud.</span><span class="sxs-lookup"><span data-stu-id="2c14f-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="2c14f-127">Les systèmes de pile intégré Azure de plage de taille de 4 à 12 nœuds et prise en charge conjointement par le partenaire de matériel et Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2c14f-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="2c14f-128">Systèmes de pile Azure intégré permet d’implémenter de nouveaux scénarios pour vos charges de travail de production.</span><span class="sxs-lookup"><span data-stu-id="2c14f-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="2c14f-129">Kit de développement de pile Azure</span><span class="sxs-lookup"><span data-stu-id="2c14f-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="2c14f-130">Kit de développement Microsoft Azure pile est un déploiement à un seul nœud de pile Azure, ce qui vous permet d’évaluer et d’en savoir plus sur la pile de Azure.</span><span class="sxs-lookup"><span data-stu-id="2c14f-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="2c14f-131">Vous pouvez également utiliser le Kit de développement de pile Azure comme environnement de développement, où vous pouvez développer à l’aide des API et des outils qui sont compatibles avec Azure.</span><span class="sxs-lookup"><span data-stu-id="2c14f-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="2c14f-132">Kit de développement Azure pile n’est pas destinée à être utilisé comme un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="2c14f-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2c14f-133">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2c14f-133">Additional resources</span></span>

-   <span data-ttu-id="2c14f-134">**Cloud hybride Azure**</span><span class="sxs-lookup"><span data-stu-id="2c14f-134">**Azure hybrid cloud**</span></span>

    [<span data-ttu-id="2c14f-135">https://www.Microsoft.com/cloud-Platform/Hybrid-cloud</span><span class="sxs-lookup"><span data-stu-id="2c14f-135">https://www.microsoft.com/cloud-platform/hybrid-cloud</span></span>](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="2c14f-136">**Pile Azure**</span><span class="sxs-lookup"><span data-stu-id="2c14f-136">**Azure Stack**</span></span>

    [<span data-ttu-id="2c14f-137">https://Azure.Microsoft.com/Overview/Azure-Stack/</span><span class="sxs-lookup"><span data-stu-id="2c14f-137">https://azure.microsoft.com/overview/azure-stack/</span></span>](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="2c14f-138">**Comptes de Service Active Directory pour les conteneurs Windows**</span><span class="sxs-lookup"><span data-stu-id="2c14f-138">**Active Directory Service Accounts for Windows Containers**</span></span>

    [<span data-ttu-id="2c14f-139">https://docs.Microsoft.com/Virtualization/windowscontainers/Manage-Containers/Manage-ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="2c14f-139">https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="2c14f-140">**Créer un conteneur avec prise en charge d’Active Directory**</span><span class="sxs-lookup"><span data-stu-id="2c14f-140">**Create a container with Active Directory support**</span></span>

    [<span data-ttu-id="2c14f-141">https://blogs.msdn.Microsoft.com/containerstuff/2017/01/30/Create-a-Container-with-Active-Directory-support/</span><span class="sxs-lookup"><span data-stu-id="2c14f-141">https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/</span></span>](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="2c14f-142">**Le Gestionnaire de licences Azure hybride avantage**</span><span class="sxs-lookup"><span data-stu-id="2c14f-142">**Azure Hybrid Benefit licensing**</span></span>

    [<span data-ttu-id="2c14f-143">https://Azure.Microsoft.com/Pricing/Hybrid-Use-Benefit/</span><span class="sxs-lookup"><span data-stu-id="2c14f-143">https://azure.microsoft.com/pricing/hybrid-use-benefit/</span></span>](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="2c14f-144">[Précédent](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Suivant](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="2c14f-144">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
