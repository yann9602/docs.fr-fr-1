---
title: "IHostTaskManager::SwitchToTask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SwitchToTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03578a6a9579a807323d54308347f16f24ae90dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="c1b3f-102">IHostTaskManager::SwitchToTask, méthode</span><span class="sxs-lookup"><span data-stu-id="c1b3f-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="c1b3f-103">Avertit l’hôte qu’il doit éliminer la tâche actuelle.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1b3f-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1b3f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1b3f-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="c1b3f-106">[in] Parmi les [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs d’énumération indiquant l’action de l’hôte doit effectuer si l’opération demandée bloque.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1b3f-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1b3f-107">Return Value</span></span>  
  
|<span data-ttu-id="c1b3f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1b3f-108">HRESULT</span></span>|<span data-ttu-id="c1b3f-109">Description</span><span class="sxs-lookup"><span data-stu-id="c1b3f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1b3f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1b3f-110">S_OK</span></span>|<span data-ttu-id="c1b3f-111">`SwitchToTask`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="c1b3f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1b3f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1b3f-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1b3f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1b3f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1b3f-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1b3f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1b3f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1b3f-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1b3f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1b3f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1b3f-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1b3f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1b3f-120">E_FAIL</span></span>|<span data-ttu-id="c1b3f-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1b3f-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1b3f-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b3f-124">Notes</span><span class="sxs-lookup"><span data-stu-id="c1b3f-124">Remarks</span></span>  
 <span data-ttu-id="c1b3f-125">L’hôte peut basculer dans une autre tâche sous la forme souhaitée ou nécessaires.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1b3f-126">`SwitchToTask`ne spécifie pas de tâche que l’hôte doit basculer ; Il spécifie uniquement la tâche pour laquelle il doit basculer à partir de.</span><span class="sxs-lookup"><span data-stu-id="c1b3f-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b3f-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1b3f-127">Requirements</span></span>  
 <span data-ttu-id="c1b3f-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b3f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b3f-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1b3f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1b3f-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1b3f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1b3f-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b3f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b3f-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1b3f-132">See Also</span></span>  
 [<span data-ttu-id="c1b3f-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="c1b3f-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c1b3f-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c1b3f-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c1b3f-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="c1b3f-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c1b3f-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="c1b3f-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
