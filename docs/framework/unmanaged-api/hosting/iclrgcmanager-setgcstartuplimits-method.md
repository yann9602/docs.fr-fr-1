---
title: "ICLRGCManager::SetGCStartupLimits, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1fd0c31fd6f988d4ee36bfe140b95ec258d4214e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="00421-102">ICLRGCManager::SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="00421-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="00421-103">Définit la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0.</span><span class="sxs-lookup"><span data-stu-id="00421-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00421-104">En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez définir la taille du segment et taille maximale de génération 0 pour les valeurs supérieure `DWORD` à l’aide de la [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="00421-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00421-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00421-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00421-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00421-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="00421-107">[in] La taille spécifiée d’un segment de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="00421-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="00421-108">La taille du segment minimale est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="00421-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="00421-109">Segments peuvent être augmentés dans des incréments de 1 Mo ou supérieure.</span><span class="sxs-lookup"><span data-stu-id="00421-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="00421-110">[in] La taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="00421-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="00421-111">La taille minimum de la génération 0 est de 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="00421-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00421-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="00421-112">Return Value</span></span>  
  
|<span data-ttu-id="00421-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00421-113">HRESULT</span></span>|<span data-ttu-id="00421-114">Description</span><span class="sxs-lookup"><span data-stu-id="00421-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00421-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="00421-115">S_OK</span></span>|<span data-ttu-id="00421-116">`SetGCStartupLimits`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="00421-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="00421-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00421-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00421-118">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="00421-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00421-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00421-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00421-120">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="00421-120">The call timed out.</span></span>|  
|<span data-ttu-id="00421-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00421-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00421-122">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="00421-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00421-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00421-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00421-124">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="00421-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00421-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00421-125">E_FAIL</span></span>|<span data-ttu-id="00421-126">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="00421-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00421-127">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="00421-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00421-128">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="00421-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00421-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="00421-129">Remarks</span></span>  
 <span data-ttu-id="00421-130">Les valeurs qui `SetGCStartupLimits` jeux peuvent être spécifiés qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="00421-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="00421-131">Appels ultérieurs à `SetGCStartupLimits` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="00421-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00421-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="00421-132">Requirements</span></span>  
 <span data-ttu-id="00421-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00421-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00421-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00421-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00421-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00421-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00421-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00421-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00421-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00421-137">See Also</span></span>  
 [<span data-ttu-id="00421-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="00421-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="00421-139">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="00421-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="00421-140">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="00421-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="00421-141">ICLRGCManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="00421-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
