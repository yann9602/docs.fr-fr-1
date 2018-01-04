---
title: "ICLRRuntimeHost::SetHostControl, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.SetHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9727144e9504a5a3ad7ae2529286440d07633b2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="755e9-102">ICLRRuntimeHost::SetHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="755e9-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="755e9-103">Définit le pointeur d’interface que le common language runtime (CLR) peut utiliser pour obtenir l’implémentation de l’hôte de [IHostControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="755e9-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="755e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="755e9-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="755e9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="755e9-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="755e9-106">[in] Pointeur d’interface vers l’implémentation de l’hôte de [IHostControl (Interface)](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="755e9-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="755e9-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="755e9-107">Return Value</span></span>  
  
|<span data-ttu-id="755e9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="755e9-108">HRESULT</span></span>|<span data-ttu-id="755e9-109">Description</span><span class="sxs-lookup"><span data-stu-id="755e9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="755e9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="755e9-110">S_OK</span></span>|<span data-ttu-id="755e9-111">`SetHostControl`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="755e9-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="755e9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="755e9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="755e9-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="755e9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="755e9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="755e9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="755e9-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="755e9-115">The call timed out.</span></span>|  
|<span data-ttu-id="755e9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="755e9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="755e9-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="755e9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="755e9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="755e9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="755e9-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="755e9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="755e9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="755e9-120">E_FAIL</span></span>|<span data-ttu-id="755e9-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="755e9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="755e9-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="755e9-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="755e9-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="755e9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="755e9-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="755e9-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="755e9-125">Le CLR a déjà été initialisé.</span><span class="sxs-lookup"><span data-stu-id="755e9-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="755e9-126">Notes</span><span class="sxs-lookup"><span data-stu-id="755e9-126">Remarks</span></span>  
 <span data-ttu-id="755e9-127">Vous devez appeler `SetHostControl` avant que le CLR est initialisé, autrement dit, avant d’appeler [méthode Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) de la [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="755e9-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="755e9-128">Il est recommandé d’appeler `SetHostControl` immédiatement après l’appel [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou [fonction CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="755e9-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="755e9-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="755e9-129">Requirements</span></span>  
 <span data-ttu-id="755e9-130">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="755e9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="755e9-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="755e9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="755e9-132">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="755e9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="755e9-133">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="755e9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755e9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="755e9-134">See Also</span></span>  
 [<span data-ttu-id="755e9-135">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="755e9-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="755e9-136">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="755e9-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
