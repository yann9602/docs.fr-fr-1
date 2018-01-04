---
title: "Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61231715a24978e7fe57b2c9e87e7968dc0fdbc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="7509f-102">Interfaces d'hébergement du CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="7509f-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="7509f-103">Cette section décrit les interfaces non managées hôtes peuvent utiliser pour intégrer le common language runtime (CLR) dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]et les versions ultérieures dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="7509f-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="7509f-104">Ces interfaces fournissent des méthodes pour un ordinateur hôte configurer et charger le runtime dans un processus.</span><span class="sxs-lookup"><span data-stu-id="7509f-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="7509f-105">En commençant par le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], l’hébergement de toutes les interfaces ont les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="7509f-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="7509f-106">Elles utilisent la gestion de la durée de vie (`AddRef` et `Release`), l’encapsulation (contexte implicite) et `QueryInterface` à partir de COM.</span><span class="sxs-lookup"><span data-stu-id="7509f-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="7509f-107">Elles n’utilisent pas les types COM tels que `BSTR`, `SAFEARRAY`, ou `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="7509f-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="7509f-108">Aucun modèle cloisonné, d’agrégation, ou l’activation de Registre qui utilisent la [fonction CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).</span><span class="sxs-lookup"><span data-stu-id="7509f-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7509f-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7509f-109">In This Section</span></span>  
 [<span data-ttu-id="7509f-110">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="7509f-111">Fournit des méthodes qui inspectent mémoire et l’utilisation de l’UC d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="7509f-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="7509f-112">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="7509f-113">Permet à l’hôte spécifier le Gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="7509f-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="7509f-114">ICLRGCManager2, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="7509f-115">Fournit la [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) (méthode), ce qui permet à un hôte définir la taille du segment garbage collection et la taille maximale de la génération du système de garbage collection 0 pour les valeurs supérieure à `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="7509f-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="7509f-116">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="7509f-117">Fournit des méthodes qui retournent une version spécifique du CLR, répertorient tous les installés, répertorient tous les runtimes in-process, retournent l’interface d’activation et découvrir la version CLR utilisée pour compiler un assembly.</span><span class="sxs-lookup"><span data-stu-id="7509f-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="7509f-118">ICLRMetaHostPolicy, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="7509f-119">Fournit la [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) méthode qui fournit une interface CLR selon des critères de stratégie assembly managé et la version des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="7509f-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="7509f-120">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="7509f-121">Fournit des méthodes qui retournent des informations sur un runtime spécifique, y compris la version, le répertoire et l’état de charge.</span><span class="sxs-lookup"><span data-stu-id="7509f-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="7509f-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="7509f-123">Fournit des fonctions statiques globales de base pour la signature des assemblys avec des noms forts.</span><span class="sxs-lookup"><span data-stu-id="7509f-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="7509f-124">Tous les [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) méthodes retournent des valeurs HRESULT COM standard.</span><span class="sxs-lookup"><span data-stu-id="7509f-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="7509f-125">ICLRStrongName2, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="7509f-126">Fournit la possibilité de créer des noms forts dans le groupe de SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).</span><span class="sxs-lookup"><span data-stu-id="7509f-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="7509f-127">ICLRTask2, interface</span><span class="sxs-lookup"><span data-stu-id="7509f-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="7509f-128">Fournit toutes les fonctionnalités de la [ICLRTask (Interface)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); en outre, fournit des méthodes qui permettent d’abandons de threads pour être retardée sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="7509f-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7509f-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="7509f-129">Related Sections</span></span>  
 [<span data-ttu-id="7509f-130">Coclasses et interfaces d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="7509f-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="7509f-131">Décrit les interfaces d’hébergement fournis avec les versions de .NET Framework 1.0 et 1.1.</span><span class="sxs-lookup"><span data-stu-id="7509f-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="7509f-132">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="7509f-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="7509f-133">Décrit les interfaces d’hébergement fournis avec les versions de .NET Framework 2.0, 3.0 et 3.5.</span><span class="sxs-lookup"><span data-stu-id="7509f-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="7509f-134">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="7509f-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="7509f-135">Présente l’hébergement dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7509f-135">Introduces hosting in the .NET Framework.</span></span>
