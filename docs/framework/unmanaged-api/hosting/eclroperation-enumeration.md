---
title: "EClrOperation, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrOperation
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrOperation
helpviewer_keywords: EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="95952-102">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="95952-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="95952-103">Décrit l’ensemble des opérations pour lesquelles un hôte peut appliquer des actions de stratégie.</span><span class="sxs-lookup"><span data-stu-id="95952-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95952-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95952-104">Syntax</span></span>  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="95952-105">Membres</span><span class="sxs-lookup"><span data-stu-id="95952-105">Members</span></span>  
  
|<span data-ttu-id="95952-106">Membre</span><span class="sxs-lookup"><span data-stu-id="95952-106">Member</span></span>|<span data-ttu-id="95952-107">Description</span><span class="sxs-lookup"><span data-stu-id="95952-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="95952-108">L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un <xref:System.AppDomain> est déchargé de façon non progressive (brusque).</span><span class="sxs-lookup"><span data-stu-id="95952-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="95952-109">L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un <xref:System.AppDomain> est déchargé.</span><span class="sxs-lookup"><span data-stu-id="95952-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="95952-110">L’hôte peut spécifier des actions de stratégie à prendre lors de l’exécuteront des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="95952-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="95952-111">L’hôte peut spécifier des actions à entreprendre lorsque le processus s’arrête de stratégie.</span><span class="sxs-lookup"><span data-stu-id="95952-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="95952-112">L’hôte peut spécifier des actions à entreprendre lorsqu’un thread est abandonné de stratégie.</span><span class="sxs-lookup"><span data-stu-id="95952-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="95952-113">L’hôte peut spécifier des actions à entreprendre lorsqu’un abandon de thread non applicables se produit dans une région de code critique de stratégie.</span><span class="sxs-lookup"><span data-stu-id="95952-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="95952-114">L’hôte peut spécifier des actions de stratégie à prendre lorsqu’un abandon de thread non applicables se produit dans une région de code non critique.</span><span class="sxs-lookup"><span data-stu-id="95952-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95952-115">Notes</span><span class="sxs-lookup"><span data-stu-id="95952-115">Remarks</span></span>  
 <span data-ttu-id="95952-116">L’infrastructure de fiabilité du common language runtime (CLR) fait la distinction entre les abandons et ressources des échecs d’allocation qui se produisent dans les régions critiques de code et celles qui se produisent dans les régions de code non critiques.</span><span class="sxs-lookup"><span data-stu-id="95952-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="95952-117">Cette distinction est conçue pour permettre aux hôtes de définir des stratégies différentes en fonction de l’endroit où une défaillance se produit dans le code.</span><span class="sxs-lookup"><span data-stu-id="95952-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="95952-118">A *région critique de code* est un espace où le CLR ne peut pas garantir qu’abandon d’une tâche ou l’échec d’une demande de ressources affectera uniquement la tâche en cours.</span><span class="sxs-lookup"><span data-stu-id="95952-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="95952-119">Par exemple, si une tâche conserve un verrou et reçoit un HRESULT qui indique un échec lors d’une demande d’allocation de mémoire, il est insuffisant simplement pour abandonner cette tâche pour garantir la stabilité de la <xref:System.AppDomain>, car le <xref:System.AppDomain> peut contenir d’autres tâches en attente du verrou même.</span><span class="sxs-lookup"><span data-stu-id="95952-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="95952-120">Abandon en cours tâche peut provoquer les autres tâches à cesser de répondre (blocage ou) indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="95952-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="95952-121">Dans ce cas, l’hôte doit pouvoir décharger l’intégralité de <xref:System.AppDomain> plutôt que de l’instabilité du risque.</span><span class="sxs-lookup"><span data-stu-id="95952-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="95952-122">A *région non critique de code*, quant à lui, est une région où le CLR peut garantir qu’un abandon ou un échec affectera uniquement la tâche sur laquelle l’erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="95952-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="95952-123">Le CLR distingue également normale et les abandons abandons (non applicables).</span><span class="sxs-lookup"><span data-stu-id="95952-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="95952-124">En général, un abandon normal ou correct fait en sorte d’exécuter des routines de gestion des exceptions et des finaliseurs avant d’abandonner une tâche, alors qu’un abandon brutal n’apporte aucune garantie de ce type.</span><span class="sxs-lookup"><span data-stu-id="95952-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95952-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95952-125">Requirements</span></span>  
 <span data-ttu-id="95952-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95952-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95952-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95952-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95952-128">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95952-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95952-129">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95952-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95952-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95952-130">See Also</span></span>  
 [<span data-ttu-id="95952-131">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="95952-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="95952-132">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="95952-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="95952-133">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="95952-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="95952-134">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="95952-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="95952-135">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="95952-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
