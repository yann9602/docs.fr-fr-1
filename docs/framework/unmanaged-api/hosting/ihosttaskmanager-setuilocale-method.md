---
title: "IHostTaskManager::SetUILocale, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c29687d430187577ac25d8d2a007785632989ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="ed933-102">IHostTaskManager::SetUILocale, méthode</span><span class="sxs-lookup"><span data-stu-id="ed933-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="ed933-103">Avertit l’hôte que le common language runtime (CLR) a modifié les paramètres régionaux de l’interface (interface utilisateur) utilisateur ou la culture, sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ed933-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed933-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed933-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed933-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed933-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="ed933-106">[in] La valeur d’identificateur de paramètres régionaux qui mappe à la culture géographique qui vient d’être attribué et la langue.</span><span class="sxs-lookup"><span data-stu-id="ed933-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed933-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ed933-107">Return Value</span></span>  
  
|<span data-ttu-id="ed933-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed933-108">HRESULT</span></span>|<span data-ttu-id="ed933-109">Description</span><span class="sxs-lookup"><span data-stu-id="ed933-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed933-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed933-110">S_OK</span></span>|<span data-ttu-id="ed933-111">`SetUILocale`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ed933-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="ed933-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed933-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed933-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="ed933-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed933-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed933-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed933-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="ed933-115">The call timed out.</span></span>|  
|<span data-ttu-id="ed933-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed933-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed933-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="ed933-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed933-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed933-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed933-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="ed933-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed933-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed933-120">E_FAIL</span></span>|<span data-ttu-id="ed933-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ed933-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed933-122">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ed933-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed933-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed933-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ed933-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ed933-124">E_NOTIMPL</span></span>|<span data-ttu-id="ed933-125">L’ordinateur hôte n’autorise pas le code utilisateur managé de modifier la culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ed933-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed933-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="ed933-126">Remarks</span></span>  
 <span data-ttu-id="ed933-127">Le runtime appelle `SetUILocale` lorsque la valeur de la <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> propriété est modifiée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="ed933-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="ed933-128">Cette méthode fournit une opportunité pour l’ordinateur hôte exécuter des mécanismes que peut-être pour la synchronisation des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="ed933-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="ed933-129">Si un ordinateur hôte n’autorise pas les paramètres régionaux de l’interface utilisateur à partir de code managé ou n’implémente pas de mécanisme pour synchroniser les paramètres régionaux, elle doit retourner E_NOTIMPL à partir de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="ed933-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed933-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ed933-130">Requirements</span></span>  
 <span data-ttu-id="ed933-131">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed933-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed933-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed933-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed933-133">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed933-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed933-134">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed933-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed933-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed933-135">See Also</span></span>  
 [<span data-ttu-id="ed933-136">ICLRTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="ed933-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ed933-137">ICLRTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="ed933-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ed933-138">IHostTask (Interface)</span><span class="sxs-lookup"><span data-stu-id="ed933-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ed933-139">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="ed933-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="ed933-140">SetLocale (méthode)</span><span class="sxs-lookup"><span data-stu-id="ed933-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
