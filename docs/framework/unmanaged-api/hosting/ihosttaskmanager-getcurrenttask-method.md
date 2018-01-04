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
ms.workload: dotnet
ms.openlocfilehash: b3ba8cbaac28df49a2df70492c1a292ee8cd287e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="7b2bf-102">IHostTaskManager::GetCurrentTask, méthode</span><span class="sxs-lookup"><span data-stu-id="7b2bf-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="7b2bf-103">Obtient un pointeur d’interface à la tâche en cours d’exécution sur le thread de système d’exploitation à partir de laquelle cet appel est effectué.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b2bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b2bf-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b2bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7b2bf-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="7b2bf-106">[out] Un pointeur vers l’adresse d’un [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance qui représente la tâche en cours d’exécution, ou null si aucune tâche n’est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b2bf-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7b2bf-107">Return Value</span></span>  
  
|<span data-ttu-id="7b2bf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b2bf-108">HRESULT</span></span>|<span data-ttu-id="7b2bf-109">Description</span><span class="sxs-lookup"><span data-stu-id="7b2bf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b2bf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b2bf-110">S_OK</span></span>|<span data-ttu-id="7b2bf-111">`GetCurrentTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="7b2bf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b2bf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b2bf-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b2bf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b2bf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b2bf-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-115">The call timed out.</span></span>|  
|<span data-ttu-id="7b2bf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b2bf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b2bf-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b2bf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b2bf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b2bf-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b2bf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b2bf-120">E_FAIL</span></span>|<span data-ttu-id="7b2bf-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b2bf-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b2bf-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7b2bf-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="7b2bf-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="7b2bf-125">`GetCurrentTask`a été appelé sur un thread de système d’exploitation en dehors du contrôle de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b2bf-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7b2bf-126">Remarks</span></span>  
 <span data-ttu-id="7b2bf-127">L’hôte peut également définir le `pTask` paramètre null pour empêcher une tâche qu’il n’a pas initialisée d’entrer dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="7b2bf-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b2bf-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7b2bf-128">Requirements</span></span>  
 <span data-ttu-id="7b2bf-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b2bf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b2bf-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b2bf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b2bf-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b2bf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b2bf-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b2bf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2bf-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b2bf-133">See Also</span></span>  
 [<span data-ttu-id="7b2bf-134">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="7b2bf-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7b2bf-135">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7b2bf-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7b2bf-136">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="7b2bf-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7b2bf-137">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7b2bf-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
