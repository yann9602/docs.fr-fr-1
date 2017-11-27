---
title: "IHostTaskManager::GetCurrentTask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92b4ed0cd33d2e9d3399e409d2dba4eeb14a2f5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="3f05e-102">IHostTaskManager::GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="3f05e-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="3f05e-103">Obtient un pointeur d’interface à la tâche en cours d’exécution sur le thread de système d’exploitation à partir de laquelle cet appel est effectué.</span><span class="sxs-lookup"><span data-stu-id="3f05e-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f05e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f05e-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f05e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f05e-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="3f05e-106">[out] Un pointeur vers l’adresse d’un [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance qui représente la tâche en cours d’exécution, ou null si aucune tâche n’est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3f05e-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f05e-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3f05e-107">Return Value</span></span>  
  
|<span data-ttu-id="3f05e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f05e-108">HRESULT</span></span>|<span data-ttu-id="3f05e-109">Description</span><span class="sxs-lookup"><span data-stu-id="3f05e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f05e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f05e-110">S_OK</span></span>|<span data-ttu-id="3f05e-111">`GetCurrentTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3f05e-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="3f05e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f05e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f05e-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="3f05e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f05e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f05e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f05e-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3f05e-115">The call timed out.</span></span>|  
|<span data-ttu-id="3f05e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f05e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f05e-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3f05e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f05e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f05e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f05e-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="3f05e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f05e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f05e-120">E_FAIL</span></span>|<span data-ttu-id="3f05e-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3f05e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f05e-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3f05e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f05e-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3f05e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3f05e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3f05e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3f05e-125">`GetCurrentTask`a été appelé sur un thread de système d’exploitation en dehors du contrôle de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="3f05e-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f05e-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="3f05e-126">Remarks</span></span>  
 <span data-ttu-id="3f05e-127">L’hôte peut également définir le `pTask` paramètre null pour empêcher une tâche qu’il n’a pas initialisée d’entrer dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="3f05e-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f05e-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f05e-128">Requirements</span></span>  
 <span data-ttu-id="3f05e-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f05e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f05e-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f05e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f05e-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f05e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f05e-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f05e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f05e-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f05e-133">See Also</span></span>  
 [<span data-ttu-id="3f05e-134">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f05e-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3f05e-135">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f05e-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3f05e-136">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f05e-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3f05e-137">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3f05e-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
