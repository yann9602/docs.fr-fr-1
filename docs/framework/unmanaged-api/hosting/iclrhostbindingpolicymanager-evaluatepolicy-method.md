---
title: "ICLRHostBindingPolicyManager::EvaluatePolicy, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.EvaluatePolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7471b77deca7b66ba0a30b08ccf934704a7ac61d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="dc3ff-102">ICLRHostBindingPolicyManager::EvaluatePolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="dc3ff-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="dc3ff-103">Évalue la stratégie de liaison pour le compte de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc3ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc3ff-104">Syntax</span></span>  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc3ff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc3ff-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="dc3ff-106">[in] Une référence à l’assembly avant l’évaluation de stratégie.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="dc3ff-107">[in] Pointeur vers une mémoire tampon qui contient les données de stratégie.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="dc3ff-108">[in] La taille de la `pbApplicationPolicy` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="dc3ff-109">[out] Une référence à l’assembly après l’évaluation des nouvelles données de stratégie.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="dc3ff-110">[dans, out] Pointeur vers la taille de la mémoire tampon de référence assembly identité après l’évaluation des nouvelles données de stratégie.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="dc3ff-111">[out] Un pointeur vers une combinaison OR logique de [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) valeurs indiquant quelles stratégies ont été appliquées.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc3ff-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="dc3ff-112">Return Value</span></span>  
  
|<span data-ttu-id="dc3ff-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc3ff-113">HRESULT</span></span>|<span data-ttu-id="dc3ff-114">Description</span><span class="sxs-lookup"><span data-stu-id="dc3ff-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc3ff-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc3ff-115">S_OK</span></span>|<span data-ttu-id="dc3ff-116">L’évaluation s’est terminée correctement.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="dc3ff-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dc3ff-117">E_INVALIDARG</span></span>|<span data-ttu-id="dc3ff-118">Soit `pwzReferenceIdentity` ou `pbApplicationPolicy` est une référence null.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="dc3ff-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="dc3ff-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="dc3ff-120">`cbAppPolicySize`est trop petite.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="dc3ff-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc3ff-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc3ff-122">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc3ff-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc3ff-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc3ff-124">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-124">The call timed out.</span></span>|  
|<span data-ttu-id="dc3ff-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc3ff-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc3ff-126">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc3ff-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc3ff-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc3ff-128">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc3ff-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc3ff-129">E_FAIL</span></span>|<span data-ttu-id="dc3ff-130">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc3ff-131">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc3ff-132">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc3ff-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc3ff-133">Remarks</span></span>  
 <span data-ttu-id="dc3ff-134">Le `EvaluatePolicy` méthode permet à l’hôte pour influencer la stratégie de liaison pour mettre à jour d’assembly spécifique à l’hôte les exigences de contrôle de version.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="dc3ff-135">Le moteur de stratégie reste à l’intérieur du CLR.</span><span class="sxs-lookup"><span data-stu-id="dc3ff-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc3ff-136">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc3ff-136">Requirements</span></span>  
 <span data-ttu-id="dc3ff-137">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc3ff-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc3ff-138">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc3ff-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc3ff-139">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc3ff-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc3ff-140">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc3ff-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc3ff-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc3ff-141">See Also</span></span>  
 [<span data-ttu-id="dc3ff-142">ICLRHostBindingPolicyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="dc3ff-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
