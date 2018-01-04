---
title: IHostManualEvent, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent
helpviewer_keywords: IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d55500efbe808b2fce16e869422e727b8ed0b93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="df31f-102">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="df31f-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="df31f-103">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="df31f-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df31f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="df31f-104">Methods</span></span>  
  
|<span data-ttu-id="df31f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="df31f-105">Method</span></span>|<span data-ttu-id="df31f-106">Description</span><span class="sxs-lookup"><span data-stu-id="df31f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df31f-107">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="df31f-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="df31f-108">Réinitialise l’actuel `IHostManualEvent` instance à un état non signalé.</span><span class="sxs-lookup"><span data-stu-id="df31f-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="df31f-109">Set, méthode</span><span class="sxs-lookup"><span data-stu-id="df31f-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="df31f-110">Définit l’actuel `IHostManualEvent` instance à un état signalé.</span><span class="sxs-lookup"><span data-stu-id="df31f-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="df31f-111">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="df31f-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="df31f-112">Fait en `IHostManualEvent` instance attendre qu’il appartient, ou un certain laps de temps.</span><span class="sxs-lookup"><span data-stu-id="df31f-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df31f-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df31f-113">Requirements</span></span>  
 <span data-ttu-id="df31f-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df31f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df31f-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df31f-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df31f-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df31f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df31f-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df31f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df31f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df31f-118">See Also</span></span>  
 [<span data-ttu-id="df31f-119">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="df31f-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="df31f-120">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="df31f-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="df31f-121">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="df31f-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="df31f-122">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="df31f-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="df31f-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="df31f-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
