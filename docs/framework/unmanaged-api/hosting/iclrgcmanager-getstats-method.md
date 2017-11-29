---
title: "ICLRGCManager::GetStats, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06d52bd0348e4667f1e3ec43a371021922f12ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="b9239-102">ICLRGCManager::GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="b9239-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="b9239-103">Obtient un jeu de statistiques actuelles concernant le système de garbage collection du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b9239-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9239-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9239-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9239-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9239-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="b9239-106">[dans, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance qui contient les statistiques demandées.</span><span class="sxs-lookup"><span data-stu-id="b9239-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9239-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b9239-107">Return Value</span></span>  
  
|<span data-ttu-id="b9239-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9239-108">HRESULT</span></span>|<span data-ttu-id="b9239-109">Description</span><span class="sxs-lookup"><span data-stu-id="b9239-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9239-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9239-110">S_OK</span></span>|<span data-ttu-id="b9239-111">`GetStats`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b9239-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="b9239-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9239-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9239-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="b9239-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9239-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9239-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9239-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b9239-115">The call timed out.</span></span>|  
|<span data-ttu-id="b9239-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9239-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9239-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b9239-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9239-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9239-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9239-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="b9239-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9239-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9239-120">E_FAIL</span></span>|<span data-ttu-id="b9239-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b9239-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9239-122">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b9239-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9239-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9239-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9239-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9239-124">Remarks</span></span>  
 <span data-ttu-id="b9239-125">Le CLR calcule et retourne uniquement les statistiques qui sont spécifiées par le `Flags` champ `pStats`.</span><span class="sxs-lookup"><span data-stu-id="b9239-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="b9239-126">Définir le `Flags` une ou plusieurs valeurs de champ la [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) énumération pour spécifier les statistiques de la [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure doivent être définies.</span><span class="sxs-lookup"><span data-stu-id="b9239-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="b9239-127">Un exemple de l’utilisation est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b9239-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b9239-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b9239-128">Requirements</span></span>  
 <span data-ttu-id="b9239-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9239-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9239-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b9239-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9239-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9239-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9239-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9239-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9239-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9239-133">See Also</span></span>  
 [<span data-ttu-id="b9239-134">Gestion automatique de la mémoire</span><span class="sxs-lookup"><span data-stu-id="b9239-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="b9239-135">COR_GC_STATS (Structure)</span><span class="sxs-lookup"><span data-stu-id="b9239-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="b9239-136">COR_GC_STAT_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="b9239-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="b9239-137">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="b9239-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="b9239-138">ICLRControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="b9239-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b9239-139">ICLRGCManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="b9239-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="b9239-140">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="b9239-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="b9239-141">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="b9239-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b9239-142">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="b9239-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
