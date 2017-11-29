---
title: "ICLRGCManager2::SetGCStartupLimitsEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73f5678008354b312964f0cb32d768d36a641fd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="7dd4d-102">ICLRGCManager2::SetGCStartupLimitsEx, méthode</span><span class="sxs-lookup"><span data-stu-id="7dd4d-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="7dd4d-103">Définit la taille d’un segment de garbage collection et la taille maximale de la génération du système de garbage collection 0.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dd4d-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dd4d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7dd4d-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="7dd4d-106">[in] La taille spécifiée d’un segment de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="7dd4d-107">La taille du segment minimale est de 4 Mo.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="7dd4d-108">Segments peuvent être augmentés dans des incréments de 1 Mo ou supérieure.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="7dd4d-109">[in] La taille maximale spécifiée pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="7dd4d-110">La taille minimum de la génération 0 est de 64 Ko.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dd4d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7dd4d-111">Return Value</span></span>  
  
|<span data-ttu-id="7dd4d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7dd4d-112">HRESULT</span></span>|<span data-ttu-id="7dd4d-113">Description</span><span class="sxs-lookup"><span data-stu-id="7dd4d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7dd4d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7dd4d-114">S_OK</span></span>|<span data-ttu-id="7dd4d-115">`SetGCStartupLimitsEx`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="7dd4d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7dd4d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7dd4d-117">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7dd4d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7dd4d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7dd4d-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-119">The call timed out.</span></span>|  
|<span data-ttu-id="7dd4d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7dd4d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7dd4d-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7dd4d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7dd4d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7dd4d-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7dd4d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7dd4d-124">E_FAIL</span></span>|<span data-ttu-id="7dd4d-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7dd4d-126">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7dd4d-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dd4d-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="7dd4d-128">Remarks</span></span>  
 <span data-ttu-id="7dd4d-129">Les valeurs qui `SetGCStartupLimitsEx` ensembles peuvent être spécifiés uniquement avant le démarrage de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="7dd4d-130">Appels ultérieurs à `SetGCStartupLimitsEx` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="7dd4d-131">Pour définir un paramètre sans affecter l’autre, spécifiez 0 (zéro) pour le paramètre que vous ne souhaitez pas modifier.</span><span class="sxs-lookup"><span data-stu-id="7dd4d-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd4d-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7dd4d-132">Requirements</span></span>  
 <span data-ttu-id="7dd4d-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd4d-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd4d-134">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7dd4d-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7dd4d-135">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7dd4d-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7dd4d-136">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd4d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd4d-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dd4d-137">See Also</span></span>  
 [<span data-ttu-id="7dd4d-138">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="7dd4d-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="7dd4d-139">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="7dd4d-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="7dd4d-140">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="7dd4d-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="7dd4d-141">ICLRGCManager2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="7dd4d-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
