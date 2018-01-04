---
title: "ICLRRuntimeHost::UnloadAppDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.UnloadAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 481f701ae4db15b66596c3af89c2e7aff7a28f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="85c35-102">ICLRRuntimeHost::UnloadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="85c35-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="85c35-103">Décharge managé <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.</span><span class="sxs-lookup"><span data-stu-id="85c35-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85c35-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85c35-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85c35-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="85c35-106">[in] L’identificateur numérique du domaine d’application à décharger.</span><span class="sxs-lookup"><span data-stu-id="85c35-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="85c35-107">[in] `true` pour indiquer que le common language runtime (CLR) doit attendre jusqu'à ce qu’il a terminé l’exécution du thread actuel de l’application avant de tenter de décharger le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="85c35-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85c35-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="85c35-108">Return Value</span></span>  
  
|<span data-ttu-id="85c35-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85c35-109">HRESULT</span></span>|<span data-ttu-id="85c35-110">Description</span><span class="sxs-lookup"><span data-stu-id="85c35-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85c35-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="85c35-111">S_OK</span></span>|<span data-ttu-id="85c35-112">`UnloadAppDomain`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="85c35-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="85c35-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85c35-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85c35-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="85c35-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85c35-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85c35-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85c35-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="85c35-116">The call timed out.</span></span>|  
|<span data-ttu-id="85c35-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85c35-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85c35-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="85c35-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85c35-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85c35-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85c35-120">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="85c35-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85c35-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85c35-121">E_FAIL</span></span>|<span data-ttu-id="85c35-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="85c35-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85c35-123">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="85c35-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85c35-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="85c35-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85c35-125">Notes</span><span class="sxs-lookup"><span data-stu-id="85c35-125">Remarks</span></span>  
 <span data-ttu-id="85c35-126">Vous pouvez obtenir l’identificateur numérique du domaine d’application dans lequel le thread en cours s’exécute en appelant [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="85c35-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="85c35-127">Cet identificateur correspond à la <xref:System.AppDomain.Id%2A> propriété managé <xref:System.AppDomain> type.</span><span class="sxs-lookup"><span data-stu-id="85c35-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c35-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="85c35-128">Requirements</span></span>  
 <span data-ttu-id="85c35-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85c35-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c35-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85c35-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85c35-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85c35-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85c35-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c35-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c35-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85c35-133">See Also</span></span>  
 [<span data-ttu-id="85c35-134">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="85c35-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
