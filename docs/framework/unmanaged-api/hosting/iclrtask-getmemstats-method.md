---
title: "ICLRTask::GetMemStats, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.GetMemStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ad5fb2b76ef282258b9a5293b890a19420c1906
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="42352-102">ICLRTask::GetMemStats, méthode</span><span class="sxs-lookup"><span data-stu-id="42352-102">ICLRTask::GetMemStats Method</span></span>
<span data-ttu-id="42352-103">Obtient des informations sur l’utilisation de mémoire de statistiques relatives à la tâche qui en cours [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) représente l’instance.</span><span class="sxs-lookup"><span data-stu-id="42352-103">Gets statistical memory usage information related to the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42352-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42352-104">Syntax</span></span>  
  
```  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42352-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42352-105">Parameters</span></span>  
 `pMemUsage`  
 <span data-ttu-id="42352-106">[out] Un pointeur vers un [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance qui contient des détails sur l’utilisation de la mémoire de la tâche, y compris le nombre d’octets alloués.</span><span class="sxs-lookup"><span data-stu-id="42352-106">[out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42352-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="42352-107">Return Value</span></span>  
  
|<span data-ttu-id="42352-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42352-108">HRESULT</span></span>|<span data-ttu-id="42352-109">Description</span><span class="sxs-lookup"><span data-stu-id="42352-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42352-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42352-110">S_OK</span></span>|<span data-ttu-id="42352-111">`GetMemStats`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="42352-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="42352-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42352-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42352-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="42352-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42352-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42352-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42352-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="42352-115">The call timed out.</span></span>|  
|<span data-ttu-id="42352-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42352-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42352-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="42352-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42352-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42352-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42352-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="42352-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42352-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42352-120">E_FAIL</span></span>|<span data-ttu-id="42352-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="42352-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42352-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="42352-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42352-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="42352-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42352-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="42352-124">Requirements</span></span>  
 <span data-ttu-id="42352-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42352-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42352-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42352-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42352-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42352-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42352-128">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42352-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42352-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42352-129">See Also</span></span>  
 [<span data-ttu-id="42352-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="42352-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="42352-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="42352-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="42352-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="42352-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="42352-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="42352-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
