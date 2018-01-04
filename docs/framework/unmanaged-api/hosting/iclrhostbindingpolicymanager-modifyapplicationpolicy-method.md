---
title: "ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 018dc40895a79788a9eef20082d764db0b2265c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="f8158-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="f8158-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="f8158-103">Modifie la stratégie de liaison pour l’assembly spécifié et crée une nouvelle version de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="f8158-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8158-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8158-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8158-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8158-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="f8158-106">[in] L’identité de l’assembly à modifier.</span><span class="sxs-lookup"><span data-stu-id="f8158-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="f8158-107">[in] La nouvelle identité de l’assembly modifié.</span><span class="sxs-lookup"><span data-stu-id="f8158-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="f8158-108">[in] Pointeur vers une mémoire tampon qui contient les données de stratégie de liaison pour l’assembly à modifier.</span><span class="sxs-lookup"><span data-stu-id="f8158-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="f8158-109">[in] La taille de la stratégie de liaison à remplacer.</span><span class="sxs-lookup"><span data-stu-id="f8158-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="f8158-110">[in] Combinaison OR logique de [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) valeurs indiquant le contrôle de la redirection.</span><span class="sxs-lookup"><span data-stu-id="f8158-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="f8158-111">[out] Pointeur vers une mémoire tampon qui contient les nouvelles données de stratégie de liaison.</span><span class="sxs-lookup"><span data-stu-id="f8158-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="f8158-112">[dans, out] Pointeur vers la taille de la nouvelle mémoire tampon de stratégie de liaison.</span><span class="sxs-lookup"><span data-stu-id="f8158-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8158-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8158-113">Return Value</span></span>  
  
|<span data-ttu-id="f8158-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8158-114">HRESULT</span></span>|<span data-ttu-id="f8158-115">Description</span><span class="sxs-lookup"><span data-stu-id="f8158-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8158-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8158-116">S_OK</span></span>|<span data-ttu-id="f8158-117">La stratégie a été modifiée avec succès.</span><span class="sxs-lookup"><span data-stu-id="f8158-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="f8158-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f8158-118">E_INVALIDARG</span></span>|<span data-ttu-id="f8158-119">`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` était une référence null.</span><span class="sxs-lookup"><span data-stu-id="f8158-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="f8158-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f8158-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f8158-121">`pbNewApplicationPolicy`est trop petite.</span><span class="sxs-lookup"><span data-stu-id="f8158-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="f8158-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8158-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8158-123">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="f8158-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8158-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8158-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8158-125">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f8158-125">The call timed out.</span></span>|  
|<span data-ttu-id="f8158-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8158-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8158-127">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f8158-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8158-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8158-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8158-129">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="f8158-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8158-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8158-130">E_FAIL</span></span>|<span data-ttu-id="f8158-131">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f8158-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8158-132">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f8158-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8158-133">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8158-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8158-134">Notes</span><span class="sxs-lookup"><span data-stu-id="f8158-134">Remarks</span></span>  
 <span data-ttu-id="f8158-135">Le `ModifyApplicationPolicy` méthode peut être appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="f8158-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="f8158-136">Le premier appel doit fournir une valeur null pour le `pbNewApplicationPolicy` paramètre.</span><span class="sxs-lookup"><span data-stu-id="f8158-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="f8158-137">Cet appel retournera avec la valeur nécessaire pour `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="f8158-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="f8158-138">Le deuxième appel doit fournir cette valeur pour `pcbNewAppPolicySize`et pointer vers un mémoire tampon de cette taille pour `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="f8158-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8158-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8158-139">Requirements</span></span>  
 <span data-ttu-id="f8158-140">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8158-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8158-141">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8158-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8158-142">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8158-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8158-143">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8158-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8158-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8158-144">See Also</span></span>  
 [<span data-ttu-id="f8158-145">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="f8158-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
