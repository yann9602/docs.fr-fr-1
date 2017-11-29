---
title: IHostMemoryManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager
helpviewer_keywords: IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 415539be0dbed8e0cf3f9d6e5c79bf4cfac09fe2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="f0670-102">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="f0670-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="f0670-103">Fournit des méthodes qui permettent le common language runtime (CLR) pour effectuer des demandes de mémoire virtuelle via l’hôte, au lieu d’utiliser les fonctions de mémoire virtuelle Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="f0670-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0670-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f0670-104">Methods</span></span>  
  
|<span data-ttu-id="f0670-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f0670-105">Method</span></span>|<span data-ttu-id="f0670-106">Description</span><span class="sxs-lookup"><span data-stu-id="f0670-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0670-107">AcquiredVirtualAddressSpace (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="f0670-108">Avertit l’hôte que le common language runtime (CLR) a acquis la mémoire spécifiée à partir du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f0670-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="f0670-109">CreateMAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="f0670-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="f0670-110">Obtient un pointeur d’interface vers un [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance qui est utilisé pour demander des allocations de mémoire à partir d’un tas créé par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="f0670-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="f0670-111">GetMemoryLoad (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="f0670-112">Obtient la quantité de mémoire physique qui est actuellement utilisé, comme indiqué par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="f0670-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="f0670-113">NeedsVirtualAddressSpace (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="f0670-114">Avertit l’hôte que le CLR va tenter d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0670-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="f0670-115">RegisterMemoryNotificationCallback (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="f0670-116">Enregistre un pointeur vers une fonction de rappel que l’hôte appelle pour notifier le CLR de la charge actuelle de la mémoire sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f0670-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="f0670-117">ReleasedVirtualAddressSpace (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="f0670-118">Avertit l’hôte que le CLR a terminé d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f0670-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="f0670-119">VirtualAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="f0670-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="f0670-120">Sert de wrapper logique pour la fonction Win32 correspondante, qui se réserve ou valide une région de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="f0670-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="f0670-121">VirtualFree, méthode</span><span class="sxs-lookup"><span data-stu-id="f0670-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="f0670-122">Sert de wrapper logique pour la fonction Win32 correspondante, qui libère, annule sa validation ou libère et invalider une région de pages au sein de l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="f0670-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="f0670-123">VirtualProtect (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="f0670-124">Sert de wrapper logique pour la fonction Win32 correspondante, qui modifie la protection sur une région de pages validées dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="f0670-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="f0670-125">VirtualQuery (méthode)</span><span class="sxs-lookup"><span data-stu-id="f0670-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="f0670-126">Sert de wrapper logique pour la fonction Win32 correspondante, qui Récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="f0670-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0670-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0670-127">Remarks</span></span>  
 <span data-ttu-id="f0670-128">`IHostMemoryManager`fournit également des méthodes pour le CLR obtenir un pointeur par l’intermédiaire duquel pour effectuer des demandes de mémoire sur le tas et obtenir le niveau de sollicitation de la mémoire dans le processus, comme indiqué par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="f0670-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0670-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f0670-129">Requirements</span></span>  
 <span data-ttu-id="f0670-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0670-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0670-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0670-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0670-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0670-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0670-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0670-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0670-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0670-134">See Also</span></span>  
 [<span data-ttu-id="f0670-135">IHostMalloc (Interface)</span><span class="sxs-lookup"><span data-stu-id="f0670-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="f0670-136">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="f0670-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
