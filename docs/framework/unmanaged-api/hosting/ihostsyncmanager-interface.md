---
title: IHostSyncManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 951f7808e238f514ffcf19a8dda0033b7b07172c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="e4fbe-102">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="e4fbe-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="e4fbe-103">Fournit des méthodes qui permettent le common language runtime (CLR) pour créer des primitives de synchronisation en appelant l’hôte au lieu d’utiliser les fonctions de synchronisation Win32.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4fbe-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e4fbe-104">Methods</span></span>  
  
|<span data-ttu-id="e4fbe-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e4fbe-105">Method</span></span>|<span data-ttu-id="e4fbe-106">Description</span><span class="sxs-lookup"><span data-stu-id="e4fbe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4fbe-107">CreateAutoEvent (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="e4fbe-108">Crée un objet d’événement de réinitialisation automatique.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="e4fbe-109">CreateCrst, méthode</span><span class="sxs-lookup"><span data-stu-id="e4fbe-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="e4fbe-110">Crée un objet de section critique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="e4fbe-111">CreateCrstWithSpinCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="e4fbe-112">Crée un objet de section critique dont le nombre de sélection numérique pour la synchronisation.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="e4fbe-113">CreateManualEvent (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="e4fbe-114">Crée un objet d’événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="e4fbe-115">CreateMonitorEvent (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="e4fbe-116">Crée un objet d’événement de réinitialisation automatique surveillé.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="e4fbe-117">CreateRWLockReaderEvent (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="e4fbe-118">Crée un objet d’événement de réinitialisation manuelle pour l’implémentation d’un verrou de lecteur.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="e4fbe-119">CreateRWLockWriterEvent (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="e4fbe-120">Crée un objet d’événement de réinitialisation automatique pour l’implémentation d’un verrou de writer.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="e4fbe-121">CreateSemaphore (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="e4fbe-122">Crée un [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objet pour le CLR à utiliser en tant que sémaphore pour les événements d’attente.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="e4fbe-123">SetCLRSyncManager (méthode)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="e4fbe-124">Définit le [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance à associer à actuel `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4fbe-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="e4fbe-125">Remarks</span></span>  
 <span data-ttu-id="e4fbe-126">Le CLR détecte l’implémentation de l’hôte de `IHostSyncManager` en appelant le [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) méthode avec un `IID` de IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="e4fbe-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4fbe-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e4fbe-127">Requirements</span></span>  
 <span data-ttu-id="e4fbe-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4fbe-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4fbe-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4fbe-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4fbe-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4fbe-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4fbe-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4fbe-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4fbe-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4fbe-132">See Also</span></span>  
 [<span data-ttu-id="e4fbe-133">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="e4fbe-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e4fbe-134">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e4fbe-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
