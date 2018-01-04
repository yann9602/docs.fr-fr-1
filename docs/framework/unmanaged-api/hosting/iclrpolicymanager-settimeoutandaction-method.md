---
title: "ICLRPolicyManager::SetTimeoutAndAction, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeoutAndAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67150b7544f1d8d25532c564800404b634cae99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="8ed02-102">ICLRPolicyManager::SetTimeoutAndAction, méthode</span><span class="sxs-lookup"><span data-stu-id="8ed02-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="8ed02-103">Définit une valeur de délai d’attente pour l’opération spécifiée et spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’opération se produit.</span><span class="sxs-lookup"><span data-stu-id="8ed02-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ed02-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ed02-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ed02-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8ed02-106">[in] Parmi les [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valeurs, indiquant que l’opération pour laquelle définir le délai d’attente et la stratégie `action`.</span><span class="sxs-lookup"><span data-stu-id="8ed02-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="8ed02-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="8ed02-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="8ed02-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="8ed02-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="8ed02-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="8ed02-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="8ed02-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8ed02-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="8ed02-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8ed02-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="8ed02-112">[in] La nouvelle valeur de délai d’attente en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="8ed02-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="8ed02-113">Une valeur infinie, `operation` jamais de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="8ed02-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="8ed02-114">[in] Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs indiquant l’action de stratégie que le CLR doit suivre lorsque `operation` se produit.</span><span class="sxs-lookup"><span data-stu-id="8ed02-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ed02-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8ed02-115">Return Value</span></span>  
  
|<span data-ttu-id="8ed02-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ed02-116">HRESULT</span></span>|<span data-ttu-id="8ed02-117">Description</span><span class="sxs-lookup"><span data-stu-id="8ed02-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ed02-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ed02-118">S_OK</span></span>|<span data-ttu-id="8ed02-119">`SetTimeoutAndAction`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8ed02-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="8ed02-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ed02-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ed02-121">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8ed02-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ed02-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ed02-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ed02-123">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8ed02-123">The call timed out.</span></span>|  
|<span data-ttu-id="8ed02-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ed02-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ed02-125">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8ed02-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ed02-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ed02-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ed02-127">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8ed02-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ed02-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ed02-128">E_FAIL</span></span>|<span data-ttu-id="8ed02-129">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8ed02-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ed02-130">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8ed02-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ed02-131">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ed02-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ed02-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8ed02-132">E_INVALIDARG</span></span>|<span data-ttu-id="8ed02-133">Impossible de définir un délai d’attente spécifié `operation`, ou une valeur non valide a été fournie pour `action`.</span><span class="sxs-lookup"><span data-stu-id="8ed02-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ed02-134">Notes</span><span class="sxs-lookup"><span data-stu-id="8ed02-134">Remarks</span></span>  
 <span data-ttu-id="8ed02-135">`SetTimeoutAndAction`encapsule les fonctionnalités de la [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) et [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) méthodes et peut être appelé à la place d’appels consécutifs pour ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="8ed02-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ed02-136">Toutes les valeurs d’action de stratégie peuvent être spécifiés comme comportement de délai d’attente pour les opérations CLR.</span><span class="sxs-lookup"><span data-stu-id="8ed02-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="8ed02-137">Consultez la section Remarques des rubriques pour ces deux méthodes pour les valeurs valides.</span><span class="sxs-lookup"><span data-stu-id="8ed02-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed02-138">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ed02-138">Requirements</span></span>  
 <span data-ttu-id="8ed02-139">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ed02-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed02-140">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ed02-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ed02-141">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ed02-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ed02-142">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed02-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed02-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ed02-143">See Also</span></span>  
 [<span data-ttu-id="8ed02-144">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="8ed02-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="8ed02-145">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="8ed02-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="8ed02-146">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="8ed02-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="8ed02-147">SetActionOnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="8ed02-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [<span data-ttu-id="8ed02-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="8ed02-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
