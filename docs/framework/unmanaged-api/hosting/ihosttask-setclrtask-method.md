---
title: "IHostTask::SetCLRTask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="8c013-102">IHostTask::SetCLRTask, méthode</span><span class="sxs-lookup"><span data-stu-id="8c013-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="8c013-103">Associe un `ICLRTask` instance avec actuel [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="8c013-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c013-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c013-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c013-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c013-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="8c013-106">[in] Pointeur d’interface vers le `ICLRTask` instance à associer à actuel `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="8c013-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c013-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8c013-107">Return Value</span></span>  
  
|<span data-ttu-id="8c013-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c013-108">HRESULT</span></span>|<span data-ttu-id="8c013-109">Description</span><span class="sxs-lookup"><span data-stu-id="8c013-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c013-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c013-110">S_OK</span></span>|<span data-ttu-id="8c013-111">`SetCLRTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8c013-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="8c013-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c013-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c013-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8c013-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c013-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c013-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c013-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8c013-115">The call timed out.</span></span>|  
|<span data-ttu-id="8c013-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c013-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c013-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8c013-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c013-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c013-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c013-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8c013-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c013-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c013-120">E_FAIL</span></span>|<span data-ttu-id="8c013-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8c013-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c013-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8c013-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c013-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c013-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c013-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="8c013-124">Remarks</span></span>  
 <span data-ttu-id="8c013-125">Le CLR appelle `SetCLRTask` pour associer un `ICLRTask` instance avec actuel `IHostTask` instance, ce qui a été créé par un appel à [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="8c013-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c013-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8c013-126">Requirements</span></span>  
 <span data-ttu-id="8c013-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c013-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c013-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c013-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c013-129">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c013-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c013-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c013-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c013-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c013-131">See Also</span></span>  
 [<span data-ttu-id="8c013-132">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c013-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="8c013-133">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c013-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8c013-134">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c013-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8c013-135">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="8c013-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
