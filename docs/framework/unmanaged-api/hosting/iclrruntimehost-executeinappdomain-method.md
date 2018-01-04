---
title: "ICLRRuntimeHost::ExecuteInAppDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8c540c9618655e6df30ad253e0c4cccdf6624e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="2635f-102">ICLRRuntimeHost::ExecuteInAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="2635f-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="2635f-103">Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="2635f-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2635f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2635f-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2635f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2635f-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="2635f-106">[in] ID numérique de la <xref:System.AppDomain> dans lequel exécuter la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2635f-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="2635f-107">[in] Un pointeur vers la fonction à exécuter dans le texte spécifié <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="2635f-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="2635f-108">[in] Pointeur vers la mémoire allouée par l’appelant opaque.</span><span class="sxs-lookup"><span data-stu-id="2635f-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="2635f-109">Ce paramètre est passé par le common language runtime (CLR) au rappel de domaine.</span><span class="sxs-lookup"><span data-stu-id="2635f-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="2635f-110">Il n’est pas mémoire du segment de mémoire gérée par le runtime ; l’allocation et la durée de vie de cette mémoire sont contrôlées par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2635f-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2635f-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2635f-111">Return Value</span></span>  
  
|<span data-ttu-id="2635f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2635f-112">HRESULT</span></span>|<span data-ttu-id="2635f-113">Description</span><span class="sxs-lookup"><span data-stu-id="2635f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2635f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2635f-114">S_OK</span></span>|<span data-ttu-id="2635f-115">`ExecuteInAppDomain`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2635f-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="2635f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2635f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2635f-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2635f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2635f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2635f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2635f-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2635f-119">The call timed out.</span></span>|  
|<span data-ttu-id="2635f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2635f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2635f-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2635f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2635f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2635f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2635f-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2635f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2635f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2635f-124">E_FAIL</span></span>|<span data-ttu-id="2635f-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2635f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2635f-126">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2635f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2635f-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2635f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2635f-128">Notes</span><span class="sxs-lookup"><span data-stu-id="2635f-128">Remarks</span></span>  
 <span data-ttu-id="2635f-129">`ExecuteInAppDomain`permet à l’hôte d’exercer un contrôle sur lequel gérés <xref:System.AppDomain> la méthode managée spécifiée doit être exécutée dans.</span><span class="sxs-lookup"><span data-stu-id="2635f-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="2635f-130">Vous pouvez obtenir la valeur d’identificateur d’un domaine d’application, qui correspond à la valeur de la <xref:System.AppDomain.Id%2A> propriété, en appelant [GetCurrentAppDomainId, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="2635f-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2635f-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2635f-131">Requirements</span></span>  
 <span data-ttu-id="2635f-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2635f-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2635f-133">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2635f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2635f-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2635f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2635f-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2635f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2635f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2635f-136">See Also</span></span>  
 [<span data-ttu-id="2635f-137">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="2635f-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
