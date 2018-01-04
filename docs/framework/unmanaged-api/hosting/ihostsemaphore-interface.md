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
ms.workload: dotnet
ms.openlocfilehash: bcc6a9a7847932e9e469cdbffc9792e1d5860570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="26c2a-102">IHostSemaphore, interface</span><span class="sxs-lookup"><span data-stu-id="26c2a-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="26c2a-103">Représente l’implémentation de l’hôte d’un sémaphore pour le thread.</span><span class="sxs-lookup"><span data-stu-id="26c2a-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26c2a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="26c2a-104">Methods</span></span>  
  
|<span data-ttu-id="26c2a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="26c2a-105">Method</span></span>|<span data-ttu-id="26c2a-106">Description</span><span class="sxs-lookup"><span data-stu-id="26c2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26c2a-107">ReleaseSemaphore, méthode</span><span class="sxs-lookup"><span data-stu-id="26c2a-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="26c2a-108">Incrémente le nombre d’actuel `IHostSemaphore` instance de la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26c2a-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="26c2a-109">Wait, méthode</span><span class="sxs-lookup"><span data-stu-id="26c2a-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="26c2a-110">Fait en `IHostSemaphore` instance attendre qu’elle appartient ou la quantité de temps spécifiée.</span><span class="sxs-lookup"><span data-stu-id="26c2a-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26c2a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26c2a-111">Requirements</span></span>  
 <span data-ttu-id="26c2a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c2a-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26c2a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26c2a-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26c2a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26c2a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c2a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26c2a-116">See Also</span></span>  
 [<span data-ttu-id="26c2a-117">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="26c2a-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="26c2a-118">IHostAutoEvent, interface</span><span class="sxs-lookup"><span data-stu-id="26c2a-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="26c2a-119">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="26c2a-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="26c2a-120">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="26c2a-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="26c2a-121">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="26c2a-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
