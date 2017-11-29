---
title: ICLRIoCompletionManager, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbff3c39da2a18ab45f0ea03d1e1588aa61c7c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="44983-102">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="44983-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="44983-103">Implémente une méthode de rappel qui permet à l’hôte notifier le common language runtime (CLR) de l’état d’e/s spécifié des demandes.</span><span class="sxs-lookup"><span data-stu-id="44983-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44983-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="44983-104">Methods</span></span>  
  
|<span data-ttu-id="44983-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="44983-105">Method</span></span>|<span data-ttu-id="44983-106">Description</span><span class="sxs-lookup"><span data-stu-id="44983-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44983-107">OnComplete (méthode)</span><span class="sxs-lookup"><span data-stu-id="44983-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="44983-108">Notifie le CLR de l’état d’une demande d’e/s qui a été effectuée à l’aide d’un appel à la [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="44983-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44983-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="44983-109">Remarks</span></span>  
 <span data-ttu-id="44983-110">L’hôte implémente l’abstraction de terminaison d’e/s à l’aide de la [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="44983-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="44983-111">Le CLR effectue les demandes d’e/s via cette interface et l’hôte notifie l’exécution du résultat de ces requêtes à l’aide de la `ICLRIoCompletionManager` interface.</span><span class="sxs-lookup"><span data-stu-id="44983-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44983-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="44983-112">Requirements</span></span>  
 <span data-ttu-id="44983-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44983-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44983-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44983-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44983-115">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44983-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44983-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44983-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44983-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44983-117">See Also</span></span>  
 [<span data-ttu-id="44983-118">IHostIoCompletionManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="44983-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="44983-119">IHostThreadPoolManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="44983-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="44983-120">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="44983-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
