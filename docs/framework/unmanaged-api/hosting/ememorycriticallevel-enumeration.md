---
title: "EMemoryCriticalLevel, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="e8a51-102">EMemoryCriticalLevel, énumération</span><span class="sxs-lookup"><span data-stu-id="e8a51-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="e8a51-103">Contient des valeurs qui indiquent l’impact d’un échec lors de l’allocation de mémoire spécifique a été demandée, mais ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="e8a51-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8a51-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="e8a51-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e8a51-105">Members</span></span>  
  
|<span data-ttu-id="e8a51-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e8a51-106">Member</span></span>|<span data-ttu-id="e8a51-107">Description</span><span class="sxs-lookup"><span data-stu-id="e8a51-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="e8a51-108">Indique que l’allocation est critique pour l’exécution du code managé dans le domaine qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="e8a51-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="e8a51-109">Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que le domaine est toujours utilisable.</span><span class="sxs-lookup"><span data-stu-id="e8a51-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="e8a51-110">L’hôte décide quelle action à effectuer lorsque l’allocation ne peut pas être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="e8a51-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="e8a51-111">Il peut indiquer au CLR pour abandonner la `AppDomain` automatiquement, ou lui permettre de poursuivre son exécution en appelant des méthodes sur [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e8a51-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="e8a51-112">Indique que l’allocation est critique pour l’exécution du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e8a51-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="e8a51-113">Cette valeur est utilisée lors du démarrage et lors de l’exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="e8a51-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="e8a51-114">Si la mémoire ne peut pas être allouée, le CLR ne peut pas fonctionner dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e8a51-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="e8a51-115">Si l’allocation échoue, le CLR est désactivé.</span><span class="sxs-lookup"><span data-stu-id="e8a51-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="e8a51-116">Tous les appels dans le CLR échouent avec HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8a51-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="e8a51-117">Indique que l’allocation est critique pour l’exécution de la tâche qui a demandé l’allocation.</span><span class="sxs-lookup"><span data-stu-id="e8a51-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="e8a51-118">Si la mémoire ne peut pas être allouée, le CLR ne peut pas garantir que la tâche peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="e8a51-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="e8a51-119">En cas de défaillance, le CLR lève une <xref:System.Threading.ThreadAbortException> sur le thread de système d’opération physique.</span><span class="sxs-lookup"><span data-stu-id="e8a51-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8a51-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8a51-120">Remarks</span></span>  
 <span data-ttu-id="e8a51-121">Les méthodes d’allocation de mémoire définies dans le [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) et [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces prennent un paramètre de ce type.</span><span class="sxs-lookup"><span data-stu-id="e8a51-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="e8a51-122">En fonction de la gravité d’une défaillance, un hôte peut décider Échec de la demande d’allocation immédiatement ou attendre qu’il peut être satisfaite.</span><span class="sxs-lookup"><span data-stu-id="e8a51-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a51-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8a51-123">Requirements</span></span>  
 <span data-ttu-id="e8a51-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8a51-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a51-125">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8a51-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8a51-126">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8a51-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8a51-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a51-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a51-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a51-128">See Also</span></span>  
 [<span data-ttu-id="e8a51-129">ICLRMemoryNotificationCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="e8a51-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="e8a51-130">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e8a51-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)