---
title: "ICLRPolicyManager::SetActionOnFailure, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="45f01-102">ICLRPolicyManager::SetActionOnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="45f01-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="45f01-103">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre en cas d’échec spécifié.</span><span class="sxs-lookup"><span data-stu-id="45f01-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45f01-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45f01-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45f01-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="45f01-106">[in] Parmi les [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs indiquant le type d’échec pour lequel effectuer l’action.</span><span class="sxs-lookup"><span data-stu-id="45f01-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="45f01-107">[in] Parmi les [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs, indiquant l’action à entreprendre lorsqu’une défaillance se produit.</span><span class="sxs-lookup"><span data-stu-id="45f01-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="45f01-108">Pour obtenir la liste de valeurs prises en charge, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="45f01-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45f01-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="45f01-109">Return Value</span></span>  
  
|<span data-ttu-id="45f01-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45f01-110">HRESULT</span></span>|<span data-ttu-id="45f01-111">Description</span><span class="sxs-lookup"><span data-stu-id="45f01-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45f01-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="45f01-112">S_OK</span></span>|<span data-ttu-id="45f01-113">`SetActionOnFailure`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="45f01-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="45f01-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45f01-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45f01-115">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="45f01-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45f01-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45f01-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45f01-117">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="45f01-117">The call timed out.</span></span>|  
|<span data-ttu-id="45f01-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45f01-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45f01-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="45f01-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45f01-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45f01-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45f01-121">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="45f01-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45f01-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45f01-122">E_FAIL</span></span>|<span data-ttu-id="45f01-123">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="45f01-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45f01-124">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="45f01-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45f01-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="45f01-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="45f01-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="45f01-126">E_INVALIDARG</span></span>|<span data-ttu-id="45f01-127">Impossible de définir une action de la stratégie pour l’opération spécifiée, ou une action de stratégie non valide a été spécifiée pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="45f01-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45f01-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="45f01-128">Remarks</span></span>  
 <span data-ttu-id="45f01-129">Par défaut, le CLR lève une exception lorsqu’il ne peut pas allouer une ressource, telles que la mémoire.</span><span class="sxs-lookup"><span data-stu-id="45f01-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="45f01-130">`SetActionOnFailure`permet à l’hôte de substituer ce comportement en spécifiant l’action de stratégie à appliquer en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="45f01-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="45f01-131">Le tableau suivant montre les combinaisons de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) et [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valeurs prises en charge.</span><span class="sxs-lookup"><span data-stu-id="45f01-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="45f01-132">(Le préfixe FAIL_ est omis de [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) valeurs.)</span><span class="sxs-lookup"><span data-stu-id="45f01-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="45f01-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="45f01-133">NonCriticalResource</span></span>|<span data-ttu-id="45f01-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="45f01-134">CriticalResource</span></span>|<span data-ttu-id="45f01-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="45f01-135">FatalRuntime</span></span>|<span data-ttu-id="45f01-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="45f01-136">OrphanedLock</span></span>|<span data-ttu-id="45f01-137">Dépassement de capacité</span><span class="sxs-lookup"><span data-stu-id="45f01-137">StackOverflow</span></span>|<span data-ttu-id="45f01-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="45f01-138">AccessViolation</span></span>|<span data-ttu-id="45f01-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="45f01-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="45f01-140">X</span><span class="sxs-lookup"><span data-stu-id="45f01-140">X</span></span>|<span data-ttu-id="45f01-141">X</span><span class="sxs-lookup"><span data-stu-id="45f01-141">X</span></span>||||<span data-ttu-id="45f01-142">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-142">N/A</span></span>||  
|<span data-ttu-id="45f01-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="45f01-143">eThrowException</span></span>|<span data-ttu-id="45f01-144">X</span><span class="sxs-lookup"><span data-stu-id="45f01-144">X</span></span>|<span data-ttu-id="45f01-145">X</span><span class="sxs-lookup"><span data-stu-id="45f01-145">X</span></span>||||<span data-ttu-id="45f01-146">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="45f01-147">X</span><span class="sxs-lookup"><span data-stu-id="45f01-147">X</span></span>|<span data-ttu-id="45f01-148">X</span><span class="sxs-lookup"><span data-stu-id="45f01-148">X</span></span>||||<span data-ttu-id="45f01-149">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-149">N/A</span></span>|<span data-ttu-id="45f01-150">X</span><span class="sxs-lookup"><span data-stu-id="45f01-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="45f01-151">X</span><span class="sxs-lookup"><span data-stu-id="45f01-151">X</span></span>|<span data-ttu-id="45f01-152">X</span><span class="sxs-lookup"><span data-stu-id="45f01-152">X</span></span>||||<span data-ttu-id="45f01-153">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-153">N/A</span></span>|<span data-ttu-id="45f01-154">X</span><span class="sxs-lookup"><span data-stu-id="45f01-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="45f01-155">X</span><span class="sxs-lookup"><span data-stu-id="45f01-155">X</span></span>|<span data-ttu-id="45f01-156">X</span><span class="sxs-lookup"><span data-stu-id="45f01-156">X</span></span>||<span data-ttu-id="45f01-157">X</span><span class="sxs-lookup"><span data-stu-id="45f01-157">X</span></span>||<span data-ttu-id="45f01-158">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-158">N/A</span></span>|<span data-ttu-id="45f01-159">X</span><span class="sxs-lookup"><span data-stu-id="45f01-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="45f01-160">X</span><span class="sxs-lookup"><span data-stu-id="45f01-160">X</span></span>|<span data-ttu-id="45f01-161">X</span><span class="sxs-lookup"><span data-stu-id="45f01-161">X</span></span>||<span data-ttu-id="45f01-162">X</span><span class="sxs-lookup"><span data-stu-id="45f01-162">X</span></span>|<span data-ttu-id="45f01-163">X</span><span class="sxs-lookup"><span data-stu-id="45f01-163">X</span></span>|<span data-ttu-id="45f01-164">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-164">N/A</span></span>|<span data-ttu-id="45f01-165">X</span><span class="sxs-lookup"><span data-stu-id="45f01-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="45f01-166">X</span><span class="sxs-lookup"><span data-stu-id="45f01-166">X</span></span>|<span data-ttu-id="45f01-167">X</span><span class="sxs-lookup"><span data-stu-id="45f01-167">X</span></span>||<span data-ttu-id="45f01-168">X</span><span class="sxs-lookup"><span data-stu-id="45f01-168">X</span></span>|<span data-ttu-id="45f01-169">X</span><span class="sxs-lookup"><span data-stu-id="45f01-169">X</span></span>|<span data-ttu-id="45f01-170">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-170">N/A</span></span>|<span data-ttu-id="45f01-171">X</span><span class="sxs-lookup"><span data-stu-id="45f01-171">X</span></span>|  
|<span data-ttu-id="45f01-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="45f01-172">eFastExitProcess</span></span>|<span data-ttu-id="45f01-173">X</span><span class="sxs-lookup"><span data-stu-id="45f01-173">X</span></span>|<span data-ttu-id="45f01-174">X</span><span class="sxs-lookup"><span data-stu-id="45f01-174">X</span></span>||<span data-ttu-id="45f01-175">X</span><span class="sxs-lookup"><span data-stu-id="45f01-175">X</span></span>|<span data-ttu-id="45f01-176">X</span><span class="sxs-lookup"><span data-stu-id="45f01-176">X</span></span>|<span data-ttu-id="45f01-177">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="45f01-178">X</span><span class="sxs-lookup"><span data-stu-id="45f01-178">X</span></span>|<span data-ttu-id="45f01-179">X</span><span class="sxs-lookup"><span data-stu-id="45f01-179">X</span></span>|<span data-ttu-id="45f01-180">X</span><span class="sxs-lookup"><span data-stu-id="45f01-180">X</span></span>|<span data-ttu-id="45f01-181">X</span><span class="sxs-lookup"><span data-stu-id="45f01-181">X</span></span>|<span data-ttu-id="45f01-182">X</span><span class="sxs-lookup"><span data-stu-id="45f01-182">X</span></span>|<span data-ttu-id="45f01-183">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="45f01-184">X</span><span class="sxs-lookup"><span data-stu-id="45f01-184">X</span></span>|<span data-ttu-id="45f01-185">X</span><span class="sxs-lookup"><span data-stu-id="45f01-185">X</span></span>|<span data-ttu-id="45f01-186">X</span><span class="sxs-lookup"><span data-stu-id="45f01-186">X</span></span>|<span data-ttu-id="45f01-187">X</span><span class="sxs-lookup"><span data-stu-id="45f01-187">X</span></span>|<span data-ttu-id="45f01-188">X</span><span class="sxs-lookup"><span data-stu-id="45f01-188">X</span></span>|<span data-ttu-id="45f01-189">N/A</span><span class="sxs-lookup"><span data-stu-id="45f01-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="45f01-190">Spécifications</span><span class="sxs-lookup"><span data-stu-id="45f01-190">Requirements</span></span>  
 <span data-ttu-id="45f01-191">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45f01-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45f01-192">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="45f01-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45f01-193">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45f01-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45f01-194">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45f01-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f01-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45f01-195">See Also</span></span>  
 [<span data-ttu-id="45f01-196">EClrFailure (énumération)</span><span class="sxs-lookup"><span data-stu-id="45f01-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="45f01-197">EPolicyAction (énumération)</span><span class="sxs-lookup"><span data-stu-id="45f01-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="45f01-198">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="45f01-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="45f01-199">ICLRPolicyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="45f01-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
