---
title: "IHostTaskManager::CreateTask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ba71fcd35b16654ab67db3f657f7821c23b702
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="a9e4d-102">IHostTaskManager::CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="a9e4d-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="a9e4d-103">Demande que l’hôte crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9e4d-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9e4d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9e4d-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="a9e4d-106">[in] La taille demandée, en octets, de la pile demandée ou 0 (zéro) pour la taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="a9e4d-107">[in] Un pointeur vers la fonction de la tâche consiste à exécuter.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="a9e4d-108">[in] Un pointeur vers les données utilisateur à passer à la fonction, ou null si la fonction n’accepte aucun paramètre.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="a9e4d-109">[out] Un pointeur vers l’adresse d’un [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance créée par l’hôte, ou null si la tâche ne peut pas être créée.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="a9e4d-110">La tâche reste dans un état suspendu jusqu'à ce qu’elle soit démarrée explicitement par un appel à [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="a9e4d-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9e4d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a9e4d-111">Return Value</span></span>  
  
|<span data-ttu-id="a9e4d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9e4d-112">HRESULT</span></span>|<span data-ttu-id="a9e4d-113">Description</span><span class="sxs-lookup"><span data-stu-id="a9e4d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9e4d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9e4d-114">S_OK</span></span>|<span data-ttu-id="a9e4d-115">`CreateTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="a9e4d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9e4d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9e4d-117">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a9e4d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a9e4d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a9e4d-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-119">The call timed out.</span></span>|  
|<span data-ttu-id="a9e4d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a9e4d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a9e4d-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a9e4d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a9e4d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a9e4d-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a9e4d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9e4d-124">E_FAIL</span></span>|<span data-ttu-id="a9e4d-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a9e4d-126">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a9e4d-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9e4d-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a9e4d-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a9e4d-129">Pas assez de mémoire n’était disponible pour créer la tâche demandée.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9e4d-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9e4d-130">Remarks</span></span>  
 <span data-ttu-id="a9e4d-131">Le CLR appelle `CreateTask` pour demander que l’hôte crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="a9e4d-132">L’hôte retourne un pointeur d’interface vers un `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="a9e4d-133">La tâche retournée doit rester suspendue jusqu'à ce qu’elle soit démarrée explicitement par un appel à `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="a9e4d-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e4d-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9e4d-134">Requirements</span></span>  
 <span data-ttu-id="a9e4d-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9e4d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e4d-136">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9e4d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9e4d-137">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9e4d-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9e4d-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9e4d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e4d-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9e4d-139">See Also</span></span>  
 [<span data-ttu-id="a9e4d-140">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="a9e4d-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a9e4d-141">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="a9e4d-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a9e4d-142">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="a9e4d-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a9e4d-143">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="a9e4d-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
