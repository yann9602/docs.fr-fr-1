---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5456d2747bb9c55d73fcc377036f5df1e8b10db0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="56cc7-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="56cc7-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="56cc7-103">Obtient l’identité d’assembly une liaison de données pour l’assembly sur le chemin d’accès de fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="56cc7-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56cc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56cc7-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56cc7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56cc7-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="56cc7-106">[in] Le chemin d’accès au fichier à évaluer.</span><span class="sxs-lookup"><span data-stu-id="56cc7-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="56cc7-107">[in] Une valeur de la [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) énumération qui indique le type de l’identité d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="56cc7-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="56cc7-108">Fourni pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="56cc7-108">Provided for future extensibility.</span></span> <span data-ttu-id="56cc7-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur qui prend en charge par le common language runtime (CLR) version 2.0.</span><span class="sxs-lookup"><span data-stu-id="56cc7-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="56cc7-110">[out] Une mémoire tampon qui contient les données d’identité assembly opaque.</span><span class="sxs-lookup"><span data-stu-id="56cc7-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="56cc7-111">[dans, out] Un pointeur vers la taille de `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="56cc7-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56cc7-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="56cc7-112">Return Value</span></span>  
  
|<span data-ttu-id="56cc7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56cc7-113">HRESULT</span></span>|<span data-ttu-id="56cc7-114">Description</span><span class="sxs-lookup"><span data-stu-id="56cc7-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56cc7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="56cc7-115">S_OK</span></span>|<span data-ttu-id="56cc7-116">La méthode a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="56cc7-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="56cc7-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="56cc7-117">E_INVALIDARG</span></span>|<span data-ttu-id="56cc7-118">Fourni `pwzFilePath` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="56cc7-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="56cc7-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="56cc7-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="56cc7-120">La taille de `pwzBuffer` est trop petite.</span><span class="sxs-lookup"><span data-stu-id="56cc7-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="56cc7-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56cc7-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56cc7-122">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="56cc7-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56cc7-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56cc7-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56cc7-124">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="56cc7-124">The call timed out.</span></span>|  
|<span data-ttu-id="56cc7-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56cc7-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56cc7-126">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="56cc7-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56cc7-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56cc7-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56cc7-128">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="56cc7-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56cc7-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56cc7-129">E_FAIL</span></span>|<span data-ttu-id="56cc7-130">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="56cc7-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56cc7-131">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="56cc7-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56cc7-132">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="56cc7-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56cc7-133">Notes</span><span class="sxs-lookup"><span data-stu-id="56cc7-133">Remarks</span></span>  
 <span data-ttu-id="56cc7-134">`GetBindingIdentityFromFile`est généralement appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="56cc7-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="56cc7-135">Le premier appel fournit une valeur null pour `pwzBuffer`, et la méthode retourne la taille appropriée dans `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="56cc7-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="56cc7-136">Le deuxième appel fournit une mémoire tampon allouée convenablement, et la méthode retourne les données de mémoire tampon à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="56cc7-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56cc7-137">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56cc7-137">Requirements</span></span>  
 <span data-ttu-id="56cc7-138">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56cc7-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56cc7-139">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56cc7-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56cc7-140">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56cc7-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56cc7-141">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56cc7-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56cc7-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56cc7-142">See Also</span></span>  
 [<span data-ttu-id="56cc7-143">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="56cc7-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="56cc7-144">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="56cc7-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="56cc7-145">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="56cc7-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
