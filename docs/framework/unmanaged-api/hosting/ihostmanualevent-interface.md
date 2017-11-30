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
ms.openlocfilehash: 5c19125d96d5f4a9e91fc083d53f36ebebd2c569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="b700d-102">IHostManualEvent, interface</span><span class="sxs-lookup"><span data-stu-id="b700d-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="b700d-103">Fournit l’implémentation de l’hôte d’une représentation d’un événement de réinitialisation manuelle.</span><span class="sxs-lookup"><span data-stu-id="b700d-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b700d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b700d-104">Methods</span></span>  
  
|<span data-ttu-id="b700d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b700d-105">Method</span></span>|<span data-ttu-id="b700d-106">Description</span><span class="sxs-lookup"><span data-stu-id="b700d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b700d-107">Reset (méthode)</span><span class="sxs-lookup"><span data-stu-id="b700d-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="b700d-108">Réinitialise l’actuel `IHostManualEvent` instance à un état non signalé.</span><span class="sxs-lookup"><span data-stu-id="b700d-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="b700d-109">Set (méthode)</span><span class="sxs-lookup"><span data-stu-id="b700d-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="b700d-110">Définit l’actuel `IHostManualEvent` instance à un état signalé.</span><span class="sxs-lookup"><span data-stu-id="b700d-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="b700d-111">Wait (méthode)</span><span class="sxs-lookup"><span data-stu-id="b700d-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="b700d-112">Fait en `IHostManualEvent` instance attendre qu’il appartient, ou un certain laps de temps.</span><span class="sxs-lookup"><span data-stu-id="b700d-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b700d-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b700d-113">Requirements</span></span>  
 <span data-ttu-id="b700d-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b700d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b700d-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b700d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b700d-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b700d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b700d-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b700d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b700d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b700d-118">See Also</span></span>  
 [<span data-ttu-id="b700d-119">ICLRSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="b700d-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="b700d-120">IHostAutoEvent (Interface)</span><span class="sxs-lookup"><span data-stu-id="b700d-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="b700d-121">IHostSemaphore (Interface)</span><span class="sxs-lookup"><span data-stu-id="b700d-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="b700d-122">IHostSyncManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="b700d-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="b700d-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="b700d-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
