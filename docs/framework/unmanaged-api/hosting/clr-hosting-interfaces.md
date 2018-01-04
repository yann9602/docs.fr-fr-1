---
title: "Interfaces d'hébergement du CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fd954419f46313a239ddf5a309a646e3d2f1b9bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="a0bed-102">Interfaces d'hébergement du CLR</span><span class="sxs-lookup"><span data-stu-id="a0bed-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="a0bed-103">Cette section décrit les interfaces non managées hôtes peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="a0bed-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="a0bed-104">Les informations relatives à la version du .NET Framework 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a0bed-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="a0bed-105">Ces interfaces permettent à l’hôte de contrôler beaucoup plus d’aspects du runtime que les versions 1.0 et 1.1 et fournissent ainsi l’intégration entre le CLR et le modèle d’exécution de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="a0bed-106">Dans la version 1.0 et 1.1 du .NET Framework, le modèle d’hébergement activé un hôte non managé de charger le CLR dans un processus, de configurer certains paramètres et de recevoir des notifications d’événements.</span><span class="sxs-lookup"><span data-stu-id="a0bed-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="a0bed-107">Toutefois, en général, l’hôte et le CLR s’exécutaient indépendamment dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="a0bed-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="a0bed-108">Dans le .NET Framework version 2.0 et les versions ultérieures, des couches d’abstraction permettent à l’hôte fournit plusieurs ressources actuellement offertes par les types dans l’assembly Win32, et l’ensemble de fonctionnalités que l’hôte peut configurer.</span><span class="sxs-lookup"><span data-stu-id="a0bed-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0bed-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a0bed-109">In This Section</span></span>  
 [<span data-ttu-id="a0bed-110">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="a0bed-111">Fournit une méthode qui effectue un rappel pour un événement enregistré.</span><span class="sxs-lookup"><span data-stu-id="a0bed-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="a0bed-112">IApartmentCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="a0bed-113">Fournit des méthodes pour effectuer des rappels dans un thread cloisonné.</span><span class="sxs-lookup"><span data-stu-id="a0bed-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="a0bed-114">IAppDomainBinding, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="a0bed-115">Fournit des méthodes pour la configuration de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a0bed-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="a0bed-116">ICatalogServices, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="a0bed-117">Fournit des méthodes pour les services de catalogage.</span><span class="sxs-lookup"><span data-stu-id="a0bed-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="a0bed-118">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)</span><span class="sxs-lookup"><span data-stu-id="a0bed-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="a0bed-119">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="a0bed-120">Fournit des méthodes qui prennent en charge la communication entre l’hôte et le CLR sur les assemblys.</span><span class="sxs-lookup"><span data-stu-id="a0bed-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="a0bed-121">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="a0bed-122">Gère une liste d’assemblys qui sont chargés par le CLR et non par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="a0bed-123">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="a0bed-124">Fournit des méthodes pour l’hôte d’accéder à et de configurer différents aspects du CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="a0bed-125">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="a0bed-126">Fournit des méthodes qui permettent à un hôte à associer un ensemble de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="a0bed-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="a0bed-127">ICLRErrorReportingManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="a0bed-128">Fournit des méthodes qui permettent à l’hôte configurer des dumps de tas personnalisés pour le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="a0bed-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="a0bed-129">ICLRGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="a0bed-130">Fournit des méthodes qui permettent à un hôte d’interagir avec le système de garbage collection du CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="a0bed-131">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="a0bed-132">Fournit des méthodes pour l’hôte d’évaluer et de communiquer les modifications dans les informations de stratégie pour les assemblys.</span><span class="sxs-lookup"><span data-stu-id="a0bed-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="a0bed-133">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="a0bed-134">Permet à l’hôte bloquer les classes managées spécifiques, les méthodes, les propriétés et les champs de l’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="a0bed-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="a0bed-135">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="a0bed-136">Implémente une méthode de rappel qui permet à l’hôte informer le CLR de l’état des demandes d’e/s spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a0bed-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="a0bed-137">ICLRMemoryNotificationCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="a0bed-138">Permet à l’hôte de signaler des conditions de sollicitation de la mémoire à l’aide d’une approche similaire à celle de Win32 `CreateMemoryResourceNotification` (fonction).</span><span class="sxs-lookup"><span data-stu-id="a0bed-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="a0bed-139">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="a0bed-140">Fournit des méthodes qui permettent à l’hôte inscrire et désinscrire des rappels pour les événements du CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="a0bed-141">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="a0bed-142">Fournit des méthodes qui permettent à l’hôte spécifier les actions à entreprendre en cas de défaillances et des délais d’expiration de stratégie.</span><span class="sxs-lookup"><span data-stu-id="a0bed-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="a0bed-143">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="a0bed-144">Fournit des méthodes qui permettent à l’hôte d’obtenir les identités d’identification d’un assembly à l’aide des informations d’identité de l’assembly qui est internes au CLR, sans avoir à créer ou à comprendre cette identité.</span><span class="sxs-lookup"><span data-stu-id="a0bed-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="a0bed-145">ICLRReferenceAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="a0bed-146">Fournit des méthodes qui permettent à l’hôte de manipuler le jeu d’assemblys référencés par un fichier ou un flux à l’aide des données d’identité qui est internes au CLR, sans avoir à créer ou à comprendre ces identités.</span><span class="sxs-lookup"><span data-stu-id="a0bed-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="a0bed-147">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="a0bed-148">Fournit des fonctions semblables à [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), avec une méthode supplémentaire pour définir l’interface de contrôle hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="a0bed-149">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="a0bed-150">Fournit des méthodes pour l’ordinateur hôte pour obtenir des informations sur les tâches demandées et pour détecter les blocages dans son implémentation de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="a0bed-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="a0bed-151">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="a0bed-152">Fournit des méthodes qui permettent à l’hôte pour effectuer des demandes du CLR, ou pour fournir une notification au CLR sur la tâche associée.</span><span class="sxs-lookup"><span data-stu-id="a0bed-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="a0bed-153">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="a0bed-154">Fournit des méthodes qui permettent à l’hôte à demander explicitement que le CLR crée une tâche et obtenir la tâche en cours d’exécution et définir le langage géographique et la culture pour la tâche.</span><span class="sxs-lookup"><span data-stu-id="a0bed-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="a0bed-155">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="a0bed-156">Fournit des méthodes pour la validation des images (PE) exécutables portables et de rapports d’erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="a0bed-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="a0bed-157">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="a0bed-158">Fournit des méthodes pour la configuration du CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="a0bed-159">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="a0bed-160">Fournit des méthodes pour accéder au pool de threads.</span><span class="sxs-lookup"><span data-stu-id="a0bed-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="a0bed-161">IDebuggerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="a0bed-162">Fournit des méthodes pour obtenir des informations sur l’état des services de débogage.</span><span class="sxs-lookup"><span data-stu-id="a0bed-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="a0bed-163">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="a0bed-164">Fournit des méthodes pour notifier l’hôte sur le blocage et déblocage des threads par les services de débogage.</span><span class="sxs-lookup"><span data-stu-id="a0bed-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="a0bed-165">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="a0bed-166">Fournit des méthodes pour obtenir des informations sur le système de garbage collection et contrôler certains aspects du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a0bed-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="a0bed-167">IGCHost2, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="a0bed-168">Fournit la [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) méthode qui permet à un hôte définir la taille du segment garbage collection et la taille maximale de la génération du système de garbage collection zéro aux valeurs supérieur `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="a0bed-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="a0bed-169">IGCHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="a0bed-170">Fournit une méthode qui permet au garbage collector de demander à l’hôte de modifier les limites de mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="a0bed-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="a0bed-171">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="a0bed-172">Fournit des méthodes pour participer à la planification des threads qui seraient sinon bloqués pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a0bed-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="a0bed-173">IHostAssemblyManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="a0bed-174">Fournit des méthodes qui permettent à un hôte de spécifier des ensembles d’assemblys qui doivent être chargés par le CLR ou par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="a0bed-175">IHostAssemblyStore, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="a0bed-176">Fournit des méthodes qui permettent à un hôte de charger des assemblys et des modules indépendamment du CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="a0bed-177">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="a0bed-178">Fournit une représentation d’un événement de réinitialisation automatique implémenté par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="a0bed-179">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="a0bed-180">Fournit des méthodes pour configurer le chargement d’assemblys et pour déterminer quelles interfaces d’hébergement l’hôte prend en charge.</span><span class="sxs-lookup"><span data-stu-id="a0bed-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="a0bed-181">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="a0bed-182">Sert de représentation sous forme de l’hôte d’une section critique pour les threads.</span><span class="sxs-lookup"><span data-stu-id="a0bed-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="a0bed-183">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="a0bed-184">Fournit des méthodes qui notifier l’hôte d’événements dans le mécanisme de garbage collection implémentés par le CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="a0bed-185">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="a0bed-186">Fournit des méthodes qui permettent au CLR d’interagir avec les ports de terminaison d’e/s fournis par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="a0bed-187">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="a0bed-188">Fournit des méthodes pour le CLR demander des allocations fines à partir du tas via l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="a0bed-189">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="a0bed-190">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="a0bed-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="a0bed-191">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="a0bed-192">Fournit des méthodes pour le CLR effectuer des demandes de mémoire virtuelle via l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="a0bed-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="a0bed-193">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="a0bed-194">Fournit des méthodes qui informent l’hôte des actions que le CLR effectue en cas d’abandon, les délais d’attente ou d’échec.</span><span class="sxs-lookup"><span data-stu-id="a0bed-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="a0bed-195">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="a0bed-196">Permet de gérer les informations de contexte de sécurité implémentées par l’hôte au CLR.</span><span class="sxs-lookup"><span data-stu-id="a0bed-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="a0bed-197">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="a0bed-198">Fournit des méthodes qui permettent d’accéder à et contrôlent le contexte de sécurité du thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a0bed-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="a0bed-199">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="a0bed-200">Fournit une représentation d’un sémaphore implémenté par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="a0bed-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="a0bed-201">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="a0bed-202">Fournit des méthodes pour que le CLR crée des primitives de synchronisation en appelant l’hôte, au lieu d’utiliser les fonctions de synchronisation Win32.</span><span class="sxs-lookup"><span data-stu-id="a0bed-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="a0bed-203">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="a0bed-204">Fournit des méthodes qui permettent au CLR de communiquer avec l’hôte pour gérer les tâches.</span><span class="sxs-lookup"><span data-stu-id="a0bed-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="a0bed-205">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="a0bed-206">Fournit des méthodes qui permettent au CLR de travailler avec les tâches via l’hôte au lieu d’utiliser les fonctions de threading ou fiber de système d’exploitation standard.</span><span class="sxs-lookup"><span data-stu-id="a0bed-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="a0bed-207">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="a0bed-208">Fournit des méthodes pour le CLR pour configurer le pool de threads et en file d’attente des éléments de travail au pool de threads.</span><span class="sxs-lookup"><span data-stu-id="a0bed-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="a0bed-209">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="a0bed-210">Fournit des méthodes pour contrôler un objet managé.</span><span class="sxs-lookup"><span data-stu-id="a0bed-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="a0bed-211">« IObjectHandle »</span><span class="sxs-lookup"><span data-stu-id="a0bed-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="a0bed-212">Fournit une méthode pour désencapsuler les objets marshalés par valeur à partir de l’indirection.</span><span class="sxs-lookup"><span data-stu-id="a0bed-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="a0bed-213">ITypeName, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="a0bed-214">Fournit des méthodes pour obtenir des informations de nom de type.</span><span class="sxs-lookup"><span data-stu-id="a0bed-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="a0bed-215">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)</span><span class="sxs-lookup"><span data-stu-id="a0bed-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="a0bed-216">ITypeNameBuilder, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="a0bed-217">Fournit des méthodes pour la création d’un nom de type.</span><span class="sxs-lookup"><span data-stu-id="a0bed-217">Provides methods for building a type name.</span></span> <span data-ttu-id="a0bed-218">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)</span><span class="sxs-lookup"><span data-stu-id="a0bed-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="a0bed-219">ITypeNameFactory, interface</span><span class="sxs-lookup"><span data-stu-id="a0bed-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="a0bed-220">Fournit des méthodes pour détruire un nom de type.</span><span class="sxs-lookup"><span data-stu-id="a0bed-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="a0bed-221">(Cette interface prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.)</span><span class="sxs-lookup"><span data-stu-id="a0bed-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="a0bed-222">« IValidator »</span><span class="sxs-lookup"><span data-stu-id="a0bed-222">"IValidator"</span></span>  
 <span data-ttu-id="a0bed-223">Fournit des méthodes pour la validation des images (PE) exécutables portables et de rapports d’erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="a0bed-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a0bed-224">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a0bed-224">Related Sections</span></span>  
 [<span data-ttu-id="a0bed-225">Coclasses et interfaces d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="a0bed-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="a0bed-226">Contient des rubriques qui décrivent les interfaces d’hébergement fournis dans le .NET Framework version 1.0 et 1.1.</span><span class="sxs-lookup"><span data-stu-id="a0bed-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="a0bed-227">Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="a0bed-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="a0bed-228">Contient des rubriques qui décrivent les interfaces d’hébergement fournis dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0bed-228">Contains topics that describe the hosting interfaces provided in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>
