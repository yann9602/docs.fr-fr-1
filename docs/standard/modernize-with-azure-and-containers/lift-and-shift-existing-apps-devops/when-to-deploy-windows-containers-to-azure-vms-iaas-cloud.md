---
title: "Moment de déployer des conteneurs Windows aux ordinateurs virtuels de Azure (IaaS cloud)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Moment de déployer des conteneurs Windows aux ordinateurs virtuels de Azure (IaaS cloud)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 832faed135d5b8ec9f8ad0a6ca82b5fac0273284
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a><span data-ttu-id="71d32-103">Moment de déployer des conteneurs Windows aux ordinateurs virtuels de Azure (IaaS cloud)</span><span class="sxs-lookup"><span data-stu-id="71d32-103">When to deploy Windows Containers to Azure VMs (IaaS cloud)</span></span>

<span data-ttu-id="71d32-104">Si votre organisation est à l’aide de machines virtuelles Azure, même si vous utilisez également des conteneurs Windows, vous travaillez toujours avec IaaS.</span><span class="sxs-lookup"><span data-stu-id="71d32-104">If your organization is using Azure VMs, even if you are also using Windows Containers, you are still dealing with IaaS.</span></span> <span data-ttu-id="71d32-105">Cela signifie que qui traite des opérations d’infrastructure, des correctifs de système d’exploitation de la machine virtuelle et complexité de l’infrastructure pour les applications hautement évolutives lorsque vous avez besoin déployer sur plusieurs machines virtuelles dans une infrastructure à charge équilibrée.</span><span class="sxs-lookup"><span data-stu-id="71d32-105">That means that dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications when you need to deploy to multiple VMs in a load balanced infrastructure.</span></span> <span data-ttu-id="71d32-106">Les principaux scénarios pour l’utilisation de conteneurs Windows dans une machine virtuelle Azure sont :</span><span class="sxs-lookup"><span data-stu-id="71d32-106">The main scenarios for using Windows Containers in an Azure VM are:</span></span>

-   <span data-ttu-id="71d32-107">**Environnement de développement/test**: machine virtuelle de A dans le cloud est idéale pour le développement et de test dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="71d32-107">**Dev/test environment**: A VM in the cloud is perfect for development and testing in the cloud.</span></span> <span data-ttu-id="71d32-108">Vous pouvez rapidement créer ou arrêt de l’environnement en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="71d32-108">You can rapidly create or stop the environment depending on your needs.</span></span>

-   <span data-ttu-id="71d32-109">**Évolutivité de petite et moyenne taille doit**: dans les scénarios où vous devrez peut-être que quelques exemples d’ordinateurs virtuels pour votre environnement de production, la gestion d’un petit nombre de machines virtuelles peut être économique jusqu'à ce que vous pouvez déplacer vers des environnements PaaS plus avancées, telles qu’orchestrators.</span><span class="sxs-lookup"><span data-stu-id="71d32-109">**Small and medium scalability needs**: In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced PaaS environments, like orchestrators.</span></span>

-   <span data-ttu-id="71d32-110">**Environnement de production avec les outils de déploiement existants**: vous pouvez déplacer à partir d’un environnement local dans lequel vous avez investi dans les outils pour effectuer des déploiements complexes à des machines virtuelles ou les serveurs de récupération complète (comme Puppet ou outils similaires).</span><span class="sxs-lookup"><span data-stu-id="71d32-110">**Production environment with existing deployment tools**: You might be moving from an on-premises environment in which you have invested in tools to make complex deployments to VMs or bare-metal servers (like Puppet or similar tools).</span></span> <span data-ttu-id="71d32-111">Pour déplacer vers le cloud avec des modifications mineures par rapport aux procédures de déploiement environnement de production, vous pourrez continuer à utiliser ces outils pour déployer des machines virtuelles Azure.</span><span class="sxs-lookup"><span data-stu-id="71d32-111">To move to the cloud with minimal changes to production environment deployment procedures, you might continue to use those tools to deploy to Azure VMs.</span></span> <span data-ttu-id="71d32-112">Toutefois, vous souhaiterez utiliser des conteneurs Windows en tant que l’unité de déploiement pour améliorer l’expérience de déploiement.</span><span class="sxs-lookup"><span data-stu-id="71d32-112">However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="71d32-113">[Précédent](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Suivant](when-to-deploy-windows-containers-to-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="71d32-113">[Previous](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[Next](when-to-deploy-windows-containers-to-service-fabric.md)</span></span>
