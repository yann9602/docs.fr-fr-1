---
title: IHostGCManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager
helpviewer_keywords: IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0927b236af094b964261a9b2a49a33d1ea2b9391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="ac64c-102">IHostGCManager, interface</span><span class="sxs-lookup"><span data-stu-id="ac64c-102">IHostGCManager Interface</span></span>
<span data-ttu-id="ac64c-103">Fournit des méthodes qui notifier l’hôte d’événements dans le mécanisme de garbage collection implémentés par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ac64c-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="ac64c-104">Membres</span><span class="sxs-lookup"><span data-stu-id="ac64c-104">Members</span></span>  
  
|<span data-ttu-id="ac64c-105">Membre</span><span class="sxs-lookup"><span data-stu-id="ac64c-105">Member</span></span>|<span data-ttu-id="ac64c-106">Description</span><span class="sxs-lookup"><span data-stu-id="ac64c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac64c-107">SuspensionEnding (méthode)</span><span class="sxs-lookup"><span data-stu-id="ac64c-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="ac64c-108">Avertit l’hôte que le CLR reprend l’exécution de tâches sur les threads qui avaient été interrompus pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ac64c-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="ac64c-109">SuspensionStarting (méthode)</span><span class="sxs-lookup"><span data-stu-id="ac64c-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="ac64c-110">Avertit l’hôte que le CLR interrompt l’exécution de tâches pour effectuer un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ac64c-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="ac64c-111">ThreadIsBlockingForSuspension (méthode)</span><span class="sxs-lookup"><span data-stu-id="ac64c-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="ac64c-112">Avertit l’hôte que le thread à partir de laquelle l’appel de méthode a été effectué sur le point de bloquer pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ac64c-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac64c-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac64c-113">Requirements</span></span>  
 <span data-ttu-id="ac64c-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac64c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac64c-115">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac64c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac64c-116">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac64c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac64c-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac64c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac64c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac64c-118">See Also</span></span>  
 [<span data-ttu-id="ac64c-119">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="ac64c-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ac64c-120">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="ac64c-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ac64c-121">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="ac64c-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ac64c-122">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="ac64c-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="ac64c-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="ac64c-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
