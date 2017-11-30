---
title: "ICLRTaskManager::CreateTask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fa4607232eedd532456d1ffae6bc3d92e42282f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="6cae2-102">ICLRTaskManager::CreateTask, méthode</span><span class="sxs-lookup"><span data-stu-id="6cae2-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="6cae2-103">Demande explicitement que le common language runtime (CLR) crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="6cae2-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cae2-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cae2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6cae2-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="6cae2-106">[out] Un pointeur vers l’adresse d’un nouvellement créé [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), ou null si la tâche n’a pas pu être créée.</span><span class="sxs-lookup"><span data-stu-id="6cae2-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cae2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6cae2-107">Return Value</span></span>  
  
|<span data-ttu-id="6cae2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cae2-108">HRESULT</span></span>|<span data-ttu-id="6cae2-109">Description</span><span class="sxs-lookup"><span data-stu-id="6cae2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cae2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6cae2-110">S_OK</span></span>|<span data-ttu-id="6cae2-111">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6cae2-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="6cae2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6cae2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6cae2-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="6cae2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6cae2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6cae2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6cae2-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="6cae2-115">The call timed out.</span></span>|  
|<span data-ttu-id="6cae2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6cae2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6cae2-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="6cae2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6cae2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6cae2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6cae2-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="6cae2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6cae2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6cae2-120">E_FAIL</span></span>|<span data-ttu-id="6cae2-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6cae2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6cae2-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6cae2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6cae2-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6cae2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6cae2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6cae2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6cae2-125">Pas assez de mémoire est disponible pour l’allocation de la ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="6cae2-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cae2-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="6cae2-126">Remarks</span></span>  
 <span data-ttu-id="6cae2-127">Le CLR crée une nouvelle tâche automatiquement lors de l’initialisation, lorsque le code utilisateur crée un thread à l’aide de types dans les <xref:System.Threading> espace de noms, ou lorsque la taille du pool de threads est augmentée.</span><span class="sxs-lookup"><span data-stu-id="6cae2-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="6cae2-128">Il crée également des tâches lorsque le code non managé appelle une fonction managée.</span><span class="sxs-lookup"><span data-stu-id="6cae2-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="6cae2-129">`CreateTask`permet à l’hôte à demander explicitement que le CLR crée une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="6cae2-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="6cae2-130">Par exemple, l’hôte peut appeler cette méthode pour préinitialiser des structures de données.</span><span class="sxs-lookup"><span data-stu-id="6cae2-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6cae2-131">La nouvelle tâche est retournée dans un état suspendu et reste suspendue jusqu'à ce que l’hôte appelle explicitement [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="6cae2-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cae2-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6cae2-132">Requirements</span></span>  
 <span data-ttu-id="6cae2-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cae2-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cae2-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cae2-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cae2-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cae2-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cae2-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cae2-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cae2-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cae2-137">See Also</span></span>  
 [<span data-ttu-id="6cae2-138">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="6cae2-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6cae2-139">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="6cae2-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6cae2-140">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="6cae2-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="6cae2-141">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="6cae2-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
