---
title: ICLRSyncManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5406a7a2912554552697c11fd7aa7a2c0e643fa0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="d93da-102">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="d93da-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="d93da-103">Définit des méthodes qui permettent à l’hôte pour obtenir des informations sur les tâches demandées et pour détecter les blocages dans son implémentation de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="d93da-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d93da-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d93da-104">Methods</span></span>  
  
|<span data-ttu-id="d93da-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d93da-105">Method</span></span>|<span data-ttu-id="d93da-106">Description</span><span class="sxs-lookup"><span data-stu-id="d93da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d93da-107">CreateRWLockOwnerIterator, méthode</span><span class="sxs-lookup"><span data-stu-id="d93da-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="d93da-108">Demande que le common language runtime (CLR) crée un itérateur pour l’hôte à utiliser pour déterminer l’ensemble de tâches attendant un verrou de lecteur-writer.</span><span class="sxs-lookup"><span data-stu-id="d93da-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="d93da-109">DeleteRWLockOwnerIterator, méthode</span><span class="sxs-lookup"><span data-stu-id="d93da-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="d93da-110">Demande que le CLR détruise un itérateur qui a été créé par un appel à `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="d93da-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="d93da-111">GetMonitorOwner, méthode</span><span class="sxs-lookup"><span data-stu-id="d93da-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="d93da-112">Obtient la tâche qui possède le moniteur spécifié.</span><span class="sxs-lookup"><span data-stu-id="d93da-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="d93da-113">GetRWLockOwnerNext, méthode</span><span class="sxs-lookup"><span data-stu-id="d93da-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="d93da-114">Obtient la tâche suivante qui attend le verrou de lecteur-writer actuelle.</span><span class="sxs-lookup"><span data-stu-id="d93da-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d93da-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d93da-115">Requirements</span></span>  
 <span data-ttu-id="d93da-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d93da-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d93da-117">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d93da-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d93da-118">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d93da-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d93da-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d93da-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93da-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d93da-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="d93da-121">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="d93da-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="d93da-122">Threading managé et non managé</span><span class="sxs-lookup"><span data-stu-id="d93da-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="d93da-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="d93da-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
