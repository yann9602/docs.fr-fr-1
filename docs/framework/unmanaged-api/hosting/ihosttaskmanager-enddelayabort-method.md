---
title: "IHostTaskManager::EndDelayAbort, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45148c506e2f6073dc175abe4397fad2172b355e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="3d1a5-102">IHostTaskManager::EndDelayAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="3d1a5-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="3d1a5-103">Avertit l’hôte que le code managé sort de la période dans laquelle la tâche en cours ne doit pas être abandonnée, à la suite d’un appel précédent à [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d1a5-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d1a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d1a5-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3d1a5-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3d1a5-105">Return Value</span></span>  
  
|<span data-ttu-id="3d1a5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d1a5-106">HRESULT</span></span>|<span data-ttu-id="3d1a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="3d1a5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d1a5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d1a5-108">S_OK</span></span>|<span data-ttu-id="3d1a5-109">`EndDelayAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="3d1a5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d1a5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d1a5-111">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d1a5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d1a5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d1a5-113">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-113">The call timed out.</span></span>|  
|<span data-ttu-id="3d1a5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d1a5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d1a5-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d1a5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d1a5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d1a5-117">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d1a5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d1a5-118">E_FAIL</span></span>|<span data-ttu-id="3d1a5-119">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d1a5-120">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d1a5-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3d1a5-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="3d1a5-122">E_UNEXPECTED</span></span>|<span data-ttu-id="3d1a5-123">`EndDelayAbort`a été appelé sans appel correspondant à `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d1a5-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d1a5-124">Remarks</span></span>  
 <span data-ttu-id="3d1a5-125">Le CLR effectue un appel correspondant à `BeginDelayAbort` sur la tâche en cours avant d’appeler `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="3d1a5-126">En l’absence de cet appel correspondant, implémentation de l’hôte de [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) doit retourner E_UNEXPECTED à partir de `EndDelayAbort`et ne doit effectuer aucune action.</span><span class="sxs-lookup"><span data-stu-id="3d1a5-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d1a5-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3d1a5-127">Requirements</span></span>  
 <span data-ttu-id="3d1a5-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d1a5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d1a5-129">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3d1a5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d1a5-130">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d1a5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d1a5-131">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d1a5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1a5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d1a5-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="3d1a5-133">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="3d1a5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3d1a5-134">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3d1a5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3d1a5-135">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="3d1a5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3d1a5-136">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="3d1a5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
