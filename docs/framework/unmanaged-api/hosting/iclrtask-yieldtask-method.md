---
title: "ICLRTask::YieldTask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.YieldTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a02a69329958593aec546ca9c60e3d201ce2a92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="2d1b5-102">ICLRTask::YieldTask, méthode</span><span class="sxs-lookup"><span data-stu-id="2d1b5-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="2d1b5-103">Demande que le common language runtime (CLR) mette de côté la tâche qui en cours [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) représente l’instance et rendre le temps processeur disponible à d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d1b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d1b5-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2d1b5-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2d1b5-105">Return Value</span></span>  
  
|<span data-ttu-id="2d1b5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d1b5-106">HRESULT</span></span>|<span data-ttu-id="2d1b5-107">Description</span><span class="sxs-lookup"><span data-stu-id="2d1b5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d1b5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d1b5-108">S_OK</span></span>|<span data-ttu-id="2d1b5-109">`YieldTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="2d1b5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d1b5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d1b5-111">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d1b5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d1b5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d1b5-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-113">The call timed out.</span></span>|  
|<span data-ttu-id="2d1b5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d1b5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d1b5-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d1b5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d1b5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d1b5-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d1b5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d1b5-118">E_FAIL</span></span>|<span data-ttu-id="2d1b5-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d1b5-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d1b5-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d1b5-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="2d1b5-122">Remarks</span></span>  
 <span data-ttu-id="2d1b5-123">Un hôte appelle `YieldTask` pour demander des ressources processeur pour les autres tâches ou processus.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="2d1b5-124">Cette méthode est principalement destinée à autoriser le code d’exécution longue d’abandonner le temps processeur.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="2d1b5-125">Le runtime tente de mettre la tâche qui en cours `ICLRTask` instance représente dans un état où il peut produire des temps de traitement, mais aucune garantie de succès.</span><span class="sxs-lookup"><span data-stu-id="2d1b5-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d1b5-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2d1b5-126">Requirements</span></span>  
 <span data-ttu-id="2d1b5-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d1b5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d1b5-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d1b5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d1b5-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d1b5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d1b5-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d1b5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1b5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d1b5-131">See Also</span></span>  
 [<span data-ttu-id="2d1b5-132">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="2d1b5-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2d1b5-133">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="2d1b5-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2d1b5-134">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="2d1b5-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2d1b5-135">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="2d1b5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
