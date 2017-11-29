---
title: IHostSemaphore, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore
helpviewer_keywords: IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b3225186f74fceadfb3104145743823ef82fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="0ce72-102">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="0ce72-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="0ce72-103">Représente l’implémentation de l’hôte d’un sémaphore pour le thread.</span><span class="sxs-lookup"><span data-stu-id="0ce72-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ce72-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0ce72-104">Methods</span></span>  
  
|<span data-ttu-id="0ce72-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0ce72-105">Method</span></span>|<span data-ttu-id="0ce72-106">Description</span><span class="sxs-lookup"><span data-stu-id="0ce72-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ce72-107">ReleaseSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="0ce72-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="0ce72-108">Incrémente le nombre d’actuel `IHostSemaphore` instance de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0ce72-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="0ce72-109">Wait (méthode)</span><span class="sxs-lookup"><span data-stu-id="0ce72-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="0ce72-110">Fait en `IHostSemaphore` instance attendre qu’elle appartient ou la quantité de temps spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0ce72-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ce72-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0ce72-111">Requirements</span></span>  
 <span data-ttu-id="0ce72-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ce72-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce72-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ce72-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ce72-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ce72-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ce72-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce72-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce72-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ce72-116">See Also</span></span>  
 [<span data-ttu-id="0ce72-117">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="0ce72-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0ce72-118">IHostAutoEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="0ce72-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="0ce72-119">IHostManualEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="0ce72-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="0ce72-120">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="0ce72-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="0ce72-121">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="0ce72-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
