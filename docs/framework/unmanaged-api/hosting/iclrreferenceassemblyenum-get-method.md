---
title: "ICLRReferenceAssemblyEnum::Get, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRReferenceAssemblyEnum.Get
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab64f7983b5825505421e7bfbcf6866004778a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="f5bbd-102">ICLRReferenceAssemblyEnum::Get, méthode</span><span class="sxs-lookup"><span data-stu-id="f5bbd-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="f5bbd-103">Obtient l’identité d’assembly à l’index fourni.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5bbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5bbd-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5bbd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5bbd-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="f5bbd-106">[in] Index de base zéro de l’identité d’assembly à retourner.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f5bbd-107">[out] Une mémoire tampon qui contient les données d’identité.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f5bbd-108">[dans, out] La taille de la `pwzBuffer` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5bbd-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f5bbd-109">Return Value</span></span>  
  
|<span data-ttu-id="f5bbd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5bbd-110">HRESULT</span></span>|<span data-ttu-id="f5bbd-111">Description</span><span class="sxs-lookup"><span data-stu-id="f5bbd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5bbd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5bbd-112">S_OK</span></span>|<span data-ttu-id="f5bbd-113">`Get`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="f5bbd-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f5bbd-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f5bbd-115">`pwzBuffer`est trop petite.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f5bbd-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="f5bbd-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="f5bbd-117">L’énumération ne contient aucun élément plus.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="f5bbd-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5bbd-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5bbd-119">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5bbd-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5bbd-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5bbd-121">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-121">The call timed out.</span></span>|  
|<span data-ttu-id="f5bbd-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5bbd-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5bbd-123">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5bbd-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5bbd-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5bbd-125">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5bbd-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5bbd-126">E_FAIL</span></span>|<span data-ttu-id="f5bbd-127">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5bbd-128">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5bbd-129">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5bbd-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="f5bbd-130">Remarks</span></span>  
 <span data-ttu-id="f5bbd-131">`Get`est généralement appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-131">`Get` is typically called twice.</span></span> <span data-ttu-id="f5bbd-132">Le premier appel fournit une valeur null pour `pwzBuffer`et définit `pcchBufferSize` à la taille appropriée pour `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="f5bbd-133">Le deuxième appel fournit une taille appropriée `pwzBuffer`et contient les données d’identité assembly canonique à l’achèvement.</span><span class="sxs-lookup"><span data-stu-id="f5bbd-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5bbd-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f5bbd-134">Requirements</span></span>  
 <span data-ttu-id="f5bbd-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5bbd-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bbd-136">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5bbd-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5bbd-137">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5bbd-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5bbd-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bbd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bbd-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5bbd-139">See Also</span></span>  
 [<span data-ttu-id="f5bbd-140">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="f5bbd-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f5bbd-141">ICLRReferenceAssemblyEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="f5bbd-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
